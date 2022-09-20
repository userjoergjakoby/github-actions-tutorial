# Structure of Workflows
As mentioned in the previous chapter, workflows are defined as `.yml` inside the folder `/.github/workflows/`.
This chapter will explain the basic structure of these `.yml` files.

## Events
Events define when the workflow is triggered.
If the workflow should start when a pull request opened or updated, it could look like this:
```yml
on:
  pull_request_target:
    types: [opened, synchronize, reopened]
```
There are many types of events. You can find out more about them
[here](https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows).

## Jobs
Jobs define the environment and which steps should run to complete the pipeline. For example:
```yml
jobs:
  docs:
    name: 'Checkout code'
    runs-on: ubuntu-latest

    steps:
      - name: '☁️ Checkout repository'
        uses: actions/checkout@v3
        with:
          ref: ${{ github.event.pull_request.head.sha }}
```
The code above defines a job `Checkout Code` which runs inside an ubuntu container (`runs-on: ubuntu-latest`).  
There is one step inside the job which will check out the code.
The step is using a predefined action from GitHub to do so.

## Actions
It is possible to define actions which include code that should run inside a workflow.  
[Here](https://github.com/actions) you can find predefined actions from GitHub.
There also is a GitHub Organisation with Atos internal Actions ([ATOS-Actions](https://github.com/ATOS-Actions)).

## Next step (Running tests in GitHub actions)
[Continue with the tutorial](running-tests.md)
