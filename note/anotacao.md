### Mudanças no Node

Antes para usar o express, era necessário chamar através de uma constante.

~~~~JS
const express = require('express')
~~~~

Agora com a nova atualização do node, possível importar o express diretamente, mas para isso é chamamos o module no arquivo `package.json`
~~~~json
{
  "name": "server",
  //Chamando o module
  "type": "module",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
}

~~~~

Chamando o express - ATUALIZADA

o arquivo do tipo `.js` passa a ser do tipo `.mjs`

~~~~js
import express from 'express'
~~~~
<hr>

### Preparando o build
Como a aplicação está utilizando o typescript, podemos dar um commando executavel que é
````
npx tsc --init
````
Vai criar um arquivo de configuração typescript `tsconfig.json`.
*   O module deste arquivo deve usar o ECMA.
*   Define o rootDir, nesse caso é o "./src"
*   Define o outDir, no caso "./build" 

Após isso, dar o commando, o commando run foi adicionado manualmente no `package.json`
````
npm run build
````

### Recarregamento do Server com o SQL

Quando se usar tsnd com o prisma deve passar a flag --exit-child, ele desconecta o banco de dados e criar uma nova conexão.

````json
  "scripts": {
    "build": "tsc",
    "dev": "tsnd --exit-child src/server.ts"
  },
````

### Commandos para prisma

-   `npx prisma --datasource-provide [banco de dados]`
-   `npx prisma migrate dev` - dar atualização ao BD
-   `npx prisma studio` - criar uma interface gráfica para o banco de dados