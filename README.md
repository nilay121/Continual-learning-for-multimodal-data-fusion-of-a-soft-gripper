# Continual learning for multimodal data fusion of a soft gripper
Continual learning (CL) refers to the ability of an algorithm to continuously and incrementally acquire new knowledge from its environment while preserving previously learned information. Traditional models trained on a single data modality often fail to generalize when exposed to different modalities. A simple strategy to address this limitation is to fuze multiple modalities by concatenating their features and training the model on the combined representation. However, this generally requires retraining the model from scratch whenever a new domain is introduced. In this paper, we propose a CL algorithm that incrementally learns from multiple data modalities by combining class-incremental and domain-incremental learning settings. We validate our algorithm on a custom multimodal dataset composed of tactile signals collected from a soft sensorized pneumatic gripper and visual data consisting of nonstationary object images captured from video sequences. Additionally, we evaluate our method on a subset of the publicly available VGGSound dataset, which integrates both visual and audio signals corresponding to various real-world activities. To further demonstrate the robustness and real-time applicability of our approach, we conduct an object classification experiment using a soft sensorized gripper and an external camera setup, all synchronized through the robot operating system framework.

## Install the dependencies in a virtual environment

- Create a virtual environment (Python version 3.8.10) 
  
  ```bash
  python3 -m venv Multimodal_cl
  ```

- Activate the virtual environment
  ```bash
  . Multimodal_cl/bin/activate
  
- Install the dependencies

  ```bash
  pip3 install -r requirements.txt
  ```
## Steps to follow
- Put the gripper dataset in the "dataset" folder
- Run the "dataset_vidToImage.py" file to extract train test images from video frame
- Run the "unsupervised_dataset.py" file to generate the unlabeled data for SSL
- Put the pre-trained feature extractors in the "pre_trained_models" folder

## Ros implementation
- Install ROS1 (Noetic Ninjemys distribution) on Ubuntu 20.04.
- Follow the steps provided in the "ros_instruction" file to create the ROS package.
- Copy paste the python scripts for publisher and subscriber nodes alongwith the pre-trained feature extractor and the saved matrices to the dedicated folders.

## Different combinations
- Intra layer feature representation
  ```
  python3 main.py --enable_ilfr True --enable_ssl False --ssl_type None 
  ```

- Semi Supervised learning
  - Unique class case
    ```
    python3 main.py --enable_ilfr True --enable_ssl False --ssl_type unique
    ```
  - Random class case
    ```
    python3 main.py --enable_ilfr True --enable_ssl True --ssl_type None 
    ```

- Intra layer feature representation
  ```
  python3 main.py --enable_ilfr True --enable_ssl True --ssl_type random 
  ```
  
## To cite the paper
  ```bash
@article{kushawaha2024continual,
  title={Continual learning for multimodal data fusion of a soft gripper},
  author={Kushawaha, Nilay and Falotico, Egidio},
  journal={Advanced Robotics Research},
  pages={202500126},
  year={2024},
  publisher={Wiley Online Library}
}
  ```
