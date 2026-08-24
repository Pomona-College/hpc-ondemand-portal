---
title: "RStudio and GPU Resources"
teaching: 15
exercises: 10
---

:::::::::::::::::::::::::::::::::::::: questions
- How do you launch RStudio from OnDemand?
- What is the RStudio interface layout?
- How do you request GPU resources for interactive apps?
- How do you verify GPU access in Jupyter or R?
::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives
- Launch an RStudio session and navigate the interface
- Execute R code and install R packages
- Request GPU resources when launching interactive apps
- Verify GPU availability and use GPU-accelerated libraries
::::::::::::::::::::::::::::::::::::::::::::::::::

## Launching RStudio

1. Click **Interactive Apps** in the left sidebar
2. Select **RStudio Server**
3. Configure resources (similar to Jupyter -- cores, memory, time)
4. Click **Launch** and wait for allocation
5. Click **Connect to RStudio** when the session is ready

## RStudio Interface Layout

Once launched, RStudio provides four panels:

- **Script editor** (top-left): Write and save R scripts
- **Console** (bottom-left): Execute R commands interactively
- **Environment/History** (top-right): View loaded variables and command history
- **Files/Plots/Packages** (bottom-right): Browse files, view plots, manage packages

## Running R Code

Write code in the script editor or directly in the console:

First create a small sample file to work with, then read it back, summarize,
and plot (in real work you would read your own data from
`/bigdata/lab/<labname>/` instead):

```r
library(tidyverse)

# Create a small sample dataset in your home directory
dir.create("~/rstudio-demo", showWarnings = FALSE)
write.csv(data.frame(variable1 = rnorm(8), variable2 = rnorm(8)),
          "~/rstudio-demo/data.csv", row.names = FALSE)

df <- read.csv("~/rstudio-demo/data.csv")
summary(df)

ggplot(df, aes(x = variable1, y = variable2)) +
  geom_point() +
  theme_minimal()
```

![A working version of the example: write a small sample CSV first, then read, summarize, and plot it — all four RStudio panes in action.](fig/07-rstudio-run-sample-script.png){alt='The four-panel RStudio Server interface. The editor and console show R code writing an eight-row sample CSV to the home directory, loading tidyverse, reading the file back, and printing a summary. The Plots pane displays a scatter plot and the Environment pane lists a data frame of 8 observations of 2 variables.'}

### Installing R Packages

In the console:

```r
install.packages("ggplot2")
install.packages("dplyr")
library(ggplot2)
```

Or use the **Packages** tab in the bottom-right panel to install graphically.

::::::::::::::::::::::::::::::::::::: callout
## Save Your Work

Interactive sessions have time limits. Save scripts and results frequently with **Ctrl+S**. Download important files or save to /bigdata for durability. Do not wait until your session expires -- save early and often.
::::::::::::::::::::::::::::::::::::::::::::::::::

## Requesting GPU Resources

When launching Jupyter or RStudio, select GPU options in the resource form:

- **GPU type**: A100 (80 GB) or L40S (48 GB)
- **GPU count**: Usually 1 for interactive work
- **Partition**: Select `gpu` to access GPU nodes

### Verifying GPU in Jupyter (Python)

```python
import torch
print(torch.cuda.is_available())       # Should print True
print(torch.cuda.get_device_name(0))   # Shows GPU model

import tensorflow as tf
print(tf.config.list_physical_devices('GPU'))
```

### Verifying GPU in R

```r
library(tensorflow)
tf$config$list_physical_devices('GPU')
```

### GPU-Accelerated Libraries

Once GPU is verified, use it for computation:

```python
import torch
x = torch.randn(1000, 1000).cuda()
y = torch.mm(x, x)
```

Monitor GPU usage from a terminal with `nvidia-smi`.

## Resource Guidelines

- **Small datasets** (< 100 MB): 1--2 cores, 4 GB memory, no GPU
- **Medium datasets** (100 MB -- 10 GB): 2--4 cores, 8--16 GB memory
- **GPU work**: Request only when needed -- GPUs are a shared resource
- Close sessions when finished to free resources for others

::::::::::::::::::::::::::::::::::::: challenge

## Challenge: Launch RStudio and Explore

