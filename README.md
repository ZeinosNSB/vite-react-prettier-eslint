# React + TypeScript + Vite + ESLint + Prettier

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules, Prettier format.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Expanding the ESLint configuration

This configuration is a minimal setup for ESLint and Prettier (I use IDE Webstorm to creat Vite+React+TypeScript project). You can expand it by adding more ESLint plugins and rules to enforce code quality and consistency. Here are some common ESLint plugins that you can add to the configuration:

Install Prettier and the ESLint plugins for Prettier:

```
npm install --save-dev prettier eslint-plugin-prettier eslint-config-prettier
```

Install ESlint plugin for React and React Hooks:

```
npm install --save-dev eslint-plugin-react eslint-plugin-react-hooks
```

Install Eslint plugin for automatically sort import statements in JavaScript or TypeScript code: 
```
npm install --save-dev eslint-plugin-simple-import-sort
```

Other optional plugins:
```
npm install --save-dev eslint-plugin-jsx-a11y
```
## Setup for ESlint and Prettier

Setup the ESLint configuration in `.eslintrc.js`:

```js
module.exports = {
  root: true,
  env: { browser: true, es2020: true },
  extends: [
    'eslint:recommended',
    'plugin:@typescript-eslint/recommended',
    'plugin:react-hooks/recommended',
    'plugin:prettier/recommended',
    'plugin:react/recommended',
  ],
  ignorePatterns: ['dist', '.eslintrc.cjs'],
  parser: '@typescript-eslint/parser',
  parserOptions: {
    ecmaFeatures: { jsx: true },
    ecmaVersion: 'latest',
    sourceType: 'module',
    project: ['./tsconfig.json', './tsconfig.node.json'],
    tsconfigRootDir: __dirname
  },
  settings: {
    react: {
      version: 'detect'
    },
    'import/resolver': {
      node: {
        paths: ['src'],
        extensions: ['.js', '.jsx', '.ts', '.tsx']
      }
    }
  },
  plugins: ['react-refresh', 'prettier', 'simple-import-sort'],
  rules: {
    'prettier/prettier': ['error', {}, { usePrettierrc: true }],
    'react/react-in-jsx-scope': 'off',
    'react/prop-types': 'off',
    'simple-import-sort/imports': 'error',
    'simple-import-sort/exports': 'error',
    '@typescript-eslint/explicit-function-return-type': 'off',
    'react-refresh/only-export-components': [
      'warn',
      { allowConstantExport: true }
    ]
  }
}
```
Setup for Prettier in `.prettierrc`:

```json
{
  "arrowParens": "always",
  "semi": false,
  "trailingComma": "none",
  "singleQuote": true,
  "printWidth": 90,
  "tabWidth": 2,
  "endOfLine": "auto",
  "bracketSpacing": true,
  "jsxBracketSameLine": false,
  "jsxSingleQuote": true
}
```

This setup will use the recommended ESLint rules for TypeScript, React, and React Hooks. It will also use the Prettier recommended rules and the simple-import-sort plugin to automatically sort import statements. 

> Reference: [TheSwordBreaker repo](https://github.com/TheSwordBreaker/vite-reactts-eslint-prettier)
