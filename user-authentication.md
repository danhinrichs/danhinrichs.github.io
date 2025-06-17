---
layout: default
---

# User Authentication
Just here for the code? Click [here](#the-code)
## How it works
Like many things in technology, a real life example is often the best way of explaining more complicated topics. When it comes to web-based user authentication, I like to think of the analogy of a painter doing work at your house. Often this person is given a spare key or is told of a door that will remained unlocked so that they can some in and do work on the house even if the owner is not home. Upon entering the house using the key, you know that they've entered the correct house, and some basic characteristics about them, such as their name, seem correct as well. However, before you let them paint the walls of your home, you want to verify their identity through a driver's license and a business card. The painter hands you the documents. You can trust the information given on the driver's license since it comes from a reliable source(the government), and you can be confident in their ability to paint your home because their business card comes from a painting company, so you ultimately let them in to paint your house.

Modern user authentication uses the [OAuth 2.0](https://oauth.net/2) protocol in order to authenticate and authorize users. Today, this process has been greatly abstracted, so developers really only need to focus on these three areas:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1. Login using username and password  <br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2. Generation of access and ID token <br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3. Authorization of user upon API request  <br /><br />
![Octocat](./oauth2.png)

#### Login
The flow starts the user typing in their credentials onto the **client** application(think any typcial login page). These credentials are then send to an **identity provider** for verification. Here are some popular modern identity providers:
<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1. [KeyCloak](https://www.keycloak.org) <br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2. [Okta](https://www.okta.com) <br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2. [Frontegg](https://frontegg.com) <br />
#### Tokens
Upon successful login, the authorization server response back with an access token and ID token. These tokens are used for very distinct purposes. The ID token includes basic encoded information about the user(first name, username, email, etc.). The access token on the other hand is how later on in the flow the identity provider can confim that the user is in fact who they say they are.
## The code

