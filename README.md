# **Virtual Machines — Setup Guide for Ubuntu, R, RStudio, and Biostrings**

**Author:** phD *Caterina Giachino*
**Contact:** **[caterina.giachino@unina.it](mailto:caterina.giachino@unina.it)**

A step-by-step guide to help beginners learn how to work with Virtual Machines, install Ubuntu Linux, and set up a bioinformatics environment with R, RStudio, and the Biostrings package.

---

## **📘 Table of Contents**

1. [What is a Virtual Machine?](#what-is-a-virtual-machine)
2. [Creating the Ubuntu Virtual Machine](#creating-the-ubuntu-virtual-machine)
3. [Installing R and RStudio](#installing-r-and-rstudio)
4. [Installing Biostrings](#installing-biostrings)
5. [Your Learning Environment](#your-learning-environment)

---

# **1. What is a Virtual Machine?**

A **Virtual Machine (VM)** is a software-based computer that runs inside your actual computer.

A VM allows you to:

* Create a safe, isolated environment for experiments
* Install operating systems (e.g., Ubuntu Linux) without modifying your real machine
* Practice programming and bioinformatics
* Reset or delete the environment at any time

In this guide, we will use **VMware Workstation 17 Player** to create a VM running **Ubuntu 22.04**. Then we will install **R**, **RStudio**, and the **Biostrings** package for sequence analysis.

---

# **2. Creating the Ubuntu Virtual Machine**

## **Step 1 — Download Ubuntu**

Download the ISO image from:
🔗 [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)

Use: **ubuntu-22.04.1-desktop-amd64.iso**

---

## **Step 2 — Create the VM in VMware Player**

1. Open **VMware Workstation 17 Player**
2. Click **Create a New Virtual Machine**
3. Select the Ubuntu ISO
4. Continue with the default settings until resource allocation

---

## **Step 3 — Allocate System Resources**

Suggested configuration:

* **RAM:** 4–8 GB
* **Processors:** 4 cores
* **Keyboard layout:** Italian

---

## **Step 4 — Ubuntu Installation Settings**

Inside the installer, select:

* **Normal installation**
* **Install third-party software (graphics, Wi-Fi, etc.)**
* Disk option → **Erase disk and install Ubuntu**
* Virtual disk size → **≥ 35 GB**

---

## **Step 5 — First Boot Settings**

After installation:

* Skip the online account
* Skip feedback
* Skip "Ubuntu Pro"
* Install all system updates
* Switch to **Full Screen** in VMware Player

Your Ubuntu system is now ready! 🎉

---

# **3. Installing R and RStudio**

Open the **Terminal**:
`CTRL + ALT + T`

---

## **Step 1 — Add the CRAN Repository Key**

```bash
wget -qO- https://cloud.r-project.org/bin/linux/ubuntu/marutter_pubkey.asc | \
sudo tee /etc/apt/trusted.gpg.d/cran_ubuntu_key.asc
```

---

## **Step 2 — Install version tools**

```bash
sudo apt install lsb-core
sudo apt-get install lsb-release
lsb_release -v
```

---

## **Step 3 — Add R repository (Ubuntu 22.04 – Jammy)**

```bash
sudo add-apt-repository "deb https://cloud.r-project.org/bin/linux/ubuntu jammy-cran40/"
```

---

## **Step 4 — Install R**

```bash
sudo apt update
sudo apt install --no-install-recommends r-base
```

---

## **Optional — Add additional precompiled R packages**

```bash
sudo add-apt-repository ppa:c2d4u.team/c2d4u4.0+
sudo apt update
```

---

## **Step 5 — Install RStudio Desktop**

Download the `.deb` file:
🔗 [https://posit.co/download/rstudio-desktop/](https://posit.co/download/rstudio-desktop/)

Install it:

```bash
sudo apt install ./rstudio-*.deb
```

---

# **4. Installing Biostrings**

We install only **Biostrings**.

---

## **Option A — Install via Ubuntu repositories**

```bash
sudo apt-get update
sudo apt-get install r-bioc-biostrings
```

---

## **Option B — Install directly inside R (recommended)**

Start R:

```bash
if (!require("BiocManager")) install.packages("BiocManager")
BiocManager::install("Biostrings")
```

Only the required dependencies will be installed. ✔

---

# **5. Your Learning Environment**

You now have a fully functional virtual environment for:

* Working safely with Linux
* Practicing R and RStudio
* Learning sequence manipulation
* Using **Biostrings** for DNA/RNA/protein analysis


---

When I first entered the world of Bioinformatics, I was not yet confident with coding. I was afraid that a wrong command could break my computer — a computer I had bought with my own savings. Using a Virtual Machine completely changed my experience:
it allowed me to experiment freely, make mistakes, learn, and explore without fear of damaging anything. I hope this setup can help people who, like me, felt overwhelmed at the beginning.


**Keep learning, be curious, and don’t be afraid to try things out.**
This VM is your **protected, dedicated workspace for learning bioinformatics**. 

**Have fun, everyone!** 🚀

