---
id: faqs
title: FAQs
description: Frequently asked questions by users.
---

## How do I make a feature request?

There are several ways you can add your vote for a feature request:

- Get on our [Discord server](https://discord.gg/NbePDqG) and let us know your ideas 
- Send us an email with your request at [team@modifyhq.com](mailto:team@modifyhq.com)
- Tweet at [@ModifyHQ](http://twitter.com/ModifyHQ) with your ideas

We'll go through each request to collect the data and make sure it is added to our planning sessions and product roadmap. Thanks in advance for taking the time!

## I found a bug! What should I do? 

If you find a bug, please send us a quick message on our [Discord server](https://discord.gg/NbePDqG) or email [support@modifyhq.com](mailto:support@modifyhq.com)

If possible, please provide the following info to help us track down and resolve the problem quicker:

- Modify version (click on your avatar at the bottom of the left navigation bar, and `About` in the menu)
- Browser type and version
- The URL of the Modify page where the bug is occurring (if applicable)
- Screenshots, GIFs and videos of the bug are super helpful if you're able to send them!

## What is an artifact?

Check out [reference] for definitions of all Modify concepts, including `artifacts`.

## What plain text formats does Modify support?

Markdown (most of the GitHub-flavoured markdown spec), [MDX](https://mdxjs.com/) and yaml. 

Send us a feature request if you'd like other formats supported!

## Do I need to commit changes I make to artifacts? 

Uncommitted changes are saved to Modify's database, so you won't lose them if you don't commit them. 

However, since committing also pushes them to a remote branch defined in a connector, we recommend you do, as it's a good way for you to retain access to your data.

## How can I edit artifacts in a GitHub or Bitbucket connector?

Artifacts and directories in a GitHub or Bitbucket connector's remote branch are protected by default.

You'll therefore need to create an editable workspace branch before you can edit the connector's contents. 

To do this, click the branch button in the top right of the repository's header bar and complete the form.

## Does Modify integrate changes made directly to my GitHub or Bitbucket connector's remote branch?

Changes integrated into your remote branch outside of Modify are automatically read by Modify and shown in the remote branch in Modify's repository page. 

During a review, changes on a downstream workspace branch are integrated into the remote branch via a fast forward merge. If this cannot be performed due to divergences, these will need to be integrated, and conflicts resolved, before a fast forward merge can be performed.

See `External Git provider connectors` in [reference] for more detail. 

## How can I export my data? 

All changes to files in GitHub and Bitbucket connectors are persisted in GitHub and Bitbucket. 

Exports from Modify Git connectors are a feature on our roadmap that we will prioritise based on feedback. 

## Can I define my own jobs? 

Yes. Jobs can be executed on any external system that can be triggered by an HTTP call.

If you would like to trigger jobs using a different method, please send us a feature request! 

## Does Modify have an API I can use? 

Not yet, but a public API is on the roadmap! We're still collecting use cases to help our team with the implementation. 

It would be super helpful if you could tell us: What would you use an API for?

Please send us a message on our [Discord server](https://discord.gg/NbePDqG) or [tweet at us](https://twitter.com/ModifyHQ) with your use case. Thanks! 🙏