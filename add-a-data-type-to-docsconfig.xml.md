# Add a data type to DocsConfig.xml

Each API member has a data type that can be predefined (Number, String, Boolean) or custom ([BarGaugeBarInfo](https://js.devexpress.com/Documentation/ApiReference/Common/Object_Structures/BarGaugeBarInfo/), [ExcelExportDataGridProps](https://js.devexpress.com/Documentation/ApiReference/Common/Object_Structures/ExcelExportDataGridProps/), [DiagramShape](https://js.devexpress.com/Documentation/ApiReference/Common/Object_Structures/dxDiagramShape/)). In an API reference article, a type refers to a resource that gives more information about it. For example, on the following image, everything in orange are types displayed as links (original help topic: [Diagram.onRequestEditOperation](https://js.devexpress.com/Documentation/ApiReference/UI_Components/dxDiagram/Configuration/#onRequestEditOperation)). 

![Diagram - onRequestEditOperation API description](https://github.com/RomanTsukanov/devextreme-wiki-draft/blob/master/images/add-a-type-to-docsconfig-ref-example.jpg?raw=true)

Correspondence between a type and a link is defined in the following file:

```
%path_to_the_website%\WebSites.JS\App_Data\DocsConfig.xml
```

It's an XML document that contains a collection of `DataType` entries, each of which has the following structure:

```xml
<DataType>
    <Text>[Display Text](/link/to/my/type)</Text>
    <RegExp>^dxMyType$</RegExp>
</DataType>
```

Here, `<RegExp>` is a regular expression used to select the needed type; `<Text>` is a substitution for the matched type. Refer to the DocsConfig.xml file for real-world examples.