# VISION---BASED-ROBORTIC-ARM-SIMULATION


<img width="250" height="314" alt="Screenshot 2026-06-19 at 11 34 45 AM" src="https://github.com/user-attachments/assets/0479deac-902a-4890-87c3-8ce663616b61" />

# Project Overview
This project implements a Computer Vision  system for robotic grasping using a 7-DOF KUKA robotic arm in a PyBullet simulation.
The agent uses visual input to perform grasping tasks and is trained with the Inverse Kinematics.
The goal is to optimize grasp success using  Segementation mask in the computer vision.

# Institution: INDIAN INSITUTE OF SPACE AND SCIENCE TECHNOLOGY, TRIVANDRUM, KERALA.

# Course: INTERNSHIP PROJECT -  DEPARTMENT OF AVIONICS.

 Author:  RIYA ROSE ROY.
 
 Date: JUNE 25, 2026.
# Environment Details
 1. Simulator: PyBullet 
 
 2. Robot: KUKA 7DOF arm with a parallel-jaw gripper
 
 3. Inputs: RGB camera images
 
 4. Outputs: 5D continuous action vector
    [dx, dy, dz, rotation_angle, gripper_control]


# COMPUTER VISION SETUP

Segmentation Mask Generation (Primary CV Technique)

The virtual camera in PyBullet generates a segmentation image, where each pixel is labeled with the ID of the object it belongs to.

source_objects, uid_mask, tray_masks = get_source_objects_from_current_frame(env).

Algorithm used: Pixel-wise semantic segmentation (provided by the simulator).

# UID-Based Object Identification

  Every object loaded into PyBullet receives a unique identifier (UID).

  target_uid = env.get_uid_by_color(target_name).

  Algorithm used: Object-to-UID lookup (dictionary or mapping-based identification).


# Pixel-to-World Coordinate Association

  Instead of estimating 3D positions from images, the project retrieves object positions directly from the simulaton.

  target_pos, _ = p.getBasePositionAndOrientation(uid).

  Algorithm used: Association between segmented object IDs and simulator world coordinates.
  
  
# Perception-Based Verification
  After a pick-and-place operation, the project verifies whether the selected object is still visible in the source tray or has appeared in the destination tray:

  verify_transfer(env, target_uid, uid_mask, tray_masks)

  Algorithm used: Mask-based verification.


  # experiment
  <img width="848" height="469" alt="Screenshot 2026-06-23 at 12 20 49 AM" src="https://github.com/user-attachments/assets/9b56a1d0-eb79-4eff-bf9a-b3f8d182550e" />

  





