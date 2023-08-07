# Sample Hammer Project
An example GitHub project for a Hammer map.<br>
After cloning this, fill in all of the `TODO` parts.

<br>

## Folder structure

* assets
    * Custom assets used by the map into this folder
        * materials, models, scripts, sound
    * Copy-paste them into the equivalent garry's mod folders, or use symbolic links
        * E.g. garrysmod/materials/mapname -> this_project/assets/materials/mapname
* release
    * This folder is what you will publish to the workshop
* mapname.vmf
    * This is your hammer project

<br>


## How to use Git and GitHub
1. Download [GitHub desktop](https://desktop.github.com/) to manage projects using Git on your machine
2. Sign up to GitHub to host your projects
    * Alternative- GitLab
3. Follow the guides on [how to use GitHub desktop](https://docs.github.com/en/desktop)
4. To make changes to the project
    * Make your changes to the files
    * Add & commit all changed files in GitHub Desktop
    * Push the changes up to GitHub



<br>

<br>
<br>


# References
* A bullet point list of useful inspiration images/sources
* `TODO`

<br>
<br>

# Environment Setup
* Link to required assets for your map
* `TODO`

<br>
<br>


# Tester names
* Use this section to record the names of people who have helped test/develop your map, so you can thank them later
* `TODO`

<br>
<br>

# How to release your map

## Build the map & pack custom content into it
1. Rename the map source file
    * Give it the final map name
        * e.g. mapname_v1
        * `TODO`
    * You must do this BEFORE compiling, or things like cubemaps will be scoped to the wrong map name and may not work fully
2. Open the map in the Garry's Mod Hammer editor
3. Compile the map
    * Set BSP to normal
    * Set VIS to normal (optimise what is visible)
    * Set RAD to normal (lighting)
4. Open up VIDE - https://developer.valvesoftware.com/wiki/VIDE
    * Open the "Pakfile lump editor" tool (🗺 ✏)
    * Open the map
    * Click Scan
    * Click browse
    * Find the Garry's mod directory (`C:\Program Files (x86)\Steam\steamapps\common\GarrysMod\garrysmod`)
    * Click scan (this may take a while)
    * Click Auto
    * Ensure that custom files are added
    * Click Apply
    * ENSURE THAT THE DECALS ARE ADDED
        * MANUALLY ADD THE DECAL FILES
            * https://www.tophattwaffle.com/packing-custom-content-using-vide-in-steampipe/
                * "Manually Packing Content in VIDE"
                1. Add the files
                2. Click cancel on the window that pops up
                3. Type in the folder path (e.g. materials\badger\ttt)
            * Files
                * `TODO`: list your decals here
    * ENSURE THAT THE SOUNDSCAPE IS ADDED
        1. Make sure the soundscape has the same name as the map
            * assets/scripts/soundscapes_mapname.txt
        2. Add the soundscape
        3. MANUALLY ADD THE SOUNDSCAPE SOUND FILES
            * https://www.tophattwaffle.com/packing-custom-content-using-vide-in-steampipe/
                * "Manually Packing Content in VIDE"
            * Make sure to not try to add any GMod/HL2 sounds- https://www.badgercode.co.uk/source-sounds/
            * Files
                * `TODO`: List your custom sounds (used in the soundscape) here
    * Click Save
5. Copy the packed map into the garry's mod maps folder
6. Open the map in-game and build the cubemaps
    1. `sv_cheats 1`
    2. `building_cubemaps 1`
    3. `buildcubemaps`
    4. `mat_hdr_level 0` (to go to LDR)
    5. `restart` (to reload map)
    6. `buildcubemaps`
    7. `mat_hdr_level 2` (to go back to HDR)
    8. `restart`
7. Copy the bsp out of the Garry's Mod Maps folder back into the project folder
    * This version will contain both cubemaps and the packed content

<br>
<br>

## Test the map
1. Change your game settings to disable custom content
    * In the garry's mod folder, rename- `download`, `materials`, `models` and `sound`
        * Add `old` to the end of the name
    * Set GMod launch options to `-noworkshop -noaddons`
2. Launch the game and play on your map
3. Verify there are no missing textures/models/sounds
4. Once happy, put your game settings back to normal
    * Rename your folders back to their original names- `download`, `materials`, `models` and `sound`
        * A new materials folder may have appeared; merge/delete it
    * Remove the launch settings `-noworkshop -noaddons`

<br>
<br>

## Publish to the workshop

1. Move the workshop version of the map into release/maps
2. Add the thumbnail to release/maps/thumb/map_name.png
3. Add a nodegraph to support NPCs
    * [Add AI nodes to your map](https://www.youtube.com/watch?v=r3jgAIsbySg)
    * Play the map in-game to re-generate the nodegraph
        * You will find it in your garry's mod folder- garrysmod/maps/graphs/mapname.ain
    * Copy this file to release/maps/graphs/map_name.ain
    * Copy this from the maps folder in your GMod folder
4. Add a navmesh to support bots
    * [Setting up maps for bots](https://www.youtube.com/watch?v=hShf-Kl7EHY) (navmesh)
    * Used by nextbots- https://developer.valvesoftware.com/wiki/NextBot
    * You might need to do this first
        * Open the map
        * Point your crosshair at a walkable surface
        * Type nav_mark_walkable
        * Then run nav_generate (this may take some time and freeze your game until it's done)
5. Package & release the workshop addon
    * Using the VSCode extension GMod SDK- https://www.youtube.com/watch?v=DtX3Lu9trwE
        * You will need to open the "release" folder in another VSCode window
6. Change the thumbnail, title and description
    * There is an example thumbnail in this project- `example-workshop-thumbnail.jpg`
    * Thumbnails need to be 512x512 pixels, JPGs with "progressive" unchecked/disabled
    * You can use the GMod SDK to update your thumbnail- https://www.youtube.com/watch?v=DtX3Lu9trwE

