---
title: "Shell Access and Command-Line Computing"
teaching: 20
exercises: 15
---

:::::::::::::::::::::::::::::::::::::: questions
- How do you access the command line through OnDemand?
- What is a Web Terminal session?
- How do you manage multiple terminal sessions?
- What commands are available in OnDemand shell access?
::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives
- Launch and use the Web Terminal from OnDemand
- Execute HPC commands without SSH
- Manage multiple concurrent terminal sessions
- Navigate the file system and manage resources using shell
- Understand limitations and best practices for web-based terminals
::::::::::::::::::::::::::::::::::::::::::::::::

## Web Terminal Access

The Web Terminal in OnDemand provides a full command-line shell through your browser, eliminating the need to install SSH clients or learn command-line interfaces. It connects to a login node on Sagehen.

::::::::::::::::::::::::::::::::::::: callout
## Important: Login vs. Compute Nodes

The Web Terminal connects to a login node, designed for small, quick tasks like editing files and submitting jobs. For intensive computations, submit SLURM jobs instead. Running computationally heavy tasks on the login node can affect other users.
::::::::::::::::::::::::::::::::::::::::::::::::

## Launching the Web Terminal

### Method 1: Through Interactive Apps

1. Open OnDemand at https://ondemand.hpc.pomona.edu/
2. Navigate to "Interactive Apps" menu (left sidebar)
3. Find and click "Web Terminal" or "Shell Access"
4. Click "Launch"
5. After a brief loading period, a terminal window opens in your browser

### Method 2: Through Clusters Menu

1. Go to Clusters menu
2. Select "Sagehen Shell Access"
3. A terminal launches in a new tab

The terminal takes a few seconds to initialize the first time. Once loaded, you have a fully functional bash shell.

## Using the Web Terminal

### Basic Operations

The Web Terminal behaves like a standard Linux terminal. You can execute standard commands for:

- Checking your current directory: pwd
- Listing files: ls, ls -la
- Changing directories: cd /rhome/username
- Viewing file contents: cat, head
- Creating directories: mkdir
- Copying and moving files: cp, mv

### Text Editing

You can use command-line editors from the web terminal:

- Nano: A beginner-friendly editor (Ctrl+X to exit)
- Vim: An advanced editor (:wq to save)
- Default editor: edit command for text files

### Job Submission

Submit SLURM jobs directly from the terminal with sbatch. View job status with squeue. Cancel jobs with scancel. Check cluster information with sinfo.

A typical job script includes:

```
#!/bin/bash
#SBATCH --job-name=MyJob
#SBATCH --partition=normal
#SBATCH --nodes=1
#SBATCH --time=01:00:00
#SBATCH --output=job.log

echo "Starting job at $(date)"
sleep 30
echo "Job complete"
```

### Module Management

Load software modules for your work:

- module avail: List available modules
- module load: Load a specific module
- module list: See currently loaded modules
- module unload: Remove a module
- module purge: Clear all modules

## Multiple Terminal Sessions

### Opening Multiple Terminals

You can open multiple terminal windows simultaneously through OnDemand. Each terminal is independent and can run different tasks. Use multiple terminals to monitor jobs while editing code, or to run multiple processes in parallel.

Browser tabs help organize your work:

- Rename tabs to identify their purpose
- Switch between tabs with mouse or keyboard shortcuts
- Closing a tab closes that terminal session

## File Operations in the Terminal

### Working with Data

Standard Linux commands work for file operations:

- wc -l: Count lines in files
- grep: Search for patterns in text
- sort and uniq: Organize data
- tar and gzip: Compress and archive files
- File manipulation: ls, cp, mv, rm, etc.

### Creating Python Scripts

Python scripts can be created and executed from the terminal. Load Python with module load if needed, or use the system Python. Create files with editors or echo commands, then execute with python3.

### Running Shell Scripts

