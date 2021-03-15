# Run the website on your machine

Our website project is stored in the following Mercurial repo: https://hg/mobile_website

## Table of contents

- [Configure the website project](#configure-the-website-project)
  - [Download and install TortoiseHg GUI](#download-and-install-tortoisehg-gui)
  - [Clone the website repo](#clone-the-website-repo)
  - [Update security settings](#update-security-settings)
  - [Open the WebSites.sln solution](#open-the-websitessln-solution)
  - [Define WebSites.JS as a startup project](#define-websitesjs-as-a-startup-project)
  - [Disable "Stop debugger when browser window is closed" (optional)](#disable-stop-debugger-when-browser-window-is-closed-optional)
- [Fork and clone the documentation repository](#fork-and-clone-the-documentation-repository)
  - [Fork the documentation repo](#fork-the-documentation-repo)
  - [Clone the documentation repo](#clone-the-documentation-repo)
  - [Download and install a GUI to work with Git](#download-and-install-a-gui-to-work-with-git)
  - [Open tabs in SourceTree](#open-tabs-in-sourcetree)
  - [Run the website](#run-the-website)
- [Generate content maps](#generate-content-maps)

## Configure the website project

### Download and install TortoiseHg GUI

You can get it from https://tortoisehg.bitbucket.io/. This is a GUI client for Mercurial repos. Other GUI clients exist, but we recommend sticking with TortoiseHg because the entire DevExtreme team uses it.

### Clone the website repo

Select File > Clone Repository. In the appeared window, do the following:

- Specify https://hg/mobile_website as Source and a folder on your machine as Destination.
- Expand Options and check Do not verify host certificate to prevent the SSL:CERTIFICATE_VERIFY_FAILED error.
- Click Clone and wait&mdash;this process takes a while.

    ![Clone window](https://github.com/RomanTsukanov/devextreme-wiki-draft/blob/master/images/run-website-on-your-machine-clone-window.jpg?raw=true)

### Update security settings

Open the Security window, query a host fingerprint, and enter your CORP username and password, as shown on the image below:

![Security window](https://github.com/RomanTsukanov/devextreme-wiki-draft/blob/master/images/run-website-on-your-machine-security-window.jpg?raw=true)

### Open the WebSites.sln solution

Go to the folder with cloned website project and open WebSites.sln in Visual Studio. You may see the following error message:

![.NET Framework error](https://github.com/RomanTsukanov/devextreme-wiki-draft/blob/master/images/run-website-on-your-machine-net-framework-error.jpg?raw=true)

Don't change the framework version. Instead, modify the VS installation to include .NET Framework 4.6.2. In Visual Studio, select Tools > Get Tools and Features to run Visual Studio Installer. In this installer, switch to the Individual components tab, select .NET Framework 4.6.2 components, and click Modify:

![.NET Framework installation](https://github.com/RomanTsukanov/devextreme-wiki-draft/blob/master/images/run-website-on-your-machine-net-framework-installation.jpg?raw=true)

After installation, try to open WebSites.sln again, and the issue should be gone.

### Define WebSites.JS as a startup project

In Solution Explorer, right-click WebSites.JS and click Set as Startup Project. Do not run the project as you haven't added documentation sources yet. Now, you should fork and clone the documentation repo.

### Disable "Stop debugger when browser window is closed" (optional)

Visual Studio stops the project when you close the tab with it in the browser. You don't need this feature because our website tracks changes in source files and applies them without a restart.

To disable it, go to Tools > Options > Projects and Solutions > Web Projects and deselect the Stop debugger when browser window is closed checkbox.

## Fork and clone the documentation repository

### Fork the documentation repo

Go to https://github.com/DevExpress/devextreme-documentation and click Fork in the upper-right corner. Branches in this repo correspond to major DevExtreme releases (20_1, 20_2, 21_1, and so on).

### Clone the documentation repo

Go to the folder where you cloned the website project and run `PrepareWebSite.bat`. It will prompt you to enter your GitHub nickname. This .bat creates multiple clones of the docs repo&mdash;one for every major DevExtreme version.

#### Why do I need multiple clones?

We maintain docs for three DevExtreme versions (previous, current, and future), each has a separate branch. Let's call them "main branches". When you edit docs, you create many other branches-descendants from the main branches. With so many branches at hand, it's easy to confuse which branch descents from which. Multiple clones make sure that this doesn't happen as you always work with a specific branch and its descendants in a separate clone. With multiple clones, it's also easy to run multiple docs versions on the website simultaneously.

### Download and install a GUI to work with Git

The DevExtreme team mostly uses SourceTree - https://www.sourcetreeapp.com/ If you are a devoted user of the command line, install SourceTree anyway because your collagues might need it when you will work on some document together.

### Open tabs in SourceTree

Open the SourceTree, select File > Open, and specify a folder with a cloned docs version. For example, %path_to_the_site%\Docs\Source\20_2. This is where you will be working with version 20.2. Repeat this step for all the needed versions (previous, current, and future).

### Run the website

Open WebSites.sln (if you haven't done it yet) and press F5.

## Generate content maps

Content maps are XML files compiled from .md sources. Each docs version have its own pair of content maps: `JS-ApiReference.xml` and `JS-Howto.xml`. Content maps are stored alongside the md sources:

![Generated content maps](https://github.com/RomanTsukanov/devextreme-wiki-draft/blob/master/images/generate-content-maps-xml-files.jpg?raw=true)

Usually, content maps are generated automatically when you run the website project. For this, you need node.js:

1. Download node.js from https://nodejs.org/en/download/ and install it. 

1. Open PowerShell and type the `node -v` command to check your node version. It should be 12+.

1. Ensure that this node.js instance is the only one on your computer: check the following folder: C:\Program Files (x86). If there is a nodejs folder, delete it. 

You can also generate content maps manually. This may be needed if the website project throws an error when generating content maps.

1. Go to %path_to_the_site%\Docs\Source\20_2 or a folder with another docs version and open it in PowerShell or another command line terminal.

1. Run the following command to install all the needed tools:

        npm i

    If the installation fails, open `package.json` in this folder. Check the following line: `devextreme-internal-tools`. Its value should be `"stable"`.

1. Run the following command to generate the content maps:

        npm run generate-content-map