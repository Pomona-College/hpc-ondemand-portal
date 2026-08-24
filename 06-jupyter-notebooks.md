---
title: "Launching Jupyter Notebooks"
teaching: 15
exercises: 10
---

:::::::::::::::::::::::::::::::::::::: questions
- How do you launch a Jupyter notebook from OnDemand?
- How do you configure resources for your notebook session?
- How do you use notebook cells, run code, and write documentation?
- How do you install additional Python packages?
::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives
- Launch a Jupyter notebook session from OnDemand
- Configure CPU, memory, and time for your session
- Create and execute code and markdown cells
- Upload data and install packages in the notebook environment
::::::::::::::::::::::::::::::::::::::::::::::::::

## Launching Jupyter

1. Click **Interactive Apps** in the left sidebar
2. Select **Jupyter Notebook** (or **Jupyter Lab**)
3. Configure your resources:
   - **CPU cores**: 1--4 for most work
   - **Memory**: 4--16 GB depending on dataset size
   - **Time**: 1--8 hours
   - **GPU** (optional): Select if you need accelerated computing
4. Click **Launch**
5. Wait for allocation (typically 1--5 minutes)
6. Click **Connect to Jupyter** when the session is ready

::::::::::::::::::::::::::::::::::::: callout
## First Launch Takes Time

When you request Jupyter, expect to wait 1--5 minutes for resource allocation, especially during busy hours. The system is requesting compute nodes for your session. Subsequent launches typically start faster.
::::::::::::::::::::::::::::::::::::::::::::::::::

## Using Jupyter Notebooks

### Creating a Notebook

Click **New** then **Python 3** to create a new notebook. Each notebook is a `.ipynb` file saved in your working directory.

### Cell Types and Execution

- **Code cells**: Write Python code and press **Shift+Enter** to execute
- **Markdown cells**: Write formatted text, headings, and documentation
- **Output**: Results, tables, and plots appear directly below each cell

A common first cell:

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
print("Libraries loaded successfully!")
```

### Uploading Data

1. Use the Jupyter file browser on the left to navigate to your data
2. Or click the **Upload** button within Jupyter
3. Read files in your notebook:

```python
data = pd.read_csv('/bigdata/lab/<labname>/data.csv')
print(data.head())
```

Use absolute paths (like `/bigdata/lab/<labname>/`) to avoid confusion about your working directory.

### Installing Packages

Install additional packages directly from a notebook cell:

```python
!pip install scikit-learn
!pip install seaborn
```

Or open a terminal in Jupyter (**New** > **Terminal**) for more complex installations.

## Session Management

- Sessions expire after idle time or when the requested time limit is reached
- Save your work frequently with **Ctrl+S**
- Download important notebooks before your session expires
- Check remaining time in the OnDemand Active Jobs view

Use batch jobs (`sbatch`) for computations longer than 8 hours instead of interactive Jupyter sessions.

::::::::::::::::::::::::::::::::::::: challenge

## Challenge: Create Your First Notebook

1. Launch a Jupyter notebook from OnDemand with 1 core, 4 GB memory, and 1 hour
2. Create a new Python 3 notebook
3. In cell 1, import numpy, pandas, and matplotlib
4. In cell 2, create a sample dataset:
   ```python
   data = np.random.normal(loc=50, scale=10, size=500)
   df = pd.DataFrame({'values': data})
   print(df.describe())
   ```
5. In cell 3, create a histogram:
   ```python
   plt.hist(df['values'], bins=25, edgecolor='black')
   plt.xlabel('Value')
   plt.ylabel('Frequency')
   plt.title('Sample Distribution')
   plt.show()
   ```
6. Save your notebook

:::::::::::::::::::::::::::::::: solution

1. Jupyter launches after 1--5 minutes of resource allocation
2. A new notebook opens with an empty code cell
3. All three libraries import without errors
4. `df.describe()` prints count, mean, std, min, max, and quartiles
5. A histogram appears inline showing a normal distribution centered around 50
6. The notebook saves as an `.ipynb` file in your working directory

If your session takes a long time to start, the cluster may be busy -- try reducing your resource request or launching during off-peak hours.

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: keypoints
- Launch Jupyter from Interactive Apps with configurable CPU, memory, and time
- Expect 1--5 minutes for initial resource allocation
- Use code cells for Python and markdown cells for documentation
- Install packages with !pip install directly in notebook cells
- Save work frequently and download notebooks before sessions expire
- Use batch jobs for computations longer than 8 hours
::::::::::::::::::::::::::::::::::::::::::::::::::

<!-- highlight <labname>/<myusername> placeholders in code blocks; remove if the varnish theme handles this natively -->
<script>(function(){var CSS='.sh-placeholder{color:#c2410c;font-weight:700}[data-bs-theme="dark"] .sh-placeholder,html.dark .sh-placeholder{color:#fdba74}@media (prefers-color-scheme: dark){[data-bs-theme="auto"] .sh-placeholder{color:#fdba74}}';var RX=/<labname>|<myusername>/g;function firstMatch(el){var w=document.createTreeWalker(el,NodeFilter.SHOW_TEXT,null),nodes=[],full='';while(w.nextNode()){nodes.push({n:w.currentNode,s:full.length});full+=w.currentNode.nodeValue;}RX.lastIndex=0;var m;while((m=RX.exec(full))){var s=m.index,e=s+m[0].length,inSpan=false,parts=[];for(var j=0;j<nodes.length;j++){var ns=nodes[j].s,ne=ns+nodes[j].n.nodeValue.length;if(ne<=s||ns>=e)continue;parts.push({node:nodes[j].n,a:Math.max(s-ns,0),b:Math.min(e-ns,nodes[j].n.nodeValue.length)});var p=nodes[j].n.parentNode;while(p&&p!==el){if(p.classList&&p.classList.contains('sh-placeholder')){inSpan=true;break;}p=p.parentNode;}}if(!inSpan&&parts.length)return parts;}return null;}function wrapParts(parts){for(var i=parts.length-1;i>=0;i--){var t=parts[i].node,txt=t.nodeValue,a=parts[i].a,b=parts[i].b;var span=document.createElement('span');span.className='sh-placeholder';span.textContent=txt.slice(a,b);var f=document.createDocumentFragment();if(a>0)f.appendChild(document.createTextNode(txt.slice(0,a)));f.appendChild(span);if(b<txt.length)f.appendChild(document.createTextNode(txt.slice(b)));t.parentNode.replaceChild(f,t);}}function run(){var st=document.createElement('style');st.textContent=CSS;document.head.appendChild(st);document.querySelectorAll('pre,code').forEach(function(el){var guard=0,parts;while((parts=firstMatch(el))&&guard++<500){wrapParts(parts);}});}if(document.readyState==='loading'){document.addEventListener('DOMContentLoaded',run);}else{run();}})();</script>
