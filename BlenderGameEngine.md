#support for subset of Sensors and Actuators in ogredotscene

## Supported Sensors: ##
  * Collision
  * Near
  * Radar
  * Touching
  * Raycast
  * Message

## Supported Actuators: ##
  * Shape Action
  * Edit Object
  * Camera
  * Constraint
  * Message
  * Motion
  * Sound
  * Visibility

_note: Shape Action_
The most common thing a designer will want to do is have an event trigger an animation.  The BGE contains an Actuator called "Shape Action", with useful properties like: start/end frame, and blending.  It also contains a property called "Action" but this is hidden because the exporter ignores action names and instead uses the names of NLA strips when exporting Ogre animation tracks.  The current workaround is to hijack the "Frame Property" attribute and change its name to "animation".  The designer can then simply type the name of the animation track (NLA strip).  Any custom syntax could actually be implemented here for calling animations, its up to the engine programmer to define how this field will be used.  For example: "**.explode" could be implemented to mean "on all objects" play the "explode" animation.**

```
		<node name="Monkey">
			<position x="-1.97660720348" y="2.18365383148" z="1.1644307375"/>
			<quaternion w="1.0" x="0.0" y="0.0" z="-0.0"/>
			<scale x="1.0" y="1.0" z="1.0"/>
			<game>
				<sensors>
					<sensor name="Near" type="NEAR">
						<component name="property" type="str" value=""/>
						<component name="distance" type="float" value="1.0"/>
						<component name="reset_distance" type="float" value="2.0"/>
					</sensor>
					<sensor name="Touch" type="TOUCH">
						<component name="material" type="Material" value="Material.001"/>
					</sensor>
					<sensor name="Radar" type="RADAR">
						<component name="property" type="str" value=""/>
						<component name="axis" type="str" value="YAXIS"/>
						<component name="angle" type="float" value="0.0"/>
						<component name="distance" type="float" value="0.0"/>
					</sensor>
					<sensor name="Message1" type="MESSAGE">
						<component name="subject" type="str" value="hello world"/>
					</sensor>
					<sensor name="Collision" type="COLLISION">
						<component name="property" type="str" value=""/>
					</sensor>
					<sensor name="Ray" type="RAY">
						<component name="ray_type" type="str" value="PROPERTY"/>
						<component name="property" type="str" value=""/>
						<component name="material" type="str" value=""/>
						<component name="axis" type="str" value="YAXIS"/>
						<component name="range" type="float" value="0.00999999977648"/>
						<component name="use_x_ray" type="bool" value="False"/>
					</sensor>
				</sensors>
				<actuators>
					<actuator name="Camera" type="CAMERA">
						<component name="object" type="Object" value="Monkey"/>
						<component name="height" type="float" value="0.0"/>
						<component name="min" type="float" value="0.0"/>
						<component name="max" type="float" value="0.0"/>
						<component name="axis" type="str" value="X"/>
					</actuator>
					<actuator name="Message" type="MESSAGE">
						<component name="to_property" type="str" value="message to something"/>
						<component name="subject" type="str" value="hello world"/>
						<component name="body_message" type="str" value="extra data"/>
					</actuator>
					<actuator name="Edit Object" type="EDIT_OBJECT">
						<component name="dynamic_operation" type="str" value="RESTOREDYN"/>
						<component name="linear_velocity" type="vector" value="0.0 0.0 0.0"/>
						<component name="mass" type="float" value="0.0"/>
						<component name="mesh" type="POINTER" value=""/>
						<component name="mode" type="str" value="DYNAMICS"/>
						<component name="object" type="POINTER" value=""/>
						<component name="time" type="int" value="0"/>
						<component name="track_object" type="POINTER" value=""/>
						<component name="use_3d_tracking" type="bool" value="False"/>
						<component name="use_local_angular_velocity" type="bool" value="False"/>
						<component name="use_local_linear_velocity" type="bool" value="False"/>
						<component name="use_replace_display_mesh" type="bool" value="False"/>
						<component name="use_replace_physics_mesh" type="bool" value="False"/>
					</actuator>
					<actuator name="Visibility" type="VISIBILITY">
						<component name="apply_to_children" type="bool" value="False"/>
						<component name="use_occlusion" type="bool" value="False"/>
						<component name="use_visible" type="bool" value="True"/>
					</actuator>
					<actuator name="Shape Action" type="SHAPE_ACTION">
						<component name="frame_blend_in" type="int" value="0"/>
						<component name="frame_end" type="int" value="0"/>
						<component name="animation" type="str" value="*.explode"/>
						<component name="frame_start" type="int" value="0"/>
						<component name="mode" type="str" value="PLAY"/>
						<component name="property" type="str" value=""/>
						<component name="use_continue_last_frame" type="bool" value="False"/>
					</actuator>
				</actuators>
			</game>
			<entity actor="True" anisotropic_friction="False" damping_rot="0.10000000149" damping_trans="0.0399999991059" friction_x="1.0" friction_y="1.0" friction_z="1.0" ghost="False" inertia_tensor="0.40000000596" lock_rot_x="False" lock_rot_y="False" lock_rot_z="False" lock_trans_x="False" lock_trans_y="False" lock_trans_z="False" mass="1.0" mass_radius="1.0" meshFile="Monkey.mesh" name="Monkey" physics_type="RIGID_BODY" velocity_max="0.0" velocity_min="0.0"/>

```