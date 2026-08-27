---
title: "What is OnDemand?"
teaching: 15
exercises: 5
---

:::::::::::::::::::::::::::::::::::::: questions
- What is OnDemand and why use it?
- How does OnDemand differ from SSH?
- What are the benefits for HPC users?
::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives
- Understand the purpose and benefits of OnDemand
- Learn the difference between OnDemand web interface and command-line SSH access
- Identify use cases where OnDemand is most valuable
::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction to OnDemand

OnDemand is a web-based interface to access and control Sagehen HPC resources without requiring SSH knowledge or specialized terminal software. It provides a graphical dashboard through which you can manage files, submit jobs, monitor computations, and run interactive applications directly from your web browser.

## Why Use OnDemand?

OnDemand provides several advantages over traditional SSH access:

- **No SSH knowledge required**: Access HPC resources through a familiar web browser
- **Graphical file manager**: Upload, download, and organize files without command-line tools
- **Interactive applications**: Run Jupyter notebooks, RStudio, and other interactive apps directly
- **Job monitoring**: Visualize job status and monitor resource usage in real time
- **Multiple workspaces**: Maintain different computational sessions simultaneously
- **Mobile-friendly**: Access resources from tablets and laptops with limited terminal capabilities

::::::::::::::::::::::::::::::::::::: callout
## Perfect for Beginners

OnDemand is ideal if you're new to HPC and prefer graphical interfaces. You can accomplish most common tasks without learning command-line tools. Point, click, and go!
::::::::::::::::::::::::::::::::::::::::::::::::

![Everything OnDemand can launch, in one menu.](fig/interactive-apps-menu.png){alt='The Interactive Apps dropdown menu open on the OnDemand dashboard. It lists a Desktop entry, then a GUIs group containing Autodock Vina, Comsol, Cryosparc, Gaussian, MATLAB, Mathematica, Qgis, Schrodinger, Stata and Tycho, then a Servers group containing Jupyter Notebook and RStudio Server.'}

## OnDemand vs SSH Access

While SSH remains powerful for advanced users, OnDemand complements it by offering:

| Feature | OnDemand | SSH |
|---------|----------|-----|
| Learning curve | Low | Steep |
| File management | Graphical | Command-line |
| Interactive apps | Direct support | Manual setup |
| Job submission | Web form | Script writing |
| Device compatibility | All browsers | Terminal only |

## Accessing OnDemand

OnDemand at Pomona College is available at:

```
https://ondemand.hpc.pomona.edu/
```

Access requires:
- Valid Pomona College credentials
- DUO Multi-Factor Authentication (MFA)
- Active HPC account approved by your PI

## What You Can Do in OnDemand

### File Management
- Browse your home directory (`/rhome/<myusername>`)
- Manage research data in /bigdata
- Upload and download files
- Create new directories
- Edit text files

### Job Submission
- Submit batch jobs without writing SLURM scripts
- Monitor job progress
- View job output in real-time
- Cancel running jobs

### Interactive Applications
- Launch Jupyter notebooks with GPU support
- Start RStudio for statistical computing
- Access web terminals for command-line work
- Run custom interactive applications

### System Resources
- Check CPU and memory availability
- Monitor cluster status
- View node information
- Track quota usage

::::::::::::::::::::::::::::::::::::: callout
## Important: Authentication Required

You'll need valid Pomona College credentials and DUO Multi-Factor Authentication to access OnDemand. Ensure your HPC account is active before attempting to log in. Contact its-hpc@pomona.edu if you have access issues.
::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: challenge

## Challenge: Explore the Concept

Consider your typical workflow on Sagehen. Which tasks would benefit most from using OnDemand instead of SSH? Think about:
1. File management tasks
2. Data exploration work
3. Interactive development
4. Batch processing

:::::::::::::::::::::::::::::::: solution

There is no single correct answer, but common answers include:
- **File management**: OnDemand is superior for uploading large datasets or browsing files
- **Data exploration**: Jupyter notebooks through OnDemand are ideal for exploratory analysis
- **Learning**: Beginners benefit from OnDemand's graphical interface
- **Multiple tasks**: OnDemand allows running several applications simultaneously in separate browser tabs
- **Mobile/remote**: OnDemand works anywhere you have internet and a browser

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

## Next Steps

Now that you understand what OnDemand offers, let's explore the dashboard and learn to navigate its features.

::::::::::::::::::::::::::::::::::::: keypoints
- OnDemand is a web-based interface for accessing Sagehen HPC resources
- It requires no SSH knowledge and works in any modern web browser
- OnDemand is ideal for file management, interactive computing, and job monitoring
- Pomona's OnDemand is available at https://ondemand.hpc.pomona.edu/
- OnDemand complements SSH access rather than replacing it
::::::::::::::::::::::::::::::::::::::::::::::::

<!-- highlight <labname>/<myusername> placeholders in code blocks; remove if the varnish theme handles this natively -->
<script>(function(){var CSS='.sh-placeholder{color:#c2410c;font-weight:700}[data-bs-theme="dark"] .sh-placeholder,html.dark .sh-placeholder{color:#fdba74}@media (prefers-color-scheme: dark){[data-bs-theme="auto"] .sh-placeholder{color:#fdba74}}';var RX=/<labname>|<myusername>/g;function firstMatch(el){var w=document.createTreeWalker(el,NodeFilter.SHOW_TEXT,null),nodes=[],full='';while(w.nextNode()){nodes.push({n:w.currentNode,s:full.length});full+=w.currentNode.nodeValue;}RX.lastIndex=0;var m;while((m=RX.exec(full))){var s=m.index,e=s+m[0].length,inSpan=false,parts=[];for(var j=0;j<nodes.length;j++){var ns=nodes[j].s,ne=ns+nodes[j].n.nodeValue.length;if(ne<=s||ns>=e)continue;parts.push({node:nodes[j].n,a:Math.max(s-ns,0),b:Math.min(e-ns,nodes[j].n.nodeValue.length)});var p=nodes[j].n.parentNode;while(p&&p!==el){if(p.classList&&p.classList.contains('sh-placeholder')){inSpan=true;break;}p=p.parentNode;}}if(!inSpan&&parts.length)return parts;}return null;}function wrapParts(parts){for(var i=parts.length-1;i>=0;i--){var t=parts[i].node,txt=t.nodeValue,a=parts[i].a,b=parts[i].b;var span=document.createElement('span');span.className='sh-placeholder';span.textContent=txt.slice(a,b);var f=document.createDocumentFragment();if(a>0)f.appendChild(document.createTextNode(txt.slice(0,a)));f.appendChild(span);if(b<txt.length)f.appendChild(document.createTextNode(txt.slice(b)));t.parentNode.replaceChild(f,t);}}function run(){var st=document.createElement('style');st.textContent=CSS;document.head.appendChild(st);document.querySelectorAll('pre,code').forEach(function(el){var guard=0,parts;while((parts=firstMatch(el))&&guard++<500){wrapParts(parts);}});}if(document.readyState==='loading'){document.addEventListener('DOMContentLoaded',run);}else{run();}})();</script>
