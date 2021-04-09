# Prepare a new docs version

## Table of contents

- [Add a new branch to your fork on GitHub](#add-a-new-branch-to-your-fork-on-github)
    - [Clone your fork](#clone-your-fork)
    - [Add upstream](#add-upstream)
- [Ignore docs sources in TortoiseHg](#ignore-docs-sources-in-tortoisehg)
- [Add version to AssemblyInfo.json](#add-version-to-assemblyinfojson)
- [Add DevExtreme sources to the website](#add-devextreme-sources-to-the-website)
    - [Generate DevExtreme sources](#generate-devextreme-sources)
    - [Reference scripts and styles](#reference-scripts-and-styles)
- [Set up static content publishing](#set-up-static-content-publishing)

## Add a new branch to your fork on GitHub

Documentation in the [devextreme-documentation](https://github.com/DevExpress/devextreme-documentation) repository is divided into branches, each branch contains documentation for a major release. When developers start working on a new major release, they add a new branch. You need to add the same branch to your fork. Follow these steps to do it:

### Clone your fork

Open SourceTree and select File -> Clone / New to open the Clone window. In this window, set Source Path to your fork and Destination to a path to the folder where the sources of the new version will be located. Most likely, you will need to create a new folder under `path-to-the-website\Docs\Source`. Name it as the version number, but with an underscore instead of a period, for example, `21_1`. The following image illustrates the Clone window with correct settings:

![SourceTree - The Clone window](https://github.com/RomanTsukanov/devextreme-wiki-draft/blob/master/images/prepare-a-new-docs-version-clone-window.jpg?raw=true)

### Add upstream

In SourceTree, select Repository -> Add Remote. In the appeared Repository Settings window, click Add: 

![SourceTree - Repository Settings](https://github.com/RomanTsukanov/devextreme-wiki-draft/blob/master/images/prepare-a-new-docs-version-repository-settings.jpg?raw=true)

In the appeared Remote details window, enter `upstream` as Remote name and `https://github.com/DevExpress/devextreme-documentation` as URL / Path. Leave the rest of the settings untouched and click OK:

![SourceTree - Remote details](https://github.com/RomanTsukanov/devextreme-wiki-draft/blob/master/images/prepare-a-new-docs-version-remote-details.jpg?raw=true)

Upstream should appear in the left-hand menu under Remotes. Right-click it and select Fetch from upstream:

![SourceTree - Fetch from upstream](https://github.com/RomanTsukanov/devextreme-wiki-draft/blob/master/images/prepare-a-new-docs-version-fetch-upstream.jpg?raw=true)

Now, you can expand upstream and double-click the branch with the new version to checkout it. This will create a local branch.

![SourceTree - Checkout branch](https://github.com/RomanTsukanov/devextreme-wiki-draft/blob/master/images/prepare-a-new-docs-version-checkout-branch.jpg?raw=true)

Finally, push this branch to your fork.

## Ignore docs sources in TortoiseHg

The previous steps added many files to TortoiseHg, because the documentation destination path is inside the website project. Add this destination path to the `.hgignore` file located in the root of the website folder:

```
Docs/Source/21_1/
```

## Add version to AssemblyInfo.json

Open the AssemblyInfo.json file located in the following folder: `path_to_the_website\WebSites.JS\App_Data` and add the new version number to the `SiteVersions` array:

```json
{
  "SiteVersions": [
    // ...
    "21.1.1"
  ]
}
```

## Add DevExtreme sources to the website

### Generate DevExtreme sources

DevExtreme sources are used to run examples embedded into the documentation. To generate the sources, fork the [DevExtreme repository](https://github.com/DevExpress/DevExtreme), go to the branch with the new version (for example, `21_1`), and run the following commands:

```
npm i
npm run build
```

The sources will be compiled into the `artifacts` folder. Copy the `css` and `js` folders from there. Then, open the following directory:

```
path_to_the_website\WebSites.JS\SharedStatic\DevExtreme
```

Create a version folder in this directory, for example `21_1`, and paste the `css` and `js` folders into this folder.

### Reference scripts and styles

References to scripts and styles are stored in partial views. Every docs version has one view for scripts and one for styles. You can find the views in the following directories:

```
path_to_the_website\WebSites.JS\Views\StaticPage\Runner\scripts\
path_to_the_website\WebSites.JS\Views\StaticPage\Runner\styles\
```

In each directory, copy and paste the last view and rename it as the new version. Then, open the views in a text editor, find entries of the old version, and replace them with the new version.

The views are ready. Now, you need to add them to the project so that they are included when publishing the website. Open WebSites.sln in Visual Studio, go to the `scripts` / `styles` folder, right-click the view, and select Include in Project:

![Visual Studio - Include view in project](https://github.com/RomanTsukanov/devextreme-wiki-draft/blob/master/images/prepare-a-new-docs-version-add-runner-to-solution.jpg?raw=true)

## Set up static content publishing

Static content (images, applications) requires additional configuration to be published. Open the following file in a text editor:

```
path_to_the_website\WebSites.JS\WebSites.JS.wpp.targets
```

Add a new `CustomVersion` to the `ItemGroup` of the following `Target`:

```xml
<Target Name="Versions">
    <ItemGroup>
        <!-- ... -->
        <CustomVersion Include="21_1"></CustomVersion>
    </ItemGroup>
</Target>
```

Finally, commit everything to TortoiseHg, and that's it!