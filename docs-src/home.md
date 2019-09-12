# UniRoomy Backend Documentation Home Page

## API definition

### Endpoints

| Method     | Endpoint         | Usage                                                  | Passed data format        | Returned data format                                                |
|--------    |--------------    |----------------------------------------------------    |-----------------------    |-----------------------------------------------------------------    |
| POST       | /api             | GraphQL endpoint (see <a href="https://uniroomy-backend.herokuapp.com/graphiql" target="_blank">schema definition</a>) | GraphQL query             | { data: object }                                  |
| GET        | /graphiql        | Visual GraphQL editor with schema documentation.<br/> Just open this endpoint <br/>(<a href="https://uniroomy-backend.herokuapp.com/graphiql" target="_blank">https://umiroomy-backend.herokuapp.com/graphiql</a>)<br/> in a browser and run GraphQL queries<br/> using Visual GraphQL query builder. | -                         | -                                  |
| POST       | /login           | Login user                                             | {<br/> email: string,<br/> password: string<br/>} |  {<br/>user: object,<br/> token: string<br/>}      |
| GET        | /logout          | Logout user                                          | { access_token: string }  |  -      |
| POST       | /register        | Register a new user                                    | {<br/> email: string,<br/> firstName: string,<br/> lastName: string,<br/> dateOfBirth: string,<br/>roleId: int,<br/>universityId: int,<br/>}  |  -      |

## Visual UniRoomy GraphQL builder

  <a href="https://uniroomy-backend.herokuapp.com/graphiql" target="_blank">https://umiroomy-backend.herokuapp.com/graphiql</a>
