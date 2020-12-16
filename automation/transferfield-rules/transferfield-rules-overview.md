# Transferfield Rules

text...

## Transferfield validation by ruleset definition

Ensure the integrity of Transferfields rules using validation json definitions per extensions.

![](https://raw.githubusercontent.com/dynasist/ALStudio/master/media/ALStudio_CLI2.png)

**Parameters:**

`-w, --workspaces` : input folder of projects. 

It can be a single path or a comma-separated list of paths. In case of many apps within a main folder, specifying the main folder path is sufficient.

`o, --output` : path to save the validation result json file (optional).

You need to specify the complete path including filename.

**Validation Rules:**

Validation works using ruleset files named `transferfields.rules.json` that are placed into the root of each app folder. You can define rules per app.

```json
[
    {
        "Name": "Custom Table Transferfields",
        "Source": "MySalesTable",
        "Fields": [
            {
                "Id": 1,
                "Requirement": 2
            },
            {
                "Id": 2,
                "Requirement": 2
            },
            {
                "Id": 3,
                "Requirement": 2
            },
            {
                "Id": 5,
                "Requirement": 1
            }
        ],
        "Destinations": [
            "MySalesTargetTable1",
            "MySalesTargetTable2"
        ],
        "ErrorAction": 2
    }
]
```

Fields that are not listed in **Fields** member will still be validated using `Default` requirement type.


*Requirement values:*

|Value|Name|Description|
|-----|----|-----------|
|0|Default|Standard behaviour is validated only, e.g. Field Type match|
|1|MustOmit|Specifies that a field must not be present in related tables|
|2|Required|Specifies that a field must be present in related tables|

*ErrorAction values:*

|Value|Name|Description|
|-----|----|-----------|
|0|None|Validation is turned off.|
|1|Warning|Validation result only create output as warning, with ExitCode 0|
|2|Error|Validation runs normally with ExitCode 0/1 depending on result|


**Validation result:**

Result is displayed on command line output and also can be saved into a json file.
* Successful validation returns ExitCode 0. 
* Failure returns ExitCode 1, so in DevOps it will break the build.

![](https://raw.githubusercontent.com/dynasist/ALStudio/master/media/alstudio_transferfields.png)



## See Also

[link](#link)