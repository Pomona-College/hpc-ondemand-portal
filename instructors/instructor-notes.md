# OnDemand Portal Orientation - Instructor Notes

## Workshop Overview

This 2.5-hour workshop introduces beginners to the OnDemand web portal for HPC access. Participants learn to navigate the interface, manage files, access the command line, and run interactive applications.

## Learning Objectives

By the end of this workshop, learners will:
- Successfully log into OnDemand
- Navigate the dashboard and find key features
- Upload and download files
- Access the web terminal
- Launch Jupyter notebooks
- Submit batch jobs
- Monitor job progress

## Pre-Workshop Preparation

1. Verify all participants have:
   - Valid Pomona accounts
   - DUO MFA configured
   - Active HPC accounts
   - Working web browsers

2. Test OnDemand access yourself
3. Prepare example files for demonstrations
4. Have backup plans if cluster is offline

## Episode-by-Episode Teaching Guide

### Episode 1: What is OnDemand? (15 min teaching + 5 min exercise)

**Key Points to Emphasize:**
- OnDemand is a web interface, not a replacement for SSH
- No command-line knowledge required
- Graphical file manager is powerful for beginners
- Can run multiple applications simultaneously

**Demonstration:**
- Show login screen and dashboard
- Explain each menu section
- Highlight differences from SSH

**Interactive Exercise:**
- Have learners log in and navigate to Home Directory
- Show how to upload a test file
- Celebrate first interaction with OnDemand

**Common Questions:**
- "Is OnDemand slower than SSH?" (Slightly, but user-friendly)
- "Can I still use SSH?" (Yes, both work together)
- "What if I mess up files?" (Most stored safely with backups)

### Episode 2: Dashboard Navigation (20 min teaching + 10 min exercise)

**Key Points to Emphasize:**
- Consistent layout across all OnDemand pages
- Three main sections: Files, Jobs, Apps
- Help is always available via ? icon
- Status indicators use color coding

**Demonstration:**
- Walk through each menu item slowly
- Show how to access profile/account settings
- Demonstrate session management
- Explain timeout and re-authentication

**Interactive Exercise:**
- Have learners navigate to each main section
- Locate their disk quota
- Find current cluster status
- Identify available partitions

**Tips for Teaching:**
- Use large screen/projector for visibility
- Pause after each section for questions
- Have ready answers for "Where do I find...?"
- Remind about browser cache if pages look odd

### Episode 3: File Manager (20 min teaching + 15 min exercise)

**Key Points to Emphasize:**
- Four main storage locations: /rhome, /bigdata, /scratch, /tmpfs
- /rhome and /bigdata share a single 1 TB lab quota on BeeGFS
- /bigdata is for collaborative research data
- /scratch is non-persistent SSD; auto-deleted when the job completes — there is no grace period.

**Demonstration:**
- Upload a file (preferably <10 MB for speed)
- Download it back
- Create a directory and move a file
- Show quota usage in Accounts/Usage
- Demonstrate file permissions

**Interactive Exercise:**
- Each learner uploads a test file
- Creates a new directory
- Moves file into directory
- Downloads file back to verify round-trip
- Checks their disk quota

**Trouble Spots:**
- Upload may be slow with many concurrent uploads
- Drag-and-drop doesn't work in all browsers
- Some learners may accidentally delete files
- Path confusion (/bigdata vs /rhome)

**Solutions:**
- Break class into small groups for uploads
- Show explicit Upload button as fallback
- Explain deletion is permanent (no trash)
- Clarify path with absolute paths in challenges

### Episode 4: Shell Access (20 min teaching + 15 min exercise)

**Key Points to Emphasize:**
- Web Terminal is a full bash shell
- Same commands as SSH work here
- Good for running jobs and file operations
- Less suitable for interactive programs (vim, top)

**Demonstration:**
- Launch web terminal from OnDemand
- Show basic commands: ls, pwd, cd
- Submit a simple SLURM job
- Show job output
- Demonstrate module loading

**Interactive Exercise:**
- Launch web terminal
- Navigate to home directory
- Create a new directory
- View files with ls
- Submit a simple job (sleep 30)
- Check job status
- View job output when complete

**Teaching Tips:**
- Many learners have never used bash before
- Use simple commands first (ls, pwd)
- Explain that "command not found" is normal (need module load)
- Show job submission without complex SLURM script details

**Potential Issues:**
- Learners may type passwords or sensitive data in terminal
- Slow typing on web terminal causes lag
- Jobs fail due to typos or missing modules
- Terminal disconnections on slow connections

### Episode 5: Interactive Applications (20 min teaching + 15 min exercise)

**Key Points to Emphasize:**
- Jupyter notebooks combine code and documentation
- RStudio provides full R IDE
- Resource allocation determines launch time
- Sessions timeout; download work before expiry

**Demonstration:**
- Launch Jupyter notebook
- Show cells, markdown, output
- Create simple Python code cell
- Create matplotlib visualization
- Save notebook
- Close notebook and show it's gone (session ended)

