In order to exploit all the features provided by OAN, you need to install some external softwares.

Install the [Boost](https://www.boost.org/) libraries

    sudo apt install -y libboost-all-dev

Install [GStreamer](https://gstreamer.freedesktop.org/documentation/installing/on-linux.html?gi-language=c) 

    sudo apt install -y libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev libgstreamer-plugins-bad1.0-dev gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav gstreamer1.0-tools gstreamer1.0-x gstreamer1.0-alsa gstreamer1.0-gl gstreamer1.0-gtk3 gstreamer1.0-qt5 gstreamer1.0-pulseaudio

Be sure to install the usb_package to stream the rgb camera data to a ROS2 topic

    sudo apt install -y ros-<ros2-distro>-usb-cam

We need [pip](https://pip.pypa.io/en/stable/installation/) in order to install some python packages

    sudo apt install -y wget
    wget 'https://bootstrap.pypa.io/get-pip.py'
    python3 get-pip.py

Now add the local bin folder to the path

    echo "export PATH=$PATH:~/.local/bin" >> ~/.bashrc
    source ~/.bashrc

Use pip to install PyAudio

    sudo apt install -y portaudio19-dev
    pip install PyAudio

Install the OpenAI Python library

    pip install --upgrade openai

and setup you API key for a single project as reported in the [official guide](https://platform.openai.com/docs/quickstart/step-2-set-up-your-api-key). Note that to use the code as it is you need to set the environment variable 

    echo "export OPENAI_API_KEY=<your_key>" >> ~/.bashrc

To install the Text-To-Speech and Speech-To-Text services provided by the Google Cloud Platform, you need to:

 - [Set up your Google Cloud project](https://cloud.google.com/speech-to-text/docs/before-you-begin?hl=en#setting_up_your_google_cloud_platform_project)  
 - [Install the gcloud CLI ](https://cloud.google.com/sdk/docs/install?hl=en)
 - [Install the Speech To Text Python Library](https://cloud.google.com/speech-to-text/docs/transcribe-client-libraries?hl=en#client-libraries-install-python) 
 - [Install the Text To Speech Python Library](https://cloud.google.com/text-to-speech/docs/libraries#install) 

In order to use OAN as it is, please set the following environment variable if you have not done it already

    echo "export GCP_OAN_ID="<your_google_project_id>" >> ~/.bashrc