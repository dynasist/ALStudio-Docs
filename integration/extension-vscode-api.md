
# External API for VSCode extension developers

AL Studio has a public API that is available for other VSCode extension developers.
This API is provided even in the Free version and can be re-used by free/opensource extensions free of charge, without purchasing license.

Main API functions:
```typescript
export interface IExternalAPIService {
    isWorkspaceScanned: boolean;
    onWorkspaceScanned: Function | undefined;
    getObjects(): Array<CollectorItemExternal>;
    getNextId(type: ALObjectType, projectNameOrFilePath: string): Promise<number>;
    getSymbolUri(type: ALObjectType, name: string, standardFormat: boolean): Uri | null;
    getALLanguageApiService(): IALLanguageApiService;
}
```

Complete type definitions are available on GitHub: https://github.com/dynasist/ALStudio/blob/master/extension.d.ts

## Properties

### isWorkspaceScanned (Property)

Indicates whether the initial workspace scanning has been finished.

#### **Syntax**
```typescript
isWorkspaceScanned: boolean;
```

### onWorkspaceScanned (Property)

Event fired when the initial workspace scanning is finished. You can subscribe to this event by assigning a simple function to it.

Example:
```typescript
alStudioAPI.onWorkspaceScanned = () => {
    console.log('Workspace has been scanned!');
}
```

#### **Syntax**
```typescript
onWorkspaceScanned: Function | undefined;
```

## Methods

### getObjects (Method)

Gets the complete set of objects collected from files and symbol packages. It containes Objects, EventPublishers and EventSubscribers as well.
This list is automatically maintained by AL Studio, calling *getObjects()* will always return the latest, updated set.

#### **Syntax**
```typescript 
getObjects(): Array<CollectorItemExternal>;
```

### getALLanguageApiService (Method)

Gets a simplified API reference for *AL Language Extension* itself.

#### **Syntax**
```typescript
getALLanguageApiService(): IALLanguageApiService;
```

### getSymbolUri (Method)

Gets generated preview URI for symbol objects. This can be used to manually show source code preview window of specific symbols.

#### **Syntax**

```typescript
getSymbolUri(type: ALObjectType, name: string, standardFormat: boolean = false): Uri | null;
```

### getNextId (Method)

Gets the next available object ID for the given object type in the specified Application name or file path. 
`projectNameOrFilePath` can be an:
1. App name exactly how it is defined in `app.json`, e.g. `Base Application`
2. Absolute filepath of any object within an app folder
3. Absolute filepath of the app folder
4. Absolute filepath of the app.json file

In latter case, the proper `app.json` will be implicitly search for.

#### **Syntax**

```typescript
getNextId(type: ALObjectType, projectNameOrFilePath: string): Promise<number>;
```

## Getting an AL Studio API reference in another VSCode extension:

See below example how to get our API reference in your extension. This sample is placed in the extension loading process, e.g. `activate` function in `extension.ts`. However, you may get a reference later on demand as well.

```typescript

// extension.ts

import { extensions } from 'vscode';

export async function activate(context: ExtensionContext) {
    // you code...

    let alStudioAPI = await getAlStudioAPI();
}

async function getAlStudioAPI() {
    let alStudio: Extension<any> = extensions.getExtension('dynasist.al-studio')!;
    if (alStudio) {
        if (!alStudio.isActive) {
            await alStudio.activate();
        }

        return alStudio.exports;
    }
}

```


## See Also

[Visual Studio Code - Extension API](https://code.visualstudio.com/api)

[Visual Studio Code - Extension Get Started](https://code.visualstudio.com/api/get-started/your-first-extension)