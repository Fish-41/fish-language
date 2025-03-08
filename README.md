# fish-language

This is a pseudo language for use with dedicated CMD OOT Blocks in GNU Radio to more easily run different commands without the need to edit generated flowgraph code.

## Features

Able to edit the top level flowgraph as well as run commands inside other blocks including custom blocks at set times. Some other block specific commands that require specific CMD Blocks and hardware devices to work.

Currently available init commands:
* `rURI1` and `rURI2`: Used to initialize Receiving PlutoSDR 1 and 2

Currently available time block commands:
* `fg`: Used to run top level flowgraph commands
* `id`: Used to run commands for specific block IDs
* `agc` (bool): Used to turn on and off the AGC when used with the CMD AGC block
* `br1` and `br2`: Used to set the frontend bandwidth of Receiving PlutoSDR 1 and 2

## Format

All text outside designated 'blocks' will be ignored. Designated block rules are as follows:
* Init block is started with `init:` and ended with `end`.
* Time blocks are started with `t=` and then the time as an integer that it should be ran at. The time blocks are also ended with `end`.

Spaces and tabs are not necessary, compiler will handle them, but new commands must be on new lines.

Type handling:
* When using `fg` and `id` an unspecified type will be assumed to be `string`
* `bool`: Valid options are `t` and `f`

`fg` is used to run top level flowgraph commands. If for example you had a variable called `var` which you wanted to set to True you would type:
* `fg = set_var(t):bool`

`id` is used to run commands inside blocks using their id. If for example you had a block called `blk`, which had a function called set_var and you wanted to pass the argument 1.5 as a float, you would type:
* `id = blk.set_var(1.5):float`

## Requirements

Needs a dedicated CMD OOT Block inside GNU Radio to make use of it.

## Extension Settings

Include if your extension adds any VS Code settings through the `contributes.configuration` extension point.

For example:

This extension contributes the following settings:

* `myExtension.enable`: Enable/disable this extension.
* `myExtension.thing`: Set to `blah` to do something.

## Known Issues

No known isssues currently.

## Release Notes

Users appreciate release notes as you update your extension.

### 1.0.0

Initial release of grammer and pretty colours.

