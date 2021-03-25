# Rearrange articles in the documentation tree

You can modify the documentation tree in the following file:

```
%path_to_the_website%\Docs\Source\%docs_version%\MenuConfig.xml
```

It's an XML document that contains a collection of `MenuRule` entries, each of which has the following structure:

```xml
<MenuRule SourcePattern="ApiReference:%regexp%" Destination="%destination/path%" />
```

or

```xml
<MenuRule SourcePattern="Howto:%regexp%" Destination="%destination/path%" />
```

Menu rules map folders and MD files to specific positions in the documenation tree. To understand how the rules work, we need an example. Let's imagine that we have a folder called `50 React Components`, and it contains the following files and subfolders:

```
50 React Components
- 02 Create a DevExtreme Application.md
- 05 Add DevExtreme to a React Application
    - 00 Add DevExtreme to a React Application.md
    - 01 One-Command Setup.md
    - ...
- 20 State Management
    - 0 State Management.md
    - 3 Controlled Mode.md
    - ...
- 40 Component Configuration Syntax
    - 00 Component Configuration Syntax.md
    - 05 Static Property Value.md
    - ...
```

And suppose that we want to do the following alterations:

- Rename `React Components` to `React`.
- Move `02 Create a DevExtreme Application.md` and `05 Add DevExtreme to a React Application` to a new `Getting Started` folder.
- Leave the rest of the articles under `React`.

So, the result that we want to see in the documentation tree would be the following:

```
React
- Getting Started
    - Create a DevExtreme Application
    - Add DevExtreme to a React Application
        - One-Command Setup
        - ...
- State Management
- Component Configuration Syntax
```

To achieve this, we should add the following rules to the MenuConfig.xml:

```xml
<!-- Move "Create a DevExtreme Application" and "Add DevExtreme to a React Application" to "React/Getting Started" -->
<MenuRule SourcePattern="Howto:^50 React Components/(02 Create a DevExtreme Application|05 Add DevExtreme to a React Application)" Destination="bb12 React/ab02 Getting Started/$1" />

<!-- Move the rest of the "React Components" contents to "React"-->
<MenuRule SourcePattern="Howto:^50 React Components/(.*?)" Destination="bb12 React/ab$1" />

<!-- Hide the "React Components" folder itself -->
<MenuRule SourcePattern="Howto:^50 React Components" Destination="" />
```
Note that each rule contains the `Howto` prefix. It specifies that the rule moves custom documents, or guides. If you want to move an API reference article, use the `ApiReference` prefix.

Also note the prefixes in `Destination` values (`bb12`, `ab02`, `ab`). Articles in the documentation tree are sorted in alphabetical order, and these prefixes allow you to control the sorting. They are not hardcoded anywhere, so you can come up with your own prefixes.
