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

## Etapes
- Télécharger/cloner mmps + nots des github

- Lancer openpose -> mettre le fichier que l’on a obtenu nous

## Processus pour générer tous les csv:

https://github.com/centralelyon/tt-mmpose/blob/main/test_mmpose_inference.py 

- Lancer “lancer_mmpose_sur_video()” sur l’ensemble des clips

https://github.com/centralelyon/tt-mmpose/blob/main/position_camera.py 

- Modifier en haut la variable “points_2d” qui indique les points de la table

- Modifier “image_size”

- Ça permet d’obtenir les paramètres de la caméra

- Utiliser la fonction “calculer_position_3d_pieds()”
- 
https://github.com/centralelyon/tt-dev/blob/main/ui/utils_annotation.py 

- Créer le fichier de position avec “creation_csv_position_joueur_grace_pieds()”

- Faire correspondre les numéros des personnes aux bons joueurs “reatribution_joueurs_grace_pieds()”

- Créer pour chaque clip un nouveau fichier d’annotation “creation_csv_enrichi_nouveau_referentiel()”

## Fichier générés:
Pose avec mmpose _pose_2d_mmpose.csv

- La position des pieds en 3d _pose_2d_mmpose_convertion_3d.csv

- La position des joueurs en se basant sur la moyenne des pieds _position_joueur_grace_pieds.csv

- La position des joueurs en se basant sur la moyenne des pieds en gardant que les joueurs et en les numérotant correctement _position_joueur_grace_pieds_ordonne.csv

- Un nouveau csv enrichi avec les nouvelles infos pour le nouveau référentiel _enrichi_new_ref.csv

## Génération de la vidéo 3D:

- https://github.com/centralelyon/tt-mmpose/blob/main/test_render_image.py 

- Utiliser la fonction “enregistrement_image()” afin de générer des images de la scène 3D pour chaque frame

- https://github.com/centralelyon/tt-mmpose/blob/main/creer_video_depuis_images.py 

- Utiliser la fonction “create_video_from_images()”
