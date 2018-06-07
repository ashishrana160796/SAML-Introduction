## Introduction

SAML is open-standard for authenciating & authorizing data exchange between two parties. This is done with the help
of set of XML-based messages can be called as tokens. A set of XML based protocol messages and bindings plus
a profile for use-case consitute a open standard for exchanging information known as SAML. 

### Use Cases 

1. A web-browser based SSO : Here, web-browser is being re-directed to w/o any information depending URL entered. This is called _"Passive"_ profile meaning client is passively engaged with SPs and IDPs.

2. Active code sits on device : In this case a coded device is to make active API calls to SPs for exchange of information if session exists. This is called _"Active"_ profile. In this case like above standard way exist for communicating between IDP and client. But, here different ways of communicating between client & SPs exists like for making API calls either in the form of cookies, JSON, http requests. 

Other protocols for authorization & authenticiation are OAuth( _gives information limited access to an HTTP service without providing password_ ), JWT( _claims encoded as JSON objects & signed as JWS plus encrypted with JWE_ ) etc.

### Problems while not using SAML 

Consider a use-case where CRM server is there with different multiple customer services and different users. Different users have different permissions that provide different level of access in CRM server.
Problems with such configuration as follow :

* If user is removed or moved to other access level it has to updated everywhere like in CRM server's access list etc.
* A list of user has to maintained with redundant id's if multiple IDs are being used for different SAS service in place.
* Multiple services with multiple IDs are needed to be maintained & updated list is needed. All the basic database problems will come in this like removal of user if a service gets removed & user is part of that service but user is still part of organization.

### SAML Advantages (_Except obvious SSO_)

* Users pre-filled from from organization profile like with LDAP and active directory as directory service provider.
* Only one source of true active users. No consistency problem as such. Easy managing of access.


### Working

In SAML, __principle__(_user_) wants to access resources from Service Provider(_SP_) and _SP_ uses _assertions_ in the form of let's say tokens from __Identity Provider__(_IdP_).
__IdP__ uses some method to like username or password to authenciate the user & establish session.
