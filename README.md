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


![1](https://github.com/user-attachments/assets/873b3a55-166b-463e-aa15-1b2cdaae3e8e)
![2](https://github.com/user-attachments/assets/a50310c2-14e6-470b-98d4-8d6d386f6b0d)
![3](https://github.com/user-attachments/assets/27181437-8189-46f7-be20-d76499e209e9)
![4](https://github.com/user-attachments/assets/e1077b09-9368-4ccb-a232-95c5e7571985)
![5](https://github.com/user-attachments/assets/a57decff-0bf1-4153-b385-823e0d7eae76)
![6](https://github.com/user-attachments/assets/02d9784d-85ff-44b1-8652-2c2bc1cc2393)
![7](https://github.com/user-attachments/assets/6af22648-5537-46d6-aae0-6bf1f711809c)
![8](https://github.com/user-attachments/assets/1a517480-d29a-4207-b3a5-5c084a2d6925)
![9](https://github.com/user-attachments/assets/5a62c6f2-ecf1-4812-8e36-77944cc7cf8b)
![10](https://github.com/user-attachments/assets/ea7836ce-33f0-4825-9d2b-3b6910eeb1f2)
![11](https://github.com/user-attachments/assets/292fef12-0533-4724-9fda-4952ffdbb280)


Open the README.md file to find detailed information, terminologies, and variables related to the floorplan, synthesis, and other stages. This file outlines the parameters and their default values, which can be adjusted later to meet specific design requirements. For instance, the floorplan stage includes parameters such as core utilization, aspect ratio, core margin, and input/output horizontal and vertical metal layers. Default values for these parameters can be found in the corresponding TCL file, such as floorplan.tcl for the floorplan stage.




**Running the run_floorplan Command**
**1.	Generate DEF File:**
-	Execute the run_floorplan command.
- This generates a DEF (Design Exchange Format) file containing details about the rows, their coordinates, orientation, and location.
- The file starts with the die area, showing the die coordinates.
o	Units for measurements and coordinates are specified (e.g., 1 micron = 1000 database units).
**2.	Viewing the Layout:**
-	To view the layout after floorplanning, use the magic -T command in the terminal.
-	Provide the paths to the technology file, PDKs, technology LEF, and DEF files.
**3.	Opening the Design in Magic:**
-	Upon opening the design in Magic, you'll see a box shape corresponding to the defined aspect ratio (1:1 aspect ratio results in a square shape).
-	Pins are placed equidistantly across the entire die area.
-	Macros or IPs (intellectual properties) are visible at this stage, but standard cells within the die are not visible yet. They will become visible after completing the placement stage.
-	Note: Standard cells might appear in the bottom left corner of the Magic window, outside the cell area.
**4.	Inspecting Macros:**
-	You can inspect the different macro cells placed at this stage by zooming in on the design.
-	Select a cell in the design and type what in the tkcon (Tcl console) window to get information about the selected cell.



