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
__IdP__ uses some method to like username or password to authenciate the user & establish session. Digital signatures are used to specify the connection's authenticiation.

SAML core's means syntax and semantics of assertions for transmission & request. SAML's core define what is being transmitted not how to transmit and request. Bindings of SAML determine how to map requests & responses onto standard messaging & communication protocol. Examples of such bindings are SOAP and ReST. In ReST url of very large length can be problematic if because each vendor limits url length but otherwise this is better protocol.  

A profile in a use-case is a combination of assertions, protocols and bindings. Security is provided in SAML with TLS, XML encryption, XML signature.

### Structure

SAML uses HTTP communication protocol as its basis.

* XML is used for SAML exhange of messages.
* XML Schema is used to specify assertions & protocols.
* SAML 2.0 in comparison to SAML 1.1 provide encrypted Identifiers, Attributes & Assertions.

### SOAP vs ReST

ReST combined JSON provides great functionality advantage. ReST is faster with less bandwidth. Another advantage of SOAP is that it offers built-in retry logic to compensate for failed communications, not present in ReST. ReST accesses data whereas SOAP works on with applicaton logic.


### Detailed Study with Use Case

#### Assertions 

These are interpreted in the following way. Assertion A was issued at time t by issuer R regarding subject S provided conditions C are valid.
Assertions contains authorization information, attribute information (_name value pair_) & authenticiation information. 

#### Protocols

It Describes how SAML components are packaged within a SAML request. Most important SAML protocol is query. Same three types of queries authentication, authorization and attribute(_most important_) type of query. From SAML 1.1 which is having only query protocols, SAML 2.0 expands the notion of protocol considerably. The following protocols are described in detail in SAML 2.0 Core:

* Assertion Query and Request Protocol
* Authentication Request Protocol
* Artifact Resolution Protocol
* Name Identifier Management Protocol
* Single Logout Protocol
* Name Identifier Mapping Protocol

#### Bindings

A SAML binding is a mapping of a SAML protocol message onto standard messaging formats and/or communications protocols. For example, the SAML SOAP binding specifies how a SAML message is encapsulated in a SOAP envelope, which itself is bound to an HTTP message.

  ![SAML Over SOAP Over HTTP](https://upload.wikimedia.org/wikipedia/commons/2/2a/Saml-over-soap-over-http.svg)  
&emsp;_Fig 1. SAML Over SOAP Over HTTP_

#### Profiles

A SAML profile describes in detail how SAML assertions, protocols, and bindings combine to support a defined use case. The most important SAML profile is the Web Browser SSO Profile.

#### Steps

* Request the target source SP.
* Get redirected to SSO service at IdP.
* Request SSO service at IdP with response in XHTML form.
* Request following service at SP & get redirected to target source.

If again the target source is requested with base url being same, user will be directly able to access the service as connection exists between them already.

---

#### References 
* https://en.wikipedia.org/wiki/Security_Assertion_Markup_Language
* https://github.com/jch/saml/blob/master/shibboleth-administration.md
* https://stackify.com/soap-vs-rest/
