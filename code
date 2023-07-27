# Imports
from niryo_robot_python_ros_wrapper import *
import rospy

# Initializing ROS node
rospy.init_node('niryo_ned_example_python_ros_wrapper')

niryo_robot = NiryoRosWrapper()

# - Constants
workspace_name = "conveyorkejriwal"  # Robot's Workspace Name

# The observation pose
observation_pose = (0.18, 0., 0.35, 0., 1.57, -0.2)
# The Place pose
place_pose1 = (0., -0.25, 0.1, 0., 1.57, -1.57)

place_pose2=(0., -0.25, 0.143, 0.435, 1.34, -1.57)

place_pose3=()

# - Main Program
# Calibrate robot if robot needs calibration
niryo_robot.calibrate_auto()
# Changing tool
niryo_robot.update_tool()

while (True):
    niryo_robot.move_pose(*observation_pose)
# Trying to pick target using camera


    ret = niryo_robot.vision_pick(workspace_name,
                              height_offset=-6,
                              shape=ObjectShape.ANY,
                              color=ObjectColor.ANY)

    obj_found, shape_ret, color_ret = ret

    if obj_found and color_ret in["RED","BLUE"]:
        niryo_robot.place_from_pose(*place_pose1) #for red and blue plastic waste
    else:
        niryo_robot.place_from_pose(*place_pose2) #for green paper waste

    niryo_robot.move_pose(*observation_pose)
