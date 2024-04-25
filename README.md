# Wall-Completer
This project proposes a much more general method to complete wall, floor, ceiling,.... or any thing in planar surface in 3D Point Cloud Reconstruction

## Poblem statement
Real life 3D Point Cloud is usually noisy, missing. There are usually 2 task we should care about 3D Point Cloud Reconstruction
* Structural Completion (Wall, Column, Floor, Ceiling,.. )
* Object Completion (Table, Chair, Sofa,.. )
The reason to reconstruction 3D Point Cloud are vary. Since 3D is taking in attention more and more.
## This project solve
Assume we have points of a room, house,... But real life point cloud of these walls are really noisy, we want to reconstruct them to have nice form, better view for 3d represent.
The brief Solution of my is below:
1. Collect all point cloud of walls ( do not care instances, number of walls )
2. Only take **x and y** dimension. This mean We have a 2D representation 
3. We downsampling these poins to about 2000 points
4. Use Convex Hull to find points that make a smallest Convex that contain every point inside it
5. From these point, we iterate each point next to each other. Make a line of points between them. Now we should have a Dense Convex.
6. We linspace z dimension from 0 to original max z. Then concat each z to the Dense Convex. This process is to build 3D from 2D ( only for planar ).
7. Now we should have a new Dense Wall.

For example images, you can see in folder "Images"

> [!NOTE]
> The main file is "local.py", you should see my modification in there.
> 
> Raw point clouds can be found in 2 folder "np_points" (raw after denoise ) and "wall_nphuc" (raw).
> 
> You shoul read the ConVex Hull algorithm 
