# Update Notes

This repository provides resources and scripts to help ease the burden of generating updates for an offline dev environment built around .NET Core and Angular. See the [OfflineEnvironmentPrep](https://github.com/JaimeStill/OfflineEnvironmentPrep) repository for more information.

After everything is retrieved using the steps that follow, the `environment-update` folder can be brought into the offline environment and the updates can be applied.

## Apps

* [.NET Core SDK](https://dotnet.microsoft.com/download)
    * [.NET Core Hosting Bundle](https://dotnet.microsoft.com/download/dotnet-core)
* [NodeJS](https://nodejs.org/en/download/current/)
* [Git](https://git-scm.com/download/win)
* [Yarn](https://yarnpkg.com/en/docs/install#windows-stable)
* [Visual Studio Code](https://code.visualstudio.com/docs/?dv=win64)
* [Chrome](https://www.google.com/intl/en/chrome/browser/desktop/index.html?standalone=1)
* [Firefox](https://www.mozilla.org/en-US/firefox/all/#product-desktop-release)

### Code Extensions

* [Angular Language Service](https://marketplace.visualstudio.com/items?itemName=Angular.ng-template)
* [C#](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)
* [Color Info](https://marketplace.visualstudio.com/items?itemName=bierner.color-info)
* [Debugger for Chrome](https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-chrome)
* [editorconfig](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig)
* [MSBuild](https://marketplace.visualstudio.com/items?itemName=tintoy.msbuild-project-tools)
* [npm Intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.npm-intellisense)
* [Polacode](https://marketplace.visualstudio.com/items?itemName=pnp.polacode)
* [SCSS Formatter](https://marketplace.visualstudio.com/items?itemName=sibiraj-s.vscode-scss-formatter)
* [SVG](https://marketplace.visualstudio.com/items?itemName=jock.svg)
* [tslint](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-typescript-tslint-plugin)

#### Code Themes

* [Atom One Dark](https://marketplace.visualstudio.com/items?itemName=akamud.vscode-theme-onedark)
* [Forest Night](https://marketplace.visualstudio.com/items?itemName=sainnhe.forest-theme)
* [Gatito](https://marketplace.visualstudio.com/items?itemName=pawelgrzybek.gatito-theme)
* [Horizon](https://marketplace.visualstudio.com/items?itemName=jolaleye.horizon-theme-vscode)
* [Material Icon Theme](https://marketplace.visualstudio.com/items?itemName=PKief.material-icon-theme)
* [New Moon](https://marketplace.visualstudio.com/items?itemName=taniarascia.new-moon-vscode)


> Copy contents of `%USERPROFILE%\.vscode\extensions\ms-vscode.csharp-{version}` to `environment-update\user-profile\.vscode\extensions`

## .NET Core

1. Make sure `dotnet-ef` is up to date:
    * `dotnet tool update --global dotnet-ef`
    * Copy updated tools directory to `environment-update\user-profile\.dotnet`
2. Download the latest .NET Core SDK and save to `environment-update\apps`
3. Run the `update-dotnet` script

## Angular

1. Run the `update-ng` script
2. Roll back incorrect dependency packages.
    * For example, if `zone.js@0.10.2` is installed, but `@angular/core@8.2.14` depends on `zone.js@~0.9.1`, use `npm view zone.js versions --json` to find the latest `0.9.x` version, and install it using `yarn add zone.js@0.9.x`.
3. Save the latest version of the `node-sass` binaries, if missing, from [Releases](https://github.com/sass/node-sass/releases) to `environment-update\infrastructure\node-sass`
4. Save the latest build of `.node-gyp` from `%USERPROFILE%\.node-gyp` to `environment-update\user-profile\.node-gyp`
