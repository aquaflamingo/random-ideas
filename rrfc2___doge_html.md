# RRFC2 - Doge HTML
Part of the reason the early internet was fun was because it was less serious. An example of this nostalgia is Dogecoin, the fun meme cryptocurrency coin created as a satirical commentary about cryptocurrency. Despite it's best efforts to be a joke, the irony of Dogecoin's success is its derivative "meme value", that is, its capacity as a phenomenon to be easily interpreted, shared, remixed and reshared (see [Image Macro](https://en.wikipedia.org/wiki/Image_macro)). 

As a fun idea, what if there was a parallel application protocol, call it DogeNet or DogeHTTP , wherein webpages would be written and transferred in a novel markup format inspired by the original quirky Doge speak macro.

![Original Doge Meme](https://upload.wikimedia.org/wikipedia/en/5/5f/Original_Doge_meme.jpg) 

In other words, a new "parallel" application layer protocol `doge://` that re-skins the web as it were using Doge theme entirely for fun. 

[How to does a browser render](https://medium.com/jspoint/how-the-browser-renders-a-web-page-dom-cssom-and-rendering-df10531c9969)

## Components
- **DHTML**: Doge Hypertext Markup Language, a markup language that uses `<wow>`,`<very>`, `<such>` tags to markup the content. *Everything* is comic sans formatted, i.e. there is no style sheets and no way to turn off this formatting.

- **WowBrowser**: A new browser built from scratch that interprets only DHTML content `text/dhtml` via `doge://` links

- **MuchPayments**: Built in Dogecoin payment API using the [402 Payment Required HTTP Protocol](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/402)

