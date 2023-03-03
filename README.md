# Cosmospeed

*Cosmospeed* is a basic driving simulation game with procedurally generated engine audio and torque output from [*Engine Simulator*](https://github.com/Engine-Simulator/engine-sim-community-edition).

![Alt text](docs/public/cosmospeed_cover_v2.png?raw=true)

## Download
This game is currently only available to Patreon members. If you'd like to become a member and get access to this game and other perks, consider joining [here](https://www.patreon.com/atg_engine_simulator).

## Installing the Game
The game comes as a `.zip` file and does not include an installer. Installing the game is as simple as unzipping the `.zip` file and placing the game folder wherever you like on your computer.

## Running the Game
1. Open the `bin/` folder in the game directory
![Alt text](docs/public/03_running_game.png?raw=true)
2. Run `cosmospeed.exe`
![Alt text](docs/public/04_running_game.png?raw=true)

**If you encounter a DLL error**, you need to install some standard dependencies. These installers are included for you in the `installation/` folder in the game. Run the installers located in this folder and the errors should go away.

## Controls
| Action | Input |
| :---: | :---: |
| Starter | Hold `s` key |
| Steer left | Move mouse left **OR** Left arrow key |
| Steer right | Move mouse right **OR** Right arrow key |
| Part throttle | `q`, `w`, `e` |
| Full throttle | `r` |
| Brake | `MMB` **OR** `space` key |
| Clutch | `shift` key |
| Shift up | `LMB` **OR** `up` arrow key |
| Shift down | `RMB` **OR** `down` arrow key |
| Reset vehicle | `backspace` key |
| Change camera | `tab` key |
| Zoom (with some cameras only) | Mouse wheel |
| Fullscreen | `f` key |
| Exit game | `escape` key |

**The game intentionally hides the cursor and locks the mouse to the center of the screen.** To release the mouse, press the Windows key or tab into another application to take focus away from the game window. Reactivating the game window will re-hide the cursor.

### Toggling Between Mouse Steering and Keyboard Steering
Pressing either the `left arrow` or `right arrow` keys will toggle the game to keyboard steering. To toggle back to mouse steering, press any of the mouse buttons.

### Free-cam controls
From the cockpit view, **press tab 3 times to activate free-cam.**
| Action | Input |
| :---: | :---: |
| Look left/right/up/down | Move mouse |
| Move forward/back/left/right | `w`/`s`/`a`/`d` keys |
| Fly forward/fly backward | `r`/`f` keys |
| Move slowly | Hold `MMB` |

## Changing Engines
1. Open `assets/main.mr` in the game directory
2. On line 7, change the text enclosed in the quotes with the path to your engine's file. The path is relative to the `assets/` directory

![Alt text](docs/public/01_changing_engines.png?raw=true)

## Changing Vehicles
1. Open `assets/main.mr` in the game directory
2. On line 12, change the text enclosed in the quotes with the path to the vehicle you'd like to use. The path is relative to the `assets/` directory

![Alt text](docs/public/02_changing_vehicles.png?raw=true)

### Builtin Vehicles
Cosmospeed comes with 3 default vehicles located in `assets/vehicles/`:
1. `default_vehicle.mr`
2. `goofy_vehicle.mr`
3. `italian_vehicle.mr`

## Resolving Issues

### Low framerate
This is a fairly CPU intensive demo so it's possible that the game will run worse than the normal *Engine Simulator*. Reducing the simulation frequency in your engine inside the `.mr` script has the same effect in *Cosmospeed* and will trade audio quality and simulation stability for better performance.

### Game Crashes Upon Opening
If the game crashes immediately when opened, follow these steps:
1. Open the `bin/` folder inside the main game directory
2. Scripting syntax errors/mistakes will be shown in `error_log.log`. Resolve any errors that are reported here
3. Next check `engine_sim.log` for other *Engine Simulator* failures like generic engine mistakes or missing audio files
4. If the previous steps did not resolve the issue, there may be some other bug with the game. Join the [*Engine Simulator Official* Discord Server](https://discord.gg/engine-sim-official) and ask one of the moderators or @AngeTheGreat for help

## Creating Your Own Vehicle
1. Copy and paste one of the default vehicles (the `.mr` file) in `assets/vehicles/`
2. Rename the file to whatever you like and place it in the same directory
3. Open the `.mr` file
4. The settings near the bottom of the `vehicle` node are specific to *Cosmospeed*. Some settings above this are also used by the game. Modify these values as you see fit to match your vehicle. Refer to the table below for information about what they do
![Alt text](docs/public/05_vehicle_modding.png?raw=true)
5. Follow the steps above in *Changing Vehicles* to use your new vehicle

| Setting | Function |
| :---: | :---: |
| `mass` | The vehicle's mass |
| `drag_coefficient` | The vehicle's aerodynamic drag coefficient |
| `diff_ratio` | The vehicle's differential gear ratio |
| `tire_radius` | The radius of the vehicle's tires (ie the distance from the center of the tire to the outside of the rubber) |
| `rolling_resistance` | Generic resistance the car will have to moving |
| `stiffness` | **UNUSED** |
| `damping` | **UNUSED** |
| `max_flex` | **UNUSED** |
| `limit_flex` | **UNUSED** |
| `simulate_flex` | **UNUSED** |
| `max_brake_force` | **UNUSED** [Use `max_brake_torque` instead] |
| `coeff_static_friction` | Friction coefficient between the tire and the ground while not sliding |
| `coeff_dynamic_friction` | Friction coefficient between the tire and the ground while sliding |
| `wheel_base` | The distance from the front to rear wheel centers |
| `track` | The distance from the center of the left front/rear tire to the center of the right front/rear tire |
| `max_brake_torque` | The maximum torque that the brakes can apply per wheel |
| `center_of_mass` | The vehicle's center of mass compared to the center of the wheelbase. Example: A value of +3 centimeters indicates the center of mass is located 3 centimeters **in front** of the center of the wheelbase. -3 would indicate the center of mass falls towards the rear of the car, 3 centimeters from the center of the wheelbase |
| `weight_transfer_bias` | The simulation doesn't account for weight transfer. To roughly approximate it, this value can be used to exaggerate the effect of the center of mass on the tire downforce which in a very crude way can resemble weight transfer |
| `vehicle_asset_file` | The path to the visual assets for the vehicle. The path is relative to the game's main directory. See the next section about modding these asset files |

### Creating Your Own Vehicle Asset File
The `modding/` folder contains some useful resources for game modding. To start modding:

#### 1. Install [Blender](https://www.blender.org/download/)

#### 2. Install the Delta Interchange Export Blender Plugin
1. Find `interchange_export_addon.zip` in the `modding/` folder 
2. Open Blender
3. Go to `Edit`, `Preferences...`, `Add-ons`
4. In the top right corner, press `Install...` and navigate to the file found in step 1. Press `Install Add-on`
![Alt text](docs/public/06_blender_plugin.png?raw=true)
5. Enable the plugin by clicking the check next to it in the list of plugins installed. If it's not on the screen, search for "delta" in the search box in the top right of the window
![Alt text](docs/public/07_blender_plugin.png?raw=true)

#### 3. Open `modding/vehicle_template.blend`
The scene should look something like this:
![Alt text](docs/public/08_blender.png?raw=true)

#### 4. Create a copy and test the exporter
1. Click `File`, `Save As...` and save wherever you like on your computer with a descriptive name
2. Press `a` to select all currently visible objects in the scene
3. Click `File`, `Export` and from the dropdown select `Delta Interchange Asset (.dia)`. If this option doesn't appear, try reinstalling the addon from step 2
3. Name the file something descriptive and place it in the `assets/vehicles/` folder. Keep all the default settings and press `Export Delta Asset`
![Alt text](docs/public/09_blender.png?raw=true)
4. Change the `vehicle_asset_file` parameter in your vehicle's `.mr` file to point to this new asset file
![Alt text](docs/public/10_blender.png?raw=true)
5. Follow the steps for changing vehicles above and make sure `main.mr` points to your new car's `.mr` file
6. Run *Cosmospeed*
![Alt text](docs/public/11_blender.png?raw=true)

#### 5. Change the vehicle model
1. Hide the `Rig` collection and unhide the `VehicleBody` collection in Blender
![Alt text](docs/public/12_blender.png?raw=true)
2. This collection contains all the geometry that makes up the vehicle's body. By default it is a single sphere. Place and edit geometry as needed to construct a car body. See below for a simple example. **IMPORTANT: try to only use regular mesh objects. Modifiers like `Subdivision` are supported but more exotic objects like metaballs or curves may not work as expected**
![Alt text](docs/public/13_blender.png?raw=true)
Make sure all objects fall under the `VehicleBody` collection
![Alt text](docs/public/14_blender.png?raw=true)
3. Switch back to the `Rig` layer and hide the `VehicleBody` layer. You should now see the new vehicle body in the rig
![Alt text](docs/public/15_blender.png?raw=true)
4. Select all and export the scene again as was done before
5. Run *Cosmospeed* and confirm that the new car body is now shown in-game
![Alt text](docs/public/16_blender.png?raw=true)

#### 6. Adjusting the steering wheel
1. The steering wheel mesh can be edited in exactly the same way as the car body mesh by modifying the `SteeringWheel` collection shown in the `Scene Collection` view on the right of the screen
2. To adjust the cockpit driving position in game, first return to the `Rig` collection
3. Select the `CameraEye` empty and move it to a suitable location. You can visualize the camera position by pressing 0. **IMPORTANT: The camera is there for visualization purposes, do not try to move it as this will have no effect in-game.**
![Alt text](docs/public/17_blender.png?raw=true)
4. Once the camera eye is positioned correctly, you can also adjust the camera target by moving the `CameraTarget` empty
5. To adjust the steering wheel position, select the `SteeringWheelRoot` object and move it so that the steering wheel is positioned correctly and visible in the camera
![Alt text](docs/public/18_blender.png?raw=true)
![Alt text](docs/public/19_blender.png?raw=true)
6. Export the scene to verify the seating position and steering wheel position in-game
![Alt text](docs/public/20_blender.png?raw=true)

#### 7. Adjusting the wheel models
1. The wheel mesh can be edited the same way as the steering wheel and car body. No modifications are required in `Rig` because the game places the tires automatically based on the car's wheelbase and track
**IMPORTANT: The wheel model MUST have an overall radius of 1 meter, otherwise it will not appear to be the correct size in-game. Follow the wheel model in the `vehicle_template.blend` as an example**

#### 8. General alignment and scale
1. *Cosmospeed* uses the same scale as Blender, so 1 meter in Blender will equate to 1 meter in-game. It is better to keep your car model in-line with real-world measurements for this reason
2. You will sometimes need to adjust the position of the vehicle model in order to align it with the vehicle in-game. A useful rule to remember is the `VehicleRoot` empty will always be at the exact center of the 4 wheels in-game (and at z=0)

#### 9. Materials
1. *Cosmospeed* supports a small number of builtin materials. These are conveniently listed in the `Materials` collection. Assign these materials to your objects to color your model
![Alt text](docs/public/21_blender.png?raw=true)
![Alt text](docs/public/22_blender.png?raw=true)
The material names assigned in Blender will be mapped to the builtin materials in *Cosmospeed*
![Alt text](docs/public/23_blender.png?raw=true)

#### 9. Complete!
If something didn't work as expected in this tutorial, please create an issue in this GitHub repo and @AngeTheGreat will take a look.
