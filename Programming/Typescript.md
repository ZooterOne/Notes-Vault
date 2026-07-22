# Setup

## Manual

```
npm init
```

setup project with `package.json`.

```
npm install typescript @types/node --save-dev
npx tsc --init
```

install **Typescript** and setup with `tsconfig.json`.

### VSCode

Edit `tsconfig.json` and uncomment options for **NodeJS**. Make sure `sourceMap` is `true` for debugging.

**Transpiling**: `Ctrl+Shift+B` and select `tsc: build - tsconfig.json`.

**Debugging**: `Ctrl+Shift+D` and create a `launch.json` file. Add line `"preLaunchTask": "tsc: build - tsconfig.json",`.

## Vite

```
npm create vite@latest
```

setup a new project using **Vite**.

## Phaser

```
npm create @phaserjs/game@latest [project-name]
```

setup a new project using **Phaser**.

Edit `package.json` adding `"private": true` and removing unnecessary lines.

### VSCode

 - Edit `tsconfig.json` adding `"sourceMap": true` for debugging.
 - Add `Integrated Browser: Launch` to **Run And Debug** configuration for debugging.
 - **Terminal | Run Task** and select `npm: dev` to start the local development server.

## ESLint

```
npm install eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin --save-dev
npx eslint --init
```

install and setup **ESLint**.

```
npx eslint
```

run **ESLint** to check for errors.

```
npx eslint --fix
```

run **ESLint** to check for errors and fix fixable errors.

### VSCode

```
code --install-extension dbaeumer.vscode-eslint
```

install **VSCode** plugin.

## Terser

```
npm install terser --save-dev
```

install **Terser** minification tool.

```json
export default {
    build: {
        minify: 'terser',
        terserOptions: {
            format: {
                comments: false
            }
        }
    }
}
```

save as `vite.config.js` to enable **Terser** and remove comments.

# Packages

```
npm install
```

install all required packages (from `package.json`).

```
npm update
```

update all installed packages.

```
npm install <package>
```

install a new package.

```
npm install <package> --save-dev
```

install a new package for development only.

```
npm config get cache
```

get the path where the package cache is stored.

# Building and running

```
npm run dev
```

run the project.

```
npm run build
```

build the distributable folder (`dist`).