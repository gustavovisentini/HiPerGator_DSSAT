# HiPerGator_DSSAT
Configuration of DSSAT on HiPerGator

# DSSAT-CSM-OS Installation on HiPerGator

This guide provides a step-by-step process to install **DSSAT-CSM-OS** and set up its data repository on **HiPerGator**.

## 1️⃣ Access HiPerGator
Log in via SSH:
```bash
ssh your_username@hpg.rc.ufl.edu
```

## 2️⃣ Load Required Modules
```bash
module load gcc
module load cmake
```


## 3️⃣ Clone and Compile DSSAT

Create for example a folder projects/your_source_here
```bash
git clone https://github.com/DSSAT/dssat-csm-os.git
cd dssat-csm-os
mkdir build && cd build
cmake ..
make
```

## 4️⃣ Set Up DSSAT Data Repository
```bash
cd ~
git clone https://github.com/DSSAT/dssat-csm-data.git
mkdir -p ~/DSSAT_DATA
mv dssat-csm-data/* ~/DSSAT_DATA
export DSSAT_DATA=~/DSSAT_DATA
echo "export DSSAT_DATA=~/DSSAT_DATA" >> ~/.bashrc
source ~/.bashrc
```

## 5️⃣ Run a Test Simulation
```bash
cd ~/dssat-csm-os/build/bin
./dscsm048 B ~/DSSAT_DATA/Experiments/MZCER047.MZX
```

## 📝 Notes
- Ensure you have the necessary permissions to execute the DSSAT binaries.
- Modify the experiment files as needed before running simulations.
- Check output logs (`*.OUT` and `WARNING.OUT`) for any errors or warnings.

For further details, refer to the [DSSAT Documentation](https://dssat.net/).
