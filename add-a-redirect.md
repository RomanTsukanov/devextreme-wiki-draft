# Add a redirect

Redirects are stored in the following file:

```
%path_to_the_website%\WebSites.JS\App_Data\Redirect.xml
```

Examples with commentaries:

```xml
<!-- Redirect from Filtering to Filtering and Searching since v20.1 -->
<Redirect
    source="/Documentation/Guide/Widgets/DataGrid/Filtering/"
    destination="/Documentation/Guide/UI_Components/DataGrid/Filtering_and_Searching/"
    fromversion="20_1">
</Redirect>


<!-- Redirect from Filter Nodes to Search Nodes since v17.2 up until v19.2 -->
<Redirect
    source="/Documentation/Guide/Widgets/TreeView/Filter_Nodes/"
    destination="/Documentation/Guide/Widgets/TreeView/Search_Nodes/"
    fromversion="17_2"
    toversion="19_2">
</Redirect>

<!-- Redirect from Visual Elements to Overview in v20.1 only -->
<Redirect
    source="/Documentation/Guide/Widgets/Scheduler/Visual_Elements/"
    destination="/Documentation/Guide/UI_Components/Scheduler/Overview/"
    version="20_1">
</Redirect>
```

Whenever you add a redirect, search the entire XML document for your `source` link. If this link is used as a `destination` for another redirect, you have to add more redirects. For example, if you add the following redirect:


```xml
<Redirect
    source="/Documentation/Guide/Themes_and_Styles/SVG-Based_Widgets_Customization/"
    destination="/Documentation/Guide/Themes_and_Styles/SVG-Based_Components_Customization/"
    fromversion="20_2">
</Redirect>
```

... search the document for `SVG-Based_Widgets_Customization`. If you find a redirect where this term is used as `destination`, add the `toversion` attribute to it and create one more redirect that maps the oldest link to the newest one:

```xml
<Redirect
    source="/Documentation/Guide/Widgets/Common/Data_Visualization_Widgets/Appearance_Customization/"
    destination="/Documentation/Guide/Themes_and_Styles/SVG-Based_Widgets_Customization/"
    fromversion="18_2"
    toversion="20_1">
</Redirect>

<Redirect
    source="/Documentation/Guide/Widgets/Common/Data_Visualization_Widgets/Appearance_Customization/"
    destination="/Documentation/Guide/Themes_and_Styles/SVG-Based_Components_Customization/"
    fromversion="20_2">
</Redirect>
```