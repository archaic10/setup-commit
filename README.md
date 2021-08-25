## Sumary

------

This project implements a pattern commit using commitlint to force the developer to commit to a pattern, and using commitzen, to create a mandatory form by performing a commit formatting to the standard used by the angular community which is the conventional changelog

## Dependencys

------

You will need install :

- Commitlint
- Husky
- Commitzen

## Process installation

------

```
yarn add @commitlint/config-conventional @commitlint/cli
```

or

```
npm install @com	mitlint/config-conventional @commitlint/cli
```

Create a file with name "commitlint.config.js" enter the code below:

`module.exports = {extends: ['@commitlint/config-conventional']}`

Install husky to set the command to run whenever a commit happens:

```
yarn add husky
```

or 

```
npm install husky
```

Enter the code below to check commits before they are created:

```
npx husky add .husky/commit-msg 'npx --no-install commitlint --edit "$1"'
```

Install the commitizen:

```
yarn add commitizen
```

or 

```
npm install commitizen
```

After, to initialize your project to use the cz-conventional-changelog adapter by typing:

```
yarn add commitizen init cz-conventional-changelog --yarn --dev --exact
```

or 

```
npm install commitizen init cz-conventional-changelog --save-dev --save-exact
```

To finish, create a file named "prepare-commit-msg " inside the ./husky directory and insert the following code:

```
#!/bin/sh
. "$(dirname "$0")/_/husky.sh"

exec < /dev/tty && node_modules/.bin/cz --hook || true
```