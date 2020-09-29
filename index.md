## Welcome to OpenENDEC!
OpenENDEC is a free and open-source SAME/EAS encoding and decoding software suite with the goal of making EAS participation accessible and practical for online and low-power independent broadcasters. Built on existing reliable libraries, OpenENDEC takes the best there is to offer for individual components related to working with Specific Area Message Encoding (SAME), and puts them together to create a full alert solution.

## Setup
To run OpenENDEC, you will need to install Python 2.7 (a Python 3 version is coming soon). Other than that, the currently released portion of the OpenENDEC project is completely self-contained (at least on Windows), and future components along with the package as a whole are intended to be fully self-contained as well.

## Use
To use the encoder, currently you will have to do so via command line. 
As an example, to issue a Required Weekly Test with a duration of 15 minutes starting now with my online radio station's call targeted at the entire state of Utah, I would type this into Command Prompt while in the directory where nexdecencoder.exe is located:
```nexdecencoder.exe -e RWT -f 049000 -d 0015 -c KNLO(IP) output.wav```
Now let's briefly review the flags here:

-e is for your event code, in this example it is a Required Weekly Test (hence RWT). You can find a list of event codes here - all codes that are currently in use in the US are supported by OpenENDEC/NEXDEC Core: https://en.wikipedia.org/wiki/Specific_Area_Message_Encoding#Event_codes
-f is where you enter in the FIPS codes the alert applies to. You can find yours here: https://www.weather.gov/pimar/FIPSCodes or by simply searching "(your area here) FIPS code".
-d is the duration you want your alert to be valid for. The format is HHMM as you can see above. 
-c is for a callsign/sender ID. This can be any string of 8 characters or less.
And output.wav is the file I want it to be saved to after generating. The name can be anything as long as it still ends with the .wav file extension.
