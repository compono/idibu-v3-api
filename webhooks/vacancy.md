### disclaimer

* This is a work in pending article. Informartion provided here may change and is not yet finalised. *

## Overview

This webhooks feeds data when a vacancy is [created](http://v3-docs.idibu.com/article/277-adding-a-vacancy-article) or updated. You can use this webhook to:

- synch vacancies created in idibu with your system,
- track any changes to those vacancies,
- collect vacancy's created numbers, their livespan and ownership distribution for your custom reporting. You can potentially break this information by additional parameters like job type, location, sector and others,
- collect vacancy data for analysis purposes - ie. track whether vacancies that have longer descriptions provide more applicants then those that choose their words carefully,
- and others!

## Data

Every webhook call contains every vacancy field that is present on vacancy's details page in idibu:

- id - numerical identifier of a job on idibu's end. It's main uniqueness indicator,
- title" - vacancy title,
- search_keywords - phrase used for local search initially when vacancy becomes created and as a reference for further candidate searches,
- location - vacancy location, string,
- job_type - identified job type ,
- duration - contact duration, only available for contract job_types,
- sector - numerical identifier for chosen job sector - values can be found [here](http://www.idibu.com/images/stories/Portal_logos/idibu_sector_list.xls), 
- reference - vacancy reference - can be used as uniqueness indicator if your users do not login to idibu's direct interface where it is possible to edit a reference,
- start_date - declared position opening date
- salary that constitutes of:
	- currency - either AUD, CHF, GBP, HKD, NZD, SGD, USD or EUR,
	- salary_min - minimum salary,
	- salary_max - maximum salary,
	- salary_per - salary period either annum, month, week, day or hour,
- description - vacancy description,
- creation_date - date when the vacancy was created,
- client_name - name and surname of the consultant that created the vacancy.


## Examples

### Vacancy added example

*Header*

```
User-Agent: IdibuV3-Hookshot
X-IdibuV3-Delivery: 49da521a-c172-4819-b69a-89f59fa3cef1
X-IdibuV3-Event: update.vacancy
Content-Type: application/json
```

*Payload*
```
{
	"payload_url": "https://requestb.in/y9gkwoy9",
	"request_data": {
		"id": "7886",
		"title": "MeNextVacancy",
		"search_keywords": "",
		"location": "London",
		"job_type": "2",
		"duration": "",
		"sector": "0",
		"reference": "BB-73",
		"start_date": "2017-06-27",
		"salary": {
			"currency": "GBP",
			"salary_min": "40000.00",
			"salary_max": "50000.00",
			"salary_per": "annum"
		},
		"description": "",
		"creation_date": "2017-06-27",
		"client_name": "Consultant"
	}
}
```

### Vacancy updated example

*Header*

```
User-Agent: IdibuV3-Hookshot
X-IdibuV3-Delivery: 1fcee84b-75dd-4ee0-bbb3-260459568d31
X-IdibuV3-Event: update.vacancy
Content-Type: application/json
```

*Payload*
```
{
	"payload": {
		"id": "7886",
		"title": "MeNextVacancy",
		"search_keywords": "",
		"location": "London",
		"job_type": "2",
		"duration": "",
		"sector": "0",
		"reference": "BB-73",
		"start_date": "2017-06-27",
		"salary": {
			"currency": "GBP",
			"salary_min": "40000.00",
			"salary_max": "50000.00",
			"salary_per": "annum"
		},
		"description": "",
		"creation_date": "2017-06-27",
		"client_name": "Consultant"
	}
}
```
