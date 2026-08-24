---
title: "Navigating Storage Locations"
teaching: 10
exercises: 5
---

:::::::::::::::::::::::::::::::::::::: questions
- What storage locations are available on Sagehen?
- How do /rhome and /bigdata differ from /scratch and /tmpfs?
- What are the capacity limits for each storage location?
- When should you use each storage location?
::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives
- Identify the four storage locations and their purposes
- Understand which storage is persistent and which is temporary
- Choose the right storage location for different types of data
- Check storage quotas using quota_check.sh
::::::::::::::::::::::::::::::::::::::::::::::::::

## Storage Locations on Sagehen

Sagehen provides four storage locations, each designed for different use cases. Access them through the **Files** menu in the left navigation.

### /rhome (Home Directory)

- **Path**: `/rhome/<myusername>`
- **Purpose**: Personal files, configuration, source code, small datasets
- **Persistent**: Yes -- files are preserved across sessions
- **Quota**: Shared 1 TB lab quota with /bigdata (BeeGFS filesystem)
- **Access**: Files > Home Directory

### /bigdata (Shared Research Storage)

- **Path**: `/bigdata/lab/<labname>`
- **Purpose**: Large research datasets shared across lab members
- **Persistent**: Yes -- files are preserved across sessions
- **Quota**: Shared 1 TB lab quota with /rhome (BeeGFS filesystem)
- **Access**: Files > bigdata

### /scratch (Fast Temporary Storage)

- **Path**: /scratch
- **Speed**: SSD (very fast)
- **Purpose**: Intermediate computation results, temporary working files
- **Persistent**: No -- files are deleted when the job completes
- **Quota**: Large, but temporary only
- **Access**: Files > scratch

### /tmpfs (In-Memory Storage)

- **Path**: /tmpfs (per-node, not shared across nodes)
- **Speed**: RAM-backed (fastest possible)
- **Purpose**: Extremely fast I/O during active jobs
- **Persistent**: No -- files are deleted when the job completes
- **Capacity**: Limited by node RAM
- **Access**: Only available within running SLURM jobs

::::::::::::::::::::::::::::::::::::: callout
## Choose Your Storage Wisely

Use **/rhome** for personal files and configuration. Store large research datasets in **/bigdata** for durability and sharing with collaborators. Use **/scratch** for temporary files needed during active jobs -- but remember, scratch is non-persistent SSD and files are deleted when the job completes. Never rely on /scratch or /tmpfs for permanent storage!
::::::::::::::::::::::::::::::::::::::::::::::::::

## Checking Your Quota

Because /rhome and /bigdata share a BeeGFS filesystem, the standard `du` command does not report usage correctly. Use the provided script instead:

```bash
quota_check.sh
```

Run this from the Web Terminal or a shell session to see your current usage against the 1 TB lab quota.

## Summary Table

| Location | Persistent | Speed | Shared | Best For |
|----------|-----------|-------|--------|----------|
| /rhome | Yes | Standard | Per-user | Config, code, small files |
| /bigdata | Yes | Standard | Per-lab | Research data, results |
| /scratch | No (job) | SSD | Yes | Temp computation files |
| /tmpfs | No (job) | RAM | Per-node | High-speed I/O in jobs |

::::::::::::::::::::::::::::::::::::: challenge

## Challenge: Match the Storage Location

For each scenario below, choose the best storage location (/rhome, /bigdata, /scratch, or /tmpfs):

1. You need to store a 200 GB genomics reference dataset that your whole lab uses.
2. You are writing a Python script for your analysis pipeline.
3. Your SLURM job produces 50 GB of intermediate files that are only needed during computation.
4. You need the fastest possible I/O for reading millions of small temporary files during a single job.
5. You want to keep your `.bashrc` and SSH configuration files.

:::::::::::::::::::::::::::::::: solution

1. **/bigdata** -- Large, shared dataset that needs to persist and be accessible to the whole lab.
2. **/rhome** -- Small personal file (source code) that should persist across sessions.
3. **/scratch** -- Intermediate files only needed during the job; deleted when the job completes.
4. **/tmpfs** -- RAM-backed storage provides the fastest I/O for temporary files within a single job.
5. **/rhome** -- Personal configuration files belong in your home directory.

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: keypoints
- Sagehen has four storage locations: /rhome, /bigdata, /scratch, and /tmpfs
- /rhome and /bigdata are persistent and share a 1 TB lab quota on BeeGFS
- /scratch is non-persistent SSD storage deleted when the job completes
- /tmpfs is RAM-backed storage deleted when the job completes
- Use quota_check.sh to check usage -- du does not work correctly on BeeGFS
- Choose storage based on persistence needs, speed requirements, and sharing
::::::::::::::::::::::::::::::::::::::::::::::::::

<!-- highlight <labname>/<myusername> placeholders in code blocks; remove if the varnish theme handles this natively -->
<script>(function(){var CSS='.sh-placeholder{color:#c2410c;font-weight:700}[data-bs-theme="dark"] .sh-placeholder,html.dark .sh-placeholder{color:#fdba74}@media (prefers-color-scheme: dark){[data-bs-theme="auto"] .sh-placeholder{color:#fdba74}}';var RX=/<labname>|<myusername>/g;function firstMatch(el){var w=document.createTreeWalker(el,NodeFilter.SHOW_TEXT,null),nodes=[],full='';while(w.nextNode()){nodes.push({n:w.currentNode,s:full.length});full+=w.currentNode.nodeValue;}RX.lastIndex=0;var m;while((m=RX.exec(full))){var s=m.index,e=s+m[0].length,inSpan=false,parts=[];for(var j=0;j<nodes.length;j++){var ns=nodes[j].s,ne=ns+nodes[j].n.nodeValue.length;if(ne<=s||ns>=e)continue;parts.push({node:nodes[j].n,a:Math.max(s-ns,0),b:Math.min(e-ns,nodes[j].n.nodeValue.length)});var p=nodes[j].n.parentNode;while(p&&p!==el){if(p.classList&&p.classList.contains('sh-placeholder')){inSpan=true;break;}p=p.parentNode;}}if(!inSpan&&parts.length)return parts;}return null;}function wrapParts(parts){for(var i=parts.length-1;i>=0;i--){var t=parts[i].node,txt=t.nodeValue,a=parts[i].a,b=parts[i].b;var span=document.createElement('span');span.className='sh-placeholder';span.textContent=txt.slice(a,b);var f=document.createDocumentFragment();if(a>0)f.appendChild(document.createTextNode(txt.slice(0,a)));f.appendChild(span);if(b<txt.length)f.appendChild(document.createTextNode(txt.slice(b)));t.parentNode.replaceChild(f,t);}}function run(){var st=document.createElement('style');st.textContent=CSS;document.head.appendChild(st);document.querySelectorAll('pre,code').forEach(function(el){var guard=0,parts;while((parts=firstMatch(el))&&guard++<500){wrapParts(parts);}});}if(document.readyState==='loading'){document.addEventListener('DOMContentLoaded',run);}else{run();}})();</script>
