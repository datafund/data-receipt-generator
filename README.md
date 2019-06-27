# Consent Generator

[React](https://facebook.github.io/react) plugin for generating a Consent Receipt (CR) JSON server-side. 

Quick Use
-----------------------
Download package using [npm](https://www.npmjs.com/):

    $ npm install --save @datafund/consent-generator
                                  

<br/>Import package to your React app:
```javascript
import { ConsentGenerator } from 'consent-generator';
```

<br/>Prepare Consent Receipt data:
 ```javascript  
let formData = {
    "version": "Kantara_v1.1",
     "consentTimestamp": 1559734117,
     "collectionMethod": "Web form",
     "consentReceiptID": "d03bdfed-708a-4792-b6d2-eb336000359f",
     "publicKey": "-----BEGIN PUBLIC KEY-----\nMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAnzyis1ZjfNB0bBgKFMSv\nvkTtwlvBsaJq7S5wA+kzeVOVpVWwkWdVha4s38XM/pa/yr47av7+z3VTmvDRyAHc\naT92whREFpLv9cj5lTeJSibyr/Mrm/YtjCZVWgaOYIhwrXwKLqPr/11inWsAkfIy\ntvHWTxZYEcXLgAXFuUuaS3uF9gEiNQwzGTU1v0FqkqTBr4B8nW3HCN47XUu0t8Y0\ne+lf4s4OxQawWD79J9/5d3Ry0vbV3Am1FtGJiJvOwRsIfVChDpYStTcHTCMqtvWb\nV6L11BWkpzGXSW4Hv43qa+GSYOD2QU68Mb59oSk2OB+BtOLpJofmbGEGgvmwyCI9\nMwIDAQAB\n-----END PUBLIC KEY-----",
     "language": "English",
     "piiPrincipalId": "individual@example.com",
     "piiControllers": [
       {
         "address": {},
         "piiController": "Datafund",
         "contact": "Jani Podatek",
         "email": "info@datafund.io",
         "phone": "+386 0000000",
         "piiControllerUrl": "http://datafund.io"
       }
     ],
     "policyUrl": "https://datafund.io/legal/privacy_policy.html",
     "services": [
       {
         "service": "Service example 1",
         "purposes": [
           {
             "purpose": "Core Function",
             "consentType": "explicit",
             "purposeCategory": [
               "Billing"
             ],
             "piiCategory": [
               "Email",
               "Phone number"
             ],
             "primaryPurpose": true,
             "termination": "1 year",
             "thirdPartyDisclosure": false
           }
         ]
       },
       {
         "service": "Service example 2",
         "purposes": [
           {
             "purpose": "Marketing",
             "consentType": "explicit",
             "purposeCategory": [
               "Direct marketing",
               "Delivery"
             ],
             "piiCategory": [
               "Home address",
               "Email address",
               "Phone number"
             ],
             "termination": "1 year",
             "thirdPartyDisclosure": true,
             "thirdPartyName": "AnalyticsRus"
           }
         ]
       }
     ],
     "sensitive": true,
     "spiCat": [
       "Health status",
       "Genetic data"
     ],
     "jurisdiction": "SI"
 }
```

<br/>Add API root URL parameter:
```javascript  
let APIroot = "http://localhost:5000/api/v1/"
```

<br/>Add properties for verifying token:
```javascript  
let verifyOptions = {
                issuer: "issuer",
                subject: "subject",
                audience: "audience",
                expiresIn: "12h",
                algorithm: "RS256"
}
```

<br/>Include component in render() method of your app:
 ```javascript  
<ConsentGenerator formData={{formData}} APIroot={{APIroot}} verifyOptions={{verifyOptions}} />
```

## Props
- `formData` (json)
- `APIroot` (string)
- `verifyOptions` (json)
  
