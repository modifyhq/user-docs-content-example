---
id: create-and-collaborate
title: Create and collaborate
kind: doc
---

## Create and collaborate

The repository's editor supports real-time collaboration on any plain text [reference/#Artifact], including markdown/MDX docs and yaml registers. 

To share an artifact with someone who is already a member of your team, copy the url using the toolbar icon and send it to them.

To share an artifact with someone who is not a member of your team, click the Share button in the repository's header and send an email invite.

You can move between workspaces, workspace branches, connectors and artifacts using the breadcrumb in the header.

### Configure your layout 

You can configure your repository's layout to align with your preferences.

Use the view selector dropdown to select the view combination you want - editor or preview for markdown/MDX docs; editor, table or board for yaml registers.

### Create a markdown doc

To add a markdown [reference/#Doc], hover over a directory in your repository's tree, click the plus button, select New file and fill out the form, being sure to add an `.md` file extension.

You can now add content to your doc using [GitHub-flavoured markdown](https://github.github.com/gfm/).

<InfoMessage icon="lightbulb" header="Pro Tip" content="If your markdown is rusty, use the editor's syntax cheatsheet for a refresh and toolbar to add it to your docs"/>

### Add components with MDX

[MDX](https://mdxjs.com/) enables you to extend your markdown docs with powerful visual components.

You can use the editor's MDX cheatsheet to learn how the syntax works by clicking the syntax button in the editor's header. 

Clicking the `</>` button next to it, will launch a palette will available MDX components, where you can add MDX like this:

<ArtifactTable field="kind" exact="doc" prefix="" postfix=""/>

For contextual info on MDX syntax, you can hover over a component's name in your editor and inspect the tooltip. 

<InfoMessage icon="heart" header="What's cookin'" content="✨ We're currently working on an npm package that will allow you to use our built-in MDX and other Modify syntax in your React and Vue apps. We also plan to add to our built-in component library, as well as support third-party components so you can bring your own ✨ "/>

### Create a yaml register

To add a [reference/#Register], hover over a connector directory in your repository's tree, click the plus button, select New register and fill out the form.

You'll now see a `.modify.yaml` file in your register's directory, which contains configuration data and the schema for your register.

#### Define a schema

The quickest way to see a schema in action is to choose one of the templates provided, which you can then adapt to your own needs.

Once selected, you'll be redirected to the table view. If you inspect the `.modify.yaml` file, you'll see the schema matches the columns in the table view.

You can also use the schema editor to define or update your schema by clicking the cog button in the table view's header.

### Using different views

You can edit register source files in the editor, or with the table, board and form graphical views.

To use a graphical view, select the register directory in your tree and use the view dropdown to select the view you want. 

To use your editor, simply select the yaml files in your tree. 

Whichever view you decide to use, fields and their values are mapped between views, so they will always stay in sync.

### Upload files

You can upload files individually or in bulk by clicking the Upload files button in the repository's header.

In the modal, select a target connector and directory destination, the files you want to upload.

You can upload any files to your workspace. We provide editors for any text file format (markdown, MDX, yaml, csv, json, xml, plain text) along with live previews. 

We also provide viewers for common image formats (png, jpeg, svg) and you can download binary files for formats that don't have viewers.

MS Word documents (`*.docx`) will also be converted to markdown files automatically, to enable you to edit them and add front matter.

### Add front matter

[reference/#Front-matter] contains structured metadata that is indexed and can be used to search for and reference artifacts in your workspace using relationships and MDX elements. 

You can add it to a markdown doc or yaml register by clicking the Add front matter button in the editor or preview view headers and filling out form. 

Alternatively, you can add front matter directly to your artifact, ensuring that it is the first thing in your file and takes the form of valid yaml between triple-dashed lines e.g.

```yaml
---
id: my-id
title: My title
---
```

Currently, `id` and `title` fields are indexed automatically and searchable using the editor's artifact search.

### Define relationships

[reference/#Relationships] allow you to reference artifacts in connectors in your workspace. This can be achieved in a few ways: 

- using an artifact's `id` like so `[id-goes-here]`
- using the Link MDX component like so `<Link artifactId="..."/>`
- or by adding a relationship to front matter like so:

```yaml
---
relationships:
  - id: my-file
    direction: from | to
    kind: implements | foo | bar | baz
---
```

To search for an artifact, press CTRL + Space, search for an artifact by `id` or `title`, and add it to a file with the plus icon.

You can view a graph or table of relationships by clicking the Relationships button in the side panel on the right. 

You can then navigate between nodes in the graph or artifacts in the table using the links provided.

### Add diagrams

You can define `diagrams` using the text-based formats [mermaid](https://mermaid-js.github.io/mermaid), [graphviz](https://graphviz.org) and [nomnoml](https://nomnoml.com).

You can add example diagrams to your docs using the editor's palette.

Syntax for a simple mermaid diagram looks like:

````
```mermaid
stateDiagram-v2
    [*] --> Still
    Still --> [*]

    Still --> Moving
    Moving --> Still
    Moving --> Crash
    Crash --> [*]
```
````

which renders to:

```mermaid
stateDiagram-v2
    [*] --> Still
    Still --> [*]

    Still --> Moving
    Moving --> Still
    Moving --> Crash
    Crash --> [*]
```

Use the preview to see `diagrams` rendered on the fly and spot syntax errors.

<InfoMessage icon="lightbulb" header="Pro Tip" content="Check out the mermaid, graphviz and nomnoml websites for examples to adapt in your own diagrams."/>

### Add images 

You can upload images to your workspace using the upload feature, then using markdown syntax to reference your image file like so `![alt text](image-file.png)`.

### Use editor shortcuts

The text editor supports keyboard shortcuts for a number of common actions. Right click anywhere in the editor and select Command palette in the context menu to see a list of available shortcuts.

### Commit changes

To [reference/#Commit-changes] to your connectors, click the commit changes button in the repository's header.

Next, add a commit message describing your change, select the files you want to commit, and click the Commit button to write them to your connector's configured Git repository.

### Inspect commit history

To inspect your commit history, hover over a file in your tree and click the history icon to show a list of all your commits.

In the modal, click on a commit ID to inspect a diff of a specific commit vs. the immediately preceding one.

### Merge changes

To merge changes from one workspace branch into another click the Merge button in the repository's header.

First, ensure you have committed your changes to the branch you want to update from, otherwise they will not be able to merge.

Next, select the target branch (defaulted to your current branch) and source branch (branch to update from). 

Finally check the diff shows the expected changes and click the Update from workspace branch button to perform the merge.

Currently, conflicts are merged as part of the update operation, and can be resolved manually with a subsequent commit. We plan to improve this in the near future.
