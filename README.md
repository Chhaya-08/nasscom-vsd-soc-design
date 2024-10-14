# Familiarity with Different Directories and Tools

## Directory Exploration
- **Explore Directories:**
  - Familiarize yourself with various directories and their contents.
  - Explore each folder to understand the information they contain.

# Openlane: Automating RTL to GDS Flow

**1. Interactive Session**

   - Open an interactive session with Openlane.
   - Input all necessary packages to interact with Openlane effectively.

**2. Design Selection**

   - Openlane contains multiple design folders. For this assignment, we will work with the `picorv32a` design.

**3. File System Preparation**

   - Prepare the file system before running synthesis in Openlane.
   - Set up the design environment to ensure all necessary files are in the desired locations.
   - Merge the technology LEF (tech LEF) and the cell-level LEF (cell LEF).

**4. Preparation Stage Completion**

   - Once the preparation is complete, a `runs` directory is created within the `picorv32a` design directory. This directory is named with the current date to reflect when the LEF files were merged.

**Running Synthesis in Openlane**

 **Run Synthesis**
  - Execute the `run_synthesis` command in Openlane.
  - After completing the synthesis, Openlane provides detailed information about the cells and the number of each cell type used, including the results of the ABC run.

  **Synthesis Results**
- The total chip area for the module = 147712.918400
- The flop ratio = (Number of DFF) / (Total number of cells)
    = 1613 / 14876
    = 0.1084296854
    = 10.84296854%

After synthesis, we get the synthesized netlist (`.v`) in our synthesis results folder, which was initially empty.

![1](https://github.com/user-attachments/assets/26c329da-de10-43a7-a347-d065a7da28fc)
![2](https://github.com/user-attachments/assets/6f3c31e0-4b42-4e5f-8f23-8cbf8dbfbf5e)
![3](https://github.com/user-attachments/assets/99ba9075-41d2-4e9f-87a3-d4ee857e5911)
![4](https://github.com/user-attachments/assets/45de6cd7-7e60-4ec2-bc5a-69d76819be3d)
![5](https://github.com/user-attachments/assets/e68593f2-db1
![6](https://github.com/user-attachments/assets/c418e416-9f0b-4d4b-be50-f6f567adc135)

![7](https://github.com/user-attachments/assets/28d8d3cf-5850-487a-9381-c2c2f7287c7e)
![8](https://github.com/user-attachments/assets/dab3d511-0c9a-49a3-8360-be138a301250)
![9](https://github.com/user-attachments/assets/9941352b-414c-4d3f-b9b6-2b331ddbcd0a)

![10](https://github.com/user-attachments/assets/4e559346-5845-4460-954a-34e8bde69589)
![11](https://github.com/user-attachments/assets/14880d93-447e-4c48-b21a-7ba498fa0557)



