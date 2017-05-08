## Composing the URL variables

To keep it very quick and easy to create your integration with idibu, you are going to send ALL the information required to deal with vacancy and user synchronisation in the iFrame URL.

### Vacancy and user syncronisation rules

1. Vacancy - you will pass a variable called “vacancy” which is a unique identifier. Typically this can be the vacancy reference but IT MUST be something that your system users cannot change or manipulate, and it must be unique across all your vacancies.

2. User - you will pass 3 pieces of user information:
- User email
- User first name
- User Lastname

We will use this to work out if a new user needs to be created, or if we are working with an existing user.

### Required variables

The following list are the variables that must be passed for the integration to work:

- “integration” = use a default of “iframe”. We will supply you with your own partner name when custom styling is required for your integration. 
- “id” = your application ID created previously
- “secret” = your application SECRET created previously
- “vacancy” = unique identifier of your vacancy (will be used as the idibu reference)
- “title” = vacancy title
- “email” = email address of the user
- “fname” = first name of the user
- “lname” = last name of the user

Example required variable to test with:
>https://v3.idibu.com/c/integration/iframe/id/<ID/secret/<SECRET/vacancy/12345/title/Test%20Vacancy%20Using%20idibu%20iFrame/email/test@test.com/fname/John/lname/Doe




Next up: [Styling your integration](https://github.com/oneworldmarket/idibu-v3-api/blob/master/stuff/iFrame%20integration/Styling%20your%20integration.md)

[Back to home](https://github.com/oneworldmarket/idibu-v3-api/blob/master/stuff/iFrame%20integration/README.md)
