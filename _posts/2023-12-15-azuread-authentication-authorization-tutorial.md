---
title:  "[Tutorial] Azure AD authentication/authorization for your Java application"
header:
  teaser: "/assets/images3/500x300.png"
categories: 
  - Tutorial
tags:
  - Azure AD
  - Azure AD Authentication
  - Azure AD Authorization

---

### Overview
This tutorial to walk you through to authenticate users with Microsoft Entra ID and get authorized access to data in a Java web app using Microsoft Authentication Library.

### Learning objectives
<ul>
  <li>Register a web application with Microsoft Entra ID.</li>
  <li>Sign in users in a Microsoft Entra tenant to a Java web application.</li>
  <li>Authorize access to data in a Microsoft API.</li>
</ul>

### Overall authentication/authorization topology
#### Authentication process
![Authentication](/assets/images/Authentication.png)

(1) End user click into "Sign In" button and then send a request "/auth/sign_in" to Backend server
(2) BackEnd will send a request to /authorzie endpoint on Azure AD along with Redirect URL
(3) After collecting and verify user credential, AAD will response "Auth Code" to backend server /auth/redirect
(4) Backend server handle AAD callback request (validate auth code, exchange AuthCode as ID Tiken and Access Token) then response redirect to FrontEnd to redirect to HomePage
Token is used for communication between Backend and AAD

> **Note:** This application is stateful, so frontend and backend communicate via session.

> **Note:** Backend and AAD communicate via token

#### Authorization process
![Authorization](/assets/images/Authorization.png)

(1) End User do something on application
(2) Client (Frontend) call another APIs (CRUD something) exclude authenticate request
(3) BackEnd get context from request session and do something below:
- (Filter) Check context whether it’s authenticated or not
- (Filter) Verify context role
- (Servlet) re-auth:
    - (prefer silently) in case the access token is not valid anymore.
        - Or run authentication flow that similar with Sign-in
(4) AAD verify the token and response the information to Backend server
(5) Backend response to Frontend

> **Note:** This application is stateful, so frontend and backend communicate via session.

> **Note:** Backend and AAD communicate via token

### Tutorials
1. [Azure AD Authentication - Signin](https://dattranclouds.github.io/tutorial/azuread-authentication-signin/)
2. [Azure AD Authentication - B2C Signin](https://dattranclouds.github.io/tutorial/azuread-authentication-b2csignin/)
3. [Azure AD Authorization - Call Graph API](https://dattranclouds.github.io/tutorial/azuread-authorization-callgraphapi/)
4. [Azure AD Authorization - Groups](https://dattranclouds.github.io/tutorial/azuread-authorization-groups/)
5. [Azure AD Authorization - Roles](https://dattranclouds.github.io/tutorial/azuread-authorization-roles/)
6. [Azure AD Authentication / Authorization - Deployment](https://dattranclouds.github.io/tutorial/azuread-deployment/)
