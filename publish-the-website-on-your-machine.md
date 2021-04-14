# Publish the website on your machine

Local publishing allows you to share your results with team members.

## Table of Contents

- [Configure IIS]()
- [Publish the website to a folder]()
- [Expose the published website]()
- [Troubleshooting]()

## Configure IIS

1. **Enable IIS**           
Follow the instructions for [Windows 8](https://enterprise.arcgis.com/en/web-adaptor/latest/install/iis/enable-iis-8-components-server.htm) or [Windows 10](https://enterprise.arcgis.com/en/web-adaptor/latest/install/iis/enable-iis-10-components-server.htm).

1. **Install IIS Rewrite Module 2**         
Open Apps & features and make sure that it isn't installed yet. If not, you can download this extension at the following URL: [URL Rewrite](https://www.iis.net/downloads/microsoft/url-rewrite).

1. **Enable Windows features**      
Open Control Panel -> Programs and click Turn Windows Features. In the appeared window, expand Internet Information Services and select items as shown on the following image:

    ![Windows Features](https://github.com/RomanTsukanov/devextreme-wiki-draft/blob/master/images/publish-the-website-windows-features.jpg?raw=true)

## Publish the website to a folder

1. Create a folder in which you will publish the website.

1. Open WebSites.sln in Visual Studio. In Solution Explorer, right-click WebSites.JS.sln and select Publish:

    ![Visual Studio - The Publish item in the context menu](https://github.com/RomanTsukanov/devextreme-wiki-draft/blob/master/images/publish-the-website-visual-studio-publish-context-menu.jpg?raw=true)

1. In the appeared window, change publishing settings. This is how the window should look if everything is done right:

    ![Visual Studio - The Publish window](https://github.com/RomanTsukanov/devextreme-wiki-draft/blob/master/images/publish-the-website-visual-studio-publish-window.jpg?raw=true)

## Expose the published website

1. **Open IIS Manager**     
Control Panel -> System And Security -> Administrative Tools -> Internet Information Services (IIS) Manager

1. **Add a new website**        
In the left-hand menu, right-click Sites and select Add Website:

    ![IIS - The Add Website item in the context menu](https://github.com/RomanTsukanov/devextreme-wiki-draft/blob/master/images/publish-the-website-iis-add-website.jpg?raw=true)

1. **Configure the website**        
Specify the following parameters:
 
    - Site name: any
    - Physical path: a path to the folder in which you published the website
    - Port: any. If you leave 80, make sure that no other site uses the same port.

    ![IIS - The Add Website window](https://github.com/RomanTsukanov/devextreme-wiki-draft/blob/master/images/publish-the-website-iis-add-website-settings.jpg?raw=true)

The website should be available at the following address: `http://PCName:Port/`, for example, `http://TSUKANOV-W10:812/`. If it isn't available, try using the full PC name: `http://TSUKANOV-W10.corp.devexpress.com:812/`.

## Troubleshooting

You may encounter the following error:

```
The type or namespace name '...' could not be found (are you missing a using directive or an assembly reference?)
```

To fix it, change .NET Framework version to 4.6.2. In Solution Explorer, right-click the WebSite.JS project and select Properties. In the appeared tab, click Application in the left-hand menu and select .NET Framework 4.6.2 from the Target framework drop-down menu:

![Visual Studio - How to change target framework](https://github.com/RomanTsukanov/devextreme-wiki-draft/blob/master/images/publish-the-website-visual-studio-.net-framework.jpg?raw=true)