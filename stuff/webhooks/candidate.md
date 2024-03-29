### Disclaimer

This is a work in progress article. Information provided here is subjected to change and is not yet finalised.

IMPORTANT: Please note that our webhook system is two tier. This doc outlines the full data contained in our Advanced webhook which may be liable to additional client charges depending on the intended use. Please contact our Product Team to discuss this further before commiting to development plans.

## Overview

This webhooks feeds data when a candidate profile is [created](http://v3-docs.idibu.com/article/289-uploading-candidates-article) or updated. You can use this webhook to:

- synchronize candidates created in idibu with your system,
- track any changes to their profiles,
- collect candidate's created numbers, their data and which step of the recruitment process are they currently at. You can potentially break this information down by additional parameters like location, current position and others,
- collect candidate data for analysis purposes - i.e. track which location brought most placed candidates, what is your most successful source, etc.
- and others!

## Data

Every webhook call contains selected candidate fields that are present on candidate's profile page in idibu:

- `id` - uniq candidate's identifier
- `firstname` - candidate's first name,
- `lastname` - we're sure you know what that is,
- `job_title` - candidate's last position as declared in CV,
- `phone` - candidate's landline number,
- `phone_mobile` - candidate's mobile phone number,
- `email` - you guessed it, candidate's email,
- `address` - candidate's physical address,
- `location`
  - `lat`
  - `lng`
- `country` - the 3 field geolocation data on candidate's location,
- `background_info` - field that can be populated by a consultant with his insights on the candidate,
- `work_history` - candidates encoded work history broken into periods from latest to oldest with position title, employed dates, employer and summary of the position.
- `education_history` - candidates encoded education history broken into periods from latest to oldest with course name, education dates, school and course summary.

*Both work_history and education_history are parsed from candidate's CV and thus presence of all elements, its quality and detail depend on the CV itself and the success of the parsing process. Expect possible, thought rare, inconsistencies.*

- `created_by`
  - `id` - uniq user identifier
  - `firstname` - name of the consultant who added the candidate to the system or original owner of the vacancy the applicant applied for,
  - `lastname` - surname, as above.
- `creation_date` - date candidate was originally added to the system
- `source` - candidates original source,
- `vacancies`
  - `id` - uniq vacancy identifier
  - `reference` - vacancy reference
  - `title` - vacancy title
  - `status` 
    - `status_id` - candidate's status id
    - `status_type` - candidate's status type
- `attachments`
  - `file_id` - uniq file identifier
  - `filename` - 
  - `file_link` - 
  - `type` -
- `custom_fields`
  - `value` - 
  - `name` - 

## Examples

### Vacancy added example

*Header*

```
Request URL: https://requestb.in/y9gkwoy9
Request method: POST
User-Agent: Idibu-Hookshot
X-Idibu-Delivery: f38a0abc-dc1d-4e3c-bb63-dfc1acd9ce88
X-Idibu-Event: candidate-extend.update
Content-Type: application/json
```

*Payload*
```
{
  "payload": {
    "id": "13359",
    "firstname": "John",
    "lastname": "Doe",
    "job_title": "People and Performance Superintendent",
    "phone": "",
    "phone_mobile": "",
    "email": "john.doe@exmaple.com",
    "address": "",
    "location": {
      "lat": "0",
      "lng": "0"
    },
    "country": "",
    "background_info": "",
    "created_by": {
      "id": "164",
      "firstname": "bugtest2",
      "lastname": "bugtest2"
    },
    "creation_date": "2017-06-28 15:57:55",
    "source": "Added manually",
    "vacancies": [
      {
        "id": "4526",
        "reference": "BB-74",
        "title": "Brand new vacancy update",
        "status": {
          "status_id": "10",
          "status_type": "default"
        }
      }
    ],
    "attachments": [
      {
        "file_id": "15097",
        "filename": "Resume_John_Doe_E2P_16-07-11.pdf",
        "file_link": "https://v3-beta.idibu.com/c/cloud/get-file/clientID/164/type/apptrack/file/Y3ZfZGF0YV8yMDE3XzA2LzE2NC8xMy9lMDMzMjM3ZDQwZjI5YTAwYzljMzhiNTc0MmUzZGVlZC5wZGY=/id/15097",
        "type": "cv_doc"
      }
    ],
    "custom_fields": [
      {
        "value": "",
        "name": "Current"
      },
      {
        "value": "No",
        "name": "Willing to relocate"
      },
      {
        "value": "",
        "name": "Will he/she ask questions?"
      }
    ]
  },
  "payload-information": {
    "timestamp": "2017-07-03T10:25:44+01:00",
    "webhook_event": "candidate.update"
  }
}
```