1. Launch RStudio from OnDemand with 1 core, 4 GB memory, and 1 hour
2. In the console, load the tidyverse package: `library(tidyverse)`
3. Create a sample data frame:
   ```r
   df <- data.frame(
     x = rnorm(100),
     y = rnorm(100),
     group = sample(c("A", "B"), 100, replace = TRUE)
   )
   ```
4. Create a scatter plot:
   ```r
   ggplot(df, aes(x = x, y = y, color = group)) +
     geom_point() +
     theme_minimal() +
     labs(title = "Sample Scatter Plot")
   ```
5. Save the plot with `ggsave("scatter.png")`

:::::::::::::::::::::::::::::::: solution

![The expected challenge result: 100 random points colored by group, with the data frame in the Environment pane.](fig/07-rstudio-challenge-scatter.png){alt='RStudio Server showing the challenge solution. The console echoes code creating a 100-row data frame with x, y, and a two-level group column. The Plots pane displays a chart titled Sample Scatter Plot with points in two colors for groups A and B, and the Environment pane confirms 100 observations of 3 variables.'}

1. RStudio launches after resource allocation (1--5 minutes)
2. tidyverse loads with some startup messages (this is normal)
3. The data frame appears in the Environment panel showing 100 observations of 3 variables
4. A scatter plot appears in the Plots panel with points colored by group
5. The file "scatter.png" is saved in your working directory and visible in the Files panel

If tidyverse is not installed, run `install.packages("tidyverse")` first -- this may take a few minutes.

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: keypoints
- Launch RStudio from Interactive Apps with configurable resources
- RStudio provides script editor, console, environment, and files/plots panels
- Install R packages from the console or the Packages tab
- Request GPU resources by selecting the gpu partition and GPU type (A100, L40S, RTX PRO 6000)
- Verify GPU access with torch.cuda.is_available() in Python or tf in R
- Save your work frequently -- sessions have time limits
::::::::::::::::::::::::::::::::::::::::::::::::::

<!-- highlight <labname>/<myusername> placeholders in code blocks; remove if the varnish theme handles this natively -->
<script>(function(){var CSS='.sh-placeholder{color:#c2410c;font-weight:700}[data-bs-theme="dark"] .sh-placeholder,html.dark .sh-placeholder{color:#fdba74}@media (prefers-color-scheme: dark){[data-bs-theme="auto"] .sh-placeholder{color:#fdba74}}';var RX=/<labname>|<myusername>/g;function firstMatch(el){var w=document.createTreeWalker(el,NodeFilter.SHOW_TEXT,null),nodes=[],full='';while(w.nextNode()){nodes.push({n:w.currentNode,s:full.length});full+=w.currentNode.nodeValue;}RX.lastIndex=0;var m;while((m=RX.exec(full))){var s=m.index,e=s+m[0].length,inSpan=false,parts=[];for(var j=0;j<nodes.length;j++){var ns=nodes[j].s,ne=ns+nodes[j].n.nodeValue.length;if(ne<=s||ns>=e)continue;parts.push({node:nodes[j].n,a:Math.max(s-ns,0),b:Math.min(e-ns,nodes[j].n.nodeValue.length)});var p=nodes[j].n.parentNode;while(p&&p!==el){if(p.classList&&p.classList.contains('sh-placeholder')){inSpan=true;break;}p=p.parentNode;}}if(!inSpan&&parts.length)return parts;}return null;}function wrapParts(parts){for(var i=parts.length-1;i>=0;i--){var t=parts[i].node,txt=t.nodeValue,a=parts[i].a,b=parts[i].b;var span=document.createElement('span');span.className='sh-placeholder';span.textContent=txt.slice(a,b);var f=document.createDocumentFragment();if(a>0)f.appendChild(document.createTextNode(txt.slice(0,a)));f.appendChild(span);if(b<txt.length)f.appendChild(document.createTextNode(txt.slice(b)));t.parentNode.replaceChild(f,t);}}function run(){var st=document.createElement('style');st.textContent=CSS;document.head.appendChild(st);document.querySelectorAll('pre,code').forEach(function(el){var guard=0,parts;while((parts=firstMatch(el))&&guard++<500){wrapParts(parts);}});}if(document.readyState==='loading'){document.addEventListener('DOMContentLoaded',run);}else{run();}})();</script>
