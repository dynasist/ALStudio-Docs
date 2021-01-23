# PopOut Mode

Pop-out mode allows you to use AL Studio features in Visual Studio Code and external browser windows at the same time. This provides a real multi-window experience for users having multiple monitors.

## Setup

Settings are located under `Visual Studio Code / Gear Icon / Settings / Extensions / AL Studio / PopOut section`.

|Name|Desciprion|Default Value|
|----|----------|-------------|
|Default Browser|Default Browser to be opened in App Mode.|Microsoft Edge|
|Always Open as Tab|Always open new windows as tab on system default browser.|No|
|Custom Browser Launch Command|**Mandatory for MacOS platform**. Specify your own custom command line to launch popout browser window.\r\n{0} is the actual that will be substituted.|Empty|
|Unified Search Always External|Always open Unified Search in new window.|No|
|Table Fields Always External|Always open Table Fields in new window.|No|
|Translations Always External|Always open Translation Manager in new window.|No|
|Snapshots Always External|Always open AL Snapshots in new window.|No|
|ObjectViews Always External|Always open Object Viewers/Editors in new window. E.g. Table/Page Editor, Codeunit Viewer.|No|

## Usage

PopOut button is visible on the top-right corner (left to the app icon) of AL Studio screens that support this feature. 

By clicking on the button, either a new browser tab or a new window opens depending upon setting. 

> Default behaviour on Windows systems is to open Microsoft Edge/Google Chrome in app mode. Should this fail, as a fallback method, a new browser tab will be opened using the default browser.

When `* Always External` settings are set to `Yes`, the corresponsing screen will open in new window by default. 

For example, calling `AL Search` command will open a new window outside of Visual Studio Code but will not be shown within Visual Studio Code as an internal editor tab.

## Supported Screens

* AL Home
* Unified Search
* Table Fields
* Translation Manager
* Snapshots
* Table Editor
* Page Editor
* Enum Editor
* Codeunit Viewer
* Control Add-in Viewer
* Interface Viewer

## Supported Scenarios

### Generic multi-window usage
Each supported screen can be used in a standalone window that is movable to secondary monitors.

### Using Page Editor to compare visual layouts in multiple windows
You can open many page designs in separate windows to check layout or changes at the same time.

### Using multiple Unified Search / Table Field windows
You can open multiple windows to search for by different criterias and keeping the results at hand.

## Limitations
Some funcionality may work differently or may not be available in PopOut Mode. Funcionality depending on  Visual Studio Code features are executed in the connected Visual Studio Code window.

## Unsupported Scenarios

###  Undo PopOut
PopOut calls create new, independent instances of a view, therefore it has no direct relation to the specific internal editor tab in Visual Studio Code. Closing a PopOut window will not "move" the screen back to Visual Studio Code.


## See Also

[Official website](https://al.studio)

[Pricing](https://al.studio/pricing)

[Installation](./installation.md)

