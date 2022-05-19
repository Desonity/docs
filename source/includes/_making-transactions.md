# Creating Transactions

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

