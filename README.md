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
 
* **Carlos Augusto**: (https://github.com/Jackie098)
