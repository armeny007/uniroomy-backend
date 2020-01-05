# UniRoomy Backend Documentation Home Page

## API definition

### Endpoints

| Method     | Endpoint         | Usage                                                  | Passed data format        | Returned data format                                                |
|--------    |--------------    |----------------------------------------------------    |-----------------------    |-----------------------------------------------------------------    |
| POST       | /api             | GraphQL endpoint (see <a href="https://uniroomy.co.uk:3003/api/graphiql" target="_blank">schema definition</a>) | GraphQL query             | { data: object }                                  |
| GET        | /api/graphiql           | Visual GraphQL editor with schema documentation.<br/> Just open this endpoint <br/>(<a href="https://uniroomy.co.uk:3003/api/graphiql" target="_blank">https://uniroomy.co.uk:3003/api/graphiql</a>)<br/> in a browser and run GraphQL queries<br/> using Visual GraphQL query builder. | -                         | -                                  |
| POST        | /api/login              | Login user                                          | {<br/> email: string,<br/> password: string<br/>} |  {<br/>user: object,<br/> token: string<br/>}      |
| POST        | /api/facebook-login     | Login/Register user with Facebook                            | { facebook_access_token: string }                 |  {<br/>user: object,<br/> token: string<br/>}      |
| POST        | /api/google-login     | Login/Register user with Google                            | { google_token_id: string }                 |  {<br/>user: object,<br/> token: string<br/>}      |
| GET        | /api/logout             | Logout user                                         | { access_token: string }  |  -      |
| POST       | /api/register           | Register a new user using email + password  | {<br/> email: string,<br/> password: string,<br/> first_name: string,<br/> // [optional]<br/><br/> last_name: string,<br/> // [optional]<br/> } |  {<br/>user: object,<br/> token: string<br/>}      |
| POST       | /api/add-student           | Adds new student with given _id. This endpoint should be called after /api/register  | {<br/> _id: int, <br/> uni_email: string,<br/> status_id: int<br/> } |  {<br/>success: boolean<br/>}      |
| POST       | /api/add-landlord           | Adds new landlord with given _id. This endpoint should be called after /api/register  | {<br/> _id: int, <br/> landlord_kind_id: int, <br/> company_name: string <br/> company_description: string <br/> responsible_for_houses: int <br/> responsible_for_beds: int <br/> contact_name: string <br/> contact_number: string <br/> contact_email: string <br/>  } |  {<br/>success: boolean<br/>}      |
| POST       | /api/forgot-password           | Start FusionAuth Forgot Password workflow  | {<br/> email: string<br/> } |  {<br/>status<br/>}      |
| POST       | /api/start-verify-uni-email           | Start uni-email verification workflow | {<br/> email: string<br/> uni_email: string<br/> } |  {<br/>status<br/>}      |
| GET       | /api/verify-uni-email/:token           | Verifies uni-email for a student. This endpoint is called from the verification email. | token: string |  Successful message or error (html)    |

## Visual UniRoomy GraphQL builder

  <a href="https://uniroomy.co.uk:3003/api/graphiql" target="_blank">https://umiroomy-backend.herokuapp.com/graphiql</a>
