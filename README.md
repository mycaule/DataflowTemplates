# Google Cloud Dataflow Template Pipelines

Personal fork from [`GoogleCloudPlatform/DataflowTemplates`](https://github.com/GoogleCloudPlatform/DataflowTemplates)
for in-Cloud data tasks running on [Google Cloud Dataflow](https://cloud.google.com/dataflow/) 
with [Apache Beam](https://beam.apache.org/) pipelines.

My fork uses `gradle`.

[![Open in Cloud Shell](http://gstatic.com/cloudssh/images/open-btn.svg)](https://console.cloud.google.com/cloudshell/editor?cloudshell_git_repo=https%3A%2F%2Fgithub.com%2Fmycaule%2FDataflowTemplates.git)

[Templates docs](https://cloud.google.com/dataflow/docs/templates/provided-templates).

### Building the Project

Build the entire project using the maven compile command.

```sh
gradle build
```

### Creating a Template File

```sh
gradle clean execute -DmainClass=com.google.cloud.teleport.templates.<template-class> \
    -Dexec.cleanupDaemonThreads=false \
    -Dexec.args=" \
    --project=<project-id> \
    --stagingLocation=gs://<bucket-name>/staging \
    --tempLocation=gs://<bucket-name>/temp \
    --templateLocation=gs://<bucket-name>/templates/<template-name>.json \
    --runner=DataflowRunner" \
    -Pdataflow-runner
```

### Executing a Template File

```sh
gcloud dataflow jobs run <job-name> \
--gcs-location=<template-location> \
--zone=<zone> \
--parameters paramName1=Value1,paramName2=Value2
```