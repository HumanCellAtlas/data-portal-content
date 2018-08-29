---
path: "/learn/userguides/data-processing-pipelines/workflow-best-practices"
date: "2018-05-03"
title: "Best Practices for Building Data Processing Pipelines"
---

# Best Practices for Building Data Processing Pipelines

## Our Goals in Our Best Practices

The following broad goals motivate our best practices. Here we describe them and give insight as to why these goals are important. We then explore best practices and examples to give you a sense of how to apply these goals.

- The best pipelines should be automated.
- The best pipelines should have be clearly testable.
- The best pipelines should be portable.
- The best pipelines should scale to their data.
- The best pipelines should be easy to maintain.
  
### Automation
#### What do we mean by automation?
  
Automation refers to the ability of a pipeline to run, end-to-end, without human intervention.
  
#### Why do we care about automation? 
  
Pipelines cannot scale to large amounts of data, or many runs, if manual steps must be performed within the pipeline. They also cannot be part of an automated system if they in fact are not automated. Manual steps will bottleneck your entire system and can require unmanageable operations. Moreover, manual steps performed by humans will vary, and will promote the production of data that can not be appropriately harmonized.

#### DOs and DON'Ts

- *Do*: Reduce parameterization to minimal inputs that do not vary for each input data.
- *Do*: Update manual parameters to data-driven input.
- *Do*: Offer defaults that are generally applicable for inputs that cannot be defined in a data-driven manner.
- *Do*: Offer the ability to check the status of pipeline runs.
- *Don’t*: Assume any file produced at any step of the pipeline is ok. Always check the status of underlying tools (Eg. check return codes).
- *Don’t*: Keep files produced by steps of the pipeline that errored; people will accidently use them if they exist.
- *Don’t*: Delete outputs from steps that passed when the full pipeline fails, keeping them enables you to pick up where you left off.
- *Don’t*: Use tools that are “buggy” or fragile, find alternatives or improve the tools.
  
### Testability
#### What is a testable pipeline?
  
A testable pipeline is one in which isolated sections or the full pipeline can checked for specified characteristics without modifying the pipeline’s code. Testability requires the existence of appropriate data with which to run the test and a testing checklist that reflects a clear understanding of how the data will be used to evaluate the pipeline.
  
#### Why do we care about testabilty?
  
The availability of test data enables validation that the pipeline can produce the desired outcome. Formulation of a testing checklist allows the developer to clearly define the capabilities of the pipeline and the parameters of its use.

We have developed a benchmarking platform, called [Unity](https://unity.broadinstitute.org/), to facilitate efforts to develop and test pipelines and pipeline modules.

#### DOs and DON'Ts

- *Do*: Provide toy test data with your pipeline/tool.
- *Do*: Provide the results of an execution of your pipeline/tool on the test data.
- *Do*: Refer to at least one real data set appropriate for your tool/pipeline with example output from an execution of your pipeline or tool.
- *Do*: Provide a checker tool.
- *Do*: Include an automated testing suite for pipeline tasks.
- *Do*: Include automated tests for the pipeline as an integrated unit (pipeline benchmarking).
- *Don’t*: Use tools that do not have automated testing suites.
- *Don’t*: Write tests that assume a specific instance of data.

### Portability

#### What is pipeline portability?

Pipeline portability refers to the ability of a pipeline to execute successfully on multiple technical architectures.

#### why do we care about portability?

_Science._ Science is not science if results are not reproducible; the scientific method cannot occur without a repeatable experiment that can be modified. Data processing pipelines are an essential part of some scientific inquiry and where they are leveraged they should be repeatable to validate and extend scientific discovery.

_Impact._ Pipelines will have greatest impact when they can be leveraged in multiple environments. The more technical requirements for installing and running of a pipeline, the longer it will take for a researcher to have a usable running pipeline.
  
_Maintainability._ Over the long term, it is easier to maintain pipelines that can be ran in multiple environments. Portability avoids being tied to specific infrastructure and enables ease of deployment to development environments.
