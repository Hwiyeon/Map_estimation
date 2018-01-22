Rent3D-modified is a modified data of Rent3D-CVPR2015.

The citation of Rent3D-CVPR2015:
@inproceedings{ApartmentsCVPR15,
	title = {Rent3D: Floor-Plan Priors for Monocular Layout Estimation},
	author = {Chenxi Liu and Alex Schwing and Kaustav Kundu and Raquel Urtasun and Sanja Fidler},
	booktitle = {CVPR},
	year = {2015}}

Directory Structure: Rent3D-modified
1. floorplan: Contains 215 floor plans in jpg format
  -- scaling factor of 1 pixel to meter: 0.02
2. gazebo: Contains 215 files including information of items for simulator gazebo
 2.1. txt: save the data in txt format
 2.2. mat: save the data in .mat format (the name of a variable: houseinfo)
  -- structure: n x  15 matrix (there are n walls)
     Each row contains 
     ------------------------------------------------------------------------------------
     |column|        1          |   2   |   3    |   4   |   5   |    6    |     7    |  8  |   9   |  10 |  11 |  12 |  13 |  14  |  15 |
     |          |   RoomIndex |Type|   cx  |  cy  |  phi  | width | height |  x1 |  y1  | x2  |  y2 | x3  |  y3 |  x4  |  y4 | 
  -- RoomIndex: the index of the room where an item is
  -- Type: 1~5: wall including doors (0), wall(1), Toilet(2), Sink(3), Shower(4) ,Stove(5)
  -- cx,cy, phi: the x,y position and orientation of the center of an item. (orientation: East is 0, -pi~pi)
  -- (xn,yn)  where n=1,...,4: vertices of the layout of an item
  -- unit: m
  -- Do not draw items wiht the type 'wall including doors'

3. layout: Contains 215 files including layouts of rooms
  3.1. txt: save the data in txt format
  3.2. mat: save the data in mat format
  -- structure: n x  matirx (n rooms)
     Each column contains (m, x1,y1, x2,y2, ...,): m is the number of vertices of the room

4. crop_imgs: n x n cropped images of images in floorplan

matlabcodes:
1. run0_data_modification
- generate folders floorplan, gazebo, and layout in a modified dataset using Rent3D-CVPR2015
2. run1_mat2img4tf
 - Generate crop_imgs based on gazebo/mat/ and layout/mat/
 - Generate images for training
 - dsc : the Desired Scaling Factor of 1 pixel to meter
 - dimsize: the disired size of images




