cmake_minimum_required(VERSION 2.8.3)
project(OMRosDrivers_py)
find_package(catkin REQUIRED COMPONENTS message_generation std_msgs)

catkin_python_setup()

add_message_files(FILES
    ComponentReferent.msg
    ComponentReferents.msg
    MetaAction.msg
    MetaActionResult.msg
    OMTypes.msg
    PerceptionFlow.msg
    ROSParameter.msg
    RosSingularity.msg
    ROSTopic.msg
)

catkin_install_python(PROGRAMS src/meta_actuator_node.py src/meta_sensor_node.py src/test_action.py src/test_sensing.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})

generate_messages(DEPENDENCIES std_msgs)

catkin_package(CATKIN_DEPENDS message_runtime std_msgs)

install(DIRECTORY launch
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})
