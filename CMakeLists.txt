cmake_minimum_required(VERSION 3.5)
project(depth_rois_fusion_pipeline)

find_package(ament_cmake REQUIRED)

# config.yaml をインストール
install(
  DIRECTORY config
  DESTINATION share/${PROJECT_NAME}
)

# launch ファイルをインストール
install(
  DIRECTORY launch
  DESTINATION share/${PROJECT_NAME}
)

ament_package()
