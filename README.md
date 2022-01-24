# Dasher
Script to convert Adobe Illustrator dashed strokes to actual paths.

---
## Why this project?
Adobe Illustrator does not natively provide this functionality. One can "Outline Path" or "Expand Stroke" which work with dashed strokes, but there is no feature that provides simple open paths for each dash.

---
## Installation

Download the [script files](https://github.com/mark1bean/dasher-for-illustrator/archive/master.zip). The scripts can be stored anywhere on your computer, but you must keep them all together in the same folder so that they can load each other.

---
## Quick Start

To use it straight away, just make a selection in Illustrator and run `Convert Dashed Strokes.js` script.

This script will try to find any dashed strokes in the selection and create dashes path items on a new "Dashes" layer.

> Remember: it won't work unless `Bez.js` and `Dasher.js` are in the same folder with the script.

___
### Bare bones usage

To convert one path item:
```
    var bez = new Bez({ pathItem: item });
    bez.convertToDashes(options);
```

___
### What is Dasher.js?

Dasher is a tool for generating and manipulating simple numerical patterns in the form used by Illustrator's stroke dashes.

___
### What is Bez.js?

Bez is rudimentary class I used to store the bezier path handling functions required by this project, but I may develop it further in other directions if the need arises.

---
### Known Limitations

Adobe Illustrator CS6 and above. As of 2022-01-24, tested only on AI version 26 (MacOS 12.1).

---
### System requirements

Adobe Illustrator CS6 and above. As of 2022-01-24, tested only on AI version 26 (MacOS 12.1).

---
## Acknowledgements

Thanks so much to Hiroyuki Sato, for his bezier maths code from https://github.com/Shanfan/Illustrator-Scripts-Archive/blob/master/jsx/Divide%20(length).jsx
