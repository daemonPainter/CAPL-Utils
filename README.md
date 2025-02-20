# CAPL-Utils
A collection of utility functions developed in CAPL and tested for rapid prototyping and on-the-run development of CAPL applications.

## Table of Contents
1. Installation
   1. List of files
2. Usage
3. List of Checksum Algorithms
4. Contributions
  
## Installation
Clone or download the utility files from this repository into a folder in your local environment.

To use the functions from the files, they should be included in your main script(s). To do so, add the relevant files to your configuration, in the `includes` section, like so:

```
includes
{
    #include "messageCounters.cin"    // be sure to use the right relative path to the resource
}
```

Be sure to include all relevant files for your use.
When compiling, duplicate files are typically ignored. However, try to avoid including the same library file twice. There is no way in CAPL to define include guards.

### List of files

#### messageCounters.cin

Includes functions to compute alive counters and generally locally continous and monotone sawtooth signals.

#### CRC*.cin

These files, for example `CRC8.cin` or `CRC16.cin`, define certain algorithms for CRC computation. These may be used at runtime, e.g. to checksum simulated outgoing signals.

For a complete list of available checksum algorithms, please consult the dedicated paragraph.

## Usage

As I am building this file, kindly consider the documentation provided in the files.

The documentation _should_ be Doxygen compliant, although it would be necessary to use [this extension](https://github.com/BretislavRychta/CAPL-filter-for-Doxygen) to build them. It is in the TODO list, if you were looking for ways to contribute... 🙄

## List of Checksum Algorithms

### CRC8

| Name | Function call | Polynomial | Initial Value | Final XOR | Reflection IN | Reflection OUT |
|------|---------------|------------|:-------------:|:---------:|:-------------:|:--------------:|
| SAE J1850 | computeCRC8_SAEJ1850 | 0x1D | 0xFF | 0xFF | no | no |

### CRC16

| Name | Function call | Polynomial | Initial Value | Final XOR | Reflection IN | Reflection OUT |
|------|---------------|------------|:-------------:|:---------:|:-------------:|:--------------:|
| ARC | computeCRC16_ARC | 0x8005 | 0xFFFF | 0x0000 | yes | yes |
| CCITT | computeCRC16_CCITT | 0x1021 | 0xFFFF | 0x0000 | no | no |
| CDMA2000 | computeCRC16_CDMA2000 | 0xC867 | 0xFFFF | 0x0000 | no | no |


## Contributions

Contributions are welcomed. Please create a branch and submit your files for review.

It is appreciated to have an issue opened before submission, and to use proper commit messages to have the issue automatically closed once merged.

Break down contributions into small, sensible, chunks. Bulk submissions of terabytes of files will not be considered.
