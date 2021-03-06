## Usage

1. Install NuGet

  ~~~ps
  Install-Package Auth0.Windows8.Cs
  ~~~

2. Instantiate Auth0Client

  ~~~cs
  var auth0 = new Auth0Client(
     "youraccount.auth0.com",
     "Your Client ID",
     "Your Client Secret");
  ~~~
  
  > Note: it is recommended to store the secret safely using DPAPI or something similar

3. Trigger login (with Widget) 

  ~~~cs
  auth0.LoginAsync(this).ContinueWith(t =>
  {
  /* Use t.Result to do wonderful things, e.g.: 
    - get user email => t.Result.Profile["email"].ToString()
    - get facebook/google/twitter/etc access token => t.Result.Profile["identities"][0]["access_token"]
    - get Windows Azure AD groups => t.Result.Profile["groups"]
    - etc.    
  },
  TaskScheduler.FromCurrentSynchronizationContext());
  ~~~

  ![](http://puu.sh/4c7GO.png)

Or you can use the connection as a parameter (e.g. here we login with a Windows Azure AD account)

~~~cs
auth0.LoginAsync(this, "auth0waadtests.onmicrosoft.com").ContinueWith(t => .. );
~~~

Or with specific user name and password (only for providers that support this)

~~~cs
auth0.LoginAsync(this, "my-db-connection", "username", "password").ContinueWith(t => .. );
~~~

---

## What is Auth0?

Auth0 helps you to:

* Add authentication with [multiple authentication sources](https://docs.auth0.com/identityproviders), either social like **Google, Facebook, Microsoft Account, LinkedIn, GitHub, Twitter**, or enterprise identity systems like **Windows Azure AD, Google Apps, AD, ADFS or any SAML Identity Provider**. 
* Add authentication through more traditional **[username/password databases](https://docs.auth0.com/mysql-connection-tutorial)**.
* Add support for **[linking different user accounts](https://docs.auth0.com/link-accounts)** with the same user.
* Support for generating signed [Json Web Tokens](https://docs.auth0.com/jwt) to call your APIs and **flow the user identity** securely.
* Analytics of how, when and where users are logging in.
* Pull data from other sources and add it to the user profile, through [JavaScript rules](https://docs.auth0.com/rules).

## Create a free account in Auth0

1. Go to [Auth0](http://developers.auth0.com) and click Sign Up.
2. Use Google, GitHub or Microsoft Account to login.
