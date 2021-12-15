# TS Config

This package contains the default `tsconfig.json` files for the [4s1 group](https://gitlab.com/4s1).

## Using

### Target: ES2020, Module: CommonJS

Create a `tsconfig.json` and insert:

```json
{
  "extends": "@4s1/ts-config/tsconfig-es2020-commonjs.json",
  "compilerOptions": {
    /* Basic Options */
    "outDir": "./dist",  /* Redirect output structure to the directory. */
    "rootDir": "./src",  /* Specify the root directory of input files. Use to control the output directory structure with --outDir. */
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

### Target: ES2020, Module: ES2020

Create a `tsconfig.json` and insert:

```json
{
  "extends": "@4s1/ts-config/tsconfig-es2020.json",
  "compilerOptions": {
    /* Basic Options */
    "outDir": "./dist",  /* Redirect output structure to the directory. */
    "rootDir": "./src",  /* Specify the root directory of input files. Use to control the output directory structure with --outDir. */
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

Append to `package.json`:

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

### React

Create a `tsconfig.json` and insert:

```json
{
  "extends": "@4s1/ts-config/tsconfig-react.json",
  "compilerOptions": {
  },
  "include": [
    "src"
  ]
}
```

## Additional dev config

Create a `tsconfig.dev.json` and insert:

```json
{
  "extends": "./tsconfig.json",
  "compilerOptions": {
    /* Additional Checks */
    "noUnusedLocals": false,     /* Report errors on unused locals. */
    "noUnusedParameters": false  /* Report errors on unused parameters. */
  }
}
```

Append to `package.json`:

```json
{
  "scripts": {
    "build": "rm -rf dist && tsc",
    "build:dev": "pnpm run build -- --project tsconfig.dev.json"
  }
}
```

## Prevent Prettier from formatting files

Create a `.prettierignore` and insert:

```text
/tsconfig*.json
```
