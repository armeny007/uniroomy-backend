# UniRoomi Backend API

UmiRoomy Backend API documentation

## Visual UmiRoomy GraphQL builder

  https://umiroomy.herokuapp.com/

## How to run

### To run the server

    yarn start

### To run only client part

    cd client
    yarn start

### To run both

    yarn dev
  
### To run mocha tests

    yarn test

## API definition

### Endponts

| Method     | Endpoint         | Usage                                                  | Passed data format        | Returned data format                                                |
|--------    |--------------    |----------------------------------------------------    |-----------------------    |-----------------------------------------------------------------    |
| POST       | /api             | GraphQL endpoint (see schema definition)               | GraphQL query             | {   status: string, data: object }                                  |
| POST       | /graphiql        | Visual GraphQL editor with schema documentation        | {   lispStr: string }     | {   status: string, data: object }                                  |

