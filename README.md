# Print3DModel
The Print3DModel module is a plugin for the [KITModelViewer](https://github.com/KIT-IAI/SDM_KITModelViewer) and allows the user to make changes to the IFC file and prepare it for small scale 3D printing. Through this plugin it is possible to filter elements and standard properties from the IFC and perform a model validation based on the selected scale and available printer capacity. The printable (${\color{green}in}$ ${\color{green}green}$) and problematic (${\color{red}in}$ ${\color{red}red}$) elements are identified for a preview of the final results of the printed model.

For more details: [3D Printing of BIM Model - Thesis](https://github.com/KIT-IAI/SDM_Plugin_Print3DModel/blob/main/3DPofBIMModel.pdf).

In procedings of 34. Forum Bauinformatik:  
[Conceptual planning and implementation of an automated workflow in scaled 3D printing with the aim of generating printable models from BIM data](https://doi.org/10.13154/294-10113)

## User Interface
The user interface is based on [wxWidgets](https://www.wxwidgets.org/) and was made with [wxFormBuilder](https://github.com/wxFormBuilder/wxFormBuilder).

### IFC Elements

<p align="center">
<img src="https://github.com/KIT-IAI/SDM_Plugin_Print3DModel/assets/74645544/24bab9a9-5b8a-44d5-8d27-c0cb9c231e38">
</p>

* Model Type
   <br />Pre-defined filter for model element's type based on target use case. Initialized with "Default". Model types can be edited and current choices will be saved for future use.
  <p align="center">
  <img src="https://github.com/KIT-IAI/SDM_Plugin_Print3DModel/assets/74645544/d2591a84-b35b-4e6f-864e-7622ad5924c1">
</p>

* Filter elements
   <br />Select and deselect target enitites for current work.
  <p align="center">
  <img src="https://github.com/KIT-IAI/SDM_Plugin_Print3DModel/assets/74645544/070ffc2d-3400-49e8-985b-45967571c02c">
</p>

* Property
   <br />Selected elements can be filtered throught the IFC standard properties "isExternal" and/or "LoadBearing".

### Details
<p align="center">
<img src="https://github.com/KIT-IAI/SDM_Plugin_Print3DModel/assets/74645544/63da2e92-89d6-46a0-bb24-a5b580b22b8c">
</p>

Select level of detail for windows and doors.
  
|"Detailed"          |"Simplified"          |
|:---          |:---          |
|![image](https://github.com/KIT-IAI/SDM_Plugin_Print3DModel/assets/74645544/1cc68f91-5ab9-4161-b3a9-d9ac4f5ddfce)| ![image](https://github.com/KIT-IAI/SDM_Plugin_Print3DModel/assets/74645544/ec04f298-7c27-43db-9b4e-1369533070ce)|


### Visualization
<p align="center">
<img src="https://github.com/KIT-IAI/SDM_Plugin_Print3DModel/assets/74645544/c566ce7a-bcc2-4af6-91b5-7c5d2bafd5ac">
</p>

#### Elements

|Radio button          |Description          |
|:---          |:---          |
|<img width="200" height="150" src="https://github.com/KIT-IAI/SDM_Plugin_Print3DModel/assets/74645544/02120ec4-834a-4594-8f86-d4d3e788e7af"> <br /> "Chosen"  |Show the current selected elements.          |
|<img width="200" height="150" src="https://github.com/KIT-IAI/SDM_Plugin_Print3DModel/assets/74645544/9ea34eb1-0dc3-4ab2-943f-1c88b56abb31"> <br />"Inverted" |Show the elements that have not been selected.          |
|<img width="200" height="150" src="https://github.com/KIT-IAI/SDM_Plugin_Print3DModel/assets/74645544/658d6165-6af2-4673-9701-fc89bd967307"> <br />"All"      |Show all the model's entities.          |

#### Colors

|Radio button          |Description |
|:---          |:--- |
|<img width="200" height="150" src="https://github.com/KIT-IAI/SDM_Plugin_Print3DModel/assets/74645544/a12bf890-fdad-4ca0-9d0f-c7a5456d6571"> <br /> "Color by Default"  |Show the model with default colors defined by entity's type. |
|<img width="200" height="150" src="https://github.com/KIT-IAI/SDM_Plugin_Print3DModel/assets/74645544/61f74a63-e7d6-4940-8c3c-055e88dbbd1f"> <br /> "Color by Entity"   |Show the model with colors attributed to entity. |
|<img width="200" height="150" src="https://github.com/KIT-IAI/SDM_Plugin_Print3DModel/assets/74645544/27766fc9-26f7-44ee-bc50-cf5541fe134a"> <br /> "Unicolor"          |Show model with selected color. |

### Printing Preparation
<p align="center">
<img src="https://github.com/KIT-IAI/SDM_Plugin_Print3DModel/assets/74645544/100bef86-4f93-4fe2-9c49-4b1fdd5a3c14">
</p>

* Scale
   <br /> Select scale that the model will be scaled down in the viewer.

* Printer
 <br /> Select printer with its capacity. The printer settings can be edited and will be used for the model validation.
<p align="center">
<img src="https://github.com/KIT-IAI/SDM_Plugin_Print3DModel/assets/74645544/0f2a08b4-6085-4602-a652-b37335a30171">
</p>


* Name
<br/>Name of the printer.

* Max. Length
<br/>Maximum length of the printer's printing plate in centimeter.

* Max. Height
<br/>Maximum height of the printer's assembly space in centimeter.

* Min. Thickness
<br/>Nozzle size of the printer in milimeter.

### Model Checking
   <p align="center">
   <img src="https://github.com/KIT-IAI/SDM_Plugin_Print3DModel/assets/74645544/e5163f01-ced0-4160-82e9-36289e9df81a">
   </p>
   
Run a model validation for the scaled model with the printer's parameters. Analyse resulting height, legth, thickness and solidity of each element. The printable (${\color{green}in}$ ${\color{green}green}$) and problematic (${\color{red}in}$ ${\color{red}red}$) elements are displayed as well as a printing plate (${\color{magenta}in}$ ${\color{magenta}magenta}$) based on the printer settings.

   <p align="center">
      <img src="https://github.com/KIT-IAI/SDM_Plugin_Print3DModel/assets/74645544/24968a9b-1b16-41f4-923c-3abec68dc775">
      <img src="https://github.com/KIT-IAI/SDM_Plugin_Print3DModel/assets/74645544/f166cddf-a432-4901-bc7a-7b1f2be31da1">
   </p>

### Export
<p align="center">
<img src="https://github.com/KIT-IAI/SDM_Plugin_Print3DModel/assets/74645544/56ae0130-cde3-4e77-a5b8-1bc3a0503ffb">
</p>

* Problematic Elements

|Choice          |Description |
|:---          |:--- |
|Ignore error report            |Ignore report of problematic elements and export IFC file as it is. |
|Exclude elements            |Exclude problematic elements from model. |
|Correct elements            |Attempt to correct problematic elements. Applicable only in specific scenarios. |

* Save Building storey separately
 <br />  Separate the IFC file per storey and introduce automatically auxiliary geometry to facilitate post-printing assembly.
<p align="center">
  <img width="400" height="300" src="https://github.com/KIT-IAI/SDM_Plugin_Print3DModel/assets/74645544/f55ff1f6-3631-4b98-8dd3-25c1d1d7fa37">
</p>

* Save
 <br />  Convert resulting IFC file into a preferred 3D printable file format (ASCII or binary *.stl, *.3mg, *.obj).

## Document

### Print3DModel: Methods
|Method          |Description          |
|:---          |:---          |
|buildElementList()            |Get IFC data from viewer and fill "Elements" parameter. |
|updateElements()            |Update viewer with selection of entities and/or visualization. |
|chooseOpening()            |Change ParametricDoorWindow to Simplified or Detailed. Update viewer with selection of "Details". |
|changeScale(scale)            |Scale elements to selected in "Printing Preparation". |
|checkModel(min.Thickness, scale)            |Model validation for solidity and minimum thickness. It saves problematic elements. |
|checkMeasurements(maxLenght, maxHeight)            |Model validation for max. lenght and max. height. |
|getPrintingPlate(maxLenght)            |Add printing plate to viewer with printer settings information. |
|checkModel(min.Thickness, scale)            |Model validation for solidity and minimum thickness. |
|correctProblematicElements()            |Correct problematic elements for specific cases. |
|FileSaveFeature(fileformat, name)            |Save printable file for model or each storey. |


### Print3DParameter
|Parameter          |Description |Type  |
|:---          |:--- |:--- |
|Elements            |Contains all element types and their entities with selection information. Identified by the entity's type name. |struct  |
|Problematic Elements            |List with oid of entities that were problematic for printing. |integer  |
|Separated            |Model is to be saved separated by storey. |bool  |
|isExternal            |Filter "isExternal" standard property. |bool  |
|loaded            |Filter "LoadBearing" standard property. |bool  |

#### Elements struct
|Attribute          |Description          |Type  |
|:---          |:---          |:---          |
|Name            |Name of entity's Type (Example: "IfcWall"). |string  |
|Selection            |Identify if user selected current type. |bool  |
|Subelements            |List with all entities of current type identified by oid. |struct  |

##### Subelements struct
|Attribute         |Description          |Type  |
|:---          |:---          |:---          |
|Oid            |Objekt ID  |integer  |
|Name            |Name of Entity |string  |
|Selection            |Identify if user selected current entity |bool  |
|Id            |Global ID |integer  |

### Model Types
|Attribute          |Description |Type  |
|:---          |:--- |:---          |
|Name            |Name of model type |string  |
|Entity Type List            |List of the names of the entity types for the current model type ("IfcWall", "IfcWindow", etc.) |string  |

## Dependencies

### Use of vcpkg:

|Package Name         |Install Command                            |
|:---                 |:---                                       |
|wxwidgets            |vcpkg install wxwidgets triplet=x64-windows|

## How to cite
```bibtex
@inproceedings{Lourenzi.2023,
   author       = {Shuchen Di, Fernanda Lourenzi, Andreas Geiger, Karl-Heinz Häfele, Svenja Lauble},
   title        = {Conceptual planning and implementation of an automated workflow in scaled 3D printing with the aim of generating printable models from BIM data},
   pages        = {209-216},
   publisher    = {{Ruhr University of Bochum}},
   editor       = {Sigalov, K. and Hagedorn, P. and Schönfelder, P. and Faltin, B. and Zentgraf, S. and Block, M.},
   booktitle    = {Proceedings of 34. Forum Bauinformatik},
   year         = {2023}
}

@software{Print3DModel,
   title        = {Print3DModel},
   author       = {{Fernanda Lourenzi}},
   url          = {https://github.com/KIT-IAI/SDM_Plugin_Print3DModel},
   date         = {2023}
}
```
