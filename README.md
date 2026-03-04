# STAR-CCM+ Batch Automation Tool

## Overview

This project automates batch CFD simulations in STAR-CCM+ using Python.

It performs:
- Automated case creation from template
- Macro modification using parameter placeholders
- Batch execution via command line
- Automatic extraction of pressure difference (ΔP)
- Summary report generation

The tool is designed for parameter sweep studies and CFD workflow automation.

---

## Motivation

Manual execution of multiple STAR-CCM+ cases is time-consuming and error-prone.

This tool demonstrates:
- Engineering automation mindset
- Integration between Python and STAR-CCM+
- Batch simulation orchestration
- Result post-processing

---

## Project Structure
main.py → Entry point (orchestrates batch run)
star_runner.py → Simulation execution logic
logger_config.py → Centralized logging setup
batch_config.json → Parameter definitions
sim.java → STAR macro template


---

## How It Works

1. Reads simulation parameters from `batch_config.json`
2. Copies template `.sim` file for each case
3. Modifies Java macro placeholders:
   - {{MESH_SIZE}}
   - {{CASE_NAME}}
4. Executes STAR-CCM+ in batch mode
5. Extracts ΔP from exported CSV
6. Writes summary report

---

## Example Configuration

```json
{
  "star_executable": "starccm+",
  "template_sim": "bend_tube.sim",
  "java_macro": "sim.java",
  "simulations": [
    {
      "case_name": "baseline",
      "mesh_size": 200
    },
    {
      "case_name": "refined",
      "mesh_size": 150
    }
  ]
}
