WiX MSI Wrapper
===============

About the code
--------------
This framework will allow one to 'wrap' an exe installer into an MSI for 
quick and easy deployment in a corporate environment.

This may reduce or negate the need for 'capture' apps, such as AppDeploy Repackager.

Using from source
---------------
### Prerequisites
- .Net environment (Native Windows, Mono, etc)
- WiX Toolset

### Creating package
After cloning the repository, copy the requested .exe installer into the 
directory and edit the .wxs script for the .exe name.

Run the WiX tools- `candle *.wxs` then `light *.wixobj`, and the MSI will
be created.


License
----------------
	This program is free software; you can redistribute it and/or modify
	it under the terms of the GNU General Public License as published by
	the Free Software Foundation; either version 2 of the License, or
	(at your option) any later version.
	
	This program is distributed in the hope that it will be useful, but
	WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY
	or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License
	for more details.
