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




# Running the run_floorplan Command

**1.	Generate DEF File:**

-	Execute the run_floorplan command.
- This generates a DEF (Design Exchange Format) file containing details about the rows, their coordinates, orientation, and location.
- The file starts with the die area, showing the die coordinates.
-	Units for measurements and coordinates are specified (e.g., 1 micron = 1000 database units).
  
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

![1](https://github.com/user-attachments/assets/a07557fe-befb-479f-bbc1-b57926f5ebd6)
![2](https://github.com/user-attachments/assets/765f022a-d352-4368-adcf-b51cd9a80f92)
![3](https://github.com/user-attachments/assets/91272df5-6d39-40d8-bd5b-248dcec0d455)
![4](https://github.com/user-attachments/assets/e6d7106a-2153-4c3a-b797-8120e371e04b)
![5](https://github.com/user-attachments/assets/7105d0e0-ea15-468f-b3f1-bc3f02e12e10)
![6](https://github.com/user-attachments/assets/9c5ee259-f4dc-4998-923b-273b40a472ed)
![7](https://github.com/user-attachments/assets/2ee10941-cd28-4651-9da2-53a1e17ea342)
![8](https://github.com/user-attachments/assets/436c7609-fa58-4dde-9f04-e6d554c87de5)
![9](https://github.com/user-attachments/assets/ae678862-7855-46f2-95da-cd709f0a369d)
![10](https://github.com/user-attachments/assets/0b65949f-b7aa-4cd6-ae7d-fa4867d31bca)
![11](https://github.com/user-attachments/assets/0021d9db-3016-4d36-b04e-6601c057ab25)


# Proceeding to the Placement Stage
**1.	Run Placement Command:**
   
-	After completing the floorplan stage, proceed to the placement stage where standard cells are placed.
-	Execute the run_placement command in the Openlane terminal.

**2.	Generate Placement DEF File:**
   
- This command generates a placement DEF file located under the results directory.
-	To visualize the changes in the floorplan design after placement, use the Magic tool again with the updated DEF file.
  
**3.	Viewing the Design after Placement:**
   
-	Use the same magic -T command as before, but now point to the placement DEF file.
magic -T <tech_file> -pdk <pdk_path> -lef <lef_file> -def <new_floorplan_def_file>
-	The design will now show standard cells placed inside the core area along with the macros.
  
**4.	Handling Overlaps and Legalization:**
   
-	Initially, you may see standard cells and macros overlapping each other. This is resolved during the legalization step.
-	Placement is done in three steps:
-	Global Placement: Provides an initial placement of cells.
-	Detailed Placement: Refines the placement to reduce overlap and improve the design's quality.
- Legalization: Ensures that all cells are placed without overlaps and meet design rules.
   
**5.	Components Placed:**
-	At this stage, tap cells, decap cells, macros, and standard cells are all placed within the design.

  ![1](https://github.com/user-attachments/assets/5adaf539-4feb-4dd8-a098-0d0bf3d0bede)
![2](https://github.com/user-attachments/assets/d87463b7-b196-476b-aa12-8678a9433533)
![3](https://github.com/user-attachments/assets/dbd19f15-df9e-4a41-a14a-9c960425f9e8)



# Adjusting Pin Placement with FP_IO_MODE
**1.	Understanding FP_IO_MODE:**
-	The FP_IO_MODE parameter is used to define the placement of pins.
-	Previously, setting this parameter placed the pins equidistant from each other around the design.
  
  **2.	Modifying Pin Placement:**
-	To concentrate the pins in a specific portion of the design, set FP_IO_MODE to 2.
-	This adjustment changes the pin distribution as shown in the image below.
  
**3.	Re-run the Floorplan:**
-	After modifying FP_IO_MODE, re-run the floorplan stage to apply the changes.
-	This involves executing the floorplan command again, which regenerates the DEF file with the new pin placements.
  
**4.	Steps to Apply Changes:**
-	Update the FP_IO_MODE setting in the appropriate configuration file or directly in the Openlane environment.

![1](https://github.com/user-attachments/assets/a20de4b1-cc0d-4a85-a4fc-2db386dd0350)
![2](https://github.com/user-attachments/assets/3a542192-7a62-4b7d-8f1a-8c90ccb76adb)

# Cloning and Setting Up the Inverter Design in Openlane
**1.	Clone the Repository:**
-	Clone the repository containing the MAG files for the inverter and NMOS/PMOS for Sky130: git clone <repository_url>
-	This will add a new directory named vsdstdcelldesign to your Openlane directory.
**2.	Open the Inverter Design in Magic:**
-	Open the Magic tool with the cloned inverter MAG file:
magic -T <tech_file> <path_to_inverter.mag>
-	This will display the layout of the inverter.
**3.	Viewing the Layout:**
-	Different layers are shown with different colors:
	Metals are defined with blue.
	Polysilicon is shown in red.
	The right side displays a palette showing each layer:
	Metal 1: Purple
	Metal 2: Pink cross
**4.	Labelling Layers for Clarity:**
-	Define text labels for each layer to better understand the functionality of the circuit:
 	Go to the cell, select the text option, and define the text label.
-	Define each port (input, output, or inout) to specify their functionality:
-	Use the tkcon window to write commands to define them as signals and ports.
**5.	Extracting the Design:**
-	Extract the file in the vsdstdcelldesign directory as a .ext file:
-	Generate the .spice file: ext2spice
**6.	Modifying the Spice File:**
-	Open the generated .spice file.
-	Modify the file to match the Sky130 definitions for NMOS and PMOS as per the cloned pshort and nshort libraries.
-	Save the modified .spice file.
**7.	Running Simulation with Ngspice:**
-	Run Ngspice to simulate the inverter:
ngspice <path_to_inverter.spice>
-	Plot the output vs. input with respect to time to observe the transient waveforms.
**8.	Improving Simulation Results:**
-	If there are spikes in the output, increase the load capacitor value to reduce the spikes.
-	Re-run the simulation to check the effects of the load capacitor.
**9.	Calculating Performance Metrics:**
-	Calculate the rise and fall transition times.
-	Determine the cell delays.
By following these steps, we can clone, set up, simulate, and analyze the inverter design in the Openlane environment using the Magic and Ngspice tools. This process helps in understanding the layout, functionality, and performance of the circuit.







