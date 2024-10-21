### Disclaimer

This is a work-in-progress article. Information provided here is subject to change and is not yet finalised.

## Overview

This webhook feeds data when a candidate profile is [created](http://v3-docs.idibu.com/article/289-uploading-candidates-article) or updated. You can use this webhook to:

- synchronize candidates created in idibu with your system,
- track any changes to their profiles,
- collect candidates' created numbers, their data and which step of the recruitment process are they currently at; you can potentially break this information down by additional parameters like location, current position, and others,
- collect candidate data for analysis purposes - i.e. track which location brought most placed candidates, what is your most successful source, etc.
- and others!

## Data

Every webhook call contains selected candidate fields that are present on the candidate's profile page in idibu:

- `id` - candidate's unique identifier inside the idibu system
- `firstname` - candidate's first name
- `lastname` - candidate's last name
- `comms_status` - either `applied` or `unsubscribed` if the candidate opted out of communications
- `email` - candidate's email address
- `background_info` - field that can be populated by a consultant with his insights on the candidate
- `created_by` - identifies the consultant who added the candidate to the system or the original owner of the vacancy the applicant applied for
  - `id` - unique identifier of the company account inside the idibu system
  - `profile_id` - unique identifier of the user profile inside the idibu system
  - `email` - consultant's email address
  - `firstname` - consultant's first name
  - `lastname` - consultant's last name
- `creation_date` - timestamp of when the candidate was originally added to the system
- `source` - the name of the source (e.g. a job board) of the candidate
- `vacancies` - identifies the vacancies for which the candidate applied
  - `id` - unique identifier of the vacancy inside the idibu system
  - `reference` - vacancy reference
  - `title` - vacancy title
  - `status` - candidate's current status against the vacancy
    - `status_id` - unique identifier of the ID inside the idibu system
    - `status_type` - either `default` (for system statuses) or `extra` (for custom statuses defined by the user)
    - `label` - name of the status
- `attachments` - lists all the files attached to the application
  - `file_id` - unique identifier of the file inside the idibu system
  - `filename` - full name and filetype extension of the file
  - `file_link` - URL that allows to download the file directly
  - `type` - type of the file (e.g. `cv_doc`, `image`, `note`, `document`, etc.)
- `payload-information`
  - `timestamp` - the exact timestamp of when the webhook was sent
  - `webhook_event` - either `candidate.create` or `candidate.update`

## Examples

### New candidate added to the Vacancy

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
		"id": "12345",
		"firstname": "Jess",
		"lastname": "Quincy",
		"comms_status": "applied",
		"email": "jessquincy@fakeemail.com",
		"background_info": "",
		"created_by": {
			"id": "123",
			"profile_id": "456",
			"email": "timparker@fakeemail.comm",
			"firstname": "Tim",
			"lastname": "Parker"
		},
		"creation_date": "2024-10-17T16:53:12+02:00",
		"videos": [],
		"source": "Aptrack Test Feed",
		"vacancies": [
			{
				"id": "98765",
				"reference": "TP-1234",
				"title": "Recruitment Consultant",
				"status": {
					"id": "11",
					"type": "default",
					"label": "Applicants"
				}
			}
		],
		"attachments": [
			{
				"file_id": "67890",
				"filename": "Jess_Quincy_CV.docx",
				"file_link": "https://v3.idibu.com/c/cloud/get-file/clientID/123/type/apptrack/file/oEYEdXIJ8rO5Cb8vBaGVqV0sI5Y6djzIDFx2TIsuquRUZUvFSBerrSbHa9MHyjstuU7exRO7OA9gi31z/id/67890",
				"type": "cv_doc"
			}
		]
	},
	"payload-information": {
		"timestamp": "2024-10-17T16:53:12+02:00",
		"webhook_event": "candidate.create"
	}
}
```


