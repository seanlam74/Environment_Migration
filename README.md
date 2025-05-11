# ✅ Migrating Conda Environments and Jupyter Kernels to a New Laptop

This guide helps you **export Conda environments** and **Jupyter kernels** from your **old laptop** and set them up on a **new laptop**, using **GitHub** to transfer the configuration files.

---

## 📦 Step 1: Export Conda Environments (Old Laptop)

### 1. List all your Conda environments:
```bash
conda env list
```

### 2. Export each environment to a `.yml` file:
Replace `myenv` with each environment name:
```bash
conda activate "myenv"
conda env export --no-builds > myenv.yml
```

### 3. Organize your exports:
```bash
mkdir conda_env_exports
mv *.yml conda_env_exports/
cd conda_env_exports
```

---

## 🚀 Step 2: Push to GitHub

### 1. Create a private GitHub repo (e.g., `conda-env-backup`)

### 2. Push your `.yml` files to GitHub:
```bash
git init
git remote add origin https://github.com/<yourusername>/conda-env-backup.git
git add .
git commit -m "Exported Conda environments"
git push -u origin main
```

---

## 💻 Step 3: Clone and Restore on New Laptop

### 1. Clone the repo:
```bash
git clone https://github.com/<yourusername>/conda-env-backup.git
cd conda-env-backup/conda_env_exports
```

### 2. Recreate each Conda environment:
```bash
conda env create -f myenv.yml
```

---

## 🧠 Step 4: Register Environments as Jupyter Kernels

After recreating the environments, make them available in Jupyter.

For each environment:

### 1. Activate it:
```bash
conda activate myenv
```

### 2. Register it with Jupyter:
```bash
python -m ipykernel install --user --name myenv --display-name "Python (myenv)"
```

- `--name` is the internal ID (no spaces)
- `--display-name` is what appears in the Jupyter UI

Repeat for each environment.

---

## 🧪 Step 5: Verify in Jupyter Notebook

Launch Jupyter Notebook:
```bash
jupyter notebook
```

Then in the menu:  
`Kernel > Change Kernel` → You should see:
- Python (myenv)
- Python (other-env)


## 📁 Summary

✅ Environments exported with `conda env export`  
✅ Transferred via GitHub  
✅ Recreated using `conda env create`  
✅ Jupyter kernels registered with `ipykernel`  

You’re ready to code again—just as you left it!
