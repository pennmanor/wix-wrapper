# WiX MSI Wrapper

## About the code

This framework will allow one to 'wrap' an exe installer into an MSI for quick
and easy deployment in a corporate environment.

This may reduce or negate the need for 'capture' apps, such as AppDeploy
Repackager.

## Using from source

### Prerequisites

- .Net environment (Native Windows, Mono, etc)
- WiX Toolset

### Creating package

After cloning the repository, copy the requested .exe installer into the
directory and edit the .wxs script for the .exe name.

Currently, `owncloud.wxs` simply needs the indicated edits on lines 2-6, making
the appropriate updates for .exe filename, GUID, et cetera.

GUIDs for the new installer version may be created via [web
tools](http://www.guidgen.com/). *N.B. all GUIDs must be be in majuscule case.*

**Package creation may be done automatically:** After ensuring that the WiX
tools are in the Windows Path, simply run the `make_installer.bat` file. The
script will automatically clear any artifacts from previous builds and generate
a new MSI package.

**Package creation may also be done manually:** Using the standard WiX tools-
first, `candle *.wxs` then `light *.wixobj`, and the MSI will be created.

## Contributing
### Code
Any improvements are more than welcome. Please submit a pull request and I'll
take a look.
### Issues
If you run into bugs, or need assistance with the creation of the MSI package,
please open a GitHub Issue.

## License

	This program is free software; you can redistribute it and/or modify
	it under the terms of the GNU General Public License as published by
	the Free Software Foundation; either version 2 of the License, or
	(at your option) any later version.

	This program is distributed in the hope that it will be useful, but
	WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY
	or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License
	for more details.
