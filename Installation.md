# Installing the Addon #
  * You can simply copy io\_export\_ogreDotScene.py to your blender installation under blender/2.61/scripts/addons/
  * Or you can use blenders interface, under user-prefs, click addons, and click 'install-addon'
  * then you have to enable the addon under user-prefs


## Dependencies ##
### Required ###
  1. blender2.6
  1. Install Ogre Command Line tools to the default path (C:\\OgreCommandLineTools)
    * http://www.ogre3d.org/download/tools
    * (Linux users may use Wine, build from source, or apt-get ogre-tools)
    * OSX: [NightElf's OSX Guide](http://www.ogre3d.org/forums/viewtopic.php?f=4&t=61485&start=175#p431851)

### Optional: ###
  1. Install NVIDIA DDS Tools
    * [NVIDIA\_Texture\_Tools\_x64\_2.08.0601.1625.exe](http://developer.nvidia.com/sites/default/files/akamai/tools/files/NVIDIA_Texture_Tools_x64_2.08.0601.1625.exe)
    * **version 2.08 is old** if you have problems, compile from source:
```
svn checkout http://nvidia-texture-tools.googlecode.com/svn/trunk/ nvidia-texture-tools-read-only
```

  1. Install Image Magick
    * http://www.imagemagick.org
  1. OgreMeshy
    * http://ogremeshy.sourceforge.net/
  1. RealXtend
    * http://realxtend.wordpress.com/