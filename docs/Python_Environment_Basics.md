# Python Environment Basics

## 1. Check Python Version

To check the installed Python version:

```bash
python --version
```

You can also use:

```bash
python3 --version
```

---

## 2. Create a Project Directory

Create a new directory for your Python project:

```bash
mkdir my_project
cd my_project
```

---

## 3. Create a Virtual Environment

Create a Python virtual environment inside the project:

```bash
python -m venv .venv
```

Here, `.venv` is the name of the virtual environment.

The project structure will look like:

```text
my_project/
└── .venv/
```

---

## 4. Check the Project Directory

On Windows, use:

```cmd
dir
```

---

## 5. Activate the Virtual Environment

For Windows Command Prompt:

```cmd
.venv\Scripts\activate.bat
```

After activation, you should see something similar to:

```text
(.venv) C:\path\to\my_project>
```

This means the virtual environment is active.

### Windows PowerShell

If you are using PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

---

## 6. Install Python Packages

Once the virtual environment is activated, install the required packages:

```bash
pip install numpy pandas jupyter
```

This installs:

* `numpy` — Numerical and scientific computing
* `pandas` — Data manipulation and analysis
* `jupyter` — Interactive notebooks

---

## 7. Open the Project in Visual Studio Code

To open the current project directory in Visual Studio Code:

```bash
code .
```

VS Code should open the `my_project` directory.

Make sure VS Code is using the Python interpreter from your virtual environment:

```text
.venv
```

---

# Python Dependencies

A Python project may require multiple packages. It is a good practice to maintain a `requirements.txt` file containing the installed dependencies.

## 8. Create `requirements.txt`

With the virtual environment activated, run:

```bash
python -m pip freeze > requirements.txt
```

This creates a file named:

```text
requirements.txt
```

For example:

```text
numpy==2.x.x
pandas==2.x.x
jupyter==...
```

The exact versions will depend on what is installed in your environment.

---

## 9. Install Dependencies from `requirements.txt`

When setting up the project on another machine or creating a new environment, install all dependencies using:

```bash
python -m pip install -r requirements.txt
```

This reads the `requirements.txt` file and installs the specified packages.

---

# Complete Workflow

A typical workflow for creating a new Python project is:

```bash
mkdir my_project
cd my_project

python -m venv .venv

.venv\Scripts\activate.bat

python -m pip install numpy pandas jupyter

python -m pip freeze > requirements.txt

code .
```

## Project Structure

After completing the setup, the project may look like:

```text
my_project/
│
├── .venv/
│
├── requirements.txt
│
└── ...
```

## Quick Reference

| Task                       | Command                                      |
| -------------------------- | -------------------------------------------- |
| Check Python version       | `python --version`                           |
| Create project directory   | `mkdir my_project`                           |
| Enter project directory    | `cd my_project`                              |
| Create virtual environment | `python -m venv .venv`                       |
| Activate on Windows CMD    | `.venv\Scripts\activate.bat`                 |
| Activate on PowerShell     | `.venv\Scripts\Activate.ps1`                 |
| Install packages           | `python -m pip install numpy pandas jupyter` |
| Create dependency file     | `python -m pip freeze > requirements.txt`    |
| Install dependencies       | `python -m pip install -r requirements.txt`  |
| Open project in VS Code    | `code .`                                     |

---
