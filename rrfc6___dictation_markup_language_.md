# RRFC6 - Dictation Markup Language - DiML
Although Computer Vision has progressed a long way to day, there is still limitations in it's abilities for document text detection.  Handwriting transcription, for example, is still difficult especially for individuals who have poor pensmenship. Based on some experiments with [Minimal Google Cloud Vision APIs](https://github.com/aquaflamingo/gcloud-minimal-vision-apis-text-detection), some handwritten samples are relatively unrecognizable by the algorithms still. Although this is really a human problem (i.e. improve your damn pensmenship), handwriting is a fairly ingrained trait that is hard to improve over time. What's more, if an individual possess hundreds of hand written notes, improving one's handwriting ex post-facto, does little. One final lacking capability is that Cloud Vision API and OCR providers struggle with structured notes that use headings, bullets and sub points. 

Unfortunately, one is at an impasse if they are desiring to some how digitize hundreds to thousands of handwritten notes over the years: 
1. Manual transcribe via typing (Could take a while)
2. Use OCR and try to decipher results (Probably just as difficult as point 1 and would take more time)

The basic problem seems to be the "bulk transcription" from paper format to digital. The main avenue described in the previous paragraphs has via image capture format (i.e. snapping a picture), which is the "easiest way" as far as on could tell. However, one interesting observation is that certain dictation and text-to-speech engines such as Apple's dictation keyboard are fairly excellent once trained sufficiently. Instead of exporting the written data via image capture what about transcription via dictation? 

The main issue one might run into is related to conserving structured notes (i.e. headings, points, etcetera). Borrowing some inspiration from Markdown's use of common characters to indicate styling and basic token processing, perhaps we could devise a simple "Dictation Markup Language" or DML for short.

## Specification
To begin, we need four basic content elements:
1. **Section** which indicate breaks between completely different content
2. **Heading** which indicate unique content within a section
3. **Point** which indicate bullet point items under a heading; and
4. **Subpoint** which elaborate on a particular point
	1. In reality this is not necessary for a basic prototype but is a nice to have

Next, we have the issue of translating the above content elements into *easy to capture* keywords or tokens for the dictation engine. Anecdotal experiments indicate a combination of basic words and grammatical symbols ensure high quality slicing between the keyword and "real content" . Consider:

```diml

'section' -> is the keyword for a new section
'q.' -> is the keyword for a new heading ("q" has too much collision with common words)
'p.' -> is the keyword for a new point
'sp.' -> is the keyword for a new subpoint
```

Finally, there is the need for a `stop` token to indicate breakage between the keyword elements. For brevity and content collision avoidance perhaps the semi-colon `;` character. 

A raw DiML payload would look like the following captured from a dictation session from book notes for [King, Warrior, Magician, Lover: Rediscovering the Archetypes of the Mature Masculine](https://archive.org/details/kingwarriormagic00moor_1):
```diml
section; Q. King warrior magician lover; Q. Male psychology; P. We do not want to destroy our boyhood pyramids – we want to grow them; P. The mature male archetypes all go together the king the magician the warrior and the lover; P. Think of archetypes like chairs at a board meeting; section; Q. The king archetype; P. Organizing the ordinary and fertility/blessing; P. Believed to have to follow the right order the Tao; P. Keeps harmony in the spiritual world i.e. the unconscious; SP. Murdoch slaying the dragon in Babylon Mattia; SP. Young men are starving for this blessing from older men - the king energy; P. The voice of calm rationality, minimizing punishment and maximizing praise; 
```

The above is raw, but, it would be trivial to derive a token parsing engine which uses the `DiML` keywords above to parse the payload into a basic markdown file:

```markdown
# Section
## King Warrior Magician Lover
## Male Psychology
* We do not want to destroy our boyhood pyramids - we want to grow them
* The mature male archetypes all go together the king the magician the warrior and lover
* #.. etcetera
```

It isn't a massive improvement but it is incrementally better than manual transcription. There is a marginal time investment in the dictation phase of content, as well as proof reading, but perhaps it could be slightly faster and automated in comparison to raw transcription. 

