## Loading the iFrame

It's swift and easy to create your integration with idibu, you just need to send ALL the information required to deal with the vacancy and user synchronisation to the iFrame URL.

### Endpoint URL

You will need to use a specific `endpoint_url` for your CRM integration. The format of the URL should be: `https://v3.idibu.com/c/integration/[crm_name]`

`[crm_name]` will be the name value we provide for your CRM. Please [contact us](https://www.idibu.com/contact-support/) to request this integration name value, quoting the text above.

### IMPORTANT - Please use the HTTP POST method

While we do support HTTP GET, we _strongly_ recommend to use POST.

If you use the GET method, you are limited to a maximum of 2,048 characters, minus the number of characters in the actual path - that means Job Descriptions can easily get cut off.

If you still prefer to use the GET method (in which case it is suggested to not pass the Job Description as part of the request), please ensure all your parameters are URL encoded.

### Vacancy and user synchronisation rules

1. Vacancy - you will pass a variable called `vacancy` which is a unique identifier. Typically, this can be the vacancy reference but it _must_ be something that your system's users cannot change or manipulate, and it must be unique across all your vacancies.

2. User - you will pass 4 pieces of user information:
- Your user ID
- User email
- User first name
- User last name

We will use this to work out if a new user needs to be created, or if we are working with an existing user.

### Required variables

The following variables **must** be passed for the integration to work:

- `id` - your application ID created previously
- `secret` - your application SECRET created previously
- `vacancy` - unique identifier of your vacancy (will be used as external CRM entity ID)
- `crm_reference` - (optional) reference of your vacancy. If empty, the system will use the `vacancy` parameter.
- `title` - vacancy title
- `userid` - your unique user id
- `email` - email address of the user
- `fname` - first name of the user
- `lname` - last name of the user

Example required variables URL to test with:
```
https://v3.idibu.com/c/integration/[crm_name]?id=<ID>&secret=<SECRET>&vacancy=12345&title=Test%20Vacancy%20Using%20idibu%20iFrame&userid=1234&email=test@test.com&fname=John&lname=Doe
```

### Recommended variables

The following list are the variables **we highly recommend** to provide the best possible user experience to our mutual clients:

#### User group

- `group` - group to assign the new user to. We recommend always using a default group because you can apply permissions to this group for all new users to inherit

#### Location

To provide us with the vacancy, you have 2 options - supply the geolocation or the postcode:

-  `lat` - Latitude value
-  `lng` - Longitude value

OR

-  `country` - supply the 2-digit ISO 3166 country code (https://www.iso.org/iso-3166-country-codes.html) if you want idibu to find the geolocation using the `map-postcode` parameter.
-  `map-postcode` - rather than providing geolocation, you can provide a postcode as the location source. idibu will use the Google location API to get the geolocation.

Note: if you supply both, the geolocation will take precedence.

#### Other variables

- `type` - Job type (click [here](https://github.com/oneworldmarket/idibu-v3-api/blob/master/stuff/iFrame%20integration/Variable%20data%20references.md) for available values)
- `sector` - send the idibu vacancy sector (click [here](https://github.com/oneworldmarket/idibu-v3-api/blob/master/stuff/iFrame%20integration/Variable%20data%20references.md) for available values)
- `starts` - vacancy start date - in `yyyy-mm-dd` format
- `currency` - salary currency sent in standard 3-character ISO format (see https://www.iso.org/iso-4217-currency-codes.html)
- `minsalary` - minimum salary (e.g. 2000)
- `maxsalary` - maximum salary (e.g. 3000)
- `per` - salary payment interval  (see [list](https://github.com/oneworldmarket/idibu-v3-api/blob/master/stuff/iFrame%20integration/Variable%20data%20references.md) for available values)
- `benefits` - extra benefits
- `salarydesc` - optional salary text override - if supported by the posting destination, it will be displayed instead of all the other salary data
- `description` - full description of the role

Example recommended variables URL to test with:

```
https://v3.idibu.com/c/integration/[crm_name]?id=<ID>&secret=<SECRET>&vacancy=12345&title=Test%20Vacancy%20Using%20idibu%20iFrame&userid=1234&email=test@test.com&fname=John&lname=Doe&lat=51.0&lng=-0.1&type=1&sector=18&starts=2017-06-24&currency=GBP&minsalary=25000&maxsalary=35000&per=1&benefits=Premium%20Health%20Care&salarydesc=30000%20GBP%20or%20more&description=Lorem%20ipsum%20dolor%20sit%20amet%2C%20consectetur%20adipiscing%20elit.%20Aenean%20malesuada%20risus%20orci%2C%20vitae%20congue%20elit%20pulvinar%20a.%20Curabitur%20metus%20eros%2C%20accumsan%20a%20mi%20vitae%2C%20consequat%20finibus%20metus.%20Nam%20venenatis%20at%20orci%20quis%20convallis.%20%0D%0A%0D%0APellentesque%20nec%20quam%20laoreet%2C%20pretium%20ex%20sed%2C%20lacinia%20mi.%20Vestibulum%20tristique%2C%20magna%20eget%20dictum%20egestas%2C%20felis%20erat%20malesuada%20lorem%2C%20vitae%20sollicitudin%20lacus%20quam%20sed%20risus.%20Proin%20feugiat%20bibendum%20ligula%20non%20venenatis.%20Phasellus%20tincidunt%20metus%20at%20tellus%20rhoncus%2C%20ac%20hendrerit%20est%20blandit.
```

### Other variables

Below are the remaining variables you can utilise to improve the user experience:

- `kws` - search keywords (`title` will be used if this is not supplied) - improves auto-matching candidates to the vacancy, accepts boolean
- `duration` - textual description of the duration of a contract or temporary position
- `lpage` - enable landing pages for this vacancy
- `lpageid` - ID of the landing page to use with this vacancy
- `appurl` - external Application URL where candidates would be redirected instead of applying directly through idibu

### Important! Re-synching existing Vacancies
Please keep in mind that if a Vacancy has already been posted out (i.e. a functional Advert was created), the above variables that you pass to the iframe will NOT update the parameters that have been previously set on the Vacancy.

This is because we consider the data present in the idibu system to be the final source of truth. After syncing your Vacancy data into idibu, your users may update some of the Vacancy details there as part of the posting process. These updated details would then be lost if overridden by your system's data when re-opening the existing Vacancy in the iframe again - which is why we do not allow such a scenario currently.

Next up: [Styling your integration](https://github.com/oneworldmarket/idibu-v3-api/blob/master/stuff/iFrame%20integration/Styling%20your%20integration.md)

[Back to home](https://github.com/oneworldmarket/idibu-v3-api/blob/master/stuff/iFrame%20integration/README.md)
