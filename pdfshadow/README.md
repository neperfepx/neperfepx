# pdfshadow

##### Version 1.0.1-6

## Description

`pdfshadow` is a general script that converts the first page of a PDF document into a PNG file including a shadowing effect.  It can also take an arbitrary image as input.

## Prerequisites

The `pdftk` and `convert` (from ImageMagick) commands must be available

## Usage

The script is simply to be called as

```
$ pdfshadow input output [page number]
```

where `input` is a PDF file (or an image file), `output` the name of the output file, and `page number` is the optional page number (default `1`).

## Installation

The script should be copied to a standard directory (which belongs to `$PATH`) to make it available system-wide.
