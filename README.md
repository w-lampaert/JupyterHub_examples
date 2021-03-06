# JupyterHub examples
Notebooks, databases and ppt to run examples. The recorded lunchbox session can be found [here](https://kuleuven.mediaspace.kaltura.com/media/JupyterHub-LunchBox-2021-10-19/1_lxer6oid)

## Python notebook
To be able to run the Python notebook, you need to install a correct conda environment yourself. In this case an environment called p39env:

`conda create -n p39env python=3.9 tensorflow-gpu ipykernel`

Add this kernel to your VSC_HOME/.local folder:


```
source activate p39env
python -m ipykernel install  --prefix=${VSC_HOME}/.local/ --name 'p39env'
```

Now, the kernel should appear in your kernel list and work fine. The matplotlib package is not yet installed, but will be installed in the notebook.

In the notebook, we use a locally stored pickle dataset to show that we can read from VSC_DATA. As it is too big to save ont GitHub, you can download and save it as follows (in a Python interpreter):
```
import os
import pickle
import tensorflow as tf

os.chdir('jupyterHUB_examples')
os.mkdir('py_notebook_ex')

dt = tf.keras.datasets.mnist.load_data()
with open('mnist.pickle', 'wb') as f:
    pickle.dump(dt, f)
```
Now you should be able to run the notebook without any problems.


## R notebook

Similar as for the Python notebook, first install a R conda environment:

`conda create -n r41env -c conda-forge r-base r-ggplot2 r-factoextra jupyter_client r-irkernel`

Add the kernel to your VSC_HOME/.local folder:

```
source activate r41env
Rscript -e 'IRkernel::installspec(prefix="${VSC_HOME}/.local/", name="r41env", 	displayname="r41env")’
```
This kernel should be available in your kernel list now as well.

