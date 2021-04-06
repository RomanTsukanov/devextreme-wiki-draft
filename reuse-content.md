# Reuse content (text, code snippets, images)

## Predefined placeholders

Placeholders are useful when you want to reuse a code snippet or a piece of text with links. Predefined placeholders can be used regardless of how you reuse content; whether through [inheritance](#inheritance-by-default), [imports](#imports), or [includes](#includes), the placeholders work the same.

The following list describes the predefined placeholders and their replacements:

- `{widgetName}`    
Stands for a component name that starts with a lower-case letter: `dataGrid`, `treeList`, `chart`.

- `{WidgetName}`        
Stands for a component name that starts with an upper-case letter: `DataGrid`, `TreeList`, `Chart`.

- `{widget-name}`       
Stands for a component name written in kebab case: `data-grid`, `tree-list`, `chart`.

- `{basewidgetpath}`        
Stands for the following part of an API reference link:     
`https://js.devexpress.com/Documentation/ApiReference/UI_Components/dx{WidgetName}/`

    For example, this notation: `{basewidgetpath}/Configuration/#autoNavigateToFocusedRow` produces the following individual links:

    - https://js.devexpress.com/Documentation/ApiReference/UI_Components/dxDataGrid/Configuration/#autoNavigateToFocusedRow
    - https://js.devexpress.com/Documentation/ApiReference/UI_Components/dxTreeList/Configuration/#autoNavigateToFocusedRow
    
- `{currentpath}`          
Stands for the URL path up until the member name.

    There's only one use case for this placeholder: when you describe a hidden type and need to refer from one property of it to another. For example, [ExportLoadPanel](https://github.com/DevExpress/devextreme-documentation/tree/20_2/api-reference/_hidden/ExportLoadPanel) is a hidden type. In the [shadingColor](https://github.com/DevExpress/devextreme-documentation/blob/20_2/api-reference/_hidden/ExportLoadPanel/shadingColor.md) property description, we refer to the [shading](https://github.com/DevExpress/devextreme-documentation/blob/20_2/api-reference/_hidden/ExportLoadPanel/shading.md) property, which belongs to the same type. In all other cases, prefer `{basewidgetpath}`.

## Inheritance by default

Inheritance by default is a way to share big parts of API reference (entire components or types) to avoid text duplication. If a Child component inherits a Parent component, Child will be added all files of Parent. If Child already contains a file from Parent, the website will merge the content from both files. The merged version will have all attributes (`type`, `default`, `acceptValues`) and sections (short and full descriptions, function parameter descriptions) from the Child file plus those attributes and sections from the Parent file that are missing from the Child file. For example, if a Child file misses a full description, the website will take it from a Parent file with the same name.

Inheritance by default is called so because if a Child inherits a Parent, there's no way to exclude a file or attribute from being inherited. If you need to inherit only specific parts from a specific document, use [imports](#imports).

### Inheritance in the source code (the `inherits` attribute)

Inheritance can be specified in the source code by developers. In this case, DocGen adds the `inherits` attribute to Child. For example, in the following example, DataGrid inherits [GridBase](https://github.com/DevExpress/devextreme-documentation/tree/20_2/api-reference/10%20UI%20Components/GridBase):

[Example](https://raw.githubusercontent.com/DevExpress/devextreme-documentation/20_2/api-reference/10%20UI%20Components/dxDataGrid/dxDataGrid.md)

### Custom inheritance (the `inheritsType` attribute)

Alternatively, you can add the `inheritsType` attribute. It works similarly to `inherits`, but it isn't generated automatically. In the following example, dxHtmlEditor.Options.mentions inherits [dxHtmlEditorMention](https://github.com/DevExpress/devextreme-documentation/tree/20_2/api-reference/_hidden/dxHtmlEditorMention):

[Example](https://raw.githubusercontent.com/DevExpress/devextreme-documentation/20_2/api-reference/10%20UI%20Components/dxHtmlEditor/1%20Configuration/mentions/mentions.md)

## Imports

## Includes

### Without custom placeholders

### With custom placeholders