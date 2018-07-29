We added an option to use encrypted SDK_IDs when sending events via the [Web SDK](https://github.com/optimove-tech/Web-SDK-Integration-Guide), [iOS SDK](https://github.com/optimove-tech/iOS-SDK-Integration-Guide) or [Android SDK](https://github.com/optimove-tech/Android-SDK-Integration-Guide), to gain an extra level of security. This will prevent other people from sending irrelevant/rogue events to us using plaintext SDK_IDs (this can be used to generate blasts of event calls that will result in actual campaigns, for example).

This functionality applies only to SDK_IDs that are generated on the server side. It does not apply to VisitorIDs that are generated on the client side. 

## **In order to implement:**
1.	Request an encryption key from the Optimove Product Integration Team
2.	Implement SDK_IDs encryption on the customer server side, as shows in the encryption examples:
* [.NET](https://github.com/optimove-tech/Reporting-Encrypted-CustomerID/tree/master/SDKEncryption)
* [NodeJS](https://github.com/optimove-tech/Reporting-Encrypted-CustomerID/tree/master/JSEncryption/EncryptionJSApp)
* [PHP](https://github.com/optimoveproductintegration/Reporting-Encrypted-CustomerID/tree/master/phpEncryption)

>**Note:** 
> You can use additional server-side programming languages. The above are only examples.

3.	Use the encrypted SDK_IDs in all SDK calls implemented
5.	Optimove will perform the decryption and process the events

## **The encryption method we use:**
* Authenticated encryption using CBC encryption with initialization vector and HMAC for the authenticating the message.
* HMAC – Hash-based message authentication code https://en.wikipedia.org/wiki/Hash-based_message_authentication_code 
* Before encryption, the SDK_IDs length supports up to 90 characters only.
