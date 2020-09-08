---
layout: tutorial
title: "Submitting a Job on a Supercomputer"
date: 2020-09-08
author: Adam Batten
subtitle: A beginners guide to writing and submitting Slurm jobs.
thumbnail: "/assets/images/slurm.png"
---

This tutorial for submitting jobs is primarily aimed at people who will be using the [Ozstar supercomputer](https://supercomputing.swin.edu.au/ozstar/) at the [Swinburne University of Technology](https://www.swinburne.edu.au/). However most of the tutorial should be generally applicable to anyone using a [Slurm](https://slurm.schedmd.com/overview.html) based job scheduler. This tutorial is based on the Ozstar/Slurm documentation found [here](https://supercomputing.swin.edu.au/docs/2-ozstar/oz-slurm-create.html).  

Many students in the [Centre of Astrophysics and Supercomputing](https://astronomy.swin.edu.au/) at Swinburne have found it difficult to determine exactly what to do when they want to submit a job to Ozstar. This tutorial attempts give detailed instructions so that someone that is a complete beginner will understand how to submit their own jobs.

### This Tutorial Covers:
- [Writing a job submission script](#writing-a-job-submission-script).
	- [The Shebang](#1-the-shebang)
	- [#SBATCH](#2-sbatch)
	- [Loading Modules](#3-loading-modules)
- [Submitting a job submission script](#submitting-a-job-submission-script).
- [Querying the state of a job](#querying-the-state-of-a-job).
- [Canceling a job](#canceling-a-job).
- [Example Job Submission Scripts](#examples)

### This Tutorial Assumes You Can:
- Log into Ozstar (or another system using Slurm)
- Write a shell script

### Some Key Definitions:
- Slurm: A job scheduler. When you submit a job you are submitting it to Slurm. This program works to organise and schedule when all of the jobs will run after they have been submitted. Slurm determines the optimal way to allocate CPUs, time and memory to jobs based on what has been requested. 

## Writing and Submitting A Job

Submitting a job on Ozstar is a two step process:

1) First you have to request resources from Ozstar. This will normally include the amount of memory you need, the number of CPUs you want to use and how long you expect to be using the resources. This step is called a ''resource request". An example resource request using English could be: 
*<center>"I want to use 200 MB of memory on 1 CPU core for 2 hours".</center>*

2) The second step is where you say what you want these resources to be doing. This includes specifying what software is needed, which scripts you want to run, and how to execute them. This step is called the 'job step'. An example job step could be: 

*<center>"I want to load python and then execute a python script".</center>*
    
Luckily, you can do both of these steps at the same time using a "submission script". 

### Writing a Job Submission Script
A submission script is just a shell script that is formatted in a specific way such that it contains both your resource request and your job step. 
Here is an example of a simple submission script called `my_slurm_job.sh`. This submission script will run a python script called `example_python_job.py`.

```shell
#!/bin/bash

#SBATCH --ntasks=1
#SBATCH --mem-per-cpu=100MB
#SBATCH --time=00:30:00

module purge
module load anaconda3/5.0.1

source activate py3

python example_python_job.py
```

There are four main components to a submission script: [The Shebang](#1-the-shebang), [#SBATCH](#2-sbatch), [Loading Modules](#3-loading-modules), 

### 1 The Shebang
```
#!/bin/bash 
```

The first component is the very first line: `#!/bin/bash`. This line has many names including: 'shebang', 'shabang', 'hashbang', 'pound-bang', 'hash-pling' and probably lots of other ridiculous sounding names. This line serves the purpose of defining which 'interpreter' to use when executing the script. 

In this case we are effectively saying:  "This is a Bash (Bourne-Again Shell) script, so execute this script with a Bash shell". 
    
Since all of your submission scripts will be likely be a Bash script, this line will be the same for every submission script you write. 

    
### 2 #SBATCH
```shell
#SBATCH --ntasks=1
#SBATCH --mem-per-cpu=100MB
#SBATCH --time=00:30:00
```
The second component is where you request resources and it includes is all the lines that start with `#SBATCH`. Any line in your submission script that begins with `#SBATCH` is understood by Slurm to be a resource request or an additional option related to the job.

{% include note_card.html type="warning" text="Notice the # in front. This can be easy to forget but is important." %}

In this example script we are requesting: 1 CPU (`#SBATCH --ntasks=1`), 100 MB of RAM (`#SBATCH --mem-per-cpu=100MB`) for 30 minutes (`#SBATCH --time=00:30:00`).

There are lots of additional options that you include here, for instance you can include the option to have SLURM send you an email when your job starts and ends.

Example:
```shell
#SBATCH --mail-user=name@swin.edu.au
#SBATCH --mail-type=ALL
```
You can see a complete list of parameters using `man sbatch`. I have also listed more examples of options that may be useful at the end of this tutorial.

<div class="card bg-info mb-3">
  <div class="card-header text-white">Note</div>
  <div class="card-body bg-light">
    <p class="card-text">A good rule of thumb is: The more resources you request, the longer it will take for your job to start. 
    So asking for way more time and RAM than you actually need is not a good idea. 
    Unfortunately, this tutorial can not tell you how much resources your job will require. 
    You will have have to determine that for yourself. 
    If you are using python, you can look into using packages such as <a href="https://github.com/pythonprofilers/memory_profiler">memory_profiler</a> and <a href="https://github.com/pyutils/line_profiler">line_profiler</a> to help estimate the memory usage and timing of a script.</p>
  </div>
</div>

### 3 Loading Modules
```shell
module purge
module load anaconda3/5.0.1

source activate py3
```

The third component is where you load all the modules that are necessary to run your script. Ozstar uses modules to manage the software it has installed. If you want to use a module you first have to load it. To load a module use the following command: `module load <module_name>/<software_version>`. You can search for modules using `module spider <module_name>`. We will be executing a python script using the example submission script, hence we have to load the modules for anaconda and the Conda environment that all the packages are install in.
 
- `module purge` unloads all loaded modules.
- `module load anaconda3/5.0.1` loads Anaconda. I recommend using the `anaconda3/5.0.1` version of instead of `anaconda3/5.1.0` because there is a significant bug in the later version on Ozstar related to Conda environments. 
- `source activate py3` loads a Conda environment that I have called `py3`. In this environment I have installed all of the necessary packages required to execute the `example_python_job.py`.

Here is a list of a few common modules that you might need to load: `gcc/7.3.0`, `hdf5/1.10.1`, `openmpi/3.0.0`, 

{% include note_card.html type="info" text="If you are using python I highly recommend that you use Conda environments when working on Ozstar. Anaconda environments will save you lots of time, stress and effort in the long run." %} 

### 4 Computing Step  

```shell
python example_python_job.py
```
This final component is where you say what you want to actually run on the requested resources.
In the example, we have a single line `python example_python_job.py` indicating that our job will run the `example_python_job.py` script. This the job step. It is also possible to list multiple steps in a submission script and they will be performed one after another. 

Example:
```shell
python example_python_job.py
python example_python_job2.py
python_example_python_job3.py
```
In this case, after the first job step is completed the second job step (`example_python_job2.py`) will begin. In your resource request you will have to allow for the time and memory requirements for all of the job steps.


### Submitting a Job Submission Script

After you have finished writing a submission script, you can submit it to Slurm with the `sbatch` command.

```shell
>>> sbatch my_slurm_job.sh
sbatch: Submitted batch job 99999999
```

If the job is successfully submitted, it will respond with the `jobid` that was assigned to the job. In this example the `jobid` is 99999999.


{% include note_card.html type="info" text="You can also submit a job to the queue from within a submission script. This can be useful for automating a pipeline of scripts that need to be completed in a sequence." %}

### Querying the State of a Job

You can find out about the state of your job and all other jobs in the queue using the command `squeue`.

```
>>> squeue --user=yourusername
```
This will give you the status of all your running and submitted jobs.
You can also neglect the `--user=yourusername` to view the entire job queue for all users.

The output of `squeue --user=yourusername` should look like the figure below. 

!["An image of the output of squeue after using sbatch on my_slurm_job.sh"](/assets/images/slurm_squeue.png)

The columns of the output are as follows:

- `JOBID`: The JOBID that is given to the job. This is unique amongst all jobs current and past.
- `PARTITION`: The type of 'queue' that the job is in. This is usually given by the name of the type of CPU the job is waiting to start on.
- `NAME`: The name of the job.
- `USER`: The username of the person that submitted the job.
- `ST`: The status of the job.
	- `R`: Currently Running
	- `PD`: Waiting for Resources (Pending)
- `TIME`: The length of time the job has been running. If the job hasn't started it will say `0:00`. 
- `NODES`: The number of 'nodes' that the job has requested. A 'node' is a collection of many CPUs, and Ozstar has a few different types of node with different abouts of CPUs on each. For example the `john` (`PARTITION = skylake`) nodes have 32 CPUs each. 
- `NODELIST(REASON)`: If the job is running (`ST = R`) this is the list of nodes that the job is using. If the job is pending (`ST = PD`) this is why the job is pending.

You can also use the [Ozstar Job Monitor Website](https://supercomputing.swin.edu.au/monitor/) for a graphical view of all the job that are running and in the queue.

### Canceling a Job
Sometimes you will have a job that you need to cancel for some reason. You can cancel a running or submitted job at any time with `scancel jobid`.

```shell
>>> scancel 99999999
```

You can also cancel all of your jobs with `scancel --u username` or you can only cancel your "Pending" jobs with `scancel -t PD`.


### Examples

#### Example 0
```shell
#!/bin/bash

#SBATCH --ntasks=1
#SBATCH --mem-per-cpu=100MB
#SBATCH --time=00:30:00

module purge
module load anaconda3/5.0.1

source activate py3

python example_python_job.py
```
This is the same example as shown throughout this tutorial.


#### Example 1
```shell
#!/bin/bash

#SBATCH --ntasks=1
#SBATCH --mem-per-cpu=100MB
#SBATCH --time=00:30:00

#SBATCH --job-name=Calculate_Mean
#SBATCH --output=slurm_output.txt

#SBATCH --mail-user=name@swin.edu.au
#SBATCH --mail-type=ALL
#SBATCH --account=oz999

module purge
module load anaconda3/5.0.1

source activate py3

python example_python_job.py
```
This is essentially the same as [Example 0](#example-0) but wit a few additional parameters.

The parameter `--job-name` is being used to give a more meaningful name to the job.
This is the name that will show up as `NAME` when using `squeue`.

The parameter `--output` is defining the file that all of the Slurm output (i.e. print statements) will be directed. 

The parameters `--mail-user` and `--main-type` makes Slurm send an email when your job starts and completes.

The parameter `--account` is setting which group account this job belongs is associated with.

### Summary
This tutorial is not meant as comprehensive article covering all there is to know about using Slurm; but hopefully by now you feel confident enough to be able to write you own bash scripts and get jobs running on Ozstar.  
