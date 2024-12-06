## Loading the iFrame

It's very quick and easy to create your integration with idibu, you just need to send ALL the information required to deal with vacancy and user synchronisation to the iFrame URL.

### Endpoint url

You will need to use a specific `endpoint_url` for your crm integration. The format of the url should be: `https://v3.idibu.com/c/integration/[crm_name]`

`[crm_name]` will be the name value we provide for your CRM. Please contact <v3-support@idibu.com> to request this integration name value, quoting the text above.

### IMPORTANT - Please use POST METHOD and not GET

While we do support the GET method, we STRONGLY recommend and request you do not use it unless it is absolutely necessary. Please use the POST method.

If you are using the GET method, you are limited to a maximum of 2,048 characters, minus the number of characters in the actual path. That means Job Descriptions get cutoff, integrations fail and we have unhappy customers. So, again - unless you have a very compelling reason to use GET and are willing to ensure your data remains within URL length limitations, please use POST :)

In case you still prefer to use GET method, please make sure all your parameters are URL encoded.

### Vacancy and user syncronisation rules

1. Vacancy - you will pass a variable called “vacancy” which is a unique identifier. Typically this can be the vacancy reference but IT MUST be something that your system users cannot change or manipulate, and it must be unique across all your vacancies.

2. User - you will pass 4 pieces of user information:
- Your user ID
- User email
- User first name
- User last name

We will use this to work out if a new user needs to be created, or if we are working with an existing user.

### Required variables

The following list are the variables that **must** be passed for the integration to work:

- Use a default of “idibu” as your partner name which will load the default idibu styles. We will supply you with your own partner name when custom styling is required for your integration. 
- `id` = your application ID created previously
- `secret` = your application SECRET created previously
- `vacancy` = unique identifier of your vacancy (will be used as external crm entity id)
- `crm_reference` = (optional) reference of your vacancy. If empty system will use the value from `vacancy` parameter. If you would like to provide a reference separately which is different then `vacancy` parameter.
- `title` = vacancy title
- `userid` = your unique user id
- `email` = email address of the user
- `fname` = first name of the user
- `lname` = last name of the user

Example required variables URL to test with:
```
https://v3.idibu.com/c/integration/[crm_name]?id=<ID>&secret=<SECRET>&vacancy=12345&title=Test%20Vacancy%20Using%20idibu%20iFrame&userid=1234&email=test@test.com&fname=John&lname=Doe
```

### Recommended variables

The following list are the variables **we highly recommend** to provide the best possible user experience to our mutual clients:

#### User group

- `group` = group to assign the new user to. We recommend always using a default group because you can apply permissions to this group for all new users to inherit

#### Location

To provide us with the vacancy, you have 2 options - supply the geolocation or the postcode:

-  `lat` = Latitude value
-  `lng` = Longitude value

OR

-  `country` = supply the 2-digit ISO 3166 country code (https://www.iso.org/iso-3166-country-codes.html) if you want idibu to find the geolocation using the postcode
-  `map-postcode` = rather then provide a geolocation, you can provide a post code as a location source. idibu will use the google location API to get the geolocation. You must supply the country too so we know where to search.

Note: if you supply both the geolocation will take precedent.

#### Other variables

- `type` = Job type (see [list](https://github.com/oneworldmarket/idibu-v3-api/blob/master/stuff/iFrame%20integration/Variable%20data%20references.md) for available values)
- `sector` = send the idibu vacancy sector (see [list](https://github.com/oneworldmarket/idibu-v3-api/blob/master/stuff/iFrame%20integration/Variable%20data%20references.md) for available values)
- `starts` = vacancy start date - in yyyy-mm-dd format with leading zeroes (e.g. 2013-06-25)
- `currency` - salary currency sent in standard 3 character format  (see http://www.xe.com/iso4217.php)
- `minsalary` - minimum salary (e.g. 2000)
- `maxsalary` - maximum salary (e.g. 3000)
- `per` - salary payment interval  (see [list](https://github.com/oneworldmarket/idibu-v3-api/blob/master/stuff/iFrame%20integration/Variable%20data%20references.md) for available values)
- `benefits` - extra benefits (e.g. Premium%20Health%20Care)
- `salarydesc` - optional salary text override (e.g. 2000%20GBP%20or%20more)
- `description` - full description of the role

Example recommended variables URL to test with:

```
https://v3.idibu.com/c/integration/[crm_name]?id=<ID>&secret=<SECRET>&vacancy=12345&title=Test%20Vacancy%20Using%20idibu%20iFrame&userid=1234&email=test@test.com&fname=John&lname=Doe&lat=51.0&lng=-0.1&type=1&sector=18&starts=2017-06-24&currency=GBP&minsalary=25000&maxsalary=35000&per=1&benefits=Premium%20Health%20Care&salarydesc=30000%20GBP%20or%20more&description=Lorem%20ipsum%20dolor%20sit%20amet%2C%20consectetur%20adipiscing%20elit.%20Aenean%20malesuada%20risus%20orci%2C%20vitae%20congue%20elit%20pulvinar%20a.%20Curabitur%20metus%20eros%2C%20accumsan%20a%20mi%20vitae%2C%20consequat%20finibus%20metus.%20Nam%20venenatis%20at%20orci%20quis%20convallis.%20%0D%0A%0D%0APellentesque%20nec%20quam%20laoreet%2C%20pretium%20ex%20sed%2C%20lacinia%20mi.%20Vestibulum%20tristique%2C%20magna%20eget%20dictum%20egestas%2C%20felis%20erat%20malesuada%20lorem%2C%20vitae%20sollicitudin%20lacus%20quam%20sed%20risus.%20Proin%20feugiat%20bibendum%20ligula%20non%20venenatis.%20Phasellus%20tincidunt%20metus%20at%20tellus%20rhoncus%2C%20ac%20hendrerit%20est%20blandit.
```

### “Nice to have” variables

The following list the remaining variables you can utilise to improve the user experience:

- `kws` = Search keywords (we will use the title if this is not supplied) - it’ll help us with auto-matching candidates to the vacancy, accepts Boolean
- `duration` = Textual d.escription of the duration of a contract position
- `lpage` = Enable landing pages for this vacancy
- `lpageid` = ID of the landing page to use with this vacancy

### Important! Re-synching existing Vacancies
Please keep in mind that if a Vacancy has already been posted out (i.e. a functional Advert was created), the above variables that you pass to the iframe will NOT update the parameters that have been previously set on the Vacancy.

This is because we consider the data present in the idibu system to be the final source of truth. After syncing your Vacancy data into idibu, your users may update some of the Vacancy details there as part of the posting process. These updated details would then be lost if overridden by your system's data when re-opening the existing Vacancy in the iframe again - which is why we do not allow such a scenario currently.

Next up: [Styling your integration](https://github.com/oneworldmarket/idibu-v3-api/blob/master/stuff/iFrame%20integration/Styling%20your%20integration.md)

[Back to home](https://github.com/oneworldmarket/idibu-v3-api/blob/master/stuff/iFrame%20integration/README.md)
