# Converting BIM to Virtual World for Facility Management Operations

This article summarizes my undergraduate thesis work - converting Building Information Models (BIM) into virtual worlds for facility management (FM) operations. You can read my thesis work from the following:

- ICCCBE 2016 (PDF)
- Undergraduate thesis submission (PDF)

**Technologies Used**: Autodesk Revit, Unity, Python, JavaScript, C#, SQL

## Table of Contents
  - [Background & Problem Statement](#background--problem-statement)
  - [Objective](#objective)
  - [Methodology](#methodology)
    - [Converting BIM into Unity](#converting-bim-into-unity)
    - [Connecting Live Data Feeds](#connecting-live-data-feeds)
    - [](#)
    - [Integrating Equipment Interactions](#integrating-equipment-interactions)
  - [Results](#results)


## Background & Problem Statement

Facilities management (FM) in buildings requires coordination of space, assets, and maintenance information for the building to run as cost-effective as possible. FM operations include:

- Maintaining inventory of physical assets, including mechanical and HVAC equipment
- Managing maintenance crews and tasks
- Utilizing sensors and computer systems to monitor building health

Since buildings have dynamic facility systems, monitoring building health in real-time is challenging. Managers may wait for information verification which increases facility-related expenditures. These situations stem from physical limitations like identifying faulty equipment in person and data discrepancies between equipment sensors and the environment. For example:

- Disturbing an office space when searching for problematic duct systems in a ceiling
- Faulty thermostat readings leading to room temperature issues

I researched virtual worlds for FM operations to help mitigate physical and data limitations that facility managers face.  A virtual world is a digital twin of a physical space rendered in a gaming engine. Converting BIM into a gaming engine allows you to integrate interactivity components, including physical movement, object interactivity, and database incorporation. These components are difficult or impossible to incorporate in BIM using standard BIM tools.

## Objective

The objective of my thesis to use the Unity game engine to develop a virtual world of a 17 story facility and integrate interactive components for FM operations (Figure 1). Interactivity within the virtual world will help facility managers with day-to-day operations without being in the physical location such as identifying faulty systems or viewing equipment data in real-time.

</br>

<img src="./media/method.png" width="800" height="300" />
<figcaption><b>Figure 1: BIM to Unity workflow</b></figcaption>

</br>

In the virtual world, I developed the following interactions:

- First-person movement for users to navigate the facility
- Facility databases which streams real-time data of equipment including sensors, thermostats, and HVAC units
- Interaction with equipment to display data from the database stream
- Pipe segment detection for fire sprinklers

Figure 2 shows a sample interaction with an air handling unit (AHU) where the interface displays real-time sensor data from the AHU. The next section explains my methodology to develop this virtual world.

</br>

<img src="./media/movement_demo.gif" width="724" height="490" />
<figcaption><b>Figure 2: Interaction with equipment in the virtual world</b></figcaption>

</br>

## Methodology

This section explains the methodology used to convert BIM into Unity and developing an interactive virtual world for FM operations. 

### Converting BIM into Unity

The first step was converting the BIM into a file format that Unity accepts. Importing BIM files directly into Unity loses the model's textures and meta-data. However, importing an acceptable file format like FBX will retain the model's texture and data (Figure 3a). I used Autodesk 3ds Max to export the mechanical, structural, and architectural BIM files into FBX with textures, lighting, and meta-data. I exported the FBX files into Unity and verified the textures, lighting, and meta-data in the model were still intact (Figure 3b).


</br>

<img src="./media/model_comparison.png" width="1000" height="300" />
<figcaption><b>Figure 3: Model comparison based on import method</b></figcaption>

</br>

### Adding Player Movement

I utilized Unity assets to add player movement so players could navigate the virtual world. I developed JavaScript scripts to allow players to navigate the model in a first-person perspective. I added colliders to all model elements including doors, walls, floors, and equipment. Colliders prevent players from walking through elements and another layer of realism to the virtual world.

Next, I developed scripts in Unity to connect to a database with live data feeds from sensors and facility equipment.


### Connecting Live Data Feeds

I completed the following steps to connect live data feeds into the virtual world (Figure 4):

1. Requested facility data from the facility's Building automation systems (BAS) using REST requests
2. Stored BAS data into a SQL database so data can be imported into Unity
3. Developed C# scripts in Unity to connect the virtual world with the SQL database

Next, I developed scripts so players could interact with equipment and view data feeds.

<img src="./media/bas.jpg" width="1000" height="200" />
<figcaption><b>Figure 4: Connecting BAS data into the virtual world</b></figcaption>

### Integrating Equipment Interactions

To integrate equipment interactions, I developed a user interface (UI) in JavaScript to display equipment data from the SQL database (Figure 5). The UI extracts an equipment's ID, queries the database via ID to return the equipment's readings and health status, and displays the equipment's information in a popup. 

</br>

<img src="./media/ac_data.jpg" width="357" height="177" />
<figcaption><b>Figure 5: UI of an air handling unit</b></figcaption>

</br>

Next, I added a click event to all equipment in the virtual world including HVAC units, mechanical systems, and sensors. When a player clicks on an equipment element, a popup will appear and display the equipment's live data feeds and health status (Figures 6 & 7).

</br>

<img src="./media/large_room.gif" width="724" height="490"/>
<figcaption><b>Figure 6: Viewing equipment data in an office space</b></figcaption>

</br>

</br>

<img src="./media/doas_movement.gif" width="724" height="490"/>
<figcaption><b>Figure 7: Viewing data from dedicated outdoor air systems (DOAS)  </b></figcaption>

</br>

### Detecting Pipe Segments for Fire Sprinklers

To establish relationships between flow systems such as pipe networks and their connections to valves, Industry Foundation Classes (IFC) data exported from the BIM was used. IFC is a BIM specification which establishes a model’s entities and their properties within a model. Properties include physical attributes such as dimensions, spatial attributes such as the Cartesian coordinate of the entity, meta-data such as the entity’s type, and relationships between other entities.

Figure 8 shows a sample of an IFC file and its contents. IFC establishes flow systems under the `IFCRELASSIGNSTOGROUP` class which contain IFC lines as its attributes. IFC lines refer to a specific component or component property such as

-  `IFCFLOWFITTING`: describes a single entity such as a valve or 
-  `IFCDISTRUBUTIONPORT`: describes an inlet or outlet

IFC IDs are unique randomly generated IDs given to each component in the model.

</br>

<img src="./media/ifc_sample.JPG" width="720" height="286"/>
<figcaption><b>Figure 8: Sample of IFC data</b></figcaption>

</br>

To convert textual IFC relationships into interactive flow systems within the virtual world, I developed Python and C# scripts to parse IFC data and link flow systems. (Figure 9).

</br>

<img src="./media/ifc_flowchart.png" width="800" height="125"/>
<figcaption><b>Figure 9: Process of integrating IFC relationships into the virtual world</b></figcaption>

</br>

</br>

<img src="./media/pipes_1.gif" width="757" height="446"/>
<figcaption><b>Figure 7: Viewing data from dedicated outdoor air systems (DOAS)  </b></figcaption>

</br>

</br>

<img src="./media/pipes_2.gif" width="757" height="446"/>
<figcaption><b>Figure 7: Viewing data from dedicated outdoor air systems (DOAS)  </b></figcaption>

</br>

## Results
