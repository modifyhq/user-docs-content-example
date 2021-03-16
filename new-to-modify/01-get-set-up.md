---
id: get-set-up
title: Get set up
kind: doc
---

## Concepts

Modify concepts are used throughout and are defined in [reference].

## Get set up

### Sign up

Login with a GitHub or Google account and provide a unique username for your account.

A personal team will be created for your automatically, which you can invite collaborators to later on.

You'll then be directed to the Mission Control page, where you'll see some example [reference/#Workspace].

### Explore example workspaces

A workspace is a container for connectors, reviews and jobs. 

The Mission Control page comes set up with workspaces containing example content for common use cases. Click the Repository button next to the workspace name to explore.

### Set up your own workspace 

To create a new workspace, click the plus icon on the workspaces container on the Mission Control page and fill out the form.

Once created, click the Setup your workspace button, which will take you to your repository.

### Add a connector 

In your repository, click the Add connector button to a add a [reference/#Connector] to a Git repository hosted in Modify, GitHub or Bitbucket.

If you want to start exploring quickly, we recommend you choose a [reference/#Modify-hosted-connector], as you can always export your data later to GitHub or Bitbucket.

<WarningMessage header="IMPORTANT" content="You'll need accounts and Git repositories set up already to create connectors to GitHub and Bitbucket."/>

For an [reference/#External-Git-provider-connector] (GitHub and Bitbucket), you can use the OAuth-based setup flow.

First, you'll need to authenticate with your provider, install the Modify app on an organisation (GitHub) or workspace (Bitbucket) you have permissions for and (for GitHub only) configure the repositories you want to give Modify access to.

Next, you'll need to configure your connector, giving it a name and id, and selecting a remote repository and branch, then click `Add connector` to create your connector. 

Once created, your connector will appear in your repository's tree and you can view its directories and files (or artifacts, as we call them).

### Branch your workspace

For Modify connectors, you can branch your workspace at any time to work in isolation from your team. This creates branches of all connectors and their contents, and adds them to the new [reference/#Workspace-branch]`. 

For external provider connectors, you must branch your workspace before you can edit a connector's contents. 

To create a workspace branch, click the Branch workspace button in the repository's header. In the modal, select the branch you want to branch from, give your new branch a name and click the Create branch button.

Your new branch will now be selected in the breadcrumb and you can get on with collaborating on artifacts in your connectors.
