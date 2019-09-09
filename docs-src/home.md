# UniRoomi Backend Documentation Home Page

## API definition

### Endpoints

| Method     | Endpoint         | Usage                                                  | Passed data format        | Returned data format                                                |
|--------    |--------------    |----------------------------------------------------    |-----------------------    |-----------------------------------------------------------------    |
| POST       | /api             | GraphQL endpoint (see schema definition)               | GraphQL query             | { data: object }                                  |
| GET        | /graphiql        | Visual GraphQL editor with schema documentation. Just open this endpoint (<a href="https://uniroomy-backend.herokuapp.com/graphiql">https://umiroomy-backend.herokuapp.com/graphiql</a>) using a browser and run GraphQL queries using Visual GraphQL query builder. | -                         | -                                  |
| POST       | /login           | Login user                                             | {<br/> email: string,<br/> password: string<br/>} |  {<br/>user: object,<br/> token: string<br/>}      |
| GET        | /logout          | Logout user                                          | { access_token: string }  |  -      |
| GET        | /register        | Register a new user                                    | {<br/> email: string,<br/> firstName: string,<br/> lastName: string,<br/> dateOfBirth: string,<br/>roleId: int,<br/>universityId: int,<br/>}  |  -      |

## Visual UniRoomy GraphQL builder

  <a href="https://uniroomy-backend.herokuapp.com/graphiql">https://umiroomy-backend.herokuapp.com/graphiql</a>
