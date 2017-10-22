# sarcasm

**A Jupyter notebook for helping [me] make sense of sysstat sar data.**

Copyright (c) 2017 Brendon Caligari, London, UK

```{text}
This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
```

*This notebook is a quick hack that grew iteratively to help me sift through
sar files while troubleshooting system issues.  It's very badly written and in
a constant state of flux.  If anyone had to stumble across it and have a use
for it I'll be happy to try to help within reason.  But please don't have any
expectations.*

## Usage

* Follow instructions below to make sure ```file``` can recognise sysstat file type and version.
* Have a copy of ```sadf``` binaries needed to read required sysstat ```.sa``` files.
* Open ```sarcasm.ipynb``` in a Jupyter notebook (created using latest Anaconda 3 distribution) and follow instructions.

## Checking sysstat file version with ```file(1)```

```file``` doesn't seem to recognise sysstat file versions.  The following magic should fix that:

**Append signature to ```~/.magic```:**
```
# sysstat sa file
0       short   0xd596          sysstat sa file
>2      short   >0              format 0x%04x
>4      byte    x               \b; sar version %d
>5      byte    x               \b.%d
>6      byte    x               \b.%d
>7      byte    x               \b.%d

```

**Compile**:
```
cd ~
file -C -m .magic
```

## sysstat

**sysstat**, "System performance tools for the Linux operating system", is copyright (c) 1999-2017 Sebastien GODARD and is freely available under the GNU General Public License, version 2.

It can be found at:
* http://pagesperso-orange.fr/sebastien.godard/
* https://github.com/sysstat/sysstat

