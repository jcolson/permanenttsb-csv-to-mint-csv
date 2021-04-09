<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**

- [convert-to-quicken-csv](#convert-to-quicken-csv)
  - [Build status](#build-status)
  - [Quicken is a total PITA!](#quicken-is-a-total-pita)
  - [Application usage](#application-usage)
  - [how to build:](#how-to-build)
  - [Help on running](#help-on-running)
  - [Run on test file](#run-on-test-file)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# convert-to-quicken-csv

## Build status

![Go](https://github.com/jcolson/convert-to-quicken-csv/workflows/Go/badge.svg)

## Quicken is a total PITA!

If your bank doesn't pay Quicken/Intuit, they basically try to do everything in their power to disable you from importing transactions.

QIF files can't be imported into an account - as you'll get this error message from Quicken:

```
"Quicken can only import qif files into empty documents."
```

OFX files can't be imported into an account (unless your bank pays quicken) - as you'll get this error message:

```
"Quicken is unable to update this account because Web Connect support for your financial institution has been either temporarily, or permanently discontinued [CC-885]."
```

## Application usage

This app is for converting certain csv formats to something that quicken will 'allow' to import (the Mint CSV format).

Formats that can be converted

* Permanent TSB
* Banktivity (Mac financial mgmt application, like Quicken)
* Revolut exports

## how to build:

This will build for whatever platform you are running on (creates a universal binary if you are building on Darwin)

```sh
make
```

Build for all platforms

```sh
make all
```

binaries are generated in the `bin/` directory.

## Help on running

```sh
Usage of ./convert-to-quicken-csv:
  -dates string
        Year/Month, default is previous month (default "2021/1")
  -h    Help
  -input string
        The csv input file to read (default "examplepermtsb.csv")
  -type string
        Input format type.  Available options: open24, banktivity, revolut (default "open24")
```

## Run on test file

```sh
go run convert-to-quicken-csv.go -dates 2019/11
```
