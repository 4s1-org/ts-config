# TS Config

## Target: ES2020, Module: ES2020

Create a **tsconfig.json** and insert:

```json
{
  "extends": "@4s1/ts-config/tsconfig-es2020-es2020.json",
  "compilerOptions": {
    /* Basic Options */
    "outDir": "./dist",     /* Redirect output structure to the directory. */
    "rootDir": "./src",     /* Specify the root directory of input files. Use to control the output directory structure with --outDir. */
  },
  "include": [
    "src/**/*.ts"
  ],
  "exclude": [
    "src/**/*.spec.ts",
    "node_modules/"
  ]
}
```

Append to **package.json**:

```json
{
  "type": "module",
  "main": "./dist/index.js",
  "exports": "./dist/index.js",
  "typings": "./dist/index.d.ts",
  "files": [
    "dist/"
  ]
}
```

## Additional dev config

Create a **tsconfig.dev.json** and insert:

```json
{
  "extends": "./tsconfig.json",
  "compilerOptions": {
    /* Additional Checks */
    "noUnusedLocals": false,        /* Report errors on unused locals. */
    "noUnusedParameters": false     /* Report errors on unused parameters. */
  }
}
```

Append to **package.json**:

```json
{
  "scripts": {
    "build": "tsc",
    "build:dev": "tsc --project tsconfig.dev.json"
  }
}
```