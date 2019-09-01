Why dos TSLint only checks src directory?

tsconfig.json

```json
{
    "compilerOptions": {
        "outDir": "./built",
        "allowJs": true,
        "target": "es5",
        "typeRoots": ["node_modules/@types", "typings"]
    },
    "include": ["./src/**/*", "./typings/**/*"],
    "exclude": ["node_modules"]
}
```

tslint.json

```json
{
    "defaultSeverity": "error",
    "extends": [
        "tslint:recommended"
    ],
    "jsRules": {},
    "rules": {},
    "rulesDirectory": []
}
```

#### Check the whole project

it only shows errors of src directory

```bash
tslint --project .

ERROR: /Users/kiwenlau/Desktop/tslint-test/src/index.ts:1:1 - Forbidden 'var' keyword, use 'let' or 'const' instead
```

#### Check src directory

```bash
tslint "src/**/*"

ERROR: src/index.ts:1:1 - Forbidden 'var' keyword, use 'let' or 'const' instead
```

#### Check typings directory

```bash
tslint "typings/**/*"

ERROR: typings/index.d.ts:1:11 - interface name must start with a capitalized I
```