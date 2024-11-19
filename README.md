# tt-player-centric


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
