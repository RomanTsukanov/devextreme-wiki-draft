# Add code snippets

We add code snippets for four frameworks: jQuery, Angular, Vue, and React. They are displayed as an accordion. You can see an example in the [customSave](https://js.devexpress.com/Documentation/ApiReference/UI_Components/dxDataGrid/Configuration/stateStoring/#customSave) help topic.

## Table of contents

- [Snippet template]()
  - [Placeholders]()
- [Visual Studio Code configuration]()
- [Keep only relevant code lines]()

## Snippet template

The following is a template for code snippets. It uses placeholders that are described in the [Placeholders](#placeholders) section.

```
---
##### jQuery

    <!-- tab: index.js -->
    $(function() {
        $("#{widgetName}Container").dx{WidgetName}({

        });
    });

##### Angular

    <!-- tab: app.component.html -->
    <dx-{widget-name}>
    </dx-{widget-name}>

    <!-- tab: app.component.ts -->
    import { Component } from '@angular/core';

    @Component({
        selector: 'app-root',
        templateUrl: './app.component.html',
        styleUrls: ['./app.component.css']
    })
    export class AppComponent {
        constructor() {
            
        }
    }

    <!-- tab: app.module.ts -->
    import { BrowserModule } from '@angular/platform-browser';
    import { NgModule } from '@angular/core';
    import { AppComponent } from './app.component';

    import { Dx{WidgetName}Module } from 'devextreme-angular';

    @NgModule({
        declarations: [
            AppComponent
        ],
        imports: [
            BrowserModule,
            Dx{WidgetName}Module
        ],
        providers: [ ],
        bootstrap: [AppComponent]
    })
    export class AppModule { }

##### Vue

    <!-- tab: App.vue -->
    <template>
        <Dx{WidgetName}>
            
        </Dx{WidgetName}>
    </template>

    <script>
    import 'devextreme/dist/css/dx.light.css';

    import Dx{WidgetName}, {
        !!DxNestedComponents
    } from 'devextreme-vue/{widget-name}';

    export default {
        components: {
            Dx{WidgetName},
            !!DxNestedComponents
        },
        data() {
            return {
                
            }
        },
        methods: {
            
        }
    }
    </script>

##### React

    <!-- tab: App.js -->
    import React from 'react';
    import 'devextreme/dist/css/dx.light.css';

    import {WidgetName}, {
        !!NestedComponents
    } from 'devextreme-react/{widget-name}';

    export default function App() {
        return (
            <{WidgetName}>
                
            </{WidgetName}>
        );
    }

---
```

### Placeholders

Replace placeholders `{widgetName}`, `{WidgetName}`, `{widget-name}` with proper component names. For example, if you add a code snippet for the DataGrid component, the replacements will be as follows:

    {widgetName} => dataGrid
    {WidgetName} => DataGrid
    {widget-name} => data-grid

> NOTE: These placeholders were originally designed to support inheritance in help topics. The website replaces them with proper component names at runtime. Nevertheless, we recommend using component names in .md sources to indicate that a help topic is _not_ inherited or reused in any other topic.

In Vue and React, you can see the `!!DxNestedComponents` and `!!NestedComponents` placeholders. Replace them with needed nested configuration components (for example, `DxEditing` in Vue / `Editing` in React, `DxStateStoring` / `StateStoring`, `DxGrouping` / `Grouping` and so on). If your example doesn't use nested components, simply delete the placeholders along with the object within which they are declared.

## Visual Studio Code configuration

If you author docs in VS Code, you can insert the [snippet template](#snippet-template) using a key combination. Do the following to enable this feature:

1. Copy the following archive: \\corp\internal\common\4Tsukanov\VSCode_snippets.zip
1. Extract it to %APPDATA%\Roaming\Code\User

Now, the following keyboard shortcuts are available:

- Ctrl + Shift + S      
Inserts a code snippet template (S in the combination means "snippet").

- Ctrl + Shift + D          
Inserts a template for a demo button (D is for "demo").

## Keep only relevant code lines

Most of the code snippets are abbreviated: they only show how to use a particular component property or methods. When you add a code snippet, remove every code line that doesn't belong to the use-case that the snippet illustrates. For example, if you are demonstrating how to select grid records using the `selectedItemKeys` property, there's no need to show full component configuration&mdash;show how to set this property only.