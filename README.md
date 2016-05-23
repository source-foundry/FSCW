# Font Setup Creator for Windows (FSCW)

Font Setup Creator for Windows (FSCW) is a a toolkit to create a Windows desktop setup for fonts. 

It is driven by a [DATA.ini](https://github.com/source-foundry/fscw/blob/master/src/Data.ini) file that includes all necessary information about the font(s) to be installed. The Setup EXE file is automatically generated using [Inno Setup](http://www.jrsoftware.org/isinfo.php). If you do not run Windows, a build script for [AppVeyor](https://www.appveyor.com/) is also included. This allows AppVeyor to build the Setup EXE for you each time you push to your repository.

## Why this project exists

FSCW includes all best practises for font installation on Windows we have learned while creating the [Windows installer](https://github.com/source-foundry/Hack-windows-installer) for the [Hack typeface](https://github.com/chrissimpkins/Hack). 

Although it might seem like overkill to use a Windows installer for fonts, there is good reason for this on the Windows platform. A number of things can go wrong when one tries to install or update frequently updated fonts manually (see [issue #152](https://github.com/chrissimpkins/Hack/issues/152) and [issue #129](https://github.com/chrissimpkins/Hack/issues/129) in the [Hack repository](https://github.com/chrissimpkins/Hack/)). 


## License
Copyright © 2016 [Michael 'Tex' Hex](http://www.texhex.info/) / Source Foundry. Licensed under the **MIT License**. For details, please see [LICENSE.txt](https://github.com/source-foundry/Hack-test-win-installer/blob/master/LICENSE.txt).