Shell scripts can automate repetitive tasks. Create with a text editor, make executable with chmod +x, then run with ./scriptname.

## Monitoring and Resource Management

### Check System Resources

- top: View current CPU and memory usage
- sinfo: See available nodes and partitions
- squeue: View all jobs (or -u $USER for your jobs)
- scontrol show job: Get detailed job information
- hostname: See which machine you're on

### Environment Variables

Access important information about your environment and current job:

- $USER: Your username
- $HOME: Your home directory path
- $SLURM_NODELIST: Nodes allocated to your job
- hostname: The current machine name

## Terminal Limitations and Considerations

The Web Terminal has some important limitations:

- Interactive programs may have limited support
- Can only connect to systems accessible from Sagehen
- Long-idle sessions may disconnect
- Copy-paste works with Ctrl+C/Ctrl+V
- Personal SSH keys are available for other systems

## Best Practices for Web Terminal

1. Don't leave idle terminals open; close ones you're not actively using
2. Use screen or tmux for long-running processes that survive disconnections
3. Save work frequently in case of unexpected disconnections
4. Write temporary files to /scratch, not /rhome
5. Monitor resources with squeue before launching new jobs
6. Cancel idle jobs with scancel to free resources

::::::::::::::::::::::::::::::::::::: callout
## Pro Tip: Use screen or tmux

For long-running processes, use `screen` or `tmux` to create persistent sessions that survive browser disconnections. Start your process inside a screen session, then detach with Ctrl+A+D. Reconnect later even after closing your terminal.
::::::::::::::::::::::::::::::::::::::::::::::::

## Troubleshooting Terminal Issues

- Slow performance: Try a different browser or check network
- Copy-paste issues: Try Ctrl+Shift+C/Ctrl+Shift+V
- Disconnections: Open new terminal and check squeue for jobs
- Command not found: Load required module with module load
- Permission denied: Check file permissions with ls -l

::::::::::::::::::::::::::::::::::::: challenge

## Challenge: Command-Line Computing

Use the Web Terminal to complete these tasks:
1. Navigate to your /rhome directory and list all files
2. Create a new directory called "my_analysis"
3. Create a simple Python script that prints "Hello from Sagehen!"
4. Run the Python script from the terminal
5. Check the current status of the Sagehen cluster with sinfo
6. View any jobs you have running with squeue -u $USER

Record what you observe, especially:
- How many nodes are in the cluster?
- What partitions are available?
- Are you currently running any jobs?

:::::::::::::::::::::::::::::::: solution

After completing this challenge:
1. Your /rhome directory contains configuration files and personal data
2. The new directory appears in listings with mkdir
3. Your Python script executes successfully, printing the output
4. sinfo shows the cluster composition with nodes in various partitions
5. squeue -u $USER shows your jobs if running, or an empty table
6. You see partition information and node status

Common observations:
- Most nodes are idle or allocated during normal times
- Jobs have IDs starting from recent numbers
- Python/Python3 is available without module loading
- The terminal responds quickly to most commands
- Complex file operations work just like SSH access
- Cluster status changes throughout the day as jobs complete

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

## Accessing Sagehen via SSH (Alternative)

While the Web Terminal is convenient, some users prefer SSH for direct access:

```
ssh username@sagehen.hpc.pomona.edu
ssh -i ~/.ssh/id_rsa username@sagehen.hpc.pomona.edu
```

SSH provides the same shell access but requires pre-configured authentication on your local computer.

::::::::::::::::::::::::::::::::::::: keypoints
- Web Terminal provides full command-line access through your browser
- Launch from Interactive Apps or Clusters menu in OnDemand
- Run standard Linux commands, submit SLURM jobs, and manage files
- Multiple terminal sessions can run independently for parallel work
- Use screen/tmux for long-running processes that survive disconnections
- Web Terminal is convenient for beginners; SSH is available for advanced users
::::::::::::::::::::::::::::::::::::::::::::::::
