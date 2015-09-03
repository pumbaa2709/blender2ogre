#version control and UUIDs.

An OgreDotScene loader can check the previous\_export\_time and compare it to a node's version\_control._modified_ attribute to see if the modified time is newer or older, and import or not based on that.  The time is in unix time, seconds from 1970.

UUIDs are generated for each object, and saved as an attribute on the "node" element.  UUIDs can also be synced with another blend file by exporting .scene from one, and loading the .scene from the other blend file (File->Import->Ogre3D).  Syncing of UUIDs by importing .scene is done by matching object names, other version control attributes are also copied (category, title, notes, owner).  This is also the starting point for an xmlrpc-system that talks directly to a Naali/Tundra server and exchanges UUID's and perhaps a real version control system with permissions, etc.


```
<scene export_time="(float)" exported_by="(string)" previous_export_time="(float)">
	<nodes>
		<node name="(string)" uuid="(string)">
			<version_control name="$VCTYPES" type="float | int | str" value="...">
			<version_control name="$VCTYPES" type="float | int | str" value="...">
			<version_control name="$VCTYPES" type="float | int | str" value="...">
			...
			<entity>
				<version_control name="$VCMESHTYPES" type="float | int | str" value="...">

$VCTYPES = _version_,  _modified_,  _created_, _category_,  _title_,  _notes_,  _owner_
$VCMESHTYPES = _update_mesh_, _update_material_

```