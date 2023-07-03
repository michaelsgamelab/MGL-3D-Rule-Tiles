# MGL-3D-Rule-Tiles
This holds the unity package for the 3D Rule Tile system I am working on.
------------------------------------------------------------------------------
Required Packages:
2D Tilemap Editor
2D Tilemap Extras

Sample Scene Packages:
Universal RP

------------------------------------------------------------------------------
Sample Scene:

The sample scene in the package is setup as an example for how to use tool.
Set the Graphics in Project Settings to use the URP Asset in the Rendering folder.
The materials in the scene may need to be refreshed. Go to the Project tab, right-click and choose Refresh.

------------------------------------------------------------------------------
Setup for a new scene:
* Add 2D Rectangular Tilemap to Hierarchy
* Set the tag to 'Grid'
* Set Cell Swizzle to XZY
* Note: Cell Size might need to change depending on the size of the models
* Open from the top toolbar: MGL Tools > 3D Tilemap Rule Tiles
* Click 'Add New Level'
* Open from the top toolbar: Window > 2D > Tile Palette
* Change Tile Palette to GameObject Brush
* Expand Cells and Element 0 for the GameObject Brush
* Set the Game Object to a Rule Tile Prefab
* Set the Active Tilemap selection to the an existing level
* Use the Tile Palette tools to paint the rule tiles on the scene
 
------------------------------------------------------------------------------
Generate Rule Tiles:

This button will loop through all of the rule tiles in the scene and change the shown mesh and material according to the rules for the tile type set in the rule tile scriptable object. The placeholder mesh is also disabled.

Rule tile gameobjects will need to have the 'Rule Tile' tag assigned to be included.

------------------------------------------------------------------------------
Add New Level:

This button will automatically add a new rectangular tilemap object at a incremented height under the Grid gameobject.

------------------------------------------------------------------------------
Delete Obscured Tiles:

This button will loop through all of the rule tiles in the scene and delete any tiles that are fully hidden from view due to neighbor tiles of the same type surrounding from the top and side.

------------------------------------------------------------------------------
Generate Combined Meshes:

This button will go level by level and combine the shown meshes of the into larger meshes determined by the Combined Mesh Vertex Limit and hides the rule tile gameobjects.
~65000 is the max for the Combined Mesh Vertex Limit.

This function is for faster load times.

------------------------------------------------------------------------------
Delete Rule Tiles:

This button will loop through all of the rule tiles in the scene and delete them.
Deleted tiles are backed up to a text file in the 'Tilemap Backups' folder.
This backup text file just holds the name of the Prefab used for the tile and its world position.

------------------------------------------------------------------------------
Restore Deleted Rule Tiles:

This button will delete any combined meshes and read the backup text file for the scene's last deleted rule tiles.
While reading through the backup file, instances of the prefabs for the tiles are added to the scene under the corresponding grid level.

If a corresponding prefab is not found, then an error message will be shown for where the prefab was tried to be loaded from. Place any missing prefabs into the path specified and click the Restore button again and repeat the process until the errors are gone.

------------------------------------------------------------------------------
Script Reference:
RuleTile3D - Add to the tile gameobject as a component
RuleTileList3D - Add to the grid gameobject as a component
RuleTileScriptableObject - Used to create rule tile scriptable objects
