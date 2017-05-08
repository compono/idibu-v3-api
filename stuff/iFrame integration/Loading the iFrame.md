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

The following list are the variables that **must** be passed for the integration to work:

- “integration” = use a default of “iframe”. We will supply you with your own partner name when custom styling is required for your integration. 
- “id” = your application ID created previously
- “secret” = your application SECRET created previously
- “vacancy” = unique identifier of your vacancy (will be used as the idibu reference)
- “title” = vacancy title
- “email” = email address of the user
- “fname” = first name of the user
- “lname” = last name of the user

Example required variables URL to test with:
>https://v3.idibu.com/c/integration/iframe/id/<ID/secret/<SECRET/vacancy/12345/title/Test%20Vacancy%20Using%20idibu%20iFrame/email/test@test.com/fname/John/lname/Doe

### Recommended variables

The following list are the variables **we highly recommend** to provide the best possible user experience to our mutual clients:

- “group” = group to assign the new user to. We recommend always using a default group because you can apply permissions to this group for all new users to inherit

Location of the vacancy sent using two variables (Longitude, Latitude):
-  “lat” = Latitude value
-  “lng = Longitutde” value TBC the format with tech team
- “type” = Job type (see list for available values)
- “sector” = send the idibu vacancy sector (see list for available values)
- “starts” = vacancy start date - in yyyy-mm-dd format with leading zeroes (e.g. 2013-06-25)
- “currency” - salary currency sent in standard 3 character format  (see http://www.xe.com/iso4217.php)
- “minsalary” - minimum salary (e.g. 2000)
- “maxsalary” - maximum salary (e.g. 3000)
- “per” - salary payment interval  (see list for available values)
- “benefits” - extra benefits (e.g. Premium%20Health%20Care)
- “salarydesc” - optional salary text override (e.g. 2000%20GBP%20or%20more)
- “description” - full description of the role

Example recommended variables URL to test with:
```html
https://v3.idibu.com/c/integration/iframe/id/<ID>/secret/<SECRET>/vacancy/12345/title/Test%20Vacancy%20Using%20idibu%20iFrame/email/test@test.com/fname/John/lname/Doe/lat/51.0/lng/-0.1/type/1/sector/18/starts/2017-06-24/currency/GBP/minsalary/25000/maxsalary/35000/per/1/benefits/Premium%20Health%20Care/salarydesc/30000%20GBP%20or%20more/description/Lorem%20ipsum%20dolor%20sit%20amet%2C%20consectetur%20adipiscing%20elit.%20Aenean%20malesuada%20risus%20orci%2C%20vitae%20congue%20elit%20pulvinar%20a.%20Curabitur%20metus%20eros%2C%20accumsan%20a%20mi%20vitae%2C%20consequat%20finibus%20metus.%20Nam%20venenatis%20at%20orci%20quis%20convallis.%20%0D%0A%0D%0APellentesque%20nec%20quam%20laoreet%2C%20pretium%20ex%20sed%2C%20lacinia%20mi.%20Vestibulum%20tristique%2C%20magna%20eget%20dictum%20egestas%2C%20felis%20erat%20malesuada%20lorem%2C%20vitae%20sollicitudin%20lacus%20quam%20sed%20risus.%20Proin%20feugiat%20bibendum%20ligula%20non%20venenatis.%20Phasellus%20tincidunt%20metus%20at%20tellus%20rhoncus%2C%20ac%20hendrerit%20est%20blandit.
```

### “Nice to have” variables

The following list are remaining variables you can utilise to improve the user experience:

- “kws” = Search keywords (we will use the title if this is not supplied) - it’ll help us with auto-matching candidates to the vacancy, accepts Boolean
- “duration” = Textual description of the duration of a contract position
- “lpage” = Enable landing pages for this vacancy
- “lpageid” = ID of the landing page to use with this vacancy




Next up: [Styling your integration](https://github.com/oneworldmarket/idibu-v3-api/blob/master/stuff/iFrame%20integration/Styling%20your%20integration.md)

[Back to home](https://github.com/oneworldmarket/idibu-v3-api/blob/master/stuff/iFrame%20integration/README.md)
