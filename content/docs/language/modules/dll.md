---
title: DLLs
---

DLL stands for "Dynamically Linked Library". It's a filetype used to extend applications (such as Bennu), and is logically described as an "application extension" or, because different programs can make use of it, as a "shared object". These DLLs can be included in your Bennu programs as and when you wish, or not at all. In Windows DLLs have the extension .DLL (Dynamic-Link Library) and in Linux .SO (Shared Object).

Want to create DLLs? Check this out. 

## Modules

The modules you can [import]({{< ref "import" >}}) in Bennu are in fact DLLs too. Bennu has a powerful module system, which you can use to make modules of your own. You can also replace the official modules with your own and reimplement the functionality. For example, you could make a new rendering system using OpenGL or a new mod_sound, using a different sound library. 

### What does this mean for Bennu?

It means that people who are not developing the Bennu language can still add to it by writing modules for Bennu in C.

Bennu users can use this optional extra functionality. For example, if you want to add internet/network functionality to your games, there is Network.DLL. 

## Using a DLL

Each DLL may have different functionality, so it is always advisable to read the documentation that comes with the DLL (if there is any) or the page on that DLL on this wiki: List of Bennu DLLs.

First, to use the functions of any DLL you need to include this line in your code: Many DLL's require you to import them, like so:

```
import "<Path and file name of DLL here>";
```

Although there are some, like Network.DLL, which require you to include an include file (*.inc), instead of importing the DLL. The header file will do that and possibly provide more functionality.

Once successfully imported or included, functions, constants, etc of that DLL can then be used in the rest of your program in the same way that Bennu functions, constants, etc are used. Some DLLs require other DLLs to be present in the same folder. This is possible because DLLs for Bennu can make use of functionality of other DLLs, like Network.DLL uses SDL_Net.DLL. 

## DLLs and releases

When it comes to the point when you want to distribute your game or application to others, it is necessary to distribute it with all of the DLLs used, including the ones that are not directly imported into your code (see above). Lack of any DLLs used will make your game unplayable. For more information see Distributing Bennu Programs. 