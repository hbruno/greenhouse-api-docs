# Custom Fields

An organization's custom_fields.

## The custom field object

```json
{
  "id": 123456,
  "name": "Custom Field Name",
  "field_type": "job",
  "priority": 1,
  "value_type": "single_select",
  "private": true,
  "required": false,
  "require_approval": true,
  "trigger_new_version": false,
  "name_key": "custom_field_name",
  "custom_field_options": [
    {
      "id": 123,
      "name": "Name One",
      "priority": 1
    },
    {
      "id": 234,
      "name": "Name Two",
      "priority": 2
    }
  ]
}
```

### Noteworthy attributes

| Attribute | Description |
|-----------|-------------|
| id | The custom field's unique identifier |
| name | The field's name in Greenhouse |
| field_type | One of job, candidate, application, offer, rejection_question, referral_question. This is also included in the URL as an argument, which will return only custom fields that match the given type.
| priority | Numeric field used for ordering in Greenhouse.
| value_type | One of short_text, long_text, yes_no, single_select, multi_select, currency, currency_range, number, number_range, date, url, or user
| private | Boolean value to say if this field is private in Greenhouse.
| required | The object this field exists on can not be saved if this value is not set.
| require_approval | Only applicable to job custom fields, changes to this fields requires an approval flow in Greenhouse to be re-done. 
| trigger_new_version | Only applicable to offer custom fields, changes to this field creates a new offer version.
| name_key | Listed as "immutable field key" in Greenhouse, this value is based of the name of the field when it is created and does not change as the field's name is later updated.
| custom_field_options | For single_select and multi_select field_types, this is the list of options for that select.
| custom_field_options.priority | Numeric value used for ordering the custom field options.

## GET: List Custom Fields

```shell
curl 'https://harvest.greenhouse.io/v1/custom_fields/{field_type}'
  -H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 123456,
    "name": "Custom Field Name",
    "field_type": "job",
    "priority": 1,
    "value_type": "single_select",
    "private": true,
    "required": false,
    "require_approval": true,
    "trigger_new_version": false,
    "name_key": "custom_field_name",
    "custom_field_options": [
      {
        "id": 123,
        "name": "Name One",
        "priority": 1
      },
      {
        "id": 234,
        "name": "Name Two",
        "priority": 2
      }
    ]
  }
]
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/custom_fields/{field_type}`

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
| field_type | Returns only custom fields of this type. For example, if “offer” is included in the URL as the field_type, the endpoint will only return custom fields with the “offer” field type. 

<br>
[See noteworthy response attributes.](#the-custom-field-object)

This endpoint supports pagination. See the [Pagination](#pagination) section for more detail.

## GET: Retrieve Custom Field

```shell
curl 'https://harvest.greenhouse.io/v1/custom_field/{id}'
  -H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
{
  "id": 123456,
  "name": "Custom Field Name",
  "field_type": "job",
  "priority": 1,
  "value_type": "single_select",
  "private": true,
  "required": false,
  "require_approval": true,
  "trigger_new_version": false,
  "name_key": "custom_field_name",
  "custom_field_options": [
    {
      "id": 123,
      "name": "Name One",
      "priority": 1
    },
    {
      "id": 234,
      "name": "Name Two",
      "priority": 2
    }
  ]
}
```
### HTTP Request

`GET https://harvest.greenhouse.io/v1/custom_field/{id}`


### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the custom field to retrieve

<br>
[See noteworthy response attributes.](#the-custom-field-object)