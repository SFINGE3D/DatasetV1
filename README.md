# Dataset V1
This repository include the version 1 of the SFINGE3D dataset aimed at testing approaches for the online detection of gestures of multiple types (static, fine, coarse) and described in the paper:

SFINGE 3D: A novel benchmark for online detection and recognition of heterogeneous hand gestures from 3D fingers’ trajectories
by Ariel Caputo, Andrea Giachetti, Franca Giannini, Katia Lupinetti, Marina Monti, Marco Pegoraro and Andrea Ranieri
(please cite it in works using the dataset.

It includes two folders, 
## Dictionary
includes instances of segmented finger trajectories, each one encoded in a text file where the rows are consecutive fingers poses captured at 20 fps, where data are positions (x,y,z) and  orientation quaternions (x,y,z,w) of the 20 joints encoded. 
The structure of a row is summarized in the following scheme:
palmpos(x;y;z);palmquat(x,y,z,w);thumbApos(x;y;z);thumbAquat(x;y;z;w);thumBpos(x;y;z);thumbBquat(x;y;z;w);thumbEndpos(x;y;z);thumbEndquat(x;y;z;w);indexApos(x;y;z);indexAquat(x;y;z;w);indexBpos(x;y;z);indexBquat(x;y;z;w);indexCpos(x;y;z);indexCquat(x;y;z;w);indexEndpos(x;y;z);indexEndquat(x;y;z;w);middleApos(x;y;z);middleAquat(x;y;z;w);middleBpos(x;y;z);middleBquat(x;y;z;w);middleCpos(x;y;z);middleCquat(x;y;z;w);middleEndpos(x;y;z);middleEndquat(x;y;z;w);ringApos(x;y;z);ringAquat(x;y;z;w);ringBpos(x;y;z);ringBquat(x;y;z;w);ringCpos(x;y;z);ringCquat(x;y;z;w);ringEndpos(x;y;z);ringEndquat(x;y;z;w);pinkyApos(x;y;z)pinkyAquat(x;y;z;w);pinkyBpos(x;y;z)pinkyBquat(x;y;z;w);pinkyCpos(x;y;z)pinkyCquat(x;y;z;w)pinkyEndpos(x;y;z)pinkyEndquat(x;y;z;w)
where the joint positions corresponds to those reported in the following image.
Each joint is therefore characterized by 7 floats, three for position and four for the quaternion, the sequence starts from the palm, then the thumb with three joints ending with the tip and then the other four fingers with four joints each ending with the tip.

There are 13 subfolders (1-13) corresponding to the different gestures 

 1 - one (static)
 2 -  two (static)
 3 -  three (static)
 4 -  four (static)
 5 -  OK (static)
 6 -  pinch
 7 -  grab
 8 -  expand
 9 -  tap
 10 - swipe left
 11 - swipe right
 12 - swipe V
 13 - swipe O 

each one including 36 instances.

## Sequences
includes long sequences of hand poses  captured at 20 fps, similarly encoded, where a few gestures (3-5) should be localized in the correct time location. 


## Annotation and evaluation
The Sequence folder includes also a file sequencesGT.csv with the annotation of the position of the gestures to be found in each sequence. This is a text file where each line includes the following comma separated values. The first two values are the sequence index and number of gestures in the sequence.
The following are, for each gesture hidden in the sequence, the gesture label (1-13) the starting frame id, the ending frame id.

In the evaluation protocol used in the paper, a gesture is considered as correctly detected if (i) the gesture start is identified within the time window of the ground truth gesture with a margin of 20 frames at the beginning to allow slightly early detections to still be considered correct and (ii) the gesture is labelled in accordance with the ground truth. A Matlab code for the evaluation given an input file with the same encoding of sequenceGT.csv will be added to the repository
