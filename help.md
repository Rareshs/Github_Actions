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
