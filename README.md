# NLW 12ª Edição - Spacetime
Projeto da 12ª edição do NLW da [Rocketseat](https://www.rocketseat.com.br/), onde o foco é a criação de uma cápsula do tempo para armazenamento de lembranças.

## :rocket: Começando
Abaixo é possível encontrar instruções de como obter uma cópia do projeto para fins de teste e desenvolvimento.

## :exclamation: Pré-requisitos 
Para implementar e testar o projeto localmente é necessário:  
* [NodeJS](https://nodejs.org/en) v16.17.0 ou superior.
* [Postman](https://www.postman.com/)

Entre na raiz de cada uma das pastas a seguir e rode os comandos correspondentes para instalação das dependências:

| Parte       | Caminho   | Comando       |
| :---------- | :---------- | :--------- |
| API         | `/server` | `npm install` |
| Web         | `/web` | `npm install` |
| Mobile      | `/mobile` | `npx expo install` |

Assim, a pasta `node_modules` será criada em cada um dos diretórios.
### :gear: API
Parte do projeto responsável por implementar a camada de comunicação com o banco de dados, que nesse projeto é o [SQLite](https://www.sqlite.org/index.html), usando o [Prisma ORM](https://www.prisma.io/).

### Execução
```bash
  npm run dev
```

### Endpoints

#### **Registro/Login**

_Login do usuário com Github:_
```http
  POST /register
```

| Parâmetro   | Tipo       | Descrição                           |
| :---------- | :--------- | :---------------------------------- |
| `code`      | `string`   | **obrig.** Código do Github         |


#### **Memórias**

***_Busca todas as memórias de um usuário:_***
```http
  GET /memories
```
| Parâmetro | Tipo            | Descrição                       |
| :-------- | :-------------- | :-----------------------------  |
| `token`   | `Authorization` | **obrig.** Token de Autenticação|

***_Busca uma memória específica de um usuário:_***
```http
  GET /memories/:id
```
| Parâmetro   | Tipo            | Descrição                       |
| :---------- | :-------------- | :-----------------------------  |
| `token`     | `Authorization` | **obrig.** Token de Autenticação|
| `memory_id` | `UUID`          | **obrig.** ID da memória        |


***_Cria uma nova memória para o usuário:_***
```http
  POST /memories
```
| Parâmetro  | Tipo           | Descrição                        |
| :--------- | :------------- | :------------------------------- |
| `token`    | `Authorization`| **obrig.** Token de autenticação |
| `content`  | `String`       | **obrig.** Conteúdo da memória   |
| `coverUrl` | `String`       | **obrig.** Url da capa da memória|
| `isPublic` | `boolean`      | **obrig.** Se a memória é pública|

***_Altera uma memória para o usuário:_***
```http
  PUT /memories:id
```
| Parâmetro  | Tipo           | Descrição                        |
| :--------- | :------------- | :------------------------------- |
| `token`    | `Authorization`| **obrig.** Token de autenticação |
| `memory_id`| `UUID`         | **obrig.** ID da memória         |
| `content`  | `String`       | **obrig.** Conteúdo da memória   |
| `coverUrl` | `String`       | **obrig.** Url da capa da memória|
| `isPublic` | `boolean`      | **obrig.** Se a memória é pública|

***_Deleta uma memória específica para o usuário:_***
```http
  DELETE /memories/:id
```
| Parâmetro   | Tipo            | Descrição                       |
| :---------- | :-------------- | :-----------------------------  |
| `token`     | `Authorization` | **obrig.** Token de Autenticação|
| `memory_id` | `UUID`          | **obrig.** ID da memória        |

#### **Upload**
***_Upload de foto da memória:_***
```http
  POST /upload
```
| Parâmetro   | Tipo       | Descrição                           |
| :---------- | :--------- | :---------------------------------- |
| `photo`     | `file`     | **obrig.** Foto para upload         |

### :desktop_computer: Aplicação Web

Parte do projeto por implementar uma das camadas de interação do usuário com os requisitos do projeto. Foi criado usando [React](https://react.dev/) com [NextJs](https://nextjs.org/) e [TailwindCSS](https://tailwindcss.com/).

### Execução
```bash
  npm run dev
```

Permite o usuário:
* Realizar login usando sua conta Github;
* Criar uma memória e salvar em sua conta na aplicação;
* Visualizar todas as suas memórias.

### :iphone: Aplicação Mobile
Parte do projeto por implementar uma das camadas de interação do usuário com os requisitos do projeto. Foi criado utilizando [React Native](https://reactnative.dev/) com [Expo](https://expo.dev/) e [TailwindCSS](https://tailwindcss.com/).

### Execução
```bash
  npm run start
```

Permite o usuário:
* Realizar login usando sua conta Github;
* Criar uma memória e salvar em sua conta na aplicação;
* Visualizar todas as suas memórias.