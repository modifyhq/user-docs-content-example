---
id: faqs
title: FAQs
kind: doc
---

## How do I make a feature request?

There are several ways you can add your vote for a feature request:

- Get on our [Discord server](https://discord.gg/NbePDqG) and let us know your ideas 
- Send us an email with your request at [team@modifyhq.com](mailto:team@modifyhq.com)
- Tweet at [@ModifyHQ](http://twitter.com/ModifyHQ) with your ideas

We go through each request to collect data and make sure it is added to our planning sessions and roadmap. 

Thanks in advance for taking the time, we really appreciate it!

## I found a bug! What should I do?

If you find a bug, please send us a quick message on our [Discord server](https://discord.gg/NbePDqG) or email [support@modifyhq.com](mailto:support@modifyhq.com)

If possible, please provide the following info to help us track down and resolve the problem quicker:

- Modify version (click on your avatar on the left navigation bar, and `About` in the menu)
- Browser type and version
- The URL of the Modify page where the bug is occurring (if applicable)
- Screenshots, GIFs and videos of the bug are also super helpful if you're able to send them!

## What plain text formats does Modify support?

We provide editors for any text file format (markdown, MDX, yaml, csv, json, xml, plain text) along with live previews. 

We also provide viewers for common image formats (png, jpeg, svg) and you can download binary files for formats that don't have viewers.

MS Word documents (`*.docx`) will also be converted to markdown files automatically, to enable you to edit them and add front matter.

## Do I need to commit changes I make? 

Uncommitted changes to files and directories in connectors are saved to Modify's database as your working copy, so you won't lose them if you don't commit them.

However, we encourage you to commit changes frequently, as doing so writes them to a Git repository configured in a connector. 

If you're using a connector to an external Git provider, committing often means you'll able to access fresh data outside of Modify.

## Can I use Modify interchangeably with my IDE?

Yes! When using connectors to external Git providers, the base branch configured can be worked on outside of Modify using your normal workflow and tools. 

Check out [[reference/#Branches-on-external-Git-provider-connectors]] for more. 

## How do I export data from a Modify-hosted connector?

You can't do this, yet... but we'll be adding exports from Modify connectors to external Git providers soon!

## Can I define my own jobs? 

Yes! Jobs can be executed on any external system that can be triggered by an HTTP request.

## Does Modify have an API I can use? 

Not yet, but a public API is on the roadmap! We're currently collecting use cases, so we'd love to hear about what you'd use it for.

Please send us a message on our [Discord server](https://discord.gg/NbePDqG) or [tweet at us](https://twitter.com/ModifyHQ) with your use case. Thanks!