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
      - Metals are defined with blue.
	- Polysilicon is shown in red.
	- The right side displays a palette showing each layer:
	i) Metal 1: Purple
	ii) Metal 2: Pink cross

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



![1](https://github.com/user-attachments/assets/6be9f1c2-d3d3-4795-87a9-07d234900217)
![2](https://github.com/user-attachments/assets/8af95e8c-b22c-4fa2-937c-34f7cabbc622)
![3](https://github.com/user-attachments/assets/edea956a-7b91-4585-8b04-0282e159e3a8)
![4](https://github.com/user-attachments/assets/ed55b147-060b-48e5-8f6e-ac7c4967a745)
![5](https://github.com/user-attachments/assets/717cafb7-ba19-4a37-8e39-5ecacb950e17)
![6](https://github.com/user-attachments/assets/2d68c600-ba7b-4947-8c9d-8c843a47a441)
![7](https://github.com/user-attachments/assets/0846481b-acc7-4852-a1b8-ca9b95957d33)
![8](https://github.com/user-attachments/assets/e6015761-efda-4017-998f-a18ab61e4789)
![9](https://github.com/user-attachments/assets/cd760662-fcc6-46ff-ad85-03d42ea502d7)
![10](https://github.com/user-attachments/assets/639dbb02-fb16-4b3c-aa2e-d1c553201f46)


![11](https://github.com/user-attachments/assets/3fef6ea5-98a1-4f27-9b64-4ce541b9bc38)
![12](https://github.com/user-attachments/assets/0a7c7593-8a65-44d6-992b-8be79d3fdf43)
![13](https://github.com/user-attachments/assets/83d468b4-1feb-497b-a533-615f5d5e79b3)
![14](https://github.com/user-attachments/assets/611de6d8-fb69-47e8-9324-2fb7107a4b1d)
![15](https://github.com/user-attachments/assets/6e46abbb-1881-41ec-861b-2cf27763ee3e)
![16](https://github.com/user-attachments/assets/589779a9-e81f-43a8-86de-b1c15b685518)
![17](https://github.com/user-attachments/assets/a222fa39-3a14-4f29-8177-c5433dc7555e)
![18](https://github.com/user-attachments/assets/8b914cbd-8afa-43e1-ae80-b43002954ae3)
![19](https://github.com/user-attachments/assets/7c2d62c5-8819-4615-aff2-c0ff5f9b2a32)

Calculating the values by seeing the curve and values published at the terminal:

1)	**Rise transition delay:** 2.14022 – 2.24471 = -0.10383 ns
2)	**Fall transition delay :** 4.06621-4.10959 = -0.04338ns
3)	**Cell rise delay :** 2.17941 – 2.10529 = 0.07412 ns
4)	**Cell fall delay :**  4.08753 – 4.05011 = 0.03742 ns

# Standard Cell Integration and Optimization in Openlane
**1.	Understanding Design Rules:**
  -Ensure the width of cells is an odd multiple of the grid boxes.
  
**2. Standard Cell Characterization:**
   -Standard cell descriptions are located in library files at the extreme corners (slow, fast, typical).
   -Each library file defines the temperature conditions and multiple parameters for the cell under different conditions.

**3. Connecting Standard Cells to Openlane:**
     -Integrate the standard cell libraries with Openlane.
     - Invoke Openlane and rerun the synthesis stage to include the standard cells.
     
**4. Optimizing Timing:**
  -To correct TNS (Total Negative Slack), WNS (Worst Negative Slack), and slack:
i)	Adjust synthesis strategies.
ii)	Apply buffering.
iii)	Perform cell sizing.
iv)	Optimize driving cells.
v)	Rerun the synthesis stage after making these adjustments to observe the updated results.

**5. Proceeding with the Design Flow:**
    - After synthesis, proceed with the floorplan stage:
    - Continue with clock tree synthesis (CTS):
    - Check the process definitions and ensure all parameters are correctly set.
By following these steps, you can integrate standard cells, optimize timing parameters, and proceed through the design stages in Openlane, ensuring your design meets the required specifications.



![1](https://github.com/user-attachments/assets/5d2e0062-de71-429e-a8c3-917edf1bb68f)
![2](https://github.com/user-attachments/assets/213c67df-2dad-4967-8fed-d0157e2617ff)
![3](https://github.com/user-attachments/assets/f18b969a-16e0-4c87-b12f-d050f61dfeee)
![4](https://github.com/user-attachments/assets/be7789f4-ad2b-4136-93d9-c6356c3624ad)
![5](https://github.com/user-attachments/assets/b6d979c5-86d8-4f58-a985-7936dcb898eb)
![6](https://github.com/user-attachments/assets/914b4105-ea2e-47c3-896c-c0a34f6a5de1)
![7](https://github.com/user-attachments/assets/74335c10-cff9-43bf-82e1-115b9882c31b)
![8](https://github.com/user-attachments/assets/88bc5016-6037-4f0d-b9e0-6e868fe8f5a7)
![9](https://github.com/user-attachments/assets/edb9cee0-9d50-4704-b480-0b85677059ff)
![10](https://github.com/user-attachments/assets/4f77b52a-92df-41c6-b8d8-857695d479d9)
![11](https://github.com/user-attachments/assets/583de535-0d4d-4411-84ec-3aa363fe4791)
![12](https://github.com/user-attachments/assets/c2d98b70-dad2-4a78-adb4-ce7310509f0e)
![13](https://github.com/user-attachments/assets/07cc3b74-754d-447c-9b55-56ea1cda623b)
![14](https://github.com/user-attachments/assets/6a76d942-4693-411a-9347-2a134498a482)
![15](https://github.com/user-attachments/assets/f450065f-d4f2-4b29-b608-748130cbe369)
![16](https://github.com/user-attachments/assets/9a4a2eae-cfb1-4e01-9a7f-26e41ca85eb8)
![17](https://github.com/user-attachments/assets/c18a1a90-714a-47ab-993f-0155186bc9e3)
![18](https://github.com/user-attachments/assets/63c21a11-1f7a-447b-a464-6affc56842cf)
![19](https://github.com/user-attachments/assets/48e5fd35-c12e-478f-a187-3c4dd3000afc)


Creating the Power Distribution Network in Openlane
**1. Power Distribution Network (PDN) Setup:**
  -	Use Openlane to create the power distribution network (PDN).
  -	The PDN provides details about the metals used, their pitch, and the width of the metal layers.
    
**2. Power Straps and Rails:**
  -	The PDN includes power straps and rails which are essential for distributing power across the chip.
  -	The orientation and placement of these power components are critical for ensuring a reliable power supply to all parts of the design.
    
**3. Extracting PDN Information:**
   - 	The PDN tool in Openlane generates detailed information about the power network, including:
   - Metals Used: The types of metal layers used in the power distribution.
   - Pitch: The spacing between the metal layers.
   - Width: The width of each metal layer.
   - Power Straps and Rails: Detailed information about the power straps and rails, including their orientation.
     
**4. Running PDN Generation in Openlane:**
   - Execute the command to generate the power distribution network
   - Review the generated reports to understand the distribution of power across your design.
     
**5. Analyzing PDN Details:**
- Check the PDN report files for:
- The specific metals used for power and ground.
- The pitch and width of the metal layers used for power distribution.
- Details on the power straps and rails, including their placement and orientation within the design.
By following these steps, you can create and analyze the power distribution network in your design using Openlane, ensuring that all components receive adequate power and maintaining the integrity of the power supply.


![1](https://github.com/user-attachments/assets/c6e350b4-b4f6-4c57-9448-eacc612e0a27)
![2](https://github.com/user-attachments/assets/311e74a3-e235-49b5-b800-2bef9a3209a3)
![3](https://github.com/user-attachments/assets/f687ac46-66cc-46e2-a9b1-dbea1373a7cb)


# Final Step: Routing in RTL to GDS Flow
**1. Initiate Routing:**

 - The final step in the RTL to GDS flow is to perform routing.
  - Execute the routing command in the Openlane tool: run_routing
    
**2. Analyze Routing Reports:**

- After running the routing command, Openlane generates several reports that provide detailed information about the routing process.
- These reports include metrics and statistics on the routing quality, such as wirelength, via count, and congestion.
  
**3. Review the DEF File:**

  - The DEF (Design Exchange Format) file is updated after routing.
 - Open and review the DEF file to see the coordinates and orientation of the routing layers.
 - The DEF file contains:
   i) Routing Coordinates: The specific X and Y coordinates for each routing segment.
   ii) Layer Orientation: The orientation and metal layers used for routing.
   
**4. Steps to View and Verify Routing:**

   - Use a layout visualization tool (like Magic) to inspect the routing visually:
   - Check for proper routing connections, ensure there are no DRC (Design Rule Check) violations, and verify that all signals are properly routed.
     
By following these steps, you can complete the routing stage in the RTL to GDS flow, ensuring that your design is correctly and efficiently routed, with all connections meeting the necessary design rules and specifications.

![1](https://github.com/user-attachments/assets/3861da28-5991-4305-a2b1-beb8d251c5a7)
![3](https://github.com/user-attachments/assets/5a1efe1f-e468-4772-ae17-a2cf4f8cfa82)






