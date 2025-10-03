# Guardians
(*guardians*)

## Overview

### Available Operations

* [list](#list) - List Guardians
* [create](#create) - Create a new Guardian
* [search](#search) - Search Guardians
* [get](#get) - Get a Guardian
* [delete](#delete) - Delete a Guardian
* [update](#update) - Update a Guardian

## list

Returns a paginated list of all `Guardians` in your organization.

### Example Usage

<!-- UsageSnippet language="python" operationID="GuardianList" method="get" path="/guardian" -->
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
        client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
    ),
) as m_client:

    res = m_client.guardians.list(limit=1, offset=0)

    while res is not None:
        # Handle items

        res = res.next()

```

### Parameters

| Parameter                                                                                             | Type                                                                                                  | Required                                                                                              | Description                                                                                           | Example                                                                                               |
| ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| `limit`                                                                                               | *Optional[int]*                                                                                       | :heavy_minus_sign:                                                                                    | The maximum number of Guardians to return (default: 50) when listing Guardians                        | 1                                                                                                     |
| `offset`                                                                                              | *Optional[int]*                                                                                       | :heavy_minus_sign:                                                                                    | The number of Guardians to skip before starting to return results (default: 0) when listing Guardians | 0                                                                                                     |
| `retries`                                                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                      | :heavy_minus_sign:                                                                                    | Configuration to override the default retry behavior of the client.                                   |                                                                                                       |

### Response

**[models.GuardianListResponse](../../models/guardianlistresponse.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| errors.Error400ResponseBody | 400                         | application/json            |
| errors.Error401ResponseBody | 401                         | application/json            |
| errors.Error403ResponseBody | 403                         | application/json            |
| errors.Error404ResponseBody | 404                         | application/json            |
| errors.Error409ResponseBody | 409                         | application/json            |
| errors.Error429ResponseBody | 429                         | application/json            |
| errors.Error500ResponseBody | 500                         | application/json            |
| errors.MeitnerDefaultError  | 4XX, 5XX                    | \*/\*                       |

## create

Create a new Guardian

### Example Usage

<!-- UsageSnippet language="python" operationID="GuardianCreate" method="post" path="/guardian" -->
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
        client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
    ),
) as m_client:

    res = m_client.guardians.create(identity_number="20191216-1234", first_name="Lise", last_name="Meitner", external={
        "source_id": "12345678",
    }, identity_temporary=True, address={
        "postal_address": "Dalvägen 14",
        "postal_code": "169 56",
        "postal_city": "Solna",
        "country_code": "SWE",
        "municipality_code": "0184",
    }, email_address1="lise@meitner.se", email_address2="lise@gmail.com", phone_number1="+46701234567", phone_number2="+46701234567", student_i_ds=[
        "123e4567-e89b-12d3-a456-426614174000",
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                                                       | Type                                                                                                                                                                                                                                            | Required                                                                                                                                                                                                                                        | Description                                                                                                                                                                                                                                     | Example                                                                                                                                                                                                                                         |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `identity_number`                                                                                                                                                                                                                               | *str*                                                                                                                                                                                                                                           | :heavy_check_mark:                                                                                                                                                                                                                              | The identity number of the guardian, must be unique within the organization.                                                                                                                                                                    | 20191216-1234                                                                                                                                                                                                                                   |
| `first_name`                                                                                                                                                                                                                                    | *str*                                                                                                                                                                                                                                           | :heavy_check_mark:                                                                                                                                                                                                                              | The first name of the guardian                                                                                                                                                                                                                  | Lise                                                                                                                                                                                                                                            |
| `last_name`                                                                                                                                                                                                                                     | *str*                                                                                                                                                                                                                                           | :heavy_check_mark:                                                                                                                                                                                                                              | The last name of the guardian                                                                                                                                                                                                                   | Meitner                                                                                                                                                                                                                                         |
| `external`                                                                                                                                                                                                                                      | [Optional[models.GuardianCreateExternal]](../../models/guardiancreateexternal.md)                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                                                              | ExternalRequest is the External-object used on Update and Create operations, since it should only be allowed to set SourceID for the guardian, the Source-field is not included.                                                                | {<br/>"sourceID": "12345678"<br/>}                                                                                                                                                                                                              |
| `identity_temporary`                                                                                                                                                                                                                            | *Optional[bool]*                                                                                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                                                                              | If the identity number is temporary for the guardian                                                                                                                                                                                            | true                                                                                                                                                                                                                                            |
| `address`                                                                                                                                                                                                                                       | [Optional[models.GuardianCreateAddress]](../../models/guardiancreateaddress.md)                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                                                                              | The address of the guardian                                                                                                                                                                                                                     | {<br/>"postalAddress": "Dalvägen 14",<br/>"postalCode": "169 56",<br/>"postalCity": "Solna",<br/>"countryCode": "SWE",<br/>"municipalityCode": "0184"<br/>}                                                                                     |
| `email_address1`                                                                                                                                                                                                                                | *OptionalNullable[str]*                                                                                                                                                                                                                         | :heavy_minus_sign:                                                                                                                                                                                                                              | The email address of the guardian, will be used for communication with the guardian from the system and must be unique within the organization.<br/>Can be used to login to the system if password-authentication is enabled for the organization.<br/> | lise@meitner.se                                                                                                                                                                                                                                 |
| `email_address2`                                                                                                                                                                                                                                | *OptionalNullable[str]*                                                                                                                                                                                                                         | :heavy_minus_sign:                                                                                                                                                                                                                              | The secondary email address of the guardian, will not be used within the system, but will be displayed for contact information.                                                                                                                 | lise@gmail.com                                                                                                                                                                                                                                  |
| `phone_number1`                                                                                                                                                                                                                                 | *OptionalNullable[str]*                                                                                                                                                                                                                         | :heavy_minus_sign:                                                                                                                                                                                                                              | The primary phone number of the guardian, will be used for communication with the guardian from the system.                                                                                                                                     | +46701234567                                                                                                                                                                                                                                    |
| `phone_number2`                                                                                                                                                                                                                                 | *OptionalNullable[str]*                                                                                                                                                                                                                         | :heavy_minus_sign:                                                                                                                                                                                                                              | The secondary phone number of the guardian, will not be used within the system, but will be displayed for contact information.                                                                                                                  | +46701234567                                                                                                                                                                                                                                    |
| `student_i_ds`                                                                                                                                                                                                                                  | List[*str*]                                                                                                                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                                                              | The IDs of the students the guardian is responsible for.                                                                                                                                                                                        | [<br/>"123e4567-e89b-12d3-a456-426614174000"<br/>]                                                                                                                                                                                              |
| `retries`                                                                                                                                                                                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                                                                              | Configuration to override the default retry behavior of the client.                                                                                                                                                                             |                                                                                                                                                                                                                                                 |

### Response

**[models.Guardian](../../models/guardian.md)**

### Errors

| Error Type                                | Status Code                               | Content Type                              |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| errors.Error400ResponseBody               | 400                                       | application/json                          |
| errors.Error401ResponseBody               | 401                                       | application/json                          |
| errors.Error403ResponseBody               | 403                                       | application/json                          |
| errors.Error404ResponseBody               | 404                                       | application/json                          |
| errors.Error409ResponseBody               | 409                                       | application/json                          |
| errors.GuardianCreate422ResponseBodyError | 422                                       | application/json                          |
| errors.Error429ResponseBody               | 429                                       | application/json                          |
| errors.Error500ResponseBody               | 500                                       | application/json                          |
| errors.MeitnerDefaultError                | 4XX, 5XX                                  | \*/\*                                     |

## search

Search for `Guardians` with filtering capabilities.

### Example Usage

<!-- UsageSnippet language="python" operationID="GuardianSearch" method="post" path="/guardian/_search" -->
```python
from meitner import Meitner, models
from meitner.utils import parse_datetime
import os


with Meitner(
    security=models.Security(
        client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
        client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
    ),
) as m_client:

    res = m_client.guardians.search(limit=1, offset=0, guardian_filter={
        "equals": {
            "id": "123e4567-e89b-12d3-a456-426614174000",
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "created_by": "123e4567-e89b-12d3-a456-426614174000",
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_by": "123e4567-e89b-12d3-a456-426614174000",
            },
            "external": {
                "source_id": "example",
                "source": "example",
            },
            "identity_number": "example",
            "identity_temporary": True,
            "first_name": "example",
            "last_name": "example",
            "address": {
                "postal_address": "example",
                "postal_code": "example",
                "postal_city": "example",
                "country_code": "example",
                "municipality_code": "example",
            },
            "email_address1": "example",
            "email_address2": "example",
            "phone_number1": "example",
            "phone_number2": "example",
            "student_i_ds": "123e4567-e89b-12d3-a456-426614174000",
        },
        "not_equals": {
            "id": "123e4567-e89b-12d3-a456-426614174000",
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "created_by": "123e4567-e89b-12d3-a456-426614174000",
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_by": "123e4567-e89b-12d3-a456-426614174000",
            },
            "external": {
                "source_id": "example",
                "source": "example",
            },
            "identity_number": "example",
            "identity_temporary": True,
            "first_name": "example",
            "last_name": "example",
            "address": {
                "postal_address": "example",
                "postal_code": "example",
                "postal_city": "example",
                "country_code": "example",
                "municipality_code": "example",
            },
            "email_address1": "example",
            "email_address2": "example",
            "phone_number1": "example",
            "phone_number2": "example",
            "student_i_ds": "123e4567-e89b-12d3-a456-426614174000",
        },
        "greater_than": {
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
            },
        },
        "smaller_than": {
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
            },
        },
        "greater_or_equal": {
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
            },
        },
        "smaller_or_equal": {
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
            },
        },
        "contains": {
            "id": [
                "123e4567-e89b-12d3-a456-426614174000",
            ],
            "meta": {
                "created_by": [
                    "123e4567-e89b-12d3-a456-426614174000",
                ],
                "updated_by": [
                    "123e4567-e89b-12d3-a456-426614174000",
                ],
            },
            "external": {
                "source_id": [
                    "example",
                ],
                "source": [
                    "example",
                ],
            },
            "identity_number": [
                "example",
            ],
            "identity_temporary": [
                True,
            ],
            "first_name": [
                "example",
            ],
            "last_name": [
                "example",
            ],
            "address": {
                "postal_address": [
                    "example",
                ],
                "postal_code": [
                    "example",
                ],
                "postal_city": [
                    "example",
                ],
                "country_code": [
                    "example",
                ],
                "municipality_code": [
                    "example",
                ],
            },
            "email_address1": [
                "example",
            ],
            "email_address2": [
                "example",
            ],
            "phone_number1": [
                "example",
            ],
            "phone_number2": [
                "example",
            ],
            "student_i_ds": [
                "123e4567-e89b-12d3-a456-426614174000",
            ],
        },
        "not_contains": {
            "id": [
                "123e4567-e89b-12d3-a456-426614174000",
            ],
            "meta": {
                "created_by": [
                    "123e4567-e89b-12d3-a456-426614174000",
                ],
                "updated_by": [
                    "123e4567-e89b-12d3-a456-426614174000",
                ],
            },
            "external": {
                "source_id": [
                    "example",
                ],
                "source": [
                    "example",
                ],
            },
            "identity_number": [
                "example",
            ],
            "identity_temporary": [
                True,
            ],
            "first_name": [
                "example",
            ],
            "last_name": [
                "example",
            ],
            "address": {
                "postal_address": [
                    "example",
                ],
                "postal_code": [
                    "example",
                ],
                "postal_city": [
                    "example",
                ],
                "country_code": [
                    "example",
                ],
                "municipality_code": [
                    "example",
                ],
            },
            "email_address1": [
                "example",
            ],
            "email_address2": [
                "example",
            ],
            "phone_number1": [
                "example",
            ],
            "phone_number2": [
                "example",
            ],
            "student_i_ds": [
                "123e4567-e89b-12d3-a456-426614174000",
            ],
        },
        "like": {
            "external": {
                "source_id": "example",
                "source": "example",
            },
            "identity_number": "example",
            "first_name": "example",
            "last_name": "example",
            "address": {
                "postal_address": "example",
                "postal_code": "example",
                "postal_city": "example",
                "country_code": "example",
                "municipality_code": "example",
            },
            "email_address1": "example",
            "email_address2": "example",
            "phone_number1": "example",
            "phone_number2": "example",
        },
        "not_like": {
            "external": {
                "source_id": "example",
                "source": "example",
            },
            "identity_number": "example",
            "first_name": "example",
            "last_name": "example",
            "address": {
                "postal_address": "example",
                "postal_code": "example",
                "postal_city": "example",
                "country_code": "example",
                "municipality_code": "example",
            },
            "email_address1": "example",
            "email_address2": "example",
            "phone_number1": "example",
            "phone_number2": "example",
        },
        "null": {
            "meta": {
                "created_by": True,
                "updated_at": True,
                "updated_by": True,
            },
            "external": {
                "source_id": True,
                "source": True,
            },
            "address": {
                "postal_address": True,
                "postal_code": True,
                "postal_city": True,
                "country_code": True,
                "municipality_code": True,
            },
            "email_address1": True,
            "email_address2": True,
            "phone_number1": True,
            "phone_number2": True,
            "student_i_ds": True,
        },
        "not_null": {
            "meta": {
                "created_by": True,
                "updated_at": True,
                "updated_by": True,
            },
            "external": {
                "source_id": True,
                "source": True,
            },
            "address": {
                "postal_address": True,
                "postal_code": True,
                "postal_city": True,
                "country_code": True,
                "municipality_code": True,
            },
            "email_address1": True,
            "email_address2": True,
            "phone_number1": True,
            "phone_number2": True,
            "student_i_ds": True,
        },
        "or_condition": True,
    })

    while res is not None:
        # Handle items

        res = res.next()

