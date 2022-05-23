# Dasher

Script to convert Adobe Illustrator dashed strokes to actual paths.

![Convert Selected Dashed Strokes.js demo animation](images/dasher-anim.gif)

$~$
***

## Installation

Download the [latest release](https://github.com/mark1bean/dasher-for-illustrator/releases/latest/download/dasher-for-illustrator.zip). The scripts can be stored anywhere on your computer, but you must keep them all together in the same folder so that they can load each other.

$~$
***

## Quick Start

To use it straight away, just make a selection in Illustrator and run `Convert Dashed Strokes.js` script.

This script will try to find any dashed strokes in the selection and create dashes path items on a new "Dashes" layer.

> Remember: it won't work unless `Bez.js` and `Dasher.js` are in the same folder with the script.

$~$
***

## Basic usage

Using `convertToDashes` method of `Bez` to convert one path item. No options are supplied, so it will use default options (see Configuration below).

```javascript
    var item = app.activeDocument.selection[0];
    var bez = new Bez({ pathItem: item });
    bez.convertToDashes();
```

$~$
***

## Configuration

The `convertToDashes` method of Bez takes an `options` argument. If it is not supplied, defaults will be used.

| option | description | default |
| ------ | ----------- | ------- |
| `pattern`: | `Array` of [dash, gap] lengths | item's `strokeDashes` property |
| `alignDashes`: | `Boolean` (if true, align dashes to corners and path ends, scaling lengths to fit) | item's stroke dash alignment style |
| `layer`: | `Layer` to place converted dashes | Place group next to item on same layer |
| `strokeCap`: | `StrokeCap` type of line capping | item's `strokeCap` property or `StrokeCap.BUTTENDCAP` |
| `strokeColor`: | `Swatch` or `Color` to color dashes | item's `strokeColor` property (if no color, dashes won't be stroked) |
| `strokeJoin`: | `StrokeJoin` type of joints | item's `StrokeJoin` property or `StrokeJoin.MITERENDJOIN` |
| `strokeMiterLimit`: | `Number` mitre limit | 4 |
| `strokeWidth`: | `Number` width of stroke in pts | 1 |

$~$
Example:

```javascript
var options = {
    pattern: [8,2,4,2],
    alignDashes: true,
    strokeColor: app.activeDocument.swatches[5]
}

var item = app.activeDocument.selection[0];
var bez = new Bez({ pathItem: item });
bez.convertToDashes(options);
```

$~$
***

## What is Dasher.js?

Dasher is a tool for generating and manipulating simple numerical patterns in the form used by Illustrator's stroke dashes.

$~$
***

## Requires Bez.js

Bez is rudimentary class I used to store the bezier path handling functions required by this project, but I may develop it further in other directions if the need arises.
> `Bez.js` now has it's [own repo](https://github.com/mark1bean/bez-for-illustrator).

$~$
***

## Why this project?

Adobe Illustrator does not natively provide this functionality. We can "Outline Path" or "Expand Stroke", but there is no feature that provides simple open paths for each dash.

Example usages are cutting machines that require an open path to guide a tool bit or laser.

$~$
***

## Please help with testing

As of 2022-01-25, this script is hardly tested at all, and only on my machine. Adobe Illlustrator 2022 (v26), MacOS 12.1.

Please post any issues you come across.

$~$
***

## Known Limitations

In cases where the Illustrator path item is stroked with a `strokeDashes` array with *an odd number of members greater than one* Illustrator, at some path section lengths, seems to break it's own rules on how to fit the dashes. This looks to me like a bug, as it introduces strange lengths that don't seem to be logically derived from the `strokeDashes`. In these rare cases, Dasher makes a better-looking result, so I've not attempted to match Illustrator's behaviour.

$~$
***

## System requirements

Adobe Illustrator CS6 and above. As of 2022-01-24, tested only on AI version 26 (MacOS 12.1).

$~$
***

## Acknowledgements

Thanks so much to Hiroyuki Sato, for his bezier maths code from his excellent [Divide (length).js script](https://github.com/Shanfan/Illustrator-Scripts-Archive/blob/master/jsx/Divide%20(length).jsx).

Project was inspired by [a question asked by pixxxelshubser](https://community.adobe.com/t5/illustrator-discussions/js-action-split-or-break-a-dashed-line-into-separate-real-lines-by-script/m-p/12614309).
