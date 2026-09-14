# Running Jupyter-lab on Anaconda 

### About conda
`conda` is a :
- `package manager` which *download-install-update* the `packages and their dependecies`.
	-  a `packagae` is a compressed file containing `modules and libraries ( in lib/) , binaries ( in bin/) and metadata ( in info/)` 
- `environment manager` so different projects can have their respective packages.
	- `environment` is a self-contained directory in our computer containing programs, packages, libraries and scripts.
	- it creates-saves-loads-switches between different environment on your local computer.
- can `cache packagaes` so they are not downloaded again
- Hence `conda` solves both `package and environment management` problems and target `multiple programming languages`.
- facilitate `portability` and `reproducibility` 
```
conda --version
conda env list
```
### Create your Environment (Never work in base)
```
conda create --name <myenvironmentname>   => conda create --name myenv
conda create --name <myenvironmentname> <Packagae(s)>  => conda create --name myenv python=3.9 jupyterlab pandas
conda create --name <myenvironmentname> python=<specific python version>   => conda create --name myenv python=3.9
```


### Activate Your Environment
```
conda env list
conda activate myenv
conda list  # To check Installed Packagaes in this environment
conda info # To see information about environment
conda install <Packagae(s)> => conda install jupyterlab pandas dask hvplot #install required python packagaes in your conda environment

conda search -c conda-forge condastats  #To search a package like "condastats" from channel conda-forge - a coomunity package repository
conda install -c conda-forge condastats  #To install package like "condastats" from channel conda-forge - a coomunity package repository
```
- `channels` are URLs to repositories containing a collection of packages. Example : https://repo.anaconda.com/pkgs/main
	- channel can also be setup  as a location on your computer, share disk or network.

- create an environment in a specific directory rather than --name as it allows to associate environments to projects :
```
conda create --prefix <PATH> <Packagae(s)>
conda activate <PATH>
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

### Delete a Package or an Environment
```
conda remove -n <Environment_Name> <Packagae(s)> # to remove specific packagae(s)
conda remove -n <Environment_Name> --all # to remove complete environment
```


### Setup an Environment with `environment file`:
- `environment file` is a YAML (Yet Another Markup Language) file which has `name` of the environment, `channels` and `dependencies` deatils
  - (1) Create and environment YAML file :
```text
name: myenvironmentname
channels:
 - conda-forge
dependencies:
 - pandas==1.5.2 #install specific version
 - seaborn       #install latest version
 - python>=3.9   #install specific or latest version
 - pip
 - pip:
   - Flask-Testing  #pip install packages from Python central repository called PYTHON PACKAGE INDEX (PyPI)
variables:
 - VAR1: valueA
 - VAR2: valueB
```

  - (2) creare environment from a file by running below command :
```
conda  env create --file <ENVIRONMENT_FILE>
```

### How to export an Environment to a file:
```
conda env export > myenvironmentname.yml                  #write only packagaes name with version details
conda env export --from-history > myenvironmentname.yml   #write only packagaes name without version details
```
---
