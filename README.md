 ## Organizing Commits
 
Standardizing commits with *husky*, *commitzen* and *commitlint*. A practical tutorial.


## Technologes
 
Technologies used in the project.
 
* Husky version 7.0.0
* Commitlint/config-conventional version 16.2.1
* Commitizen 4.2.4
 
## Used Services
 
* Git

## Introducing each lib

  #### Husky
  Git has several hooks that fire at different times in the flow during code versioning. It is possible to manipulate such hooks, but it is a rather complex process.
  This is where the *husky* comes in, it facilitates the manipulation of hooks. 
  In our context, the *husky* will be the mediator for us to standardize the commits through the *hook* **prepare-commit-msg**
  **https://typicode.github.io/husky/#/**


  #### Commitlint
  Commitlint will bar our commit messages and verify if the message complies with the previously configured defaults. 
  We can configure a message pattern ourselves or use an existing pattern that are listed in the commitlint documentation. 
  The most common pattern is **commitlint/config-conventional**
  **https://commitlint.js.org/#/**

  #### Commitzen

  The most visual dependency of all. It guides us through a **visual menu** to specify all the information correctly and in a standardized way.
  **https://github.com/commitizen/cz-cli**

<<<<<<< HEAD
## How to use
 
  **1º** When the customer clicks the *support* button. The following will appear:  
  ![Template inicial - cliente](https://github.com/Jackie098/nlw05-node/blob/main/images-readme/client_1.png)

  **2º** When inserting the message and your e-mail (identification), the system will initiate a connection via socket and wait for an administrator to respond.  
  ![Esperando atendimento](https://github.com/Jackie098/nlw05-node/blob/main/images-readme/client_02.png)

  **3º** On the administrator page, a list of all users waiting to be serviced will be displayed.  
  ![Lista de clientes em espera](https://github.com/Jackie098/nlw05-node/blob/main/images-readme/admin_01.png)

  **4º** Clicking on a button will open a chat and the button will disappear.  
  ![Chat com cliente](https://github.com/Jackie098/nlw05-node/blob/main/images-readme/admin_02.png)

 
## Updates
 
  - Suggestions: 
    - In chat, function to delete message sending and/or edit it.
 
 
## Links
 
  - Repository: https://github.com/Jackie098/nlw05-node
    - In case of doubts or suggestions, feel free to contact and/or request **pull requests**.
 
 
## Creators
=======
## How to install

  #### Husky
  **1º** Let's start by installing husky as a development dependency:
  ```shell
  > npm install husky --save-dev
  ```

  **2º** To enable Git hooks run:
  ```shell
  > npx husky install
  ```

  **3º** To automatically have Git hooks enabled after install, edit *package.json*:
  ```shell
   > npm set-script prepare "husky install"
  ```

  This command will set the following new property in package.json:
  ```js
  // package.json
  {
    "scripts": {
      "prepare": "husky install"
    }
  }
  ```


  **4º** Now that we have Husky installed and git hooks enabled, we need to map two hooks

  - *commit-msg*
    > This hook will be used to look for errors in the message structure, that is, we will use *commitlint* here

  - *prepare-commit-msg*
    > This hook will be triggered to display commitzen visual menu

  ***Mapeando os hooks***

  - To add **pre-commit** hook
  ```shell
  npx husky add ./husky/pre-commit
  ``` 
  - To add **prepare-commit-msg** hook
  ```shell
  npx husky add ./husky/prepare-commit-msg
  ``` 
  *Note that inside the .husky file, two shell files were created*

  #### Commitlint
  **1º** First install the dependencies needed:
  ```shell
  npm install --save-dev @commitlint/{config-conventional,cli}
  ```
  If you are a *windows* user:
  ```shell
  npm install --save-dev @commitlint/config-conventional @commitlint/cli
  ```
  *This command will download default **commitlint configuration** and terminal manager (**commitlint-cli**)*

  **2º** Now, configure commitlint to use conventional config
  ```shell
  echo "module.exports = {extends: ['@commitlint/config-conventional']}" > commitlint.config.js
  ```

  *Here will be created a file to set the default commitlint configuration, named of **commitlint.config.js***

 *If you want to change the commitlint configuration, just download it and change the **config-conventional** value to the name of the configuration you downloaded*

  **3º** With the commitlint installed and configured, the last step now is to set the triggers inside the **commit-msg hook** to call commitlint as soon as we try to commit
  ```sh
  #!/bin/sh
  . "$(dirname "$0")/_/husky.sh"

  npx --no-install commitlint --edit ""
  npx commitlint --edit 
  ```
  *Your **commit-msg** file should look like this at the end*

  ***From now on, whenever you make a commit, if it's not in the accepted standard, an error will be thrown. Test!***

  #### Commitzen
  The coolest section of the tutorial. We will now configure the visual part of the commit standardization

  **1º** Install globally
  ```shell
  npm install -g commitizen
  ```
  **2º** Now, we need to initialize commitzen inside the repository 
  ```shell
  commitizen init cz-conventional-changelog --save-dev --save-exact
  ```
  *If you're using **yarn**:*
  ```shell
  commitizen init cz-conventional-changelog --yarn --dev --exact
  ```
  The above command does three things for you:
  1. Installs the cz-conventional-changelog adapter npm module
  2. Saves it to package.json's dependencies or devDependencies
  3. Adds the config.commitizen key to the root of your package.json file as shown here:

  ```js
  // package.json
  "config": {
    "commitizen": {
      "path": "cz-conventional-changelog"
    }
  }
  ```
  **3º** End finally, just add the commitzen to the prepare-commit-msg hook
  ```sh
  #!/bin/sh
  . "$(dirname "$0")/_/husky.sh"

  exec < /dev/tty && npx cz --hook || true
  ```
  *Your **prepare-commit-msg** file should look like this at the end*

  ***From now on, whenever you make a commit, a visual menu will appear for you to choose the type and enter the commit message***

  #### It's done!!!

## Extra
  If you want to use emojis in commits, just download:
  ```shell
    npm install cz-emoji
  ```
  or:
  ```shell
    npm install cz-emoji-conventional
  ```
  Now, go to ***package.json*** and change the commitizen path: *cz-conventional-changelog* to the lib you just downloaded.
  Ex: 

  **Before**

  ```js
    "config": {
      "commitizen": {
        "path": "./node_modules/cz-conventional-changelog"
      }
  }
  ```
  **After**
  ```js
    "config": {
      "commitizen": {
        "path": "./node_modules/cz-emoji-conventional"
      }
  }
  ```
  > **Attention:** If you want to use the emojis you need to reconfigure commitlint so that it sees the emoji as part of the message and not as an error.

  *I will soon explain what we can do about it.*
 
 
## Links / References
 
  - Git Hooks: https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks
  - Husky: https://typicode.github.io/husky/#/
  - Commitlint: https://commitlint.js.org/#/
  - Commitizen: https://github.com/commitizen/cz-cli
  - cz-emoji: https://www.npmjs.com/package/cz-emoji
  - cz-emoji-conventional: https://www.npmjs.com/package/cz-emoji-conventional
 
 
## Creator of tutorial
>>>>>>> check
 
* **Carlos Augusto**: (https://github.com/Jackie098)
