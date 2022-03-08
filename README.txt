OpenENDEC Project
Based on jmcmellen's sameeas scripts, as well as cuppa-joe's dsame
OpenENDEC and NEXDEC (C) 2022 Nova Labs
SAMEEAS (C) 2011 John McMellen
dsame (C) 2016 Joseph W. Metcalf
Made available under MIT License.

OpenENDEC is a project meant to eventually create the world's first fully functional open-source software EAS ENDEC (encoder/decoder), available freely to all.
Using existing, well-established and reliable libraries and building on them, OpenENDEC aspires to be the next generation of EAS equipment, finally bringing a proper alert system to online stations at no cost.

At its core is NEXDEC, the command-line/terminal and background components that make up the OpenENDEC system's core functions. So far only the NEXDEC Core EASEncode component is publicly available; however, things in development include a basic graphical interface, an audio monitor background process based on dsame, and automation for relaying alerts. 

See below for original README for sameeas (with the exception of usage examples being altered).
See the GitHub Pages website https://thegreatc0deholio.github.io/OpenENDEC for more information about the other functions, or read dsame_README.MD from the repo.

SAMEEAS
===============================================================
License (see the MIT License)

Copyright (c) 2011 John McMellen

Permission is hereby granted, free of charge, to any person
obtaining a copy of this software and associated documentation
files (the "Software"), to deal in the Software without
restriction, including without limitation the rights to use,
copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the
Software is furnished to do so, subject to the following
conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES
OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.
==============================================================

In other words, use at your own risk. This software is for testing
purposes only. No guarantees of suitability or compatibility
with any FCC approved EAS decoders are expressed or implied. 
Users of the software are encouraged to do extensive testing
before using in a production environment, if ever.

DSAME
==========================================================
License (ISC)

Copyright (c) 2016 Joseph W. Metcalf

Permission to use, copy, modify, and/or distribute this software for any purpose 
with or without fee is hereby granted, provided that the above copyright notice 
and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL 
WARRANTIES WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF 
MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY SPECIAL, 
DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING FROM 
LOSS OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER 
TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE USE OR 
PERFORMANCE OF THIS SOFTWARE. 

HOW TO USE:
==========================================================

NOTE: Usage examples are listed below this section.

The executable file is a compiled version of the four
Python scripts easencode.py (the commandline interface),
eastestgen.py (EAS message formatting), afsk.py (afsk routines),
and audioroutines.py (library functions for signal generation).
The scripts were developed using Python 2.7 and should run
correctly in any platform where Python 2.7 is installed.

The executable file nexdecencoder.exe (easencode.py) provides 
a simple commandline implementation of an EAS encoder. You 
pass it the configuration details and the result is a WAVE
file that *should* be an EAS message according to the 
structure defined by the FCC rules. This flexibility allows
the user the ability to generate a variety of activation
messages and observe the way the decoder reacts. Consult 
the FCC rules for the correct values for FIPS codes and
activation messages.

The software also provides a "fuzzer" mode wherein the user
can generate messages with incorrect or undocumented values.
This can be used to check how the decoder responds to data
that is not-defined or incorrectly formatted.

Some basic help is available on the commandline using the 
(-h) help option.

USAGE EXAMPLES
=============================================================

Generate a simple test, 15 minute duration
    nexdecencoder.exe -e RWT -f 029177 -d 0015 -c WXYZ eas-rwt.wav
    nexdecencoder.exe -e RWT -f 029177 -d 0015 -t now -c "WXYZ FM" eas-rwt.wav

Generate a test with a voice message from input.wav
    nexdecencoder.exe -e RWT -f 037124 -d 0015 -c KXYZ -a input.wav eas-rwt.wav

Fuzz mode: Generate a test with a non-standard EAS message using -z or --fuzz
    nexdecencoder.exe --fuzz "WXR-RAT-012345-111111+0123-BLAHBLAH-" output_eas.wav
    Read the FCC rules for the exact format of an EAS message
