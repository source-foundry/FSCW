# Font Setup Creator for Windows (FSCW)

Font Setup Creator for Windows (FSCW) is a a toolkit to create a Windows desktop setup installer for fonts. 

It is driven by a [DATA.ini](https://github.com/source-foundry/FSCW/blob/master/src/DATA.ini) file that includes all necessary information about the font(s) to install and uses [Inno Setup](http://www.jrsoftware.org/isinfo.php) to generate the Setup.exe file. If you do not run Windows, a build script for [AppVeyor](https://www.appveyor.com/) is also included. AppVeyor can build the Setup.exe installer automatically each time that you push to your repository.

## Why this project exists

FSCW includes all best practices for font installation on Windows that we have learned while creating the [Windows installer](https://github.com/source-foundry/Hack-windows-installer) for the [Hack typeface](https://github.com/source-foundry/Hack). 

Although it might seem like overkill to use a Windows installer for fonts, there is good reason for this on the Windows platform. A number of things can go wrong when one tries to install or update frequently updated fonts manually (see [issue #152](https://github.com/source-foundry/Hack/issues/152) and [issue #129](https://github.com/source-foundry/Hack/issues/129) in the [Hack repository](https://github.com/source-foundry/Hack/)).

## Setup experience for end users

- User downloads `(SetupExe)` from your repository and double clicks it. 
- User sees a *Windows protected your PC* message: Needs to click on `More info` and then `Run anyway`. 
- **Note:** This *Windows SmartScreen warning* can be safely ignored as it is caused only by the fact that the EXE is not digitally signed. You may want to upload the EXE file to [VirusTotal](http://www.virustotal.com) and link to the report from your repository. 
- User is asked if the font(s) should be installed ([Screenshot](https://github.com/source-foundry/FSCW/raw/master/img/screenshot-install.png)).
- User is asked to to perform a restart ([Screenshot](https://github.com/source-foundry/FSCW/raw/master/img/screenshot-restart.png)).
- Installed font(s) can be used.

To uninstall, the user goes to the *Add/Remove Programs* applet in Control Panel, selects the entry and clicks on *Uninstall* ([Screenshot](https://github.com/source-foundry/FSCW/raw/master/img/screenshot-uninstall.png)).

## How to use it

- Clone this repository
- Delete the test fonts and exchange them for your your own `*.TTF` files (in `/fonts`)
- Update the other files as you see fit (e.g. `License.txt`, icon file etc.)
- Update `src/DATA.ini` to match your own data (Name, copyright etc.)  
- **NOTE** Please always remember to update `UniqueID` in `src/DATA.ini`


## Building on Windows

- Perform the steps described in [How to use it](#how-to-use-it) 
- Download [Inno Setup](http://www.jrsoftware.org/isinfo.php)
- Please make sure the option "Inno Setup Prepocessor" is activated during install
- Open `src\FSCW.iss`
- Select *Build* - *Compile* (CTRL+F9)
- Retrieve your `(SetupExe)` from the `\out` folder

## Building using AppVeyor

[AppVeyor](https://www.appveyor.com/) is a continuous integration (CI) service that provides a Windows based environment and can be freely used for open source projects. You can use it to build `(SetupExe)` if you do not have access to a Windows installation.  

- Perform the steps described in [How to use it](#how-to-use-it)
- Create an account at [AppVeyor](https://www.appveyor.com/) (You can login using your GitHub account)
- Click on the *PROJECTS* tab
- Click *NEW PROJECT*
- Select your repository and click *Add* 
- Push to your repository and AppVeyor will create the setup EXE for you automatically (might take some minutes)
- You can download the `(SetupExe)` file by selecting your project, clicking on *LATEST BUILD* and selecting *ARTIFACTS* 

You can also change [appveyor.yml](https://github.com/source-foundry/FSCW/blob/master/appveyor.yml) so the resulting `(SetupExe)` is added as a new release to you repository. The command for this is only commented out, but requires a GitHub token. Please use *Encrypt data* in the account menu within AppVeyor.com to encrypt your token!   

## Contributions 

Any constructive contribution is very welcome, regarless if it's an [issue](https://github.com/source-foundry/FSCW/issues/new) or a [pull request](https://help.github.com/articles/using-pull-requests/).

If users of the setup experience any difficulties, please open a new [issue](https://github.com/source-foundry/FSCW/issues/new) and include the log file FSCW generates. This log file can be found in C:\Program Files\\`(DestinationFolder)`\\*Log-FSCW.txt*. Please post the entire contents of this log along with the issue.   


## License
Copyright © 2017 [Michael 'Tex' Hex](http://www.texhex.info/) / [Source Foundry](http://sourcefoundry.org/hack/). Licensed under the **MIT License**. For details, please see [LICENSE.txt](https://github.com/source-foundry/FSCW/blob/master/LICENSE.txt).

