# Installing Mamba

[Mamba](https://mamba.readthedocs.io/) is a fast package and environment manager compatible with Conda.

On the cluster, install it in your personal storage directory:

```text
/storage/<your-username>/
```

Do **not** install it into the system directories.

## 1. Go to your storage directory

```bash
cd /storage/<your-username>
```

You can usually replace `<your-username>` with `$USER`:

```bash
cd /storage/$USER
```

## 2. Download Miniforge

Miniforge includes both **Conda** and **Mamba**.

```bash
wget -O Miniforge3.sh \
  "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh"
```

## 3. Install it

Install Miniforge into your storage directory:

```bash
bash Miniforge3.sh -b -p /storage/$USER/miniforge3
```

The `-b` option performs the installation without interactive prompts.

You can now remove the installer:

```bash
rm Miniforge3.sh
```

## 4. Enable Mamba

Load Conda and Mamba:

```bash
source /storage/$USER/miniforge3/etc/profile.d/conda.sh
source /storage/$USER/miniforge3/etc/profile.d/mamba.sh
```

To make them available automatically whenever you log in, add these lines to `~/.bashrc`:

```bash
echo 'source /storage/$USER/miniforge3/etc/profile.d/conda.sh' >> ~/.bashrc
echo 'source /storage/$USER/miniforge3/etc/profile.d/mamba.sh' >> ~/.bashrc
```

Reload your shell:

```bash
source ~/.bashrc
```

Check that Mamba works:

```bash
mamba --version
```

