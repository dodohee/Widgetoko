# Widgetoko

A Node.js and Electron demonstration app written in C# then compiled to JavaScript using [Bridge](http://bridge.net) and [Retyped](https://retyped.com). 

Widgetoko enables users to connect to Twitter and watch tweets arrive in real-time that match a specified search term.

<p align="center"><img src="https://user-images.githubusercontent.com/62210/31524623-2c2e3906-af78-11e7-9e00-4df7227fa219.png"></p>

There are several options for installing Widgetoko. Packaged installers are available as .exe (Win) and .dmg (Mac), or you can build the project from the original source code.

## Introduction

[![Video Tutorial](https://user-images.githubusercontent.com/62210/31647625-8def053e-b2c6-11e7-80ad-5164f26fcbd8.png)](https://www.youtube.com/watch?v=qar056MgI5Q)

## Installers

Platform | Version | Installer
---- | ---- | ----
Win | 1.0.0 | [Widgetoko.exe](https://github.com/bridgedotnet/Archives/raw/master/Widgetoko/1.0.0/Widgetoko.exe)
Mac | 1.0.0 | [Widgetoko.dmg](https://github.com/bridgedotnet/Archives/raw/master/Widgetoko/1.0.0/Widgetoko.dmg)

## Build from source

### Requirements

1. Install [Yarn](https://yarnpkg.com)

### Start

1. Clone the [Widgetoko](https://github.com/bridgedotnet/Widgetoko) repo or [download](https://github.com/bridgedotnet/Widgetoko/archive/master.zip) source
1. Using the **Command** (Win) or **Terminal** (Mac), browse to the `/dist` directory
1. Run the following `yarn` command:

```
yarn install
```

If this is your first time running `yarn install` on the `/dist/` folder, **Yarn** may take a few minutes to download the required packages. Just let the process run. 

Once `yarn install` is complete, run the following `yarn start` command and an instance of the **Widgetoko** app should start automatically.

```
yarn start
```

### Compile C# source

The above steps will run the previously compiled JavaScript files within the `/dist` output folder, but it's also very easy to fully recompile the original C# source code in order to regenerate the JavaScript files.

The Widgetoko C# source code can be easily compiled by opening the solution in Visual Stduio, then 

1. Double click the `/src/Widgetoko.sln` file to open in Visual Studio
2. Select `Build` > `Rebuild Solution` from the main Visual Studio menu

Before you can run the app, please ensure you have run the following two `yarn` command. Run the first, and when complete, run the second. 

```
yarn install
yarn start
```

It is also possible to start Widgetoko directly from Visual Studio by clicking the **Start** button or hitting <kbd>F5</kbd> or <kbd>Ctrl</kbd> + <kbd>F5</kbd>, BUT FIRST... there two Project Properties that need to be set (see image below).

1. Right-click on the Widgetoko Project in the Solution, and select **Properties**
2. Under the **Debug** tab, select **Start external program** and paste the value `..\dist\node_modules\electron\dist\electron.exe`
3. In the **Command line arguments** field, paste the value `../../../dists`

Now the **Start** button will work as expected and the Widgetoko app will launch.

![configure-project-properties](https://user-images.githubusercontent.com/62210/31650575-2f3ec39e-b2d5-11e7-9b53-dc115179b8b4.png)

## Configure Twitter Tokens

A connection to the Twitter Stream is required, so we must register the Widgetoko app with Twitter and generate Access Tokens. This is a required step to tap into the Tweet stream.

1. Browse to https://apps.twitter.com/app/new

1. Fill in the fields (App name, Description, WebSite). You should use your own unique Application name, and any values you want for the other fields.

<p align="center"><img src="https://user-images.githubusercontent.com/62210/31524702-9fc74272-af78-11e7-9c31-98827df32c7c.png"></p>

1. Press **Create your Twitter application** button.

1. The application has been created. Now go to **Keys and Access Tokens** tab.

1. Press **Create My access token** button to generate keys.

1. That's it, all tokens are generated:

<p align="center"><img src="https://user-images.githubusercontent.com/62210/31524621-2bff5686-af78-11e7-82de-b7fa528280ce.png"></p>

1. The last step. You should copy-paste those tokens into Widgetoko app. Run Widgetoko, press <kbd>F2</kbd> (or **File** > **Options**) to open **Options** form, paste your tokens as shown below. Click **Save**.

<p align="center"><img src="https://user-images.githubusercontent.com/62210/31524622-2c17c1d0-af78-11e7-87ee-ef4add2af6ed.png"></p>

**Security Notice:**

Your tokens will be saved in **%appdata%/widgetoko/UserSettings.json** in an obfuscated format. You have several options to remove tokens afterwards:
- Just delete that file.
- Replace the **Options** form with empty values, then click **Save** to overwrite your old token values.
- Invalidate the tokens from the Twitter [app configuration](https://apps.twitter.com/app/), or just delete the app from Twitter.

## Build Installers

Creating an actual installer for the Widgetoko app is very simple. To create the installer, use the following steps:

1. Clone this repo (if you have not done so already)
1. With a **Command Window** (Windows) or **Terminal** (Mac), browse to the `/dist` directory
1. Run the following `yarn` commands:

```
yarn install
yarn build
```

Installers can be created for Mac, Windows, and Linux. The installer creation process should take no more than a few minutes, but needs to be run on each platform you support. If you want an .exe for Windows, run the command on a Windows machine. Need a Mac installer? run the command on a Mac. 

The installer files, such as .exe (Win) and .dmg (Mac), will be added to the **/dist/installers/** folder and those files can be deployed to your users.
