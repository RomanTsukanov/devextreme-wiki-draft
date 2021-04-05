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

    For example, the following link: `{basewidgetpath}/Configuration/#autoNavigateToFocusedRow` produces the following individual links:

    - https://js.devexpress.com/Documentation/ApiReference/UI_Components/dxDataGrid/Configuration/#autoNavigateToFocusedRow
    - https://js.devexpress.com/Documentation/ApiReference/UI_Components/dxTreeList/Configuration/#autoNavigateToFocusedRow
    
- `{currentpath}`

## Inheritance by default

### `inherits`

### `inheritsType`

## Imports

## Includes

### Without custom placeholders

### With custom placeholders