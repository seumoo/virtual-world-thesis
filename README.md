# Converting BIM to Virtual World for Facility Management Operations

This article summarizes my undergraduate thesis work: converting Building Information Models (BIM) into virtual worlds for facility management (FM) operations.  

## Table of Contents
  - [Background & Problem Statement](#background--problem-statement)
  - [Objective](#objective)
  - [Methodology](#methodology)
  - [Results](#results)

## Background & Problem Statement

Facilities management (FM) in buildings requires coordination of space, assets, and maintenance information for the building to run as cost-effective as possible. FM operations include:

- Maintaining inventory of physical assets, including mechanical and HVAC equipment
- Managing maintenance crews and tasks
- Utilizing sensors and computer systems to monitor building health

Since buildings have dynamic facility systems, monitoring building health in real-time is challenging. Managers may wait for information verification which increases facility-related expenditures. These situations stem from physical limitations like identifying faulty equipment in person and data discrepancies between equipment sensors and the environment. For example:

- Disturbing an office space when searching for problematic duct systems in a ceiling
- Faulty thermostat readings leading to room temperature issues

I explored using virtual worlds to help FM operations be less constrained by physical and data limitations. A virtual world is a digital twin of a physical space rendered in a gaming engine. Converting BIM into a gaming engine allows you to integrate interactivity components, including physical movement, object interactivity, and database incorporation. These components are difficult or impossible to incorporate in BIM using standard BIM tools.



## Objective

The objective of my thesis to use the Unity game engine to develop a virtual world of a 17 story facility and integrate interactive components for FM operations (Figure 1). Interactivity within the virtual world will help facility managers with day-to-day operations without being in the physical location such as identifying faulty systems or viewing equipment data in real-time.

</br>

<img src="./media/method.png" width="800" height="300" />
<figcaption><b>Figure 1: BIM to Unity workflow</b></figcaption>

</br>

I developed the following interactions to help with FM operations:

- First-person movement for users to navigate the facility
- Facility databases which streams real-time data of equipment including sensors, thermostats, and HVAC units
- Interaction with equipment to display data from the database stream
- An interface which detects connecting pipe segments for fire sprinklers

</br>

<img src="./media/movement_demo.gif" width="724" height="490" />
<figcaption><b>Figure 2: Interaction with equipment and data in the virtual world</b></figcaption>

</br>

## Methodology

This section explains the methodology used to convert BIM into Unity and developing an interactive virtual world for FM operations. 

### Converting BIM into Unity

The first step was converting the BIM into a file format that Unity accepts. Importing BIM files directly into Unity loses the model's textures and meta-data. However, importing an acceptable file format like FBX will retain the model's texture and data. I used Autodesk 3ds Max to export the mechanical, structural, and architectural BIM files into FBX with textures, lighting, and meta-data. Then, I exported the FBX files into Unity

### Connecting Live Data Feeds

### 

### Integrating Equipment Interactions

<img src="./media/bas.jpg" width="1000" height="200" />
<figcaption><b>Figure 4: Object detection from point cloud stream (3/4th view)</b></figcaption>

## Results


<video width="640" height="400" controls>
  <source src="./media/large_room_noaudio.mp4" type="video/mp4">
</video>