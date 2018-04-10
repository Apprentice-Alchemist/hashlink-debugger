# HashLink Debugger
[![Build Status](https://travis-ci.org/vshaxe/hashlink-debugger.svg?branch=master)](https://travis-ci.org/vshaxe/hashlink-debugger) [![Version](https://vsmarketplacebadge.apphb.com/version-short/HaxeFoundation.haxe-hl.svg)](https://marketplace.visualstudio.com/items?itemName=HaxeFoundation.haxe-hl) [![Installs](https://vsmarketplacebadge.apphb.com/installs-short/HaxeFoundation.haxe-hl.svg)](https://marketplace.visualstudio.com/items?itemName=HaxeFoundation.haxe-hl)

This VSCode extension allows you to compile debug HashLink JIT applications.

## Building from Source

The following instructions are only relevant for building the extension from source and are **not required when installing it from the marketplace**.

### Compiling

The VSCode debugger relies on the `hldebug` library that is not yet released (still in alpha), you will then need to checkout latest [HashLink sources](https://github.com/HaxeFoundation/hashlink) and then run `haxelib dev hldebug /path/to/hashlink/other/debugger`

You also need to clone this repository submodules so the `vscode-debugadapter-extern` directory is correctly populated.

And finally you need to get the latest version of the `format` and `hscript` libraries with `haxelib install format hscript` 

Once all dependencies are ready, you should be able to compile with `haxe hladapter.hxml`

### Installing

Please note that VSCode does not allow users to have a specific directory for a single extension, so it's easier to clone this repository directly into the `extensions` directory of VSCode (`C:\Users\<you>\.vscode\extensions` on Windows).

Before running, you need to install a few NodeJS extensions. **DO NOT** npm install, as this will install the native extensions for your current NodeJS version and not for the Electron version of VSCode (if you did this already, simply remove the node_modules directory). Instead, run `make deps`, which will npm install & compile the extensions for the latest version of VSCode.

If the extension fails to run, maybe you are using a different version of VSCode than the one you compiled for.
Open VSCode, go to Help / Activate Development Tools, then in the dev console write `process.versions.electron` and replace it in the `Makefile`,  remove `node_modules` and recompile.

## Linux / OSX version

**Only Windows is supported for now.**

Linux ans OSX versions are not yet available, this requires implementing the hld.NodeDebugApi class of hldebug using `ptrace`.
