**API Key**

API Key is a secret key that is used to authenticate your identity to us at the time of API call invocation. This is a long alpha numeric string. 

Example: AC42FF085D42479CBFA0C25BE6F004AE

* You can have multiple API Keys at the same time
* You can disable or enable API Keys
* It is always a good practice to rotate API Keys

**Storage**

It is important that API Key be protected. Best practices for storage & access of API Key:

* Do not commit the API Key to your code
* Do not package the API Key to your Android/iOS application
* API Key must not be stored in a publicly accessible system
* Only your production servers must be able to read the API Key
* If you are storing the API Key in database, then control the access to that table to only administrators & servers.
* Using a keystore is the best strategy to store such secrets
* Have ***separate API Keys*** for staging & production

To disable/enable the API Keys or to create new API Keys, please visit [Settings page](https://merchant.juspay.in/settings/api-keys) in [JusPay Merchant Dashboard](https://merchant.juspay.in)

