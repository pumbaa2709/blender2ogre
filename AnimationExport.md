## Shape Animation ##
Also uses NLA-hijacking, see below.

## Armature Animation System | OgreDotSkeleton ##
> The OgreDotSkeleton (.skeleton) format supports multiple named tracks that can contain some or all of the bones of an armature.  This feature can be exploited by a game engine for segmenting and animation blending.  For example: lets say we want to animate the upper torso independently of the lower body while still using a single armature.  This can be done by hijacking the NLA of the armature.

> NLA Hijacking:
    * define an action and keyframe the bones you want to 'group', ie. key all the upper torso bones (if you want all bones, just put a single keyframe on the armature at object level)
    * import the action into the NLA
    * name the NLA strip (this becomes the track name in Ogre)
    * adjust the start and end frames of the strip(s)