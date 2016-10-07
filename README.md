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

### Package Information

Currently, `nextcloud.wxs` simply needs the indicated edits on lines 2-6, making
the appropriate updates for .exe filename, package version, GUID (optional, see
below).

If you wish to use your own custom GUIDs, GUIDs for each new installer version
may be created via [web tools](http://www.guidgen.com/). *N.B. all GUIDs must be
be in majuscule case.*

**Package creation may be done automatically:** After ensuring that the WiX
tools are in the Windows Path, simply run the `make_installer.bat` file. The
script will automatically clear any artifacts from previous builds and generate
a new MSI package.

**Package creation may also be done manually:** Using the standard WiX tools-
first, `candle *.wxs` then `light *.wixobj`, and the MSI will be created.

### Full MSI Creation Steps:

1. Copy the official or custom built nextcloud.exe file into the project folder.
2. Edit `nextcloud.wxs` lines 2-6 as necessary. Generally, only update version and filename.
3. Run `make_installer.bat`, or run `candle *.wxs`, and `light *.wixobj`.
4. Copy the newly created nextcloud.msi to an appropriate install location (AD server, Network share, etc.)
5. Install the nextcloud.msi with any valid tool- Group Policy, Remote Admin commands, etc.


### A note about GUIDs

WiX and Windows use Globally Unique Identifiers as a way to identify software installs and other 'products' that are stored on a Windows system.
Because of the length and diversity of GUIDs, the chance of a GUID collision is near-zero.
For general purpose projects, such as this, any common GUID generator may be used.

When generating an update for the WiX file, a single new GUID is needed on the indicated line.
The GUID referring to the previous install must also be listed so that the installer can properly identify and remove the previous package.
All GUIDs must be in majuscule (upper) case.

Also of note is a hard-coded GUID in `nextcloud.wxs` line 22.
This hard-coded GUID can be used under the assumption that packages are deployed in such a method that the receiving computers have since been restarted and/or cleared the temporary file cache.


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
