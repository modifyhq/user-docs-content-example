---
id: reference
title: Reference
kind: doc
---

## Domain model 

A domain model represents a graph of related objects, or entities. Each entity in the model comprises both behavior and data. 

Modify's domain model can be visualised as an entity relationship diagram (ERD):

```nomnoml
[User]->1..*[Team]
[User]->1[Personal Team]
[Team]->0..*[Workspace]
[Personal Team]->[Workspace]
[Workspace]->1..*[Workspace Branch]
[Workspace]->0..*[Connector]
[Connector]->[Connector Branch]
[Workspace Branch]->1..*[Connector Branch]
[Workspace Branch]->0..*[Job]
[Connector Branch]->0..*[Artifact]
[Job]->0..*[Job Instance]
[Job Instance]-->[Artifact]
[Artifact]->[Relationship]
[Relationship]->[Artifact]
[Workspace Branch]->0..*[Review]
[Review]->[Review Branch]
[Review Branch]-->[Workspace Branch]
```

These entities and their relationships are described below. 

## User

A user is anyone with a Modify account. 

Users can either sign up individually or be invited to an existing team. 

If a user signs up individually, a new personal team is automatically created. Existing users can create additional teams or be invited to other existing teams.

## Team

Primarily, a team groups users and workspaces. Users collaborating in workspaces must be part of a common team.

In future, granular roles and permissions for users within a team are planned. 

## Workspace

A workspace is a child of a team and serves as a container for connectors, reviews and jobs. A team can have one or more workspaces.

### Workspace branch

A workspace has a base branch by default, and may also have one or more downstream branches. 

Connectors are always added to a workspace's base branch and can be integrated into downstream branches using the repository's merge operation.

Branching a workspace creates branches of all its connectors and their contents, including changes committed to connectors and uncommitted changes in working copy (stored in Modify).

## Connector

Connectors are read-write integrations to Git repositories hosted in Modify, GitHub or Bitbucket and can be added to a workspace's base branch from the repository or connectors page. 

A workspace can have one or more connectors, supporting teams use a mono or multiple repository strategy for managing their files, or artifacts as we call them.

### Commit changes

A commit groups changes to artifacts stored in your working copy and writes them to the Git repositories configured in your workspace's connectors. 

In Git terms, you can think of a commit as equivalent to staging, committing and pushing to a remote repository all in one.

Committing often is encouraged, as it's a great way for you to stay in control of your data.

As with code, writing a commit message helps you identify commits when you need to in the file-level commit history accessible in the repository's tree.

### Modify-hosted connector

Modify connectors are integrations with Modify-hosted Git repositories, which can be optionally exported to an external Git provider on demand.

They are created automatically with an editable base branch, though this can configured.

### External Git provider connector

Currently we support GitHub and Bitbucket as external Git providers. 

In order to add a connector to an external provider to a workspace, you must first authenticate with the provider and install the Modify app on an organisation (GitHub) or workspace (Bitbucket) in your account. 

Next, configure your connector to point at an existing remote repository and branch (e.g. `github.com/username/repo` and `master`) and add it to your workspace in Modify.

#### Branches on external Git provider connectors

The remote branch of an external provider connector is added to your workspace's base branch with a protected access mode by default. This means its contents cannot be edited directly using the repository's editor.

To edit artifacts, you must first create a downstream workspace branch. Connectors on downstream workspace branches have an editable access mode by default.

Remote branches configured in external provider connectors are **user controlled** - that is, they are created and managed outside of Modify. If you already use Git, they're simply the normal branches you're familiar with.

- Modify will only ever perform two operations on a user-controlled branch - (i) reading from it and (ii) fast-forward merging back to it when requested via a review. This ensures you can work on these branches outside of Modify, using your normal tools and workflow, *without having to worry about changes being overwritten*.

Downstream workspace branches created in Modify, on the other hand, are **Modify-controlled**  - that is, they are created in Modify at the user's request and should be interacted with solely through Modify.

- Modify-controlled branches and their changes are written back to the configured Git remote so that you always have access to their data. However, these branches should not be worked on outside of Modify, as any changes made to them *will* be overwritten by changes committed in Modify. 

## Artifact

Artifacts are files stored in connectors. You can upload any files to your workspace.

You can edit and collaborate on artifacts with any text file format (markdown, MDX, yaml, csv, json, xml, plain text).

### Doc

