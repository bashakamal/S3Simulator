# S3Simulator-A-benchmarking-Side-Scan-Sonar-simulator-dataset-for-Underwater-Image-Analysis


Kamal Basha S , [Athira. M. Nambiar](https://www.srmist.edu.in/faculty/dr-athira-m-nambiar/)

[[Paper](https://arxiv.org/abs/2408.12833)]

## S3Simulator Sample Images

| ![strip_ship_1](https://github.com/user-attachments/assets/87f5ac59-1347-4fda-b8a0-eb405c91b86d) | ![strip_ship_2](https://github.com/user-attachments/assets/b7608c0f-d6e7-418a-a7cd-bfbf7cb47586) | ![strip-air-4](https://github.com/user-attachments/assets/21f4983c-59d8-4e92-a0b6-446bb723f871) |
|---|---|---|
| ![stripe_air_1](https://github.com/user-attachments/assets/9329442b-4ab4-42b8-b55c-727cebc2f27e) | ![stripe_air_2](https://github.com/user-attachments/assets/7e403ce6-9b7b-4c8d-abe4-d92f1914b21e) | ![stripe_air_3](https://github.com/user-attachments/assets/30645ec7-0a6d-4b85-a046-6b859ec0124d) |
| ![gold_air_processed_2](https://github.com/user-attachments/assets/bcb52253-d730-40f2-b818-924d3cb1e048) | ![gold_air_processed_3](https://github.com/user-attachments/assets/ca0196de-0ad6-49c2-b00d-866db7c2ae55) | ![gold_air_processed_4](https://github.com/user-attachments/assets/bdb0c9b8-3d51-4b6c-acc9-a60e547254f0) |
| ![plane-sim-gray-1](https://github.com/user-attachments/assets/e340b1e9-e6f4-40d0-a295-e93982dcfb93) | ![Plane-sim-gray-2](https://github.com/user-attachments/assets/52a1efaf-db43-4ae4-bc86-471f92087361) | ![ship-gray-1](https://github.com/user-attachments/assets/a4ff4686-12bd-426e-a048-c74ca482ff3f) |



Acoustic sonar imaging systems are widely used for under-
water surveillance in both civilian and military sectors. However, the
acquisition of high-quality sonar datasets for training Artificial Intelli-
gence (AI) models confronts challenges such as limited data availability,
financial constraints and data confidentiality. To overcome these chal-
lenges, we propose a novel benchmark dataset of Simulated Side-Scan
Sonar images, which we term as ‘S3Simulator dataset’. Our dataset
creation utilizes advanced simulation techniques to accurately replicate
underwater conditions and produce diverse synthetic sonar imaging. In
particular, the cutting-edge AI segmentation tool i.e. Segment Anything
Model (SAM) is leveraged for optimally isolating and segmenting the ob-
ject images, such as ships and planes, from real scenes. Further, advanced
Computer-Aided Design tools i.e. SelfCAD, and simulation software such
as Gazebo are employed to create the 3D model and to optimally visualize
within realistic environments, respectively. Further, a range of compu-
tational imaging techniques are employed to improve the quality of the
data, enabling the AI models for the analysis of the sonar images. Exten-
sive analyses are carried out on S3simulator as well as real sonar datasets
to validate the performance of AI models for underwater object classifi-
cation. Our experimental results highlight that the S3Simulator dataset
will be a promising benchmark dataset for research on underwater image
analysis.


# Architecture of S3Simulator
![archi](https://github.com/user-attachments/assets/db8a0d68-27af-4083-afc2-735320f32171)

### Software Versions and Links


| Software                        | Version              | Link                                      |
|----------------------------------|----------------------|-------------------------------------------|
| **Gazebo Multi-Robot Simulator** | 11.10.2              | [Gazebo](https://gazebosim.org/home)      |
| **Ubuntu**                       | 22.04.4 LTS          |                                           |
| **Codename**                     | Jammy                |                                           |
| **SelfCAD**                      | N/A                  | [SelfCAD](https://www.selfcad.com/)       |
| **Segment Anything Model (SAM)** | N/A                  | [Segment Anything](https://segment-anything.com/) |



# Accessing the Segment Anything Model (SAM)
For this project, we utilized the Segment Anything Model (SAM), an advanced AI segmentation tool, to segment silhouette images for 3D modeling. Specifically, SAM was used to isolate objects such as ships and planes from the background for the creation of 3D models in SelfCAD.

We used the [SAM online demo](https://segment-anything.com/demo) to upload silhouette images and segment the required objects.

Steps:
1. Visit the [SAM online demo](https://segment-anything.com/demo).
2. Upload your silhouette image (e.g., ships, planes).
3. Use the intuitive SAM interface to mark and segment the object.
4. Export the segmented mask for further use in 3D modeling with SelfCAD.
5. This approach helped streamline the process of preparing images for 3D modeling and simulation in Gazebo.


# 3D Modeling with SelfCAD
After segmenting the silhouette images using Segment Anything Model (SAM), we used SelfCAD, a powerful browser-based 3D modeling tool, to convert the 2D segmented images into 3D models.

SelfCAD was instrumental in creating detailed 3D models of objects like ships and planes, which were later used in the sonar simulation process in Gazebo.

Steps:
1. Visit [SelfCAD](https://www.selfcad.com/).
2. Import the 2D segmented mask generated by SAM.
3. Use SelfCAD's intuitive 3D sculpting tools to convert the 2D image into a 3D model. Adjust parameters like size, shape, and texture to match real-world objects.
4. Export the 3D model in a format suitable for further simulation (e.g., .stl or .obj).
5. By using SelfCAD, we ensured that the generated models accurately represent real-world objects, making the simulation in Gazebo more realistic.

# Sonar Simulation with Gazebo
Gazebo is an open-source 3D robotics simulator that we used to simulate sonar images with realistic underwater environments. After generating the 3D models using SelfCAD, we imported them into Gazebo to simulate sonar effects such as shadows, noise, and varying seabed terrain.

## Steps to Set Up Gazebo:

1. Install Gazebo: Follow the instructions below to install Gazebo on Ubuntu:

```
# Add the Gazebo repository to your system's sources list
sudo sh -c 'echo "deb http://packages.osrfoundation.org/gazebo/ubuntu-stable $(lsb_release -cs) main" > /etc/apt/sources.list.d/gazebo-stable.list'

# Add the Gazebo key
wget https://packages.osrfoundation.org/gazebo.key -O - | sudo apt-key add -

# Update the package list
sudo apt-get update

# Install Gazebo version 11
sudo apt-get install gazebo11
```

Once installed, you can verify the installation by running:

```
gazebo
```

2. Load the 3D Models: Import the .obj models from the models/ directory into your Gazebo environment. Use the SDF (Simulation Description Format) file to reference the 3D models and place them within the simulation environment.

# Enhancing Realism in Sonar Images
To improve the quality and realism of the S3Simulator dataset, we employed several computational imaging techniques:

1. **Noise Variation:** Simulated various noise types, including Gaussian and salt-and-pepper noise, to replicate real-world sonar signal disturbances.

2. **Nadir Zone Effects:** Incorporated depth-dependent attenuation and angle-of-incidence adjustments to accurately reflect sonar performance directly below the sensor.

3. **Dynamic Seabed Interaction:** Modeled seabed materials and their reflectivity to simulate how different compositions affect sonar echoes, including sediment movement effects.

4. **Environmental Factors:** Simulated variable water properties, such as temperature and salinity, along with current effects, to create a more realistic underwater environment.

These techniques ensure the S3Simulator dataset provides high-fidelity sonar images, enhancing the training of AI models for underwater object classification.


# The dataset consists of the following components:

1. **Silhouette Images**  
   - **Description**: Images used for object segmentation.
   - **File Structure**:
     ```
     /dataset
       └── silhouettes
           ├── silhouette1.png
           ├── silhouette2.png
           └── ...
     ```

2. **SelfCAD 3D Images**  
   - **Description**: 3D models generated from segmented silhouettes.
   - **File Structure**:
     ```
     /dataset
       └── selfcad_3d_models
           ├── model1.obj
           ├── model2.obj
           └── ...
     ```

3. **Gazebo Images**  
   - **Description**: Sonar images simulated in Gazebo with realistic underwater environments.
   - **File Structure**:
     ```
     /dataset
       └── gazebo_images
           ├── sonar_image1.png
           ├── sonar_image2.png
           └── ...
     ```

4. **Sonar Images**  
   - **Description**: Original sonar images used for analysis and model training.
   - **File Structure**:
     ```
     /dataset
       └── sonar_images
           ├── original_sonar1.png
           ├── original_sonar2.png
           └── ...
     ```

