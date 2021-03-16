---
id: run-jobs
title: Run jobs
kind: doc
---

## Run jobs

A [reference/#Job] allows you to trigger an external service with an HTTP request to execute a job. External services include cloud services like GitHub Actions and AWS Lamdas, as well as your own infrastructure. 

Common jobs include building and publishing artifacts in Modify to the web or document formats like PDF and MS Word.

### Define a job

To define a job, navigate to the Jobs page using the left navigation and click the Create job button.

The quickest way to get going is to use an open source example job:

- Publish a Next.js docs site to Vercel - [see instructions](https://github.com/modifyhq/nextra-vercel-example)
- Publish a Gatsby site to AWS S3 - [see instructions](https://github.com/modifyhq/gatsby-aws-example)
- Publish a Jekyll site to GitHub pages - [see instructions](https://github.com/modifyhq/jekyll-github-example)

Example jobs help you set up Modify and external services quickly, and prefill parts of Modify's job definition template.

#### GitHub Actions
For a job executed on GitHub Actions, click the GitHub Actions option. The data provided in the form will be used to construct an HTTP POST request to the GitHub REST API, triggering a `workflow_dispatch` event ([see GitHub docs](https://docs.github.com/en/free-pro-team@latest/actions/reference/events-that-trigger-workflows#workflow_dispatch)). Separately, you'll also need to define a workflow file in a Git repository defining your job. [Read here](https://docs.github.com/en/free-pro-team@latest/actions/learn-github-actions/introduction-to-github-actions#overview) for more on workflows.

#### Generic jobs

For a job executed on a general external service, click the generic job option. Here you can define the HTTP method, target URL, headers, payload and basic authentication to trigger your job.

### Run a job

Once defined, your job will appear in a list on the Jobs page. To trigger it, click the start button on the list or detail pages.

Your job will now run and marked with an `In progress` status on the detail page. Once the job completes, provided the job includes a notification to the Modify API of completion status (as with all example jobs), the status of your job will change to `Finished`. 

Click the refresh button to get the up-to-date status.