Docs are version-controlled markdown and [MDX](https://mdxjs.com/) files with yaml frontmatter stored in a Git connector.

Currently we support most of the [GitHub Flavoured Markdown specification](https://github.github.com/gfm/) and Modify-provided MDX.

#### MDX 

[MDX](https://mdxjs.com/) is an authoring format that combines markdown for simple content with JSX for rich visual components.

Modify provides a set of components that can be embedded in markdown docs at the block level or inline:

```mdx
# Hello, world! 

<InfoMessage header="Info" content="Some important info"/>

Hello, world! <InfoMessage header="Info" content="Some important info"/>

```

For more info on props you can pass to Modify components, hover over the component name in your editor (`InfoMessage` in the above example) and inspect the tooltip.

To use MDX in Modify you do not need to change your file extension from `.md` to `.mdx`.

### Register

A register is tabular stored as yaml, with a variety of interfaces for editing. 

As each row of a register is a text file, it can be managed with version control.

Registers are also defined using text files, so their configuration is also version controlled.

#### How do register rows work?

Each row is a file that has fields mapped from either the frontmatter or content parts of the file.

You can use the table, board, form or editor views to edit the values of a field, and only the values changed will be modified in the underlying file.

You can also collaboratively edit rows of a register with other members of your team.

#### What kind of files can a register have?

Register rows can either be multipart yaml files (i.e. both frontmatter and content) or markdown files with frontmatter delimited by triple-dashed lines.

Data can be selected out of the body of markdown files using a syntax similar to CSS-selectors (coming soon).

#### What is a register schema?

All registers have a `.modify.yaml` file that defines the basic properties of a register (e.g. the `id` and `title`, so you can reference them) and the schema. 

This is a yaml file that you can edit in the text editor, but any changes you make will show in all register views. 

You can use the editor or the graphical schema editor to define your register's schema.

### Frontmatter

Frontmatter is user-defined metadata formatted as valid yaml located at the top of markdown, MDX and yaml files. 

Currently frontmatter supports the following fields:

```yaml
---
id: my-id
title: My title
description: My description 
---
```

Values for `id` and `title` fields can be used to search for and reference artifacts in connectors.

### Relationships

Relationships are references between artifacts defined in text, either inline or in frontmatter using an artifact's `id`.

You can use the editor's search modal (press CTRL+SPACE keys to launch), and search for artifacts by `id` and `title`.

Once added to an artifact, relationships can be visualised as graphs or tables using the respository's side panel on the right.

### Diagram

The editor supports text-based diagrams defined in [mermaid](https://mermaid-js.github.io/mermaid/#/), [graphviz](https://www.graphviz.org/) and [nomnoml](http://www.nomnoml.com/). 

Using text-based diagrams allows you to stay in your editor whilst editing diagrams, as well as version control them.

## Review

Reviews allow users to peer review changes to artifacts on a source workspace branch before merging them to a target workspace branch (e.g. from `develop` to `master`).

### Create a review

Reviews have a source branch, a target branch and reviewers. 

A review is created in its own branch, so that when you make changes in a review, you are making changes to the review branch itself rather than the source branch.

### Perform a review

To complete a review, look through the artifacts on the changes tab, make any further changes (you can do this live without the need for any PR ping pong) and commit then. You can also make comments on the activity tab. 

On the merge tab you can merge your source branch into the target after approvals have been given and automated checks passed.

#### Merging 

The only merge operation reviews support is a fast forward merge. This means any changes on the target branch must have been integrated onto the source and conflicts resolved before a merge can occur.

In practice, if the target is a remote branch of an external Git provider connector, this ensures you are able to work directly on this remote branch outside of Modify without worrying about your changes being overwritten. 

Conflicts occur when both a source and target workspace branch diverge from one another in the same place. We have a conflict resolution workflow planned in future, but for now users must resolve them manually.

## Job

Jobs allow users to define jobs in Modify that trigger an HTTP request to an external service for execution.

### Generic job

Generic jobs are jobs that can be used to trigger any relevant external service with an HTTP request. Parameters defined are used to construct the HTTP request:

- The HTTP method for calling a target URL 
- A target URL
- Optional headers
- A payload
- Credentials storing basic authentication.

### GitHub Actions

GitHub Action jobs call the GitHub REST API and trigger a `workflow_dispatch` event ([GitHub docs](https://docs.github.com/en/free-pro-team@latest/actions/reference/events-that-trigger-workflows#workflow_dispatch)), triggering a workflow to be executed remotely. 

### Example job

Example jobs provide instructions for configuring Modify and external cloud services, defining a job and running it on an external service.

You can also adapt instructions to suit your use case. Common divergences are usually sign posted, with relevant instructions.

Example jobs are all provided as open source repositories on our [GitHub page](https://github.com/modifyhq).
