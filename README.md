# FreeCAD Assembly 4 workbench

Current version 0.9.0, 2020-04-17




## Overview

This assembly workbench allows to integrate into a single container under a single coordinate system other FreeCAD objects and place them relative to the assembly and to each-other. The principle of Assembly4 is that `App::Part` and `PartDesign::Body` container objects are linked into a host parent assembly called _Model_ and of type `App::Part` using the `App::Link` interface introduced in FreeCAD v0.19. The parts that are linked can invariably be in the same document as the assembly or an external document.

As an Assembly4 model is a standard FreeCAD `App::Part` object, it can be used and manipulated with any FreeCAD tool handling `App::Part` objects. In particular, it can be inserted into another Assembly4 _Model_ to create nested assemblies. It can also contain solids and datum objects. An Assembly4 _Model_ can be a stand-alone part, an assembly, a sub-assembly, and any combinations of these.

Parts and linked parts are placed to each-other in the host parent assembly by matching their Datum Coordinate Systems (`PartDesign::CoordinateSystem` called LCS for Local Coordinate System) using the built-in FreeCAD *ExpressionEngine.* No geometry is used to place and constrain parts relative to each other, thus avoiding a lot of the topological naming problems. 


![](Resources/media/Asm4_wb1.png)


**Please Note:** objects in the same document as the linked part but outside the `App::Part` container will **not** be inserted.

**Please Note:** only _Part_ and _Body_ containers at the root of a document can be inserted. Objects inside containers cannot be used directly by Assembly 4. 



## Installation

[![FreeCAD Addon manager status](https://img.shields.io/badge/FreeCAD%20addon%20manager-available-brightgreen)](https://github.com/FreeCAD/FreeCAD-addons)

### Addon Manager (recommended)

Assembly 4 is available through the FreeCAD Addon Manager (menu **Tools > Addon Manager**). It is called _Assembly4_ in the Addon Repository.  

**Important Note:** Assembly 4 is **not** compatible with FreeCAD v0.18 and before, needs FreeCAD >= `v0.19.18353` . Pre-built binaries on the v0.19 development branch can be found [here](https://github.com/FreeCAD/FreeCAD/releases/tag/0.19_pre)




## Getting Started

You can get more information in the [user instructions](INSTRUCTIONS.md), the [technical manual](TECHMANUAL.md), and you can use the provided [example assemblies](https://github.com/Zolko-123/FreeCAD_Examples) to experiment with this workbench's features. There are also online tutorials :

* [a quick assembly from scratch](https://github.com/Zolko-123/FreeCAD_Examples/blob/master/Asm4_Tutorial1/README.md)
* [a cinematic assembly in one file, using a master sketch](https://github.com/Zolko-123/FreeCAD_Examples/blob/master/Asm4_Tutorial2/README.md)
* [a Lego assembly](https://github.com/Zolko-123/FreeCAD_Examples/blob/master/Asm4_Tutorial3/README.md)
* [Some examples to play with](https://github.com/Zolko-123/FreeCAD_Examples)







## Release notes

* 2020.04.15 (**0.9.0**) :  
PartDesign::Body can be directly imported (linked), no need to wrap them in App::Part container  

* 2020.03.15 (**version 0.8.1**) :  
Added slider for animation  
Reversed Document#Label (Name) to Document#Name (Label)  

* 2020.02.13 (**version 0.8.0**) :  
All dialogs are now resizable  
Various bugfixes  
Made the Asm4 properties of all objects homogeneous  
Moved examples and tutorials to dedicated repository (some users ran into trouble for updating the WB because they had modified the local files)  

* 2020.01.25 (**version 0.7.12**) :  
Refined datum and variables creation  

* 2020.01.22 (**version 0.7.11**) :  
Added version info to the Help dialog  

* 2020.01.21 (**version 0.7.10**) :  
bug-fix to not fall for random criss-cross linking of objects  

* 2020.01.20 (**version 0.7.9**) :  
(silly) bug-fix  

* 2020.01.18 (**version 0.7.8**) :  
added "release attachments" button  
various small fixes

* 2020.01.06 (**version 0.7.7**) :  
Moved the turorials to the Resources directory  
import libAsm4 as Asm4  
Added a Help command (dummy placeholder)  
Ported example2 to the latest Asm4 format

* 2019.12.12 (**version 0.7.6**) :  
Improved animation and datum import.

* 2019.12.02 (**version 0.7.5**) :  
Minor (but useful !) refinements for variables and animation.

* 2019.11.24 (**version 0.7.4**) :  
Added Animation command

* 2019.11.19 (**version 0.7.3**) :  
Added linkArray, a wrapper for Draft::LinkArray  
Fixes for the Fasteners command

* 2019.11.14 (**version 0.7.2**) :  
Bug-fix for importDatum  

* 2019.11.11 (**version 0.7.1**) :  
Bug-fix  

* 2019.11.05 (**version 0.7.0**) :  
Support for screws & nuts from the Fasteners workbench  
Added Variables to the Model  
The model file format has changed, former assembly models can be opened but must be re-assembled.

* 2019.10.11 (**version 0.6.4**) :  
Improved assembly in single file  
Various small fixes

* 2019.10.11 (**version 0.6.3**) :  
It is now possible to link parts from the same document as the assembly itself, allowing to make 1-file assemblies and still use all the other tools.

* 2019.10.11 (**version 0.6.2**) :  
Added page for Tutorial 1.  
Fine-tuned some functions  
Renamed icons in a consistent way  

* 2019.10.07 (**version 0.6.1**) :  
Moved the code that was in Mod_Asm4 to the root, to be compatible with the FreeCAD AddonManager

* 2019.10.05 (**version 0.6**) :  
Ported to FreeCAD-v0.19-pre, with new syntax for the ExpressionEngine

* 2019.07.23 (**version 0.5.5**) :  
Fixed a bug in partLCSlist.findItems  
New Datum Point in the Model

* 2019.07.18 (**version 0.5.4**) :  
A cosmetic update to fix a 25 year old Windows bug:  
some UTF-8 characters in the comments were not accepted on some Windows 10 machines

* 2019.06.15 (**version 0.5.3**) :  
Now the LCS can be renamed, and they show up in the LCS list in the command placeLink as such.  
It's only visual, the ExpressionEngine still uses the LCS.Name though

* 2019.05.07 (**version 0.5.2**) :  
added insertDatumCmd

* 2019.03.18 (**version 0.5.1**) :  
Part can now be linked without being placed: this is then a raw interface with App::Link  
The instance can be moved manually with the 'Transform' dragger

* 2019.03.12 (**version 0.5**) :  
moved the actual code to Mod_Asm4

* 2019.03.11 (**version 0.4.1**) :  
Added placement of Datum Point

* 2019.03.09 (**version 0.4**) :  
FreeCAD now imports as App  
insert_Link launches place_Link

* 2019.03.05 (**version 0.3.1**) :  
added the RotX-Y-Z buttons

* 2019.02.20 (**version 0.3**)  
mostly working version

* 2019.02.18 (**version 0.1**) :  
initial release of Assembly 4 WB



## Discussion
Please offer feedback or connect with the developers in the [dedicated FreeCAD forum thread](https://forum.freecadweb.org/viewtopic.php?f=20&t=34806).



## Addon Repository
This addon is hosted on a [GitHub repository](https://github.com/Zolko-123/FreeCAD_Assembly4). 



## License

LGPLv2.1 (see [LICENSE](LICENSE))
