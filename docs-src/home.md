# UniRoomy Backend Documentation Home Page

## API definition

### Endpoints

| Method     | Endpoint         | Usage                                                  | Passed data format        | Returned data format                                                |
|--------    |--------------    |----------------------------------------------------    |-----------------------    |-----------------------------------------------------------------    |
| POST       | /api             | GraphQL endpoint (see <a href="https://uniroomy.co.uk:3003/api/graphiql" target="_blank">schema definition</a>) | GraphQL query             | { data: object }                                  |
| GET        | /api/graphiql           | Visual GraphQL editor with schema documentation.<br/> Just open this endpoint <br/>(<a href="https://uniroomy.co.uk:3003/api/graphiql" target="_blank">https://uniroomy.co.uk:3003/api/graphiql</a>)<br/> in a browser and run GraphQL queries<br/> using Visual GraphQL query builder. | -                         | -                                  |
| GET        | /api/login              | Login user                                          | {<br/> email: string,<br/> password: string<br/>} |  {<br/>user: object,<br/> token: string<br/>}      |
| GET        | /api/facebook-login     | Login user with Facebook                            | { facebook_access_token: string }                 |  {<br/>user: object,<br/> token: string<br/>}      |
| GET        | /api/logout             | Logout user                                         | { access_token: string }  |  -      |
| POST       | /api/register           | Register a new user                                 | {<br/> email: string,<br/> firstName: string,<br/> lastName: string,<br/> dateOfBirth: string,<br/>roleId: int,<br/>universityId: int,<br/>}  |  -      |

## Visual UniRoomy GraphQL builder

  <a href="https://uniroomy.co.uk:3003/api/graphiql" target="_blank">https://umiroomy-backend.herokuapp.com/graphiql</a>
