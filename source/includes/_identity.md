# Identity Login

## Setting up the backend

In order to use Identity Login you need to setup a backend with which Unity will interact and open the web browser where the user can login, the logged in Public Key will be returned to the script which called the login function.

A Python Flask example is available in [`Desonity/Backend-Flask`](https://github.com/Desonity/Backend-Flask) repository. You can host this on a paid VPS or use a free service such as Heroku or Repl.it.

> A flask app is already hosted on `https://desonity-login.herokuapp.com` which you can use for testing purposes. (Not reccomended for production use as uptime cannot be guaranteed)

## Login with Identity

Create an Identity object using `Desonity.Identity()`.

> This will open the default browser and prompt the user to login with a DeSo account.

```cs
async void Start()
{
    string appName = "Docs-App-Demo";
    string backendUrl = "https://desonity-login.herokuapp.com";

    var user = Desonity.Identity(appName, backendUrl);
    string loggedInPublicKey = await user.Login();
}
```

> Optionally you can also pass a DeSo public key and perform actions using that.

```cs
async void Start()
{
    string myPublicKey = "BC1YLhF5DHfgqM7rwYK8PVnfKDmMXyVeQqJyeJ8YGsmbVb14qTm123G";
    var user = Desonity.Identity(myPublicKey);
}
```

Parameters           | Description
----------           | -----------
appName              | Name of the app that will be shown to users during Login.
backendUrl           | Url for the backend which will handle Login.
PublicKeyBase58Check | Public Key of a DeSo Profile (optional).
seedHex              | Seed Hex of the passed Public Key (optional).

<aside class="notice">
This identity object will be used repeatedly with other classs to perform actions since all data such as Public Key and Seed Hex is stored with the identity object.
</aside>
