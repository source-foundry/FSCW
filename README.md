# Font Setup Creator for Windows (FSCW)

Font Setup Creator for Windows (FSCW) is a a toolkit to create a Windows desktop setup for fonts. 

It is driven by a [DATA.ini](https://github.com/source-foundry/fscw/blob/master/src/Data.ini) file that includes all necessary information about the font(s) to install. The Setup EXE file is automatically generated using [Inno Setup](http://www.jrsoftware.org/isinfo.php). If you do not run Windows, a build script for [AppVeyor](https://www.appveyor.com/) is also included. This will cause AppVeyor to build the Setup EXE for you each time you push to your repository.

## Why this project exists

FSCW includes all best practises for font installation on Windows we have learned while creating the [Windows installer](https://github.com/source-foundry/Hack-windows-installer) for the [Hack typeface](https://github.com/chrissimpkins/Hack). 

Although it might seem like overkill to use a Windows installer for fonts, there is good reason for this on the Windows platform. A number of things can go wrong when one tries to install or update frequently updated fonts manually (see [issue #152](https://github.com/chrissimpkins/Hack/issues/152) and [issue #129](https://github.com/chrissimpkins/Hack/issues/129) in the [Hack repository](https://github.com/chrissimpkins/Hack/)).

## Setup experience for the generated setup

- Uses downloads `(SetupExe)` from your repository and double clicks it. 
- User sees a *Windows protected your PC* message, clicks on `More info` and selects `Run anyway`. 
- **Note:** The appearing *Windows SmartScreen warning* can be safely ignored as it is caused only by the fact that the EXE is not digitally signed. You may want to upload the EXE file to [VirusTotal](http://www.virustotal.com) and link to the report from your repository. 
- User asks if the font(s) should be installed
- **SCREENSHOT**
- `(SetupExe)` asks the user to perform a restart 
- Font can be used.

To uninstall, the user goes to the *Add/Remove Programs* applet in Control Panel, selects the entry and clicks on *Remove*.
**SCREENSHOT**

## How to use it

- Clone this repository
- Delete the test fonts and exchange them for your your own `*.TTF` files (in `/fonts`)
- Update the other files as you see fit (e.g. `License.txt`, icon file etc.)
- Update `src/DATA.ini` to match your own data (Name, copyright etc.)  
- **NOTE** Please always remember to update `UniqueID` in `src/DATA.ini`

## Building on Windows

- Download [Inno Setup](http://www.jrsoftware.org/isinfo.php)
  - Please make sure the option "Inno Setup Prepocessor" is activated during install
- Open `src\FSCW.iss`
- Select *Build* - *Compile* (CTRL+F9)
- Retrieve your `(SetupExe)` from the `\out` folder

## Building without Windows (using AppVeyor)

[AppVeyor](https://www.appveyor.com/) is a continuous integration (CI) service that provides a Windows based environment and can be freely used for open source projects. You can use it to build `(SetupExe)` if you do not have access to a Windows installation.  

To use it, do the following:
- Clone this repository
- Delete the test fonts and exchange them for your your own `*.TTF` files
- Update the other files as you see fitr (e.g. License.txt) 
- Update *DATA.ini* to match your font(s), copyright information etc.
- Create an account at [AppVeyor](https://www.appveyor.com/) (You can login using your GitHub account)
- Click on the *Projects* tab
- Click *NEW PROJECT*
- Select your repository in the last and click *Add* 
- Push to your repository and AppVeyor will create the setup EXE for you automatically (might take some minutes)
- You can download the EXE file by selecting your project, clicking on *LATEST BUILD* and selecting *ARTIFACTS* 



## License
Copyright © 2016 [Michael 'Tex' Hex](http://www.texhex.info/) / Source Foundry. Licensed under the **MIT License**. For details, please see [LICENSE.txt](https://github.com/source-foundry/Hack-test-win-installer/blob/master/LICENSE.txt).

