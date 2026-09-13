# Running Jupyter-lab on Anaconda 
```
conda --version
conda env list
```
### Create your Environment (Never work in base)
```
conda create --name <myenvironmentname>   => conda create --name myenv
conda create --name <myenvironmentname> python=<specific python version>   => conda create --name myenv python=3.9
```
### Activate Your Environment
```
conda env list
conda activate myenv
conda list  # To check Installed Packagaes in this environment
conda install jupyterlab pandas dask hvplot #install required python packagaes in your conda environment
conda install -c conda-forge condastats  #To install package like "condastats" from channel conda-forge package repository
```
### Run Jupyter Lab
```
jupyter-lab
```
- If Getting error like `[E 2026-09-13 20:23:36.115 ServerApp] Failed to write server-info to C:\Users\username\AppData\Roaming\jupyter\runtime\jpserver-19280.json: PermissionError(13, 'Permission denied')` 
- Fix :
  1. **Open File Explorer** and paste this path into the address bar: 
   `C:\Users\pande\AppData\Roaming\jupyter`
  2. **Click on the `runtime` folder**. If it doesn't exist, create it. If Windows prompts you that you don't currently have access, click **Continue** to permanently grant your user account permissions.
  3. If access is still denied, **right-click the `runtime` folder**, select **Properties**, and go to the **Security** tab.
  4. Click **Edit**, select your user account (or *Administrators*), check **Full control**, and click **OK** to apply the changes.


### Deactivate Your Environment
```
conda deactivate
```
