## Sumary


This project implements a pattern commit using commitlint to force the developer to commit to a pattern, and using commitzen, to create a mandatory form by performing a commit formatting to the standard used by the angular community which is the conventional changelog 

## Dependencys


You will need install :

- Commitlint
- Husky
- Commitzen
- Git-cz (just for npm)

## Observation

> Check version npm before implementing the husky, commitlint and commitzen

> Case you have a old version installed the npm, delete the  package-lock.json, and execute the command line npm install  

> Case you have a old version installed the husky, remove the register on package.json, reinstall again the husky

## Process installation


```
yarn add @commitlint/config-conventional @commitlint/cli --dev
```

or

```
npm install --save-dev @commitlint/{config-conventional,cli}
```

Create a file with name "commitlint.config.js" enter the code below:

`module.exports = {extends: ['@commitlint/config-conventional']}`

Install husky to set the command to run whenever a commit happens:

```
yarn add husky --dev
```

or 

```
npm install husky
```

To initialize the husky execute:

```
npx husky install
```

or

```
yarn husky install
```

Enter the code below to check commits before they are created:

```
npx husky add .husky/commit-msg 'npx --no-install commitlint --edit "$1"'
```

Install the commitizen:

```
yarn add commitizen --dev
```

or 

```
sudo npm install commitizen -g
```

After, to initialize your project to use the cz-conventional-changelog adapter by typing:

```
yarn add commitizen init cz-conventional-changelog --yarn --dev --exact
```

or 

```
npm install commitizen init cz-conventional-changelog --save-dev --save-exact
```
Add this script in your package json

```
"config": {
    "commitizen": {
      "path": "./node_modules/cz-conventional-changelog"
    }
 }
```

## Npm

> For commizen to work with husky using npm, a few more steps are needed:

> If you didn't use npm, skip this step

Install git-cz
```
npx git-cz
```

## Yarn

To finish, create a file named "prepare-commit-msg " inside the ./husky directory and insert the following code:

```
#!/bin/sh
. "$(dirname "$0")/_/husky.sh"

exec < /dev/tty && node_modules/.bin/cz --hook || true
```
## Npm

To finish, create a file named "prepare-commit-msg " inside the ./husky directory and insert the following code:

```
#!/bin/sh
. "$(dirname "$0")/_/husky.sh"

exec < /dev/tty && npx git-cz --hook || true
```
## Warning
> Case have problem on execution the hook, how how per example:

> hint: The '.husky/prepare-commit-msg' hook was ignored because it's not set as executable.
> hint: You can disable this warning with `git config advice.ignoredHook false

Then execute the command lines:

```
chmod ug+x .husky/*
```

```
chmod ug+x .git/hooks/*
```
