# EDA Tool Installation for Digital Design 🛠️

This task involved installing essential open-source Electronic Design Automation (EDA) tools on an Ubuntu system. These tools are fundamental for digital logic synthesis, simulation, and analysis.

---
## 1. System Requirements Check

Before beginning with the installation, it's crucial to ensure that the system meets the minimum requirements.
### Minimum System Specs:

- **RAM:** 6 GB
- **Storage:** 50 GB of free space
- **Operating System:** Ubuntu 20.04 or newer
- **CPU:** 4 cores

### Verify Your System

To verify system's specifications, we can run the following commands in terminal:

- **Check RAM size:**
```bash
    free -h
    ```

- **Check available storage capacity:**    
```bash
	df -h
```

- **Check Ubuntu version:**
```bash
    cat /etc/os-release | head -1
```

- **Check number of CPU cores:**    
```bash
    nproc
```

![[system_check.jpeg]]

---
## 2. Installation of Yosys (Synthesis Tool)

**Purpose:** **Yosys** is an open-source framework for Verilog RTL synthesis. It converts the high-level hardware description (Verilog code) into a gate-level netlist, which is a representation of the logic using standard cells.

**Installation commands:**
```bash
    # Update package lists
    sudo apt-get update
    
    # Clone the official Yosys repository
    git clone https://github.com/YosysHQ/yosys.git
    cd yosys
    
    # Install dependencies required for building Yosys
    sudo apt-get install build-essential clang bison flex \
     libreadline-dev gawk tcl-dev libffi-dev git \
     graphviz xdot pkg-config python3 libboost-system-dev \
     libboost-python-dev libboost-filesystem-dev zlib1g-dev 
    
    # Configure the build for GCC
    make config-gcc
    
    # Compile the source code 
    make
    
    # Install Yosys system-wide
    sudo make install
    ```

**Verify Installation:** Check if Yosys was installed correctly or not:
```bash
    yosys --version # Displays the installed version of Yosys
    yosys           # Launches the Yosys tool on command line
```

![[yosys.jpeg]]

___
## 3. Installation of Icarus Verilog (Simulator)

**Purpose:** **Icarus Verilog (iverilog)** is an open-source Verilog compiler and simulator. It compiles your Verilog code into an executable format and then simulates the behavior of your digital circuit to verify its functionality.

**Installation command:** 
```bash
    sudo apt-get install iverilog
```

**Verify Installation:** To confirm that `iverilog` is installed, check its version:
```bash
    iverilog -v
```

![[iverilog.jpeg]]

---
## 4. Installation of GTKWave (Waveform Viewer)

**Purpose:** **GTKWave** is a graphical waveform viewer used to analyze the results of a Verilog simulation. After running a simulation with `iverilog`, it generates a waveform file (typically with a `.vcd` extension), which you can open in GTKWave to visually inspect the signals and debug your design.

**Installation command:** 
```bash
    sudo apt install gtkwave
```

**Verify Installation:** Check the installed version to ensure the installation was successful.
```bash
    gtkwave --version
```

![[gtkwave.jpeg]]


We now have a basic open-source EDA toolchain set up for digital design projects! 🎉
