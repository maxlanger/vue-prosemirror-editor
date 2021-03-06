# Vue Prose

*This plugin was made while creating the editor for [studbits.com](https://studbits.com/). We hope you find it useful!*

A minimal [Prosemirror](https://prosemirror.net/) Wrapper for Vue.js

### Installation

```
npm install vue-prosemirror-editor
```

The `vue-prose` will install prosemirror's dependencies.

You must load the [`style/gapcursor.css`](https://github.com/ProseMirror/prosemirror-gapcursor) styles or define your own styling for the cursor.

### Basic Usage

The most basic usage with an empty editor:

```
// template
<Editor />

// script
import Editor from "vue-prosemirror-editor"

export default {
  components: {
    Editor
  }
}
```

#### Editor

The editor is a component that accepts these props:

* `doc`, an Object, the prosemirror document to be edited. (*Or you can set the `fromContent` prop to true and the document will be parsed from the element with the `#content` id.*)

* `schema`, an Object, the schema to be passed to the editor state.

* `editorProps`, an Object, any props to be passed to editor view.

* `plugins`, an Array, any editor plugins.

* `keyCommands`, a Function, that passes the editor schema so you can register any additional editor key commands.

* `inputRules`, an Array, any custom editor input rules.

* `nodeViews`, an Object, any custom editor node views.

* `interceptTransaction`, a function, can be passed to prevent an editor transaction.

* 'editable', a boolean that represents whether editing is allowed.

* `autofocus`, a boolean. Defaults to true.

* `willCreate`, an event that fires when the editor instance is about to be created. Takes no arguments.

* `didCreate`, an event that fires once the editor instance has been created. Will be called with the editor instance and may be used to configure it further.

* `wasUpdated`, an event that will fire whenever the underlying document changes. It is called with the editor state and schema.


### Advanced Usage

### Editor Views as Vue Components

This package includes a `ComponentView` utility that you can use to register
editor views as vue components.

It can be used as follows:

```
import { ComponentView } from 'vue-prosemirror-editor'
import Menu from '~/components/Menu'

export default class MenuView extends ComponentView {
  constructor (node, view, getPos) {
    // call `ComponentView` constructor with desired component and
    // any props that should be passed to it
    super(Menu, { node, view, getPos })
  }

  // make sure to update any props so that you can handle the logic
  // inside the vue component by watching for changes
  update (node, decs) {
    this.node = node
    return true
  }
}

```

#### Getting Help

If you'd like to report a bug or request a feature, please [open an issue](https://github.com/studbits/vue-prose/issues).

### License

[MIT](./LICENSE)

Copyright (c) 2017 Studbits