**Alternatively, show RStudio:**
- Show script editor, console, environment, plots pane
- Write simple R code
- Create ggplot visualization
- Show package installation

**Interactive Exercise:**
- Each learner launches Jupyter
- Creates a notebook with:
  * import statement
  * data creation (numpy array or pandas DataFrame)
  * simple calculation
  * visualization
- Download the notebook
- Close the session

**For GPU Learners (if available):**
- Show GPU allocation in launcher
- Verify GPU with pytorch/tensorflow
- Do simple GPU operation
- Monitor with nvidia-smi

**Common Challenges:**
- Long launch times on busy clusters
- Not enough GPU resources available
- Learners don't save before session timeout
- Package installation errors

**Solutions:**
- Warn about 5-10 minute launch time
- Have CPU-only notebooks as backup
- Emphasize downloading notebooks
- Have pre-installed common packages
- Show error messages when they occur

### Episode 6: Job Management (20 min teaching + 15 min exercise)

**Key Points to Emphasize:**
- Job Composer is easier than manual scripts
- SLURM scheduler manages queue fairly
- Jobs can wait hours; patience required
- Check output files after job completion

**Demonstration:**
- Create simple job in Job Composer
- Submit to normal partition
- Show job in Active Jobs view
- Wait for job to start (may take 2-10 min)
- Show job progressing
- When done, view output
- Explain stderr vs stdout

**Demonstration of Cancellation:**
- Submit another job
- Before it starts, cancel it
- Show it disappears or changes status

**Interactive Exercise:**
- Create job that:
  * Prints start time
  * Runs calculation (Python, R, or sleep)
  * Prints end time
- Submit job
- Monitor until completion
- View output
- Calculate actual runtime

**For GPU Interest:**
- Show GPU job submission with `--gres=gpu:1`
- Explain wait times for GPU are longer
- Show GPU-specific output

**Teaching Notes:**
- Cluster timing may make jobs run immediately or queue
- Use this as teaching moment about SLURM scheduling
- Some jobs may fail; use as debugging opportunity
- Explain error messages clearly

## Timing Guide

### Full Workshop (2.5 hours)
- Episode 1: 20 min
- Episode 2: 30 min
- Episode 3: 35 min
- Episode 4: 35 min
- Episode 5: 35 min
- Episode 6: 35 min
- Buffer/Wrap-up: 10 min
- **Total: 200 minutes**

### Shortened Workshop (1.5 hours)
- Episode 1: 15 min
- Episode 2: 15 min
- Episode 3: 20 min
- Episode 4: 20 min (skip shell details)
- Episode 5: 20 min (demo only, quick exercise)
- Brief overview of Episode 6 (5 min)

## Handling Common Issues During Teaching

### Cluster is Offline/Slow
- Pre-record demonstrations
- Show screenshots if live demo fails
- Explain maintenance windows
- Provide hands-on instructions for later

### Many Concurrent Uploads
- Stagger upload exercises
- Break into smaller groups
- Use /scratch for testing (faster)
- Explain bandwidth limitations

### Learners Stuck on Login
- Verify Pomona credentials
- Check DUO is configured
- Try different browser
- Have ITS contact ready

### Jobs Not Starting Quickly
- Explain cluster load
- Show cluster status (sinfo output)
- Use this as lesson on SLURM scheduling
- Have running example jobs ready to show

### Terminals or Apps Crash
- Browser refresh usually fixes
- Have alternative browser ready
- Show offline documentation
- Take this opportunity to discuss resilience

## Assessment and Feedback

### Formative Assessment
During workshop, ask:
- "Can you find the Upload button?"
- "Which storage location should we use for this 50 GB dataset?"
- "What partition would we use for GPU work?"

### Hands-On Completion
Check that each learner completes:
1. Successfully logs in
2. Uploads a file
3. Opens web terminal
4. Launches Jupyter or RStudio
5. Submits a simple job
6. Views job output

### Post-Workshop Survey
Ask about:
- Confidence with OnDemand
- Which features they'll use most
- Topics needing more depth
- Next training they want

## Resources

### Emergency Contacts
- HPC Support: its-hpc@pomona.edu
- ITS Support: (for account issues)
- OnDemand errors: Screenshot and email to its-hpc@pomona.edu

### Helpful References
- OnDemand Help: Built-in ? icon
- Sagehen Docs: https://hpc.pomona.edu/wiki/
- SLURM Docs: https://slurm.schedmd.com/
- Carpentries HPC: https://carpentries-incubator.github.io/hpc-intro/

## Post-Workshop Follow-up

Send learners:
1. Certificate of completion (if applicable)
2. Link to OnDemand help documentation
3. Info about next workshops (Security, GPU, ML)
4. Contact info for support
5. Optional: recorded session video (if recorded)

## Notes for Future Instructors

- Include more examples of real research workflows if possible
- Cluster performance varies; plan for waits
- Some learners take time with new interfaces; patience helps
- Celebrating first successful job submission is powerful
- Many learners will want to return for advanced topics
- Consider recording for asynchronous learners

Good luck with your workshop!
