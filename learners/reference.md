# OnDemand Portal Orientation - Learner Reference

## Quick Start Guide

### Logging In
1. Go to https://ondemand.hpc.pomona.edu/
2. Enter Pomona username and password
3. Complete DUO MFA
4. Dashboard appears

### Main Menu Items

**Files**
- Home Directory: Your /rhome/username
- bigdata: Group research storage
- scratch: Temporary fast storage
- tmpfs: In-memory storage (for jobs)
- Edit Files: Text editor

**Jobs**
- Active Jobs: View running/queued jobs
- Job Composer: Submit new jobs
- Cluster: View cluster status

**Interactive Apps**
- Jupyter Notebook: Python notebooks with optional GPU
- Jupyter Lab: Extended notebook interface
- RStudio Server: R statistical computing
- Web Terminal: Command-line access

**Accounts**
- Usage: Quota and resource usage
- Profile: Account settings

**Clusters**
- Sagehen Shell Access: Web terminal

## Common Commands in Web Terminal

### File Operations
```
ls                 # List files
cd dirname         # Change directory
mkdir newdir       # Create directory
cp file1 file2     # Copy file
mv file1 file2     # Move/rename
rm file            # Delete (permanent!)
pwd                # Show current location
```

### Viewing Files
```
cat filename       # View entire file
head filename      # View first 10 lines
tail filename      # View last 10 lines
less filename      # Page through file
grep pattern file   # Search for pattern
```

### Job Commands
```
sbatch script.sh   # Submit job
squeue -u $USER    # List your jobs
scancel JOBID      # Cancel job
sinfo              # Cluster status
```

### Module System
```
module avail       # Available modules
module load name   # Load module
module list        # Loaded modules
module unload name # Remove module
```

## Storage Locations Reference

| Location | Size | Purpose | Backed up |
|----------|------|---------|-----------|
| /rhome | 100 GB | Personal files | Yes |
| /bigdata | 1-10 TB | Research data | Yes |
| /scratch | Large | Temp files | No |
| /tmpfs | 256 GB | RAM disk | No |

## Sagehen Cluster Information

### Partitions
- **normal**: General purpose computing (default)
- **gpu**: GPU-accelerated computing
- **memory**: High-memory jobs

### GPU Types
- **A100**: 80 GB, for large models
- **L40S**: 48 GB, for deep learning
- **V100**: 16 GB, for research-scale work

### Job Limits
- Max time: 720 hours (30 days)
- Max GPUs: 4 per user
- Default memory: See sinfo

## Useful Keyboard Shortcuts

### In Web Terminal
- Ctrl+C: Stop running command
- Ctrl+L: Clear screen
- Up arrow: Previous command
- Ctrl+R: Search command history
- Ctrl+A: Beginning of line
- Ctrl+E: End of line

### In Jupyter Notebook
- Shift+Enter: Run cell
- Ctrl+S: Save notebook
- Esc: Leave edit mode
- A: Add cell above
- B: Add cell below
- D, D: Delete cell

### In RStudio
- Ctrl+Enter: Run selected line
- Ctrl+Shift+S: Source file
- Ctrl+Shift+O: Go to file
- Ctrl+Shift+A: Reformat code

## Transferring Files

### Upload via OnDemand
1. Click file manager
2. Click Upload button
3. Select file(s)
4. Click Start Upload

### Download via OnDemand
1. Find file in file manager
2. Right-click → Download
3. Or select and click Download button

### From Command Line
```
scp local_file username@sagehen.hpc.pomona.edu:/remote/path
scp username@sagehen.hpc.pomona.edu:/remote/file local_path
```

## OnDemand Features Quick Reference

### Dashboard Overview

The OnDemand dashboard is your home page with quick access to:

- **Files**: Browse and manage all storage locations
- **Jobs**: Submit and monitor batch jobs
- **Interactive Apps**: Launch Jupyter, RStudio, terminals
- **Account**: Check quotas and profile settings
- **Help**: Click "?" in top navigation for context-sensitive help

### File Permissions Quick Guide

```
chmod 755    Everyone can read; only owner can write
chmod 750    Owner and group can access; others cannot
chmod 700    Only owner can access (most private)
chmod 644    Everyone can read; only owner can write (for files)
```

Use in web terminal: `chmod 755 /path/to/file`

### Common Errors and Solutions

### "File not found" error
- Check file path is correct
- Use absolute path: `/rhome/username/file` not `~/file`
- Verify file exists in file manager before trying to open
- Check spelling and capitalization

### "Permission denied"
- Check file permissions in file manager: Icon with lock means restricted
- Make script executable: `chmod +x myscript.sh`
- Ask file owner for permission if needed
- Check you're in the right group

### Module not found (in Web Terminal)
- Check correct module name: `module avail`
- Some modules need version: `module load python/3.11`
- Load module before running commands: `module load python` then `python script.py`

### Quota exceeded
- Check usage in Accounts → Usage
- Move large files to /bigdata (bigger quota)
- Delete old or temporary files
- Email its-hpc@pomona.edu to request quota increase

### Upload is very slow
- Large files take time; be patient
- Faster upload at off-peak hours
- Check internet speed with speedtest.net
- Try uploading smaller chunks if file is huge (>1 GB)

### Job won't start or says "pending"
- Check cluster has available resources: Click Clusters → view sinfo output
- Jobs may wait hours during busy times
- Try requesting fewer resources
- Check job for errors in output file

### Can't launch Jupyter or RStudio
- Long launch times (5-10 min) on busy cluster are normal
- Check OnDemand session hasn't timed out
- Try stopping the app and launching again
- Check Available resources in Accounts → Usage

## OnDemand Best Practices

- **Save your work frequently**: Sessions timeout after inactivity
- **Download notebooks before closing**: Jupyter sessions are temporary
- **Use /bigdata for large datasets**: /rhome has 100 GB limit
- **Monitor job output**: Check job files for errors after completion
- **Log out when done**: Closes web terminal and interactive sessions
- **Test with small data first**: Before processing large datasets

## Storage Best Practices

| Where to Store | What | Duration | Backed Up |
|----------------|------|----------|-----------|
| /rhome/user | Personal files, code | Permanent | Yes |
| /bigdata/lab | Research data, collaboration | Permanent | Yes |
| /scratch/job_id | Temporary job files | 60 days | No |
| /tmpfs/job_id | Fast temporary data | During job only | No |

## Getting Help

- **OnDemand Help**: Click "?" icon in top right navigation
- **Documentation**: https://hpc.pomona.edu/wiki/
- **Email Support**: its-hpc@pomona.edu
- **In-person Help**: HPC office hours (see https://hpc.pomona.edu/)

## Tips for Success

1. **Start simple**: Upload a small file before trying large transfers
2. **Use web terminal sparingly**: Graphical tools are often easier for file work
3. **Save your passwords**: Store OnDemand password in password manager
4. **Know your storage paths**: Learn difference between /rhome, /bigdata, /scratch
5. **Check job status regularly**: Don't submit and forget
6. **Plan ahead for long jobs**: They may queue for hours
7. **Keep learning**: OnDemand has many features beyond basics

## Cheat Sheet: First Time Steps

1. Log into https://ondemand.hpc.pomona.edu/
2. Click Files → Home Directory
3. Upload a test file using Upload button
4. Go to Interactive Apps → Web Terminal
5. In terminal, type: cd /rhome/username && ls
6. You see your uploaded file
7. Go to Interactive Apps → Jupyter Notebook
8. Click Launch and wait for notebook to start
9. Create a Python cell with: print("Hello Sagehen!")
10. Run the cell with Shift+Enter

Congratulations - you've used all the main OnDemand features!
