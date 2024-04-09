![OAN_logo](assets/githublogo.png)


# Open Access NAO (OAN)

Open Access NAO (OAN) is an *open-source* ROS2-based software framework for HRI applications with the NAO robot.


## 1 Description

Embracing the common demand of researchers for better performance and new features for NAO, the authors took advantage of the ability to ***run ROS2 on board NAO*** to develop a framework independent of the APIs maintained by the manufacturer. 

This framework is supported by the [ROS-Sports](https://ros-sports.readthedocs.io/en/latest/) organization.

### 1.1 Main features

Our system provides NAO with not only the basic skills of a humanoid robot such as walking and reproducing movements of interest but also features often used in HRI such as: 

 - *Speech recognition/synthesis* via Google Cloud Platform.
 - *Face and object recognition* via YOLOv8.
 - use of *Generative Pre-trained Transformer (GPT) model for conversation* thanks to ChatGPT. 

The developed code is therefore configured as a ready-to-use but also highly expandable and improvable tool thanks to the possibilities provided by the ROS community.

A video showing these features is available on [YouTube](https://youtu.be/LxboNtHfDJg?si=1951kaU84Miw7Ubb).

### 1.2 Modules

This repository collects all the code on which OAN is based. The following image provides an overview of the different parts and the flow of information.

![OAN_scheme](assets/oan_scheme.jpg)

Parallelograms and ellipses are ROS packages and modules (a collection of packages), respectively. 
Dashed lines shows parts developed by the ROS community.

For a detailed description of each module please look at the related paper: [Open Access NAO (OAN): a ROS2-based software framework for HRI applications with the NAO robot](https://arxiv.org/abs/2403.13960)


## 2 Installation on your machine


### 2.1 Download OAN software

If you have never used [vcstool](https://github.com/dirk-thomas/vcstool), install it. The easyiest way is via pip

    sudo pip install vcstool

In order to help the organization of your code and syncronization with a real NAO, we suggest to create a new ROS2 workspace

    mkdir -p oan_ws/src
    cd oan_ws

Clone the OAN repository

    git clone https://github.com/antbono/OAN.git

Import all the needed packages via vcstool

    vcs import src <  OAN/oan.repos --recursive

### 2.2 Notes ROS Community Software

OAN leverages on two packages provided by the ROS Device Drivers Community.

 - [audio_common](https://github.com/ros-drivers/audio_common/tree/ros2) is necessary to use NAO speakers and microphones. Unfortunately, there is a long-standing problem for the ROS2 version of this package (see [#227](https://github.com/ros-drivers/audio_common/issues/227)). For this reason, at the moment, we use the solution proposed in [#248](https://github.com/ros-drivers/audio_common/pull/248) (you don't have to do anything).  

 - [usb_cam](https://github.com/ros-drivers/usb_cam), is used to stream the data of the NAO's rgb cameras to ROS2 topics. Although it is not necessary for building the framework, for debugging and testing it is useful to install the package on your machine: 

        sudo apt-get install ros-<ros2-distro>-usb-cam 

### 2.3 Build

Since ROS Rolling is migrating to Ubuntu 24.04 but NAO uses 22.04, we recommend to **use ROS Humble or ROS Iron**.

Build the packages

    rosdep install --from-paths src -i -r -y
    colcon build

It may take some time depending on the used machine. 
Do not choose the `--symlink-install` option if you want to use the [sync](https://github.com/ijnek/sync/tree/main) script as reported in 3.4 .

### 2.4 Install YOLOv8

Install YOLOv8 on your machine as stated in the [official guide](https://github.com/ultralytics/ultralytics).
Note that the simplest way to make YOLO and other python packages working with ROS on multiple machines, is not using any python virtual environment.


## 3 Installation on the NAO

In order to run the provided software on a real NAO v6 you need to install the custom Ubuntu OS and a version of ROS2.


### 3.1 Install the custom Ubuntu OS

The first step is to install the Ubuntu 22.04 image created by the [Nao Devils SPL team](https://naodevils.de/). Instructions are listed in [naov6_flash.md](naov6_flash.md).


### 3.2 Install ROS2

At the moment, we suggest the ROS [Humble release](https://docs.ros.org/en/humble/index.html) because most of the modules are tested on it. 

Follow the [ROS2 official guide](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html) to install the binary packages for Ubuntu. 
Please be careful and use the ROS-Base Install (Bare Bones), since the installed Ubuntu does't have a GUI.


### 3.3 Install OAN dependencies for NAO

In order to exploit all the features provided by OAN, you need to install some external softwares.

Instructions are listed in [oan_dependencies.md](oan_dependencies.md).


### 3.4 Install OAN

Finally, use the [sync](https://github.com/ijnek/sync/tree/main) script to send the packages you built on your machine to NAO. This avoids building the packages on NAO which requires a lot of time.


## 4 Usage 

To test the framework quickly, you can reproduce the aforementioned [experiment](https://youtu.be/LxboNtHfDJg?si=1951kaU84Miw7Ubb) by following the instructions on the [hni repository](https://github.com/antbono/hni).

Enjoy it! :D

