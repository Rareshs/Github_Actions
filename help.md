checkout action - enable repos to be cloned into the runner

**how to use an actions**:

in the steps:

name : whatever_name

uses: action

define options with this keyword:

with:

If i have 2 jobs, it runs them in parallel whic is the default, but it can also
be run sequentially.

keyword

needs: another_job_name

to make them work sequentally, basically it needs the job it is in need to
finish before it starts this one

**Multiple triggers**

on: [push, workflow_dispatch]

**Context information** metadata from github ${{toJson(github)}} - info about
the workflow

or env to see env variables in the workflow

**Control triggers based on branch** filters:

Ex.:

on:

pull_request:

      types:

         -opened

         - etc..

push:

      branches:

         - 'main'

         - 'releases/**' - this matches /releases/version/1 or /releases/version, must begin with releases

         - 'feat/* - this matches feat/, feat/new_login, only matches one level
      paths-ignore:
         - '.github/workflows/* - this doesnt trigger workflow when changes happend to this folder

_!! PULL requests based on fork do not trigger workflows!!_

to skip a workflow that triggers on a push simply add [skip ci] or [skip
actions]

**Job Artifacts**

What remains after building, compiled app, bundles binaries, logs and so on

**Job outputs** Used for re-using a value in different jobs

They are passed between jobs, version number commit sha file path Ex: Name of a
file generated in a previus build, it points to something, file or something

**Dependency caching**

Install dependencies on one job and make other jobs use

them instead of downloading all over again

action/cache

**Environment variables**

Ex:

env:

MONGODB_DB_NAME: test-demo

**Secrets** to get secrets from the github secrets use:

env: MONGODB_DB_PASS: ${{ secrets.MONGO_PASSWD}}

**Rewrite normal functioning**

for example if a step fails, to still go to the next step of the same job

failure() - if previus jobs or action failed - it needs to evaluate it

to add conditions:

_it needs and id_

_run_test is an id of a previus step_

if steps.run_test == failure or not

**Continue steps even if there is an error**

continue-on-error: true

#If you want your entire workflow to continue, use continue on error

#If you want a selective step to run use if checks

**Matrix jobs** Run same job with different configs, on other runners or
different version of something
