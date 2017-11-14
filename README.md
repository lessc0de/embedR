# embedR: Embedding R inside q

See Kx wiki http://code.kx.com/q/interfaces/with-r/#calling-r-from-q

## Installation

### Download
Download the appropriate release archive from [releases](../../releases/latest) page. 

### Unpack and install content of the archive 

environment     | action
----------------|---------------------------------------------------------------------------------------
Linux           | `tar xzvf embedr_linux-v*.tar.gz -C $QHOME --strip 1`
macOS           | `tar xzvf embedr_osx-v*.tar.gz -C $QHOME --strip 1`
Windows         | Open the archive and copy content of the `embedr` folder (`embedr\*`) to `%QHOME%` or `c:\q`


## Calling R

When calling R, you need to set `R_HOME`. Required are:
```
  R_HOME               - R home path      (e.g. /usr/lib/R)
```
For example, a script to load q might be:

```
  #!/bin/bash
  export R_HOME=`R RHOME`
  rlwrap q "$@"
```

### Interactive plotting
If using interactive plotting, you have to take care of some extras.
1. Call `Reventloop[]`. Note that this will override timer and `.z.ts`. It will give R library some time to process graphics event. macOS and Windows only.
2. To plot with `lattice` and/or `ggplot2` you will need to call `print` on chart object. 

## Examples

See [examples](examples) folder. 

Note: Examples are kdb+ 3.5 or higher.

### Example 1.

e4.q  is a simple example of plot 'moving window volatility' of returns. Converted from http://www.mayin.org/ajayshah/KB/R/html/p4.html

### Example 2. 

pcd.q is based on [Corporate credit card transactions 2014-15](https://data.gov.uk/dataset/corporate-credit-card-transaction-2014-15).
Please download csv file from the link above and place it in the same folder as `pcd.q` under name `pcd2014v1.csv`.

### Example 3.

http://data.london.gov.uk/datastore/package/tubenetwork-performance-data
Left for the reader :)
