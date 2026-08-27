---
title: "Submitting Batch Jobs"
teaching: 15
exercises: 10
---

:::::::::::::::::::::::::::::::::::::: questions
- How do you submit batch jobs through OnDemand?
- What is the difference between Quick Submit and uploading a script?
- How do you write a basic SLURM job script?
- How do you submit GPU jobs and job arrays?
::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives
- Access the Job Composer in OnDemand
- Submit jobs using Quick Submit and script upload
- Write a basic SLURM batch script
- Submit GPU jobs and job arrays
::::::::::::::::::::::::::::::::::::::::::::::::::

## Accessing the Job Composer

1. Click **Jobs** in the left sidebar
2. Select **Job Composer**
3. You see any previously created jobs
4. Click **New Job** to create and submit a new job

::::::::::::::::::::::::::::::::::::: callout
## Test Your Scripts First

Before submitting a job to compute nodes, test your script logic in the Web Terminal or with a small test dataset. This saves compute resources and helps you catch errors before they run on expensive hardware.
::::::::::::::::::::::::::::::::::::::::::::::::::

## Quick Submit

1. Click **New Job**
2. Fill in the job details:
   - **Job name**: A descriptive name (e.g., "Analysis_2026")
   - **Partition**: `amd`, `gpu`, or `short` (`amd` and `gpu` allow up to 30 days / 720 hours; `short` has a shorter walltime — check `sinfo -p short`)
   - **Nodes**: Usually 1
   - **Time limit**: Hours and minutes needed
   - **Memory**: Total RAM (leave blank for default)
3. Paste your script content in the editor
4. Click **Submit**

## Upload a Script

1. Click **New Job** then **Upload**
2. Select a SLURM script file from your computer
3. Review and modify parameters if needed
4. Click **Submit**

## Writing a SLURM Script

A basic batch script:

```bash
#!/bin/bash
#SBATCH --job-name=MyJob
#SBATCH --partition=amd
#SBATCH --nodes=1
#SBATCH --ntasks=4
#SBATCH --time=02:00:00
#SBATCH --output=job.log
#SBATCH --error=job.err

cd $SLURM_SUBMIT_DIR
module load miniconda3
python3 analysis.py
```

Key directives: `--job-name` identifies the job, `--partition` selects the queue, `--time` sets the wall-clock limit, and `--output`/`--error` capture stdout and stderr.

## GPU Job Submission

To request GPU resources, use the `gpu` partition with `--gres`:

```bash
#!/bin/bash
#SBATCH --job-name=GPUJob
#SBATCH --partition=gpu
#SBATCH --nodes=1
#SBATCH --gres=gpu:1
#SBATCH --time=04:00:00
#SBATCH --output=gpu_job.log

module load miniconda3 cuda/12.2.1
conda activate pytorch_env   # your conda env with PyTorch (see the ML workshop)
python3 train_model.py
```

Request a specific GPU type with `--gres=gpu:a100:1`, `--gres=gpu:l40s:1`, or `--gres=gpu:rtxpro6000:1`.

## Job Arrays

Submit multiple similar jobs at once:

```bash
#!/bin/bash
#SBATCH --job-name=analysis
#SBATCH --array=1-10
#SBATCH --partition=amd
#SBATCH --time=01:00:00

python3 analysis.py input_${SLURM_ARRAY_TASK_ID}.txt
```

Each array task gets a unique `$SLURM_ARRAY_TASK_ID` (1 through 10 in this example), letting you process multiple input files with one submission.

::::::::::::::::::::::::::::::::::::: challenge

## Challenge: Submit and Monitor a Job

1. Use Job Composer to create a job that:
   - Prints "Job starting at $(date)"
   - Sleeps for 30 seconds
   - Prints "Job completed at $(date)"
2. Submit the job to the `amd` partition
3. Watch the job progress in Active Jobs
4. When complete, view the output log
5. Note how long the job took (queue wait + runtime)

:::::::::::::::::::::::::::::::: solution

1. Your script runs successfully on the compute node
2. Active Jobs shows the job progressing: Pending then Running then Completed
3. The output log shows your date stamps and confirms completion
4. Total time includes queue wait (seconds to minutes) plus the 30-second sleep
5. Job ID is a unique number assigned by SLURM

Common observations:

- Queue time varies based on cluster load
- Output appears in the log file after job completion
- The `amd` and `gpu` partitions each allow jobs up to 30 days (720 hours); the `short` partition has a shorter max walltime — check `sinfo -p short` for the current limit

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: keypoints
- Access the Job Composer through Jobs in the left sidebar
- Quick Submit lets you paste a script; Upload lets you use an existing file
- SLURM directives control partition, time, nodes, and output locations
- Use --partition=gpu and --gres=gpu:1 for GPU jobs
- Job arrays let you submit many similar jobs with one script
- Sagehen HPC offers three partitions: `amd`, `gpu` (both with 30-day max walltime), and `short` (shorter max walltime, good for quick test/debug jobs — check `sinfo -p short`)
::::::::::::::::::::::::::::::::::::::::::::::::::
