---
path: "/develop/development-guides/testing-pipelines"
date: "2018-05-03"
title: "Pipeline Testing Guide"
---

## How do I test my pipeline in the portability service?

Currently, the portability service exists as an API that can be leveraged using command line or continuous integration tools. With this interface you can demonstrate that your pipeline runs in HCA DCP execution environments as well as other execution environments. The service records whether the pipeline was able to execute to completion without error and whether it produced the expected output results in each environment.

In order to run the test, you need the following:

1. **A pipeline.** The service supports pipelines written in WDL or CWL.
2. **Standardized data.** Standard test data to use when running the pipeline.
3. **Expected output.** Expected results from executing the pipeline on the standardized data.
4. **Checker tool.** A command-line tool for checking the pipeline’s results against the expected results. Note, a pipeline may run correctly but not produce results that are perfectly identical to the expected results depending on the stochastic nature of the underlying algorithms. This should be understood by the pipeline author and would be accounted for in the checker tool. If outputs are deterministic, this can be as simple as comparing checksums between expected and generated results.

The portability service sends the candidate pipeline and the standardized test data to one or multiple execution infrastructures, which run the pipeline in that environment and send the results back for comparison to the expected results using the checker tool provided by the pipeline developer.

## Example Pipeline Submission 
(TBD)
## Best practices in pipeline development

As we learn more about portability it is important to share that knowledge with others. We are currently defining our best practices; please check back with us.
