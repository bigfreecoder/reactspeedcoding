# Define Component Internals

This chapter does a deep dive into best practices for defining your React component internals.
We will add naming conventions to our best practice guidance, mostly following two sources.

- The official [Facebook React docs and tutorials][2]
- [Airbnb React style guide][1]

We will also add ES6 features and best practices which make your component design
more readable, reusable, and robust.

In this chapter we will also expand on our React Speed UI framework by adding several
new components.

{pagebreak}

## Naming files, folders, and modules

- Use ```.jsx``` extension for React components.
- Entry point for app is ```/app/index.jsx``` file.
- Root component name ```app``` is picked up from folder containing ```index.jsx``` file.
- PascalCase for component file names. Like ```CardStack.jsx``` component.
- Use PascalCase for referencing imported React components.
- Use camelCase for variable names representing instances of React components.
- Presentational components go into ```/app/components``` folder.
- Container components go into ```/app/containers``` folder.

- Entry point for styles is ```/app/style.css``` file which imports the partials.
- Style partials follow ```_component_name.css``` naming within ```/app/styles``` folder.

Some guidance on styles organization suggests keeping css and component jsx together. We
see several benefits of keeping styles separate and not alongside components.

- We can organize styles using the popular 7-1 pattern used by many CSS frameworks.
- We can organize partials and main imports file in one place.
- Styles for container and presentational components can be in same file logically.
- If you have a designer and developer in your team, they could be working on their own
folders with clearly defined interfaces in the form of naming conventions and organization principles.
- You can easily package your UI framework styles for independent distribution if required.

{pagebreak}

## Imports and exports

A> Note that import and export of modules is an ES6 feature.

You will start React component definition with a set of import statements referencing
modules which are your component dependencies. You will also export the component you are
defining in a ```ComponentName.jsx``` file.

- Use ```import ComponentName from 'library';``` statement to import modules.
- App entry point ```index.jsx``` requires React and ReactDOM modules.
- ReactDOM module exposes DOM-specific methods.
- React module has the core tools shared by React on different platforms like, React Native.
- You can use ```import {Module1, Module2} from 'library';``` to import specific modules
directly.

This way you can reduce some coding by referencing these modules directly.

```
import React, {PropTypes} from 'react';
```

- Alias an imported member name and use the alias within your code.

```
import React, {VeryLongModuleName as shortName} from 'react';
```

- Use ```export default``` statements to prefix component name declaration for exporting.

```
export default class Card extends React.Component {...

export default function YouTube(props) {...
```

{pagebreak}

## Stateless components

- If there are no states or refs then prefer normal functions over classes.
- Multiple stateless components are allowed per file.
- You can declare a stateless component function with props.
- Declare a stateless component function with specific properties using destructuring assignment.

```
export default function YouTube(props) {...

export default function YouTube({videoid}) {...
```

- Cannot use stateless components when rendering ```this.props.children``` within your component.

{pagebreak}

## Classes and inheritance

- Only one class defined component per file.


## Constructor and binding

When to use and how.

## Property types

Various tricks we can do with properties like spread operator, destructuring assignment,
Component for custom DOM element as property.

## State management

When to use state and how.

## Lifecycle methods

How to decide which lifecycle methods to use and why.

## Render and ReactDOM.render methods

Important things to remember about render method and ReactDOM.render.

- ReactDOM.render method should only be called after the composite components have been defined.
- ReactDOM.render instantiates the root component, starts the react framework, and injects the
markup into a raw DOM element, provided as the second argument.

{pagebreak}

## JSX features and syntax

JSX is what you write within ```render() return()``` method. JSX gets transpiled to JS
by Babel in our build environment.

- JSX HTML-like tags are React framework components representing HTML tags and attributes.
- JSX components use ```className``` instead of ```class``` when specifying CSS classes.

I> ## Chapter In Progress
I> We are still writing this chapter. Please watch this space for updates.
I> Plan is to add checklist of guidance for each section of component definition.


[1]: https://github.com/airbnb/javascript/tree/master/react
[2]: https://facebook.github.io/react/index.html