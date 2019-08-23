# LLDB Custom Commands
LLDB command aliases for making debugging easier.
In this repository I keep some command aliases that I use in my debugging daily basis.

## Usage

Setting up these commands so that you can use them in Xcode is simple, once you download the repository open a terminal and type the following replacing the ```[DIRECTORY_OF_DOWNLOAD]``` with the path of the directory where you downloaded the repo:

```
mv [DIRECTORY_OF_DOWNLOAD]/lldb-custom-commands/.lldbinit ~/.lldbinit
```

This will move de ```.lldbinit``` file to your ```$HOME``` directory where LLDB will look for it and load the commands at the start of the next debugging section.

Enjoy!

## Commands

### cpx

```cpx``` is a command alias that prints a number in a hexadecimal format, it also moves the context of the debugging section to Objective-C, making it easier to access register values and memory addresses.

```
(lldb) cpx $rdi
```

Will print the value of the register RDI in a Hexadecimal format.

### cpo and spo

These commands are similar to po, except that po uses the current debugging context for evaluating the expression given, unlike it ```cpo``` and ```spo``` alows you to force a context in spite of wich is now running in your LLDB session.

```cpo``` will force the Objective-C context and ```spo``` will force a Swift context, these are usefull command for when you want to use features that are only present in only one of those languages.

### rlook

This command is an abreviation of ```image lookup -rn``` that takes a regex expression and look for any function in the project that matches it.

### getcls

```getcls``` is a command that will try to infer the current debugging context and give you the type of the variable or address provided.

If it fails you can still use ```cgetcls``` for the same purpose in Objective-C contexts or ```sgetcls``` in Swift contexts.

### pjson

This command requires that you provide a variable of type ```Data``` and it will try to print the json formatted for it.
