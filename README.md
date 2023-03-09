# Description

There are many tools that need to be set up in a project, like linters, formatters, testing libraries, Docker files and UML processors, which can be a pretty long task. Therefore, the React-Typescript skeleton. The base React-Typescript files were created with [Vitejs](https://vitejs.dev/) and a few extras were added.

# Pre-requisites

- git
- docker
- docker-compose

# Getting started

## Install dependencies locally

### Docker Command Line Interface (dcli)

### Steps to install dependencies locally

## How to override files

# Add-ons

## ESLint

There are a couple of ways to run ESLint on the project. The first option is to run the following command:

```bash
$ npm run lint
```

The second option doesn't need a command. There are git hooks installed that will lint every `.ts` and `.tsx` file in the project before any commit.

## Prettier

Prettier can also be run in multiple ways. The first option is to use the following command:

```bash
$ npm run format
```

The second option, same as with ESLint, doesn't require any commands, it will automatically run before any commit.

The final option involves making changes in the code editor. For VSCode there is the [Prettier Extension](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) available. After installation a few more configuration steps are needed:

1. Change the Prettier config path to point to the file that has the configuration options, in this case `.prettierrc`.
2. Check the option to format on save.
3. Set the default formatter to Prettier.

This method will format the file after every save with the configuration rules from the project.

> **Pro tip:** Having auto save on will enhance the experience!

## Docker

## Tests

## PlantUML

# How we got here

## ESLint

ESLint was configured with the [Airbnb's style guide](https://github.com/airbnb/javascript). Installation steps:

1. Run the following command for **npm 5+**:

```bash
$ npx install-peerdeps --dev eslint-config-airbnb
```

2. Add "airbnb" to "extends" in the configuration file:

```
module.exports = {
  extends: [
    'airbnb',
  ],
};
```

For more information visit the [eslint-config-airbnb](https://github.com/airbnb/javascript/tree/master/packages/eslint-config-airbnb) repository.

Since this is a React project with Typescript a couple more dependencies are required. The [eslint-config-airbnb-typescript](https://github.com/iamturns/eslint-config-airbnb-typescript) configurations will be used. Installation steps:

1. [eslint-config-airbnb](https://github.com/airbnb/javascript/tree/master/packages/eslint-config-airbnb) needs to be installed first.
2. Install dependencies:

```bash
$ npm install eslint-config-airbnb-typescript \
            @typescript-eslint/eslint-plugin@^5.13.0 \
            @typescript-eslint/parser@^5.0.0 \
            --save-dev
```

3. The following configurations needs to added to ESLint config file:

```
{
 extends: ['airbnb', 'airbnb-typescript'],
  parserOptions: {
    project: './tsconfig.json'
  }
}
```

Finally, a couple more instructions needs to be added to the ESLint configuration file:

```
module.exports = {
  extends: [
    'airbnb',
    'airbnb-typescript',
    'plugin:react-hooks/recommended',
    'plugin:react/jsx-runtime',
  ],
  settings: {
    react: {
      version: 'detect'
    }
  },
  parserOptions: {
    project: './tsconfig.json'
  },
};
```

`plugin:react-hooks/recommended` and `plugin:react/jsx-runtime` are added so hooks are supported and to avoid getting errors when React hasn't been imported in the file. Setting the React version to `detect` will help find the correct React version running in the project.

## Prettier

To install prettier we need to run the following command:

```bash
$ npm install prettier eslint-config-prettier
```

`eslint-config-prettier` is installed so ESLint and Prettier can behave working together. More information can be found in this [StackOverflow question](https://stackoverflow.com/questions/44690308/whats-the-difference-between-prettier-eslint-eslint-plugin-prettier-and-eslint/44690309#44690309).

After installation a Prettier configuration file is required. These are the current Prettier configurations for this project:

```
module.exports = {
  "trailingComma": "all",
  "tabWidth": 2,
  "semi": true,
  "singleQuote": true,
  "printWidth": 120,
  "bracketSpacing": true
}

```

Finally, an extra configuration needs to be extended in the ESLint configuration file:

```
module.exports = {
  extends: [
    ...,
    'eslint-config-prettier',
  ],
};
```

As an extra a `.prettierignore` file can be added to avoid running the formatter on every file in the project which can cause some delays if the project is big.

## Git Hooks

1. Installed the following dependencies:

```bash
$ npm install --save-dev husky lint-staged
```

2. To enable git hooks automatically after install run this command:

```bash
$ npm pkg set scripts.prepare="husky install"
```

3. Create a hook by running the following commands:

```bash
$ npx husky add .husky/pre-commit "npx lint-staged"

$ git add .husky/pre-commit
```

More information can be found on the [Husky](https://github.com/typicode/husky) and [pretty-quick](https://github.com/azz/pretty-quick) documentation.

## Docker

## Tests

## PlantUML
