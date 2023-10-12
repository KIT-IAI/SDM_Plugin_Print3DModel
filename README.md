# Print3DModel
The Print3DModel module allows the user to make changes to the IFC file and prepare it for small scale 3D printing. Through this plugin it is possible to filter elements and standard properties from the IFC and perform a model validation based on the selected scale and available printer capacity. The printable (${\color{green}in}$ ${\color{green}green}$) and problematic (${\color{red}in}$ ${\color{red}red}$) elements are identified for a preview of the final results of the printed model.

## User Interface Features
The user interface was made with the aid of [wxFormBuilder](https://github.com/wxFormBuilder/wxFormBuilder).

### IFC Elements
* Model Type
   <br />Pre-defined filter for model element's type based on target use case. Initialized with "Default". Model types can be edited and current choices will be saved for future use.

* Filter elements
   <br />Select and deselect target enitites for current work.

* Property
   <br />Selected elements can be filtered throught the IFC standard properties "isExternal" and/or "LoadBearing".

### Details
Select level of detail for windows and doors.

### Visualization
#### Elements

|Radio button          |Description          |
|:---          |:---          |
|Chosen            |Show the current selected elements.          |
|Inverted          |Show the elements that have not been selected.          |
|All          |Show all the model's entities.          |

#### Colors

|Radio button          |Description |
|:---          |:--- |
|Color by Default            |Show the model with default colors defined by entity's type. |
|Color by Entity          |Show the model with colors attributed to entity. |
|Unicolor          |Show model with selected color. |

### Printing Preparation
* Scale
   <br /> Select scale that the model will be scaled down in the viewer.

* Printer
 <br /> Select printer with its capacity. The printer settings will be used for the model validation.


|Attribute          |Description |Type  |
|:---          |:--- |:---          |
|Name            |Name of the printer. |string  |
|Max. Length            |max. length of the printer's printing plate in centimeter. |integer  |
|Max. Height            |max. height of the printer's printing plate in centimeter. |integer  |
|Min. Thickness            |nozzle size of the printer in milimeter. |float  |

### Model Checking
Run a model validation for the scaled model with the printer's parameters. Analyse resulting height, legth, thickness and solidity of each element.

### Export
* Problematic Elements

|Choice          |Description |
|:---          |:--- |
|Ignore error report            |Ignore report of problematic elements and export IFC file as it is. |
|Exclude elements            |Exclude problematic elements from model. |
|Correct elements            |Attempt to correct problematic elements. Applicable only in specific scenarios. |

* Save Building storey separately
 <br />  Separate the IFC file per storey and introduce automatically auxiliary geometry to facilitate post-printing assembly.

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

