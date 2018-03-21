# Workbook Object (JavaScript API for Excel)

Workbook is the top level object which contains related workbook objects such as worksheets, tables, ranges, etc.

## Properties

| Property	   | Type	|Description| Req. Set|
|:---------------|:--------|:----------|:----|
|chartDataPointTrack|bool|True if all charts in the workbook are tracking the actual data points to which they are attached.|[1.9](../requirement-sets/excel-api-requirement-sets.md)|
|name|string|Gets the workbook name. Read-only.|[1.7](../requirement-sets/excel-api-requirement-sets.md)|
|readOnly|bool|True if the workbook is open in Read-only mode. Read-only.|[1.8](../requirement-sets/excel-api-requirement-sets.md)|
|saved|bool|True if no changes have been made to the specified workbook since it was last saved.|[1.8](../requirement-sets/excel-api-requirement-sets.md)|
|use1904DateSystem|bool|True if the workbook uses the 1904 date system.|[1.9](../requirement-sets/excel-api-requirement-sets.md)|
|usePrecisionAsDisplayed|bool|True if calculations in this workbook will be done using only the precision of the numbers as they're displayed.|[1.9](../requirement-sets/excel-api-requirement-sets.md)|

## Relationships
| Relationship | Type	|Description| Req. Set|
|:---------------|:--------|:----------|:----|
|application|[Application](application.md)|Represents the Excel application instance that contains this workbook. Read-only.|[1.1](../requirement-sets/excel-api-requirement-sets.md)|
|bindings|[BindingCollection](bindingcollection.md)|Represents a collection of bindings that are part of the workbook. Read-only.|[1.1](../requirement-sets/excel-api-requirement-sets.md)|
|customXmlParts|[CustomXmlPartCollection](customxmlpartcollection.md)|Represents the collection of custom XML parts contained by this workbook. Read-only.|[1.5](../requirement-sets/excel-api-requirement-sets.md)|
|dataConnections|[DataConnectionCollection](dataconnectioncollection.md)|Refreshes all data connections in the workbook. Read-only.|[1.7](../requirement-sets/excel-api-requirement-sets.md)|
|functions|[Functions](functions.md)|Represents a collection of worksheet functions that can be used for computation. Read-only.|[1.2](../requirement-sets/excel-api-requirement-sets.md)|
|internalTest|[InternalTest](internaltest.md)|For internal use only. Read-only.|[1.6](../requirement-sets/excel-api-requirement-sets.md)|
|names|[NamedItemCollection](nameditemcollection.md)|Represents a collection of workbook scoped named items (named ranges and constants). Read-only.|[1.1](../requirement-sets/excel-api-requirement-sets.md)|
|pivotTables|[PivotTableCollection](pivottablecollection.md)|Represents a collection of PivotTables associated with the workbook. Read-only.|[1.3](../requirement-sets/excel-api-requirement-sets.md)|
|properties|[DocumentProperties](documentproperties.md)|Gets the workbook properties. Read-only.|[1.7](../requirement-sets/excel-api-requirement-sets.md)|
|protection|[WorkbookProtection](workbookprotection.md)|Returns workbook protection object for a workbook. Read-only.|[1.7](../requirement-sets/excel-api-requirement-sets.md)|
|settings|[SettingCollection](settingcollection.md)|Represents a collection of Settings associated with the workbook. Read-only.|[1.4](../requirement-sets/excel-api-requirement-sets.md)|
|styles|[StyleCollection](stylecollection.md)|Represents a collection of styles associated with the workbook. Read-only.|[1.7](../requirement-sets/excel-api-requirement-sets.md)|
|tables|[TableCollection](tablecollection.md)|Represents a collection of tables associated with the workbook. Read-only.|[1.1](../requirement-sets/excel-api-requirement-sets.md)|
|worksheets|[WorksheetCollection](worksheetcollection.md)|Represents a collection of worksheets associated with the workbook. Read-only.|[1.1](../requirement-sets/excel-api-requirement-sets.md)|

## Methods

| Method		   | Return Type	|Description| Req. Set|
|:---------------|:--------|:----------|:----|
|[getActiveCell()](#getactivecell)|[Range](range.md)|Gets the currently active cell from the workbook.|[1.7](../requirement-sets/excel-api-requirement-sets.md)|
|[getIsActiveCollabSession()](#getisactivecollabsession)|bool|True if the workbook is being edited by multiple users (co-authoring). Read-only.|[1.9](../requirement-sets/excel-api-requirement-sets.md)|
|[getRange(address: string)](#getrangeaddress-string)|[Range](range.md)|Gets the range object specified by the address or name.|[1.9](../requirement-sets/excel-api-requirement-sets.md)|
|[getSelectedRange()](#getselectedrange)|[Range](range.md)|Gets the currently selected range from the workbook.|[1.1](../requirement-sets/excel-api-requirement-sets.md)|

## Method Details


### getActiveCell()
Gets the currently active cell from the workbook.

#### Syntax
```js
workbookObject.getActiveCell();
```

#### Parameters
None

#### Returns
[Range](range.md)

### getIsActiveCollabSession()
True if the workbook is being edited by multiple users (co-authoring). Read-only.

#### Syntax
```js
workbookObject.getIsActiveCollabSession();
```

#### Parameters
None

#### Returns
bool

### getRange(address: string)
Gets the range object specified by the address or name.

#### Syntax
```js
workbookObject.getRange(address);
```

#### Parameters
| Parameter	   | Type	|Description|
|:---------------|:--------|:----------|
|address|string|The address or the name of the range. If the sheet name is not specified, the currently-active worksheet is assumed.|

#### Returns
[Range](range.md)

### getSelectedRange()
Gets the currently selected range from the workbook.

#### Syntax
```js
workbookObject.getSelectedRange();
```

#### Parameters
None

#### Returns
[Range](range.md)

#### Examples

```js
Excel.run(function (ctx) { 
	var selectedRange = ctx.workbook.getSelectedRange();
	selectedRange.load('address');
	return ctx.sync().then(function() {
			console.log(selectedRange.address);
	});
}).catch(function(error) {
		console.log("Error: " + error);
		if (error instanceof OfficeExtension.Error) {
			console.log("Debug info: " + JSON.stringify(error.debugInfo));
		}
});
```