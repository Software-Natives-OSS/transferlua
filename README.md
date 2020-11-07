# Node wrapper for Indel's TransferLua C-Library

[Indel AG's](https://indel.ch) TransferLua is a dynamic library (`.dll`, `.so`) with a C-API that allows downloading Lua scripts to it's real-time contolling systems. This project is a wrapper around that C-API for Node.

## State

I took the "lean approach": The basic functionality is in place, but less commonly used features may not yet be. Extending it should be farely easy and everyone's invited to do so.

## Motivation

The main motivation for this project was to have Node wrapper suitable to be used by VSCode extensions.

## Installation

```sh
npm i @softwarenatives/transferlua
```

## Basic usage

```js
const transferLua = require("@softwarenatives/transferlua");

const indelTargetName = 'TargetName';
const luaStateName = 'Machine';
const options = transferLua.combineOptions(
    transferLua.OPTION_EXECUTE);

const transfer = new transferLua.LuaTransfer(indelTargetName);
transfer.sendFile(getFileLocation('helloworld.lua'), luaStateName, { options: options });
transfer.close()
```

## TODO

As mentioned, only the "thus far required" functionality is in place. Namely, the following is missing:

- "Error writer" callback not yet implemented (thus, the ability to get 'good error reporting' not given yet)
- Test coverage for various options of `SendFile` and `SendChunk` not yet given (and also not manually tested yet)
