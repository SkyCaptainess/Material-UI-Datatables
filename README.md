<div align="center">
  <img src="https://user-images.githubusercontent.com/19170080/34070522-e15d32e2-e235-11e7-8af5-fa704cdcad56.png" />
</div>

# MUI-Datatables - Datatables for Material-UI

[![Build Status](https://travis-ci.org/gregnb/mui-datatables.svg?branch=master)](https://travis-ci.org/gregnb/mui-datatables)
[![Coverage Status](https://coveralls.io/repos/github/gregnb/mui-datatables/badge.svg?branch=master)](https://coveralls.io/github/gregnb/mui-datatables?branch=master)
[![dependencies Status](https://david-dm.org/gregnb/mui-datatables/status.svg)](https://david-dm.org/gregnb/mui-datatables)
[![npm version](https://badge.fury.io/js/mui-datatables.svg)](https://badge.fury.io/js/mui-datatables)

MUI-Datatables is a data tables component built on [Material-UI V1](https://www.material-ui-next.com).  It comes with features like filtering, view/hide columns, search, export to CSV download, printing, pagination, and sorting. On top of the ability to customize styling on most views, there are two responsive modes "stacked" and "scroll" for mobile/tablet devices. 

<div align="center">
	<img src="https://user-images.githubusercontent.com/19170080/34346996-b59a8b3a-e9cb-11e7-80d5-591aef3dc1f4.gif" />
</div>

## Install

`npm install mui-datatables --save`

## Demo

[![Edit react-to-print](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/wy2rl1nyzl)

## Usage

For a simple table:

```js

import MUIDataTable from "mui-datatables";

const columns = ["Name", "Company", "City", "State"];

const data = [
 ["Joe James", "Test Corp", "Yonkers", "NY"],
 ["John Walsh", "Test Corp", "Hartford", "CT"],
 ["Bob Herm", "Test Corp", "Tampa", "FL"],
 ["James Houston", "Test Corp", "Dallas", "TX"],
];

const options = {
  filterType: 'checkbox',
};

<MUIDataTable 
  title={"Employee List"} 
  data={data} 
  columns={columns} 
  options={options} 
/>

```

Or customize columns:

```js

import MUIDataTable from "mui-datatables";

const columns = [
 {
  name: "Name",
  options: {
   filter: true,
   sort: true,
  }
 },      
 {
  name: "Company",
  options: {
   filter: true,
   sort: false,
  }
 },
 {
  name: "City",
  options: {
   filter: true,
   sort: false,
  }
 },  
 {
  name: "State",
  options: {
   filter: true,
   sort: false,
  }
 },
];

const data = [
 ["Joe James", "Test Corp", "Yonkers", "NY"],
 ["John Walsh", "Test Corp", "Hartford", "CT"],
 ["Bob Herm", "Test Corp", "Tampa", "FL"],
 ["James Houston", "Test Corp", "Dallas", "TX"],
];

const options = {
  filterType: 'checkbox',
};

<MUIDataTable 
  title={"Employee List"} 
  data={data} 
  columns={columns} 
  options={options} 
/>

```

## API


#### &lt;MUIDataTable />

The component accepts the following props:

|Name|Type|Description
|:--:|:-----|:-----|
|**`title`**|array|Title used to caption table
|**`columns`**|array|Columns used to describe table. Must be either an array of simple strings or objects describing a column
|**`data`**|array|Data used to describe table. Must be an array of simple strings
|**`options`**|object|Options used to describe table

#### Options:
|Name|Type|Default|Description
|:--:|:-----|:--|:-----|
|**`filterType `**|string|'dropdown'|Choice of filtering view. Options are "checkbox" or "dropdown"
|**`pagination`**|boolean|true|Enable/disable pagination
|**`caseSensitive `**|boolean|false|Enable/disable case sensitivity for search
|**`responsive`**|string|'stacked'|Enable/disable responsive table views. Options: 'stacked', 'scroll'
|**`rowsPerPage`**|number|10|Number of rows allowed per page
|**`rowsPerPageOptions`**|array|[10,15,20]|Options to provide in pagination for number of rows a user can select
|**`rowHover`**|boolean|true|Enable/disable hover style over rows
|**`sortFilterList`**|boolean|true|Enable/disable filter list sort
|**`sort`**|boolean|true|Enable/disable sort on all columns
|**`filter`**|boolean|true|Show/hide filter icon from toolbar
|**`search`**|boolean|true|Show/hide search icon from toolbar
|**`print`**|boolean|true|Show/hide print	 icon from toolbar
|**`download`**|boolean|true|Show/hide download icon from toolbar

## Customize Columns

On each column object, you have the ability to customize columns to your liking with the 'options' property. Example:

```js
const columns = [
 {
  name: "Name",
  options: {
   filter: true,
   sort: false
  }
 },
 ...
];  
```

#### Column:
|Name|Type|Description
|:--:|:-----|:-----|
|**`Name`**|string|Name of column (This field is required)
|**`options`**|object|Options for customizing column


#### Column Options:
|Name|Type|Default|Description
|:--:|:-----|:--|:-----|
|**`filter`**|boolean|true|Display column in filter list
|**`sort`**|boolean|true|Enable/disable sorting on column

## Customize Styling

Using Material-UI theme overrides will allow you to customize styling to your liking. First, determine which component you would want to target and then lookup the override classname. Let's start with a simple example where we will change the background color of a body cell to be red:

```js
import React from "react";
import MUIDataTable from "mui-datatables";
import { createMuiTheme, MuiThemeProvider } from 'material-ui/styles';

class BodyCellExample extends React.Component {

  getMuiTheme = () => createMuiTheme({
    overrides: {
      MUIDataTableBodyCell: {
        root: {
          backgroundColor: "#FFF"
        }
      }
    }
  })

  render() {
  
    return (
      <MuiThemeProvider theme={this.getMuiTheme()}>
        <MUIDataTable title={"ACME Employee list"} data={data} columns={columns} options={options} />
      </MuiThemeProvider>
    );

  }
}

```


## License
The files included in this repository are licensed under the MIT license.
