# Bloodthief Mapping Guide
This guide is meant to be used like a wiki for you to reference for all your mapping needs. Trenchbroom is the software that is used to make Bloodthief maps. It is free, open source, and used to make maps for many games, such as Quake, Dusk, Wrath: Aeon of Ruin, and many more. Trenchbroom is great because it’s specifically designed for making interactive maps, which makes getting started making a real level easy, but the possibilities are still limitless!

## Get Started
* [Watch the official get started tutorial](https://youtu.be/09mth4fUaH0)
* [Bloodthief mapping assets](https://drive.google.com/file/d/1IHrSjtdWp4tyQuInjpUgVuiSBSwXTLnh/view?usp=drive_link)
* [Example Map - Time Tomb](https://drive.google.com/file/d/1ug1_SbQ-79RKrOdk9USPT0Q1SCSGNpa7/view?usp=drive_link)
* [Trenchbroom Manual](https://trenchbroom.github.io/manual/latest/)
* [Dumptruck_ds Trenchbroom Tutorial Series](https://www.youtube.com/watch?v=gONePWocbqA&list=PLgDKRPte5Y0AZ_K_PZbWbgBAEt5xf74aE&index=1)
* [Entity Reference](entity-reference.md)

## Pro Tips
### Clip Textures and Water
Water and lava are prone to weird visual artifacts. You can prevent this by clipping the top/exposed parts of the water or lava. You can do this by making the whole brush a clip brush, then shift-clicking the faces you want to make the water texture, and selecting the water texture.

You will use the clip texture a lot. I assigned a hotkey so I don’t have to find the clip texture every time I need to apply it to something. Go to view -> preferences -> keyboard and find “Tags/turn selection into Clip” and assign that to your key of choice. I used backtick (`).



## FAQs

### Random parts of my map stopped working for no reason
* This issue is usually caused by empty properties in various entities. For example, if one of your entities has “property 1” in it, you should remove that. Sometimes this can happen if you hit the plus sign to add a property and forget to remove it later. If you suspect this could be the issue you can hit ctrl + A to select all entities and look at the properties panel to see if you see any strange / bad looking properties in your entire map.

### Geometry / Meshes becoming invisible behind materials with transparency
* This is due to occlusion culling. The mesh in front is culling the mesh behind. If you don’t want the mesh in front to do any culling, make it a func_detail or func_detail_illusionary


### How do I delete my own custom maps?
* Just delete the folder. Then go to Steam Workshop and delete the workshop entry.
