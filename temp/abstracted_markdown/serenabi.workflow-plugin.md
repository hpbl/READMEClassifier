# Introduction

Building continuous delivery pipelines and similarly complex tasks in Jenkins using freestyle projects and existing plugins is very awkward. You need to mix Parameterized Trigger, Copy Artifact, Promoted Builds, Conditional Build Step, and more just to express what should be a simple script. This project attempts to make it possible to directly write that script, what people often call a _workflow_ (sometimes abbreviated _flow_), while integrating with Jenkins features like slaves and publishers.

# Core features

Specific status of implementation below.

## Scripted control flow

Your whole workflow is a single Groovy script using an embedded DSL, possibly quite short and legible; there is no need to jump between multiple job configuration screens to see what is going on. Conditions, loops, variables, parallel tasks, and so on are defined using regular language constructs. At any point you can insert a shell script to do “real work” (compilation, etc.).

## Jenkins model object integration

Standard DSL functions let you run external processes, grab slave nodes, allocate workspaces, build “legacy” (freestyle) jobs, and so on.

See here for information on reusing build steps from freestyle projects.

## Pause and resume execution

If Jenkins is restarted (intentionally, or because of a crash) while your workflow is running, when it comes back up, execution is resumed where it left off. This applies to external processes (shell scripts) so long as the slave can be reattached, and losing the slave connection temporarily is not fatal either.

Flows can pause in the middle and wait for a human to approve something, or enter some information. Executors are not consumed while the flow is waiting.

## SCM integration

See here for details on using version control from a workflow.

## Pipeline stages

Workflows can be divided into sequential stages, not only for labeling but to throttle concurrency.

# Getting started

Read the tutorial to get started writing workflows.

# Installation

If you do not want to build from sources, releases (see the changelog for details on which) are available on the Jenkins update center. You need to be running a sufficiently recent Jenkins release, currently an LTS in the @abstr_number . @abstr_number .x line, or a newer weekly release.

For OSS Jenkins users, install _Workflow: Aggregator_ (its dependencies will be pulled in automatically). You will need to restart Jenkins to complete installation.

Jenkins Enterprise by CloudBees users get Workflow automatically as of the @abstr_number . @abstr_number release. Otherwise install _CloudBees Workflow: Aggregator_ from the update center. Again dependencies will be pulled in automatically, including all the OSS plugins.

# Demo

See the demo overview using Docker if you want to try a complete setup quickly.

If you want to try running recent development changes, rather than released binaries, you have two options. You can run directly from the source tree; from the root of the repository:
    
    
    mvn -DskipTests clean install && mvn -f aggregator hpi:run
    

Then visit http://localhost: @abstr_number /jenkins/ to play with the plugins.

(If your IDE supports compile-on-save mode this is especially convenient since each `hpi:run` will pick up compiled changes from member plugins without needing to run to `package` phase.)

You can also run the Docker demo with snapshot binaries:
    
    
    make -C demo run-snapshot
    

The snapshot Docker demo is mainly useful for verifying the effect of ongoing changes on future demo binary releases. You get the `cd` sample job set up, but your environment is thrown away if you kill the Docker container (for example with Ctrl-C). When using `hpi:run` the same `aggregator/work/` home directory is reused so long as you do not explicitly delete it.

# Presentations

Webinar _Orchestrating the Continuous Delivery Process in Jenkins with Workflow_ (Dec @abstr_number ): @abstr_hyperlink 

JUC San Francisco (Oct @abstr_number ): @abstr_hyperlink 

JUC Boston (Jun @abstr_number ): @abstr_hyperlink and @abstr_hyperlink 

# Development

  * Changelog
  * Ongoing plugin compatibility list
  * @abstr_hyperlink 
  * @abstr_hyperlink 
  * @abstr_hyperlink 
  * @abstr_hyperlink 
  * @abstr_hyperlink with validated merge support. @abstr_hyperlink 
  * @abstr_hyperlink 
  * @abstr_hyperlink 



# Source organization

While the implementation is divided into a number of plugins, for ease of prototyping they are all kept in one repository using snapshot dependencies.

  * `step-api` defines a generic build step interface (not specific to flows) that many plugins could in the future depend on.
  * `basic-steps` add some generic step implementations. There is more documentation there.
  * `api` defines the essential aspects of flows and their executions. In particular, the engine running a flow is extensible and so could in the future support visual orchestration languages.
  * `support` adds general implementations of some internals needed by flows, such as storing state.
  * `job` provides the actual job type and top-level UI for defining and running flows.
  * `durable-task-step` uses the `durable-task` plugin to define a shell script step that can survive restarts.
  * `scm-step` adds SCM-related steps. There is more documentation there.
  * `cps` is the flow engine implementation based on the Groovy language, and supporting long-running flows using a _continuation passing style_ transformation of the script.
  * `cps-global-lib` adds a Git-backed repository for Groovy libraries available to scripts.
  * `stm` is a simple engine implementation using a _state transition machine_, less intended for end users than as a reference for how engines can work. Currently only partly implemented.
  * `aggregator` is a placeholder plugin allowing you to `mvn hpi:run` and see everything working together, as well as holding integration tests.


