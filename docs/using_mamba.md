# Using Mamba

Mamba manages isolated software environments. On a cluster, use a separate environment for each project rather than installing packages into `base`.

## Create an environment

Create an empty environment:

```bash
mamba create -n myproject
```

Create an environment with R:

```bash
mamba create -n myproject r-base
```

Or install a specific R version:

```bash
mamba create -n myproject r-base=4.4
```

To see which R versions are available:

```bash
mamba search r-base
```

You can install several packages when creating the environment:

```bash
mamba create -n myproject r-base=4.4 r-tidyverse r-sf
```

> Packages are installed from the configured Conda channels. With Miniforge, `conda-forge` is normally the default.

---

## Activate and deactivate environments

Activate an environment:

```bash
mamba activate myproject
```

Your prompt will usually change to show the active environment:

```text
(myproject) username@cluster:~$
```

Deactivate it:

```bash
mamba deactivate
```

List your environments:

```bash
mamba env list
```

---

## Install packages

Activate the environment first:

```bash
mamba activate myproject
```

Then install packages:

```bash
mamba install r-data.table
```

Install several packages at once:

```bash
mamba install r-tidyverse r-sf r-terra
```

Most R packages on `conda-forge` use the prefix `r-`:

| R package | Mamba package |
|---|---|
| `tidyverse` | `r-tidyverse` |
| `sf` | `r-sf` |
| `terra` | `r-terra` |
| `data.table` | `r-data.table` |

Search for a package:

```bash
mamba search r-raster
```

You can also install Python packages in the same way:

```bash
mamba install python=3.12 numpy pandas
```

---

## Install packages from inside R

If a package is not available through Mamba, activate the environment and start R:

```bash
mamba activate myproject
R
```

Then install it normally:

```r
install.packages("package_name")
```

Prefer Mamba packages when available, especially for packages with compiled system dependencies such as `sf`, `terra`, or `raster`.

---

## Update packages

Update a specific package:

```bash
mamba update r-sf
```

Update all packages in the active environment:

```bash
mamba update --all
```

---

## Remove packages or environments

Remove a package:

```bash
mamba remove r-sf
```

Remove an entire environment:

```bash
mamba env remove -n myproject
```

---

## Save an environment

Export the environment to a YAML file:

```bash
mamba env export > environment.yml
```

Recreate it later with:

```bash
mamba env create -f environment.yml
```

A simple `environment.yml` can also be written manually:

```yaml
name: myproject

channels:
  - conda-forge

dependencies:
  - r-base=4.4
  - r-tidyverse
  - r-sf
  - r-terra
```

Then create the environment with:

```bash
mamba env create -f environment.yml
```

---

## Typical workflow

```bash
# Create the environment once
mamba create -n myproject r-base=4.4 r-tidyverse r-sf

# Activate it whenever you work on the project
mamba activate myproject

# Run R
R

# Leave the environment when finished
mamba deactivate
```
