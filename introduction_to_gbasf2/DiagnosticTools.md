# Diagnostic Tools 

The diagnostic tools are designed to help you identify and troubleshoot issues that may arise while using gbasf2.

```{note}
The tools for diagnostic are actively being developed. 
The following instructions may change in the future.
```

## Basic tests 

You can run a series of basic tests to check the functionality of your gbasf2 setup and grid access.

```bash
gb2_diagnostic
```

What information is shown? 

If no errors are reported, your setup and proxy are working correctly.


## Failed jobs 

If you have jobs that failed during execution, you can use the diagnostic tool to analyze the failures.

```bash
gb2_diagnostic --failed_job <jobID> 
```

For example, try to analyze a failed job from the first exercise in the Submit Jobs tutorial. 

## Jobs in Waiting status

One of the most common issues when submitting jobs to the grid is that they remain in the "Waiting" status for a long time.
You can use the diagnostic tool to investigate the reasons for this.

```bash
gb2_diagnostic --waiting_job <jobID> 
```

It will provide information about 
* The job requirements 
* Site candidates 
* Pilot job submission statistics  
* CPUTime comparisons between job requirement and site capabilities

Common issues:
1. **Site candidates not available**: This may indicate that there are no suitable sites that meet the job requirements. Contact the comp-users-forum with the information.
2. **Too long CPUTime**: Consider reducing the CPUTime requirement in your job submission, either with a more accurate estimation or reducing the complexity of the steering file.
3. **Mismatch in the resource tag**: Ensure that the global tag specified in your steering file is available at the sites where the jobs are being submitted.