## Introduction

SAML is open-standard for authenciating & authorizing data exchange between two parties. This is done with the help
of set of XML-based messages can be called as tokens. A set of XML based protocol messages and bindings plus
a profile for use-case consitute a open standard for exchanging information known as SAML. 

### Use Cases 

1. A web-browser based SSO : Here, web-browser is being re-directed to w/o any information depending URL entered. This is called _"Passive"_ profile meaning client is passively engaged with SPs and IDPs.

2. Active code sits on device : In this case a coded device is to make active API calls to SPs for exchange of information if session exists. This is called _"Active"_ profile. In this case like above standard way exist for communicating between IDP and client. But, here different ways of communicating between client & SPs exists like for making API calls either in the form of cookies, JSON, http requests. 

Other examples are protocols like OAuth( _gives information limited access to an HTTP service without providing password_ ), JWT( _claims encoded as JSON objects & signed as _ ) etc.
