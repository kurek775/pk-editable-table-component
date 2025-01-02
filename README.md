# `pk-editable-table-component`

A lightweight, customizable, and editable React table component with built-in sorting, filtering, and validation.

---

## Features

- **Dynamic Rows**: Add and delete rows programmatically.
- **Editable Fields**: Supports toggling between read-only and editable modes.
- **Sorting & Filtering**: Easily sort and filter columns.
- **Validation**: Enforce required fields during input or submission.

---

## Installation

Install the component using npm or yarn:

```bash
npm install pk-editable-table-component
```

or

```bash
yarn add pk-editable-table-component
```

---

## Usage

Import the `Table` component into your project and pass the required props.

### Basic Example

```tsx
import React from "react";
import { Table } from "pk-editable-table-component";
import "pk-editable-table-component/dist/index.css";

const App = () => {
  const headers = [
    { columnLabel: "Id", key: "id", type: "number", disabled: true },
    { columnLabel: "Name", key: "name", type: "string", required: true },
    { columnLabel: "Age", key: "age", type: "number", required: true },
  ];

  const initialData = [
    { id: 1, name: "Alice", age: 25 },
    { id: 2, name: "Bob", age: 30 },
  ];

  const handleSubmit = (data) => {
    console.log("Submitted Data:", data);
  };

  return (
    <Table
      keyVal="id"
      headers={headers}
      initialData={initialData}
      onSubmit={handleSubmit}
      editable={true}
      actions={{ create: true, edit: true, delete: true }}
      text={{
        delete: "Remove",
        addRow: "Add New Row",
        submit: "Save Changes",
      }}
    />
  );
};

export default App;
```

---

## Props

| Prop          | Type                                         | Required | Default Value                                               | Description                                              |
| ------------- | -------------------------------------------- | -------- | ----------------------------------------------------------- | -------------------------------------------------------- |
| `keyVal`      | `string`                                     | Yes      | `undefined`                                                 | Unique key for each row in the table.                    |
| `headers`     | `HeaderConfig[]`                             | Yes      | `[]`                                                        | Defines the table headers and their properties.          |
| `initialData` | `Array<Record<string, any>>`                 | Yes      | `[]`                                                        | The initial data to populate the table.                  |
| `onSubmit`    | `(data: Array<Record<string, any>>) => void` | No       | `undefined`                                                 | Callback triggered when the form is submitted.           |
| `editable`    | `boolean`                                    | No       | `false`                                                     | Enables or disables editing of the table.                |
| `actions`     | `TableActions`                               | No       | `{ create: false, edit: true, delete: false }`              | Enables or disables row creation, editing, and deletion. |
| `text`        | `TextConfig`                                 | No       | `{ delete: "DELETE", addRow: "ADD ROW", submit: "SUBMIT" }` | Customizable text for buttons.                           |

---

## Types

### `HeaderConfig`

```ts
type HeaderConfig = {
  columnLabel: string; // Label for each column
  key: string; // Unique key for each column
  type: "string" | "number"; // Type of the data in the column
  disabled?: boolean; // Whether the column is editable
  required?: boolean; // Whether the field is required
};
```

### `TextConfig`

```ts
type TextConfig = {
  delete?: string; // Text for the delete button
  addRow?: string; // Text for the add row button
  submit?: string; // Text for the submit button
};
```

### `TableActions`

```ts
type TableActions = {
  create: boolean; // Enable or disable row creation
  edit: boolean; // Enable or disable row editing
  delete: boolean; // Enable or disable row deletion
};
```

---

## Advanced Example

With validation and dynamic behavior:

```tsx
import React, { useState } from "react";
import { Table } from "pk-editable-table-component";
import "pk-editable-table-component/dist/index.css";

const AdvancedTable = () => {
  const [data, setData] = useState([
    { id: 1, name: "John", age: 22 },
    { id: 2, name: "Jane", age: 28 },
  ]);

  const headers = [
    { key: "id", type: "number", disabled: true },
    { key: "name", type: "string", required: true },
    { key: "age", type: "number", required: true },
  ];

  const handleSubmit = (submittedData) => {
    console.log("Submitted Data:", submittedData);
    setData(submittedData);
  };

  return (
    <Table
      keyVal="id"
      headers={headers}
      initialData={data}
      onSubmit={handleSubmit}
      editable={true}
      actions={{ create: true, edit: true, delete: true }}
    />
  );
};

export default AdvancedTable;
```

---

## Contributing

Contributions are welcome! Please submit issues or pull requests for any improvements or bug fixes.

---
