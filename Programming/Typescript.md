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

## ESLint

```
npm install eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin --save-dev
npx eslint --init
```

install and setup **ESLint**.

```
npm run lint
```

run **ESLint** to check for errors.

```
npm run lint:fix
```

run **ESLint** to check for errors and fix fixable errors.

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