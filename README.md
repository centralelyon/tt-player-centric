# tt-player-centric

## Steps
- Download MMPose https://github.com/open-mmlab/mmpose
- pip install bpy,numpy,pandas,opencv-python
- Use lancer_mmpose_sur_video() in test_mmpose_inference.py
  - Params:
    - video_path
    - output_csv
(We need a video of a single camera with only one point)

Using this function we get a csv file with all players positions and with a tracking provided

You need to use create_json_camera() to create camera's parameters json (function in utils.py) 
  - Params:
    - name_output_csv
    - focale length (mm)
    - optical center (tuple)
    - distorsion_k1
    - distorsion_k2
    - distorsion_k3
    - position (x,y,z)
    - rotation (x,y,z) (in degrees)

(you can use slovepnp or cameracalibrate function from opencv to compute parameters using the table as reference)

## Create video of player's position
To create the video we need more annotated data. We provide csv files of an annotated point to use as exemple
- Execute render_image.py

## Create csv with new referentiel
To create the csv with coordonates of the new referentiel we need to use create_csv_new_ref() from utils.py
exemple:
create_csv_new_ref("exemple/set_1_point_8_annotation_enrichi.csv","exemple/set_1_point_8_position_ordonne.csv")

