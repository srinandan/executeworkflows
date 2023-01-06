# Execute Workflows

This sample repository demonstrates how to synchronously execute GCP [Workflows](https://cloud.google.com/workflows/docs) from [Application Integration](https://cloud.google.com/application-integration/docs/overview).

# Description

Workflows can be triggered via EventArc, Cloud Scheduler or through the [REST API](https://cloud.google.com/workflows/docs/apis). The Workflows Execution API is an asyncronous API. In this sample, Application Integration will invoke the [Execute API](https://cloud.google.com/workflows/docs/apis), then poll the [Execution](https://cloud.google.com/workflows/docs/reference/executions/rest/v1/projects.locations.workflows.executions/get) until the Workflow has ended (successfully or failed). The result from the Workflow is sent as an output of Application Integration. Thus creating a synchronous API interface over an asynchronous API.

# Prerequisites

* The integration version JSON is downloaded [here](./src/executeworkflows.json)
* This repo uses a custom cloud builder called `integrationcli-builder`. , based on [integrationcli](https://github.com/srinandan/integrationcli) and gcloud


## Steps

1. Modify  the [overrides file](./overrides/overrides.json) to set the appropriate endpoint for Workflows.

2. Modify the [authconfig file](./authconfig/authconfig.json) to set the appropriate Service Account with permissions to execute a Workflow

3. Trigger the build manually

```sh

gcloud builds submit --config=cloudbuild.yaml --region=<region-name> --project=<project-name>
```

The integration is labeled with the `SHORT_SHA`, the first seven characters of the commit id
___

## Support

This is not an officially supported Google product