```

### Parameters

| Parameter                                                                                               | Type                                                                                                    | Required                                                                                                | Description                                                                                             | Example                                                                                                 |
| ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `limit`                                                                                                 | *Optional[int]*                                                                                         | :heavy_minus_sign:                                                                                      | The maximum number of Guardians to return (default: 50) when searching Guardians                        | 1                                                                                                       |
| `offset`                                                                                                | *Optional[int]*                                                                                         | :heavy_minus_sign:                                                                                      | The number of Guardians to skip before starting to return results (default: 0) when searching Guardians | 0                                                                                                       |
| `guardian_filter`                                                                                       | [Optional[models.GuardianFilter]](../../models/guardianfilter.md)                                       | :heavy_minus_sign:                                                                                      | Request body                                                                                            |                                                                                                         |
| `retries`                                                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                        | :heavy_minus_sign:                                                                                      | Configuration to override the default retry behavior of the client.                                     |                                                                                                         |

### Response

**[models.GuardianSearchResponse](../../models/guardiansearchresponse.md)**

### Errors

| Error Type                                | Status Code                               | Content Type                              |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| errors.Error400ResponseBody               | 400                                       | application/json                          |
| errors.Error401ResponseBody               | 401                                       | application/json                          |
| errors.Error403ResponseBody               | 403                                       | application/json                          |
| errors.Error404ResponseBody               | 404                                       | application/json                          |
| errors.Error409ResponseBody               | 409                                       | application/json                          |
| errors.GuardianSearch422ResponseBodyError | 422                                       | application/json                          |
| errors.Error429ResponseBody               | 429                                       | application/json                          |
| errors.Error500ResponseBody               | 500                                       | application/json                          |
| errors.MeitnerDefaultError                | 4XX, 5XX                                  | \*/\*                                     |

## get

Retrieves the `Guardian` with the given ID.

### Example Usage

<!-- UsageSnippet language="python" operationID="GuardianGet" method="get" path="/guardian/{id}" -->
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
        client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
    ),
) as m_client:

    res = m_client.guardians.get(id="123e4567-e89b-12d3-a456-426614174000")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | The unique identifier of the Guardian to retrieve                   | 123e4567-e89b-12d3-a456-426614174000                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.Guardian](../../models/guardian.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| errors.Error400ResponseBody | 400                         | application/json            |
| errors.Error401ResponseBody | 401                         | application/json            |
| errors.Error403ResponseBody | 403                         | application/json            |
| errors.Error404ResponseBody | 404                         | application/json            |
| errors.Error409ResponseBody | 409                         | application/json            |
| errors.Error429ResponseBody | 429                         | application/json            |
| errors.Error500ResponseBody | 500                         | application/json            |
| errors.MeitnerDefaultError  | 4XX, 5XX                    | \*/\*                       |

## delete

Delete a Guardian

### Example Usage

<!-- UsageSnippet language="python" operationID="GuardianDelete" method="delete" path="/guardian/{id}" -->
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
        client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
    ),
) as m_client:

    m_client.guardians.delete(id="123e4567-e89b-12d3-a456-426614174000")

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | The unique identifier of the Guardian to delete                     | 123e4567-e89b-12d3-a456-426614174000                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| errors.Error400ResponseBody | 400                         | application/json            |
| errors.Error401ResponseBody | 401                         | application/json            |
| errors.Error403ResponseBody | 403                         | application/json            |
| errors.Error404ResponseBody | 404                         | application/json            |
| errors.Error409ResponseBody | 409                         | application/json            |
| errors.Error429ResponseBody | 429                         | application/json            |
| errors.Error500ResponseBody | 500                         | application/json            |
| errors.MeitnerDefaultError  | 4XX, 5XX                    | \*/\*                       |

## update

Update a Guardian

### Example Usage

<!-- UsageSnippet language="python" operationID="GuardianUpdate" method="patch" path="/guardian/{id}" -->
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
        client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
    ),
) as m_client:

    res = m_client.guardians.update(id="123e4567-e89b-12d3-a456-426614174000", identity_number="20191216-1234", first_name="Lise", last_name="Meitner", external={
        "source_id": "12345678",
    }, identity_temporary=True, address={
        "postal_address": "Dalvägen 14",
        "postal_code": "169 56",
        "postal_city": "Solna",
        "country_code": "SWE",
        "municipality_code": "0184",
    }, email_address1="lise@meitner.se", email_address2="lise@gmail.com", phone_number1="+46701234567", phone_number2="+46701234567", student_i_ds=[
        "123e4567-e89b-12d3-a456-426614174000",
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                                                       | Type                                                                                                                                                                                                                                            | Required                                                                                                                                                                                                                                        | Description                                                                                                                                                                                                                                     | Example                                                                                                                                                                                                                                         |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                                                                                                                                                            | *str*                                                                                                                                                                                                                                           | :heavy_check_mark:                                                                                                                                                                                                                              | The unique identifier of the Guardian to update                                                                                                                                                                                                 | 123e4567-e89b-12d3-a456-426614174000                                                                                                                                                                                                            |
| `identity_number`                                                                                                                                                                                                                               | *str*                                                                                                                                                                                                                                           | :heavy_check_mark:                                                                                                                                                                                                                              | The identity number of the guardian, must be unique within the organization.                                                                                                                                                                    | 20191216-1234                                                                                                                                                                                                                                   |
| `first_name`                                                                                                                                                                                                                                    | *str*                                                                                                                                                                                                                                           | :heavy_check_mark:                                                                                                                                                                                                                              | The first name of the guardian                                                                                                                                                                                                                  | Lise                                                                                                                                                                                                                                            |
| `last_name`                                                                                                                                                                                                                                     | *str*                                                                                                                                                                                                                                           | :heavy_check_mark:                                                                                                                                                                                                                              | The last name of the guardian                                                                                                                                                                                                                   | Meitner                                                                                                                                                                                                                                         |
| `external`                                                                                                                                                                                                                                      | [Optional[models.GuardianUpdateExternal]](../../models/guardianupdateexternal.md)                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                                                              | ExternalRequest is the External-object used on Update and Create operations, since it should only be allowed to set SourceID for the guardian, the Source-field is not included.                                                                | {<br/>"sourceID": "12345678"<br/>}                                                                                                                                                                                                              |
| `identity_temporary`                                                                                                                                                                                                                            | *Optional[bool]*                                                                                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                                                                              | If the identity number is temporary for the guardian                                                                                                                                                                                            | true                                                                                                                                                                                                                                            |
| `address`                                                                                                                                                                                                                                       | [Optional[models.GuardianUpdateAddress]](../../models/guardianupdateaddress.md)                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                                                                              | The address of the guardian                                                                                                                                                                                                                     | {<br/>"postalAddress": "Dalvägen 14",<br/>"postalCode": "169 56",<br/>"postalCity": "Solna",<br/>"countryCode": "SWE",<br/>"municipalityCode": "0184"<br/>}                                                                                     |
| `email_address1`                                                                                                                                                                                                                                | *OptionalNullable[str]*                                                                                                                                                                                                                         | :heavy_minus_sign:                                                                                                                                                                                                                              | The email address of the guardian, will be used for communication with the guardian from the system and must be unique within the organization.<br/>Can be used to login to the system if password-authentication is enabled for the organization.<br/> | lise@meitner.se                                                                                                                                                                                                                                 |
| `email_address2`                                                                                                                                                                                                                                | *OptionalNullable[str]*                                                                                                                                                                                                                         | :heavy_minus_sign:                                                                                                                                                                                                                              | The secondary email address of the guardian, will not be used within the system, but will be displayed for contact information.                                                                                                                 | lise@gmail.com                                                                                                                                                                                                                                  |
| `phone_number1`                                                                                                                                                                                                                                 | *OptionalNullable[str]*                                                                                                                                                                                                                         | :heavy_minus_sign:                                                                                                                                                                                                                              | The primary phone number of the guardian, will be used for communication with the guardian from the system.                                                                                                                                     | +46701234567                                                                                                                                                                                                                                    |
| `phone_number2`                                                                                                                                                                                                                                 | *OptionalNullable[str]*                                                                                                                                                                                                                         | :heavy_minus_sign:                                                                                                                                                                                                                              | The secondary phone number of the guardian, will not be used within the system, but will be displayed for contact information.                                                                                                                  | +46701234567                                                                                                                                                                                                                                    |
| `student_i_ds`                                                                                                                                                                                                                                  | List[*str*]                                                                                                                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                                                              | The IDs of the students the guardian is responsible for.                                                                                                                                                                                        | [<br/>"123e4567-e89b-12d3-a456-426614174000"<br/>]                                                                                                                                                                                              |
| `retries`                                                                                                                                                                                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                                                                              | Configuration to override the default retry behavior of the client.                                                                                                                                                                             |                                                                                                                                                                                                                                                 |

### Response

**[models.Guardian](../../models/guardian.md)**

### Errors

| Error Type                                | Status Code                               | Content Type                              |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| errors.Error400ResponseBody               | 400                                       | application/json                          |
| errors.Error401ResponseBody               | 401                                       | application/json                          |
| errors.Error403ResponseBody               | 403                                       | application/json                          |
| errors.Error404ResponseBody               | 404                                       | application/json                          |
| errors.Error409ResponseBody               | 409                                       | application/json                          |
| errors.GuardianUpdate422ResponseBodyError | 422                                       | application/json                          |
| errors.Error429ResponseBody               | 429                                       | application/json                          |
| errors.Error500ResponseBody               | 500                                       | application/json                          |
| errors.MeitnerDefaultError                | 4XX, 5XX                                  | \*/\*                                     |