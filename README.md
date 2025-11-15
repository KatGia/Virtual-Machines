# **Virtual Machines — Using Ubuntu to Align Generic Sequences and Classify Them Into Phylogenetic Groups**

**Author:** phD *Caterina Giachino*
**Contact:** **[caterina.giachino@unina.it](mailto:caterina.giachino@unina.it)**

This guide explains how to install the necessary tools on Ubuntu, perform sequence alignments, and use a phylogenetic assignment tool to classify generic nucleotide sequences into lineage groups.

---

## **1. Install Miniconda**

Download and install Miniconda:

```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
```

Follow the on-screen installation instructions.

---

## **2. Create and Activate a Conda Environment**

```bash
conda create -n seq_env python=3.8
conda activate seq_env
```

Update Conda to ensure all commands work correctly:

```bash
conda update conda
```

---

## **3. Install the Phylogenetic Assignment Tool**

```bash
conda install -c conda-forge pangolin
```

Verify the installation:

```bash
pangolin --version
```

---

## **4. Install Required Alignment Tools**

### Install `zlib` dependencies (needed for alignment tools such as Minimap2):

```bash
sudo apt install zlib1g
sudo apt install zlib1g-dev
```

### Install Minimap2

```bash
sudo apt install minimap2
```

Verify that it is available:

```bash
minimap2 --version
```

If you prefer to compile Minimap2 manually, run:

```bash
make
```

inside the Minimap2 folder after installing `zlib`.

---

## **5. Install FASTA Utilities (gofasta)**

If the classification tool reports missing dependencies such as `gofasta`, install it with:

```bash
conda install -c bioconda gofasta
```

Check installation:

```bash
gofasta --help
```

---

## **6. Running Sequence Alignment**

To align your set of sequences against a reference:

```bash
minimap2 -a -x asm20 input_sequences.fasta reference.fasta -o output.sam
```

Where:

* `input_sequences.fasta` = your sequences
* `reference.fasta` = reference sequence
* `output.sam` = alignment result

---

## **7. Running Phylogenetic Group Assignment**

Once all dependencies are correctly installed, you can classify your sequences:

```bash
pangolin input_sequences.fasta -o output.csv
```

The file `output.csv` will contain:

* the assigned lineage/group
* metadata from the classification model

---

## **8. Troubleshooting**

### **Error: zlib missing**

Install:

```bash
sudo apt install zlib1g zlib1g-dev
```

---

### **Error: minimap2 not found**

```bash
sudo apt install minimap2
```

---

### **Error: gofasta not found**

```bash
conda install -c bioconda gofasta
```

---

### **Output directory message example**

If the tool prints something like:

```
Output file written to: /path/output.csv / lineage_report.csv
```

It means the classification finished successfully.

---

**Have fun, everyone!** 🚀
