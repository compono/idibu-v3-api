## Composing the URL variables

To keep it very quick and easy to create your integration with idibu, you are going to send ALL the information required to deal with vacancy and user synchronisation in the iFrame URL.

### Vacancy and user syncronisation rules

1. Vacancy - you will pass a variable called “vacancy” which is a unique identifier. Typically this can be the vacancy reference but IT MUST be something that your system users cannot change or manipulate, and it must be unique across all your vacancies.

2. User - you will pass 3 pieces of user information.
- User email
- User first name
- User Lastname

We will use this to work out if a new user needs to be created, or if we are working with an existing user.


Next up: [Styling your integration](https://github.com/oneworldmarket/idibu-v3-api/blob/master/stuff/iFrame%20integration/Styling%20your%20integration.md)

[Back to home](https://github.com/oneworldmarket/idibu-v3-api/blob/master/stuff/iFrame%20integration/README.md)
