# Transactions

## Txn Generation and Submission

Every successfull transaction on deso consists of the following steps:

1. We make a post request to a deso endpoint, endpoint returns a transaction hex.
2. We use the users seed hex and sign the transaction hex.
3. We call another endpoint and submit the signed transaction hex.
4. If everything went well, the transaction is successfull and will be synced with all nodes.

## Getting the Seed Hex

To be able to create a post using Desonity you will need the **Seed Hex** of the Public Key you are going to make the post from.

**The Seed Hex is a sensitive Token that only the owner of the Public Key should have.**

```cs
async void Start()
{
    string myPublicKey = "BC1YLhF5DHfgqM7rwYK8PVnfKDmMXyVeQqJyeJ8YGsmbVb14qTm123G";
    string mySeedHex = "NEVER GONNA GIVE YOU UP, NEVER GONNA LET YOU DOWN"; // Fake SeedHex

    var user = Desonity.Identity(myPublicKey, mySeedHex);
}
```

To get your Seed Hex, visit any website where you logged in with deso identity and open the developer console.
Navigate to the Application tab and find *identity.deso.org* under local storage. From there find the *Users* item and copy the seed hex from your public key.

Once you get your seed, you can create an Identity object and pass the public key along with its seed hex. This identity object can now be used to sign transactions 

<aside class="notice">
Currently Desonity only supports signing and submitting transactions through the seed hex process. Transactions for other users cannot be signed yet as there is no support for webview/identity service that ask users for transaction approval.
<br>
I will appreciate if anyone knowing how to implement this within Unity can contribute to the project
</aside>

## Using Desonity functions

To interact with deso APIs, you must first create an object that contains the necessasary data that will be needed by the endpoint.

To do so, you must use the `Desonity.Endpoints` namespace in you C# script. This namespace contains all the classes for any endpoint implemented within Desonity.
The endpoint object can then be passed into an appropriate function for processing.

> For example, when you want to get the posts created by a public key, you must use the `GetPostsForPublicKey` class to create an object

```cs
using Desonity;
using Desonity.Endpoints;
...

async void Start()
{
    // This payload will be later used in other funtions
    var payload = new GetPostsForPublicKey{
            Username = "weeblet",
            NumToFetch = 10,
            MediaRequired = true,
            ...
    }
}
```

Once the post request has been done and (if) the API has returned some data, you will need to use one of the classes from `Desonity.Objects` namespace to store the returned data in an object of the appropriate class.

> Continuing the above example, we will call `Desonity.Posts.getPostsForPublicKey()` and pass the `payload` we created earlier.

```cs
using Desonity;
using Desonity.Endpoints;
using Desonirt.Objects;
...

async void Start()
{
    var payload = ...;
    PostsList usersPosts = Posts.getPostsForPublicKey(payload);
    // getPostsForPublicKey has a return type PostsList,
    // which contains a List object of type PostEntry
}
```

**Summing it wup!**

- Create transaction object using class from `Desonity.Endpoints`. (payload)
- Process transaction by passing `payload` to a function.
- Store data returned in an object using class form `Desonity.Objects`.
