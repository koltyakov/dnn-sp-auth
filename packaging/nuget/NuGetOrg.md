# SPAuthN - SharePoint .Net auth via Node.js

[![NuGet version](https://img.shields.io/nuget/v/SPAuthN.svg)](https://www.nuget.org/packages/SPAuthN)
[![Downloads](https://img.shields.io/nuget/dt/SPAuthN.svg)](https://www.nuget.org/packages/SPAuthN)
![Build Status](https://koltyakov.visualstudio.com/SPNode/_apis/build/status/SPAuthN?branchName=master)
[![Gitter chat](https://badges.gitter.im/gitterHQ/gitter.png)](https://gitter.im/sharepoint-node/Lobby)

---

The wrapper for [node-sp-auth](https://www.npmjs.com/package/node-sp-auth) and [node-sp-auth-config](https://www.npmjs.com/package/node-sp-auth-config) for usage in .Net assemblies.

Allows authenticating in SharePoint in whatever you need scenarios and provides a wizard-like approach for building and managing connection config files.

---

On the first place, it is an experiment which solves one of our very specific tasks for a frontier technology stack with SharePoint/Node.js/.Net where we need running the same exactly auth mechanisms which we use in Node.js but in .Net applications. We know exactly what we're doing and why. Please use the lib only in the case when native .Net credentials strategies do not suite your app.

## For whom is this library?

For folks who used to create applications for SharePoint with authentication level powered by `node-sp-auth-config` and `node-sp-auth-config` and who desire reuse authentication settings parameters and formats in .Net application.

For geeks from geeks passionated with funky technology experiments on their way doing awesome stuff.

For the cases when one tool should rule *all possible authentication strategies in SharePoint.

And definitely not for the situations when these work for you:

- context.Credentials = new SharePointOnlineCredentials("username", "securepass");
- context.Credentials = new NetworkCredential("username", "password", "domain");
- Any other native authentication routes.

## Versions supported

- SharePoint Online
- SharePoint 2019
- SharePoint 2016
- SharePoint 2013
- SharePoint 2010 (limited support)

## Authentication options

- SharePoint Online:
  - User credentials (SAML/ADFS)
  - Add-In Only permissions
  - On-Demand authentication (using Electron popup)
- SharePoint 2019, 2016, 2013:
  - User credentials (NTLM, NTLM v2)
  - ADFS user credentials
  - Form-based authentication (FBA)
  - Form-based authentication (Forefront TMG)
  - Add-In Only permissions
  - On-Demand authentication (using Electron popup)
- SharePoint 2010:
  - User credentials (NTLM, NTMLv2)
  - Form-based authentication (FBA)
  - Form-based authentication (Forefront TMG)

Config layer and auth supports Office 365 Dedicated (SPO on custom domain) as well.

## How to install

```PowerShell
Install-Package SPAuthN
```

## How to use

```csharp
Options options = SPAuth.GetAuth();
```

That's it! Really!

Now `options.headers` object contains Cookie or Authorization which can be injected to web requests.
This is a low level, session timeouts should be controlled manually.

[See more on GitHub](https://github.com/koltyakov/SPAuthN)