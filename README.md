# Familiarity with Different Directories and Tools

## Directory Exploration
- **Explore Directories:**
  - Familiarize yourself with various directories and their contents.
  - Explore each folder to understand the information they contain.

# Openlane: Automating RTL to GDS Flow

1. Interactive Session

   - Open an interactive session with Openlane.
   - Input all necessary packages to interact with Openlane effectively.

2. Design Selection

   - Openlane contains multiple design folders. For this assignment, we will work with the `picorv32a` design.

3. File System Preparation

   - Prepare the file system before running synthesis in Openlane.
   - Set up the design environment to ensure all necessary files are in the desired locations.
   - Merge the technology LEF (tech LEF) and the cell-level LEF (cell LEF).

** 4. Preparation Stage Completion **

   - Once the preparation is complete, a `runs` directory is created within the `picorv32a` design directory. This directory is named with the current date to reflect when the LEF files were merged.

# Running Synthesis in Openlane

** Run Synthesis **
  - Execute the `run_synthesis` command in Openlane.
  - After completing the synthesis, Openlane provides detailed information about the cells and the number of each cell type used, including the results of the ABC run.

** Synthesis Results **
- The total number of cells in the design = 147712.918400
- The flop ratio = (number of DFF) / (total number of cells)
    = 1613 / 14876
    = 0.1084296854
    = 10.84296854%

After synthesis, we get the synthesized netlist (`.v`) in our synthesis results folder, which was initially empty.
