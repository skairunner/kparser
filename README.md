# K-Parser

A bidirectional converter between scml projects and klei animation files.

For the direction (klei animation files -> scml project) this tool must be used in tandem with a unity asset extractor. You will have to use the asset extractor to get the game files - specifically you are looking for the
atlas file (a single png that contains image data for an animation) and the corresponding (they have the same name)
`*.build` and `*.anim` file. Then this tool can convert that into an scml project.

For the direction (scml project -> klei animation files) this tool must be used in tandem with an actual full unity
install. Use version 2018 because that is the version that Oxygen not included runs on. This is because after this
tool creates the klei animation files from your scml project you will need to use unity to create an asset bundle
that contains the atlas file (`*.png` file), the build file (`*.build`) and the animation file (`*.anim`).

The conversion from (klei animation files -> scml project) is a lossy conversion because klei animation format is more powerful than spriter (main limitation is skew transforms aren't part of spriter). But the conversion from (scml project -> klei animation file) is correct. It may be running the animation at an incorrect speed though.

Both directions have been tested and confirmed to work. A more clear tutorial on how to use this tool to create asset mods for Oxygen not included will be made.

## Usage Guide

1. Install uTinyRipper from [here](https://github.com/mafaca/UtinyRipper).
![Image of download button](tut_step_0.png)
2. Extract uTinyRipper from the zip file
![Image of extraction](tut_step_1.png)
3. Run uTinyRipper from the exe file
![Image of exe](tut_step_2.png)
4. With uTinyRipper running open your file system and navigate to your OxygenNotIncluded_Data folder. On Windows it should be located at "C:\Program Files (x86)\Steam\steamapps\common\OxygenNotIncluded\OxygenNotIncludedData". You are looking for "sharedassets0.assets", "sharedassets1.assets", and "sharedassets2.assets"
![Image of files](tut_step_3.png)
5. Now you will need to drag and drop "sharedassets0.assets" onto your uTinyRipper application window.
![Image of uTinyRipper application landing screen with drag-n-drop](tut_step_4.png)
6. Now your uTinyRipper should look like this with a large export button in the middle. When you click this button it will prompt you to find a location to put the exported files in. I would recommend putting it in a new folder called "ONI-Exports" under your user's "Documents" directory.
![Image of uTinyRipper export button](tut_step_5.png)
7. After uTinyRipper has exported "sharedassets0.assets" you may go ahead and export the the other two "sharedassets" files or you can leave that for later and continue with the tutorial for now. You will need to bring up that directory in which your exported the ONI game files.
![Image of directory with exported files](tut_step_6.png)
8. In the "Assets" folder of one of the "sharedassets" directories you will find two folders. These are "TextAsset" and "Texture2D". A Klei animation is composed of three files - 1st an image file that contains the raw picture data for the animation (this is considered a Texture2D), 2nd and 3rd are two binary files called the build and animation files (both are considered a TextAsset).
![Image of the TextAsset and Texture2D folders](tut_step_7.png)
9. Now we can actually bring together all the files that make up a Klei animation. For this example we will look at the Klei animation called "airconditioner". In the game, this animation is used for the building called the "Thermo Regulator". The files you will need for the "airconditioner" animation are "Texture2D/airconditioner_0.png", "TextAsset/airconditioner_build.bytes", and "TextAsset/airconditioner_anim.bytes".
![Image of the texture file](tut_step_8a.png)
![Image of the binary files](tut_step_8b.png)
10. All of the files for the "airconditioner" animation together looks like this.
![Image of the directory of the files together](tut_step_9.png)
11. Now download the jar version of K-Parser from the releases section of this github repository. Click [here](https://github.com/daviscook477/kparser/releases) to download it. Put the jar somewhere useful. I recommend putting it near your folder containing the animation files.
![Image of the kparser jar](tut_step_10.png)
12. For this next step you will need to be using at least java 9. Run the jar file with the animation files as the parameters to create the scml file.
![Image of command to run](tut_step_11.png)
13. Now you will have the "scml" project file in the directory. Additional the original texture file will have been split into its component pieces.
![Image of the directory with the scml file](tut_step_12.png)
14. Next open the scml file in [Spriter](https://brashmonkey.com/). You can now examine and edit the Klei animation as a spriter project.
![Image of Spriter opening the scml file](tut_step_13.png)