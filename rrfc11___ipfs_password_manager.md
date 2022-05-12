# RRFC11 - IPFS Password Manager
The market for password managers is rather saturated as the obstacles to build a "generally working" application are low. However, several high end market participates such as 1Password have normalized zero-knowledge policies and sharing of private key material client side with the caveat: "you lose, it ya lost it". This is beneficial because, in theory if no copy of the private key material is made only the client's passphrase is capable of unencrypting the database blob.

In general a "cloud" password manager `$COMPANY` probably follows roughly this algorithm for their core app loop:

```

Start: 
- Initialize data blob for password storage
- Generate symmetric encryption key with passphrase
- Encrypt data blob with encryption key

Run:
- $APP (oneof<CLI,WWW,iOS,Android,Linux> downloads encrypted data blob 
- $APP prompts for client secret
- $APP decrypts data blob
- $APP updates data blob with new entries
- $APP encrypts mutated data blob
- $APP uploads encrypted mutated data blob to $COMPANYBACKEND, which stores blob in $CLOUD_PROVIDER

... repeat
```

In this scenario the failure modes are the following:
- `$CLOUD_PROVIDER` goes out of business
- `$CLOUD_PROVIDER` denies service to `$COMPANY`
- `$COMPANY` goes out of business
- `$COMPANY` messes up client side encryption, storage or backups for encrypted data blobs

<img width="862" alt="image" src="https://user-images.githubusercontent.com/16901597/167970935-6b44b0eb-fbc7-4acf-8613-44292acd9b7c.png">

![Cloud password manager](./images/rrfc11/cloud-password-manager)

Given that most people use Password Managers for life once signed up, there could be an opportunity for long-term design by using IPFS instead of `$CLOUD_PROVIDER` and `$COMPANYBACKEND`.

## Example:
- Encrypt data blob for passwords and store on IPFS 
- Negotiate long-term storage deals with IPFS Storage providers 
- Build thin backend to proxy calls to IPFS instead of `$CLOUD_PROVIDER`
- User can import and export their password data in a frontend agnostic way to any _n_ number of password manager `$APP` frontends. 
- 
<img width="697" alt="image" src="https://user-images.githubusercontent.com/16901597/167970923-8238fb73-ff77-4cf9-9a4d-2ba89955beb0.png">

![IPFS password manager](./images/rrfc11/ipfs-password-manager.png)

## Issues:
* Storing a secrets db, even though encrypted, in an open network forever seems like a bad idea 

