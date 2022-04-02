---
title: Desonity Documentation

language_tabs: # must be one of https://git.io/vQNgJ
  - C#

toc_footers:
  - <a href='https://github.com/Desonity'>Desonity on GitHub</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - identity

search: true
collapse: true
code_clipboard: true

meta:
  - name: description
    content: Documentation for the Desonity Unity Package
---

# Introduction

Desonity is a Package for [Unity Game Engine](https://en.wikipedia.org/wiki/Unity_(game_engine)) that allows game developers to integrate the [DeSo Blockchain](https://www.deso.org/) into their games.
  
Using this, one can add features such as NFT based access to certain regions of a game, award skins to users in the game in the form of an NFT, let users buy and sell in game items through NFTs on DeSo.

# Installation

<aside class="notice">
This guide assumes you have prior knowledge of the Unity Game Engine and its tools.
</aside>

## Install using Git Url

Open up the project in which you want to add Desonity navigate to the window menu and open the Package Manager.

![Package Manager](images/installation/package%20manager.png)

Choose add package form Git Url, paste

`https://github.com/desonity/desonity.git`

into the url field and hit add.

![Add Git Url](images/installation/add%20git%20url.png)

<aside class="notice">
Adding using Git Url requires you to have GIT pre-installed on your machine.
</aside>

Unity will now clone the repo into the Packages folder of your project and install any other needed dependencies.

If all went well, GG! You just completed step 1 of adding DeSo to your game.

# Using Desonity

> Since Desonity uses API calls to interact with the DeSo Blockchain, you must use its methods within an async method.

```cs
using UnityEngine;
using Desonity;

public class ExampleCLass : MonoBehaviour
{
    async void Start()
    {
        // Do something with Desonity
    }
}
```

To use Desonity you must add the Desonity namespace to your script files.
