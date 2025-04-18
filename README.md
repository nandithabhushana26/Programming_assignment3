# Pantheon CNPA3 Reproducibility

- **Code & Scripts:**  
- `scripts/run_experiments.sh` – launches each TCP scheme under Mahimahi  
- `scripts/generate_plots.py` – parses logs & produces Matplotlib figures  
- **Traces:** custom bandwidth-delay profiles in `traces/`  
- **README.md** – this file, with step‑by‑step reproduction instructions

## Prerequisites
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y git python2.7 python2.7-dev build-essential
sudo apt install -y mahimahi mahimahi-tools

##Setup
git clone https://github.com/your-username/pantheon-cnpa3.git
cd pantheon-cnpa3
git submodule update --init --recursive


## Running Experiments

# Usage: run_experiments.sh <trace-file> <delay-ms>
bash scripts/run_experiments.sh traces/40mbps.trace 5    
bash scripts/run_experiments.sh traces/5mbps.trace 80    

results/
├── scenario1-40mbps-5ms/{cubic,bbr,vegas}/
└── scenario2-5mbps-80ms/{cubic,bbr,vegas}/

##Generating Plots
python3 scripts/generate_plots.py --input results/ --output figures/

##Directory Structure
pantheon-cnpa3/
├── README.md
├── scripts/
│   ├── run_experiments.sh
│   └── generate_plots.py
├── traces/
│   ├── 40mbps.trace
│   └── 5mbps.trace
├── results/
└── figures/
