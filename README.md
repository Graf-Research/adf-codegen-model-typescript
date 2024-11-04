# Typescript Model - ADF Code Generator

Generator kode [ADF](https://github.com/Graf-Research/adf-core) untuk Model Interface Typescript.

**Modul ADF yang digunakan**

`Table` `Enum`

**Penggunaan CLI (Command Line)**

```bash
npx @graf-research/adf-codegen-model-typescript <file/url ADF> <folder output>
```

## Instalasi

```bash
npm install --save @graf-research/adf-codegen-model-typescript
```

## Fungsi

```typescript
import { Model } from "@graf-research/adf-core";

export type MapTSModelFilePath = {[key: string]: string};

export interface CodegenFileOutput {
  filename: string
  content: string
}

export interface ItemOutput {
  files: CodegenFileOutput[]
  map: MapTSModelFilePath
}

export interface Output {
  table: ItemOutput
  enum: ItemOutput
}

function TypescriptModel.compile(list_model: Model.Item[]): Output
```

Generator kode ini akan menghasilkan file dengan struktur folder sebagai berikut:

```
<folder output> --+-- ts-model --+-- table --+-- Model1.ts
                                 |           |   
                                 |           +-- ...
                                 |
                                 +-- enum --+-- Enum1.ts
                                            |
                                            +-- ...
```

### Contoh Terjemahan Kode

data.adf
```
table User {
  id bigint pk inc notnull
  fullname varchar(255) notnull
  username varchar(255)
  email varchar(255)
  phone_number varchar(255)
  password varchar(255) notnull
  created_at timestamp notnull
}
```

terjemahan ts-model
```typescript
export interface User {
  id: number
  fullname: string
  username?: string
  email?: string
  phone_number?: string
  password: string
  created_at: Date
}
```
