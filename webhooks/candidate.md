### Disclaimer

This is a work in progress article. Information provided here is subjected to change and is not yet finalised.

## Overview

This webhooks faeeds data when a candidate profile is [created](http://v3-docs.idibu.com/article/289-uploading-candidates-article) or updated. You can use this webhook to:

- synch candidates created in idibu with your system,
- track any changes to their profiles,
- collect candidate's created numbers, their data and which step of the recruitment process are they currently at. You can potentially break this information down by additional parameters like location, current position and others,
- collect candidate data for analysis purposes - i.e. track which location brought most placed candidates, what is your most successful source, etc.
- and others!

## Data

Every webhook call contains selected candidate fields that are present on candidate's profile page in idibu:

- firstname - candite's first name,
- lastname - we're sure you know what that is,
- job_title - candidate's last position as declared in CV,
- phone - candidate's landline number,
- phone_mobile - candidate's mobile phone number,
- address - candidate's phisical address,
- background_info - field that can be populated by a consultant with his insights on the candidate,
- country_code - the 3 field geolocation data on candidate's location,
- lat,
- lng,
- work_history - candidates encoded work history broken into periods from latest to oldest with position title, employed dates, employer and summary of the position.
- education_history - candidates encoded education history broken into periods from latest to oldest with course name, education dates, school and course summary.

*Both work_history and education_history are parsed from candidate's CV and thus presence of all elements, its quality and detail depend on the CV itself and the success of the parsing process. Expect possible, thought rare, inconsistencies.*

- email - you guessed it, candidate's email,
- appt.source - candidates original source,
- creation_date - date candidate was originally added to the system
- createby_firstname - name of the consultant who added the candidate to the system or original owner of the vacancy the applicant applied for,
- createby_lastname - surname, as above.




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
	"payload": {
		"firstname": "Paul",
		"lastname": "Edwards",
		"job_title": "People and Performance Superintendent",
		"phone": "",
		"phone_mobile": "",
		"address": "",
		"background_info": "",
		"country_code": "",
		"lat": "0",
		"lng": "0",
		"work_history": "**People and Performance Superintendent - From Feb 2011 To May 2011:**\r\n\r\nWith performance management issues to improve people management competencies\r\nContract role\r\n{Talent2 initiated 3 month    Ausenco (www.ausenco.com) [Brisbane Australia]\r\nContract; lead HR strategic\r\nAnd operational planning    Global engineering, project management services and operations solutions provider for\r\nFor two prospective EPCM    resources and energy sectors, listed on ASX and head-quartered Brisbane\r\nProjects with potential to be\r\nLead HR for the projects in    People and Performance Superintendent - Major Projects\r\nSouth America; projects    Responsible for People and Performance (P&P) strategy, planning, design and\r\nDidn't eventuate (`Mina\r\nJusta' sold by Glencore and    implementation tools for global projects\r\n`Constancia' delayed) so    Achievements\r\nWith    no    other    work\r\nAvailable, contract came to    * Developed project conditions, contracts, templates, and remuneration strategy\r\nAn end}\r\nFor South American jurisdictions; referencing/interpreting relevant local\r\n\r\n,
		"education_history": "Certified Professional Member Australian Human Resources Institute\r\nMaster of Commerce\r\nCSU (currently enrolled - International Business & International HRM)\r\n\r\n**2013:**\r\nMaster of Business Administration in Human Resource Management\r\n*    MBA (Strategic Human Resource Management) - USQ\r\n\r\n**1990:**\r\nBachelor of Arts in Psychology\r\n\r\n**Feb 2015:**\r\nDiploma\r\n\r\n**2014:**\r\nGraduate Diploma in Career Education & Development\r\n\r\n**Feb 2014 - Dec 2014:**\r\nDiploma\r\n\r\n**Jun 2017 - 2009:**\r\n*    Diversity, leadership and\r\n-    *    Board composition, structure    effective teams\r\nAnd selection criteria of\r\nDirectors",
		"email, appt.source": "p_edwards@hotmail.com",
		"creation_date": "2017-06-28 15:57:46",
		"createby_firstname": "bugtest2",
		"createby_lastname": "bugtest2"
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

