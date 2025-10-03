# Groups
(*groups*)

## Overview

### Available Operations

* [list](#list) - List Groups
* [create](#create) - Create a new Group
* [search](#search) - Search Groups
* [get](#get) - Get a Group
* [delete](#delete) - Delete a Group
* [update](#update) - Update a Group

## list

Returns a paginated list of all `Groups` in your organization.

### Example Usage

<!-- UsageSnippet language="python" operationID="GroupList" method="get" path="/group" -->
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
        client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
    ),
) as m_client:

    res = m_client.groups.list(limit=1, offset=0)

    while res is not None:
        # Handle items

        res = res.next()

```

### Parameters

| Parameter                                                                                       | Type                                                                                            | Required                                                                                        | Description                                                                                     | Example                                                                                         |
| ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| `limit`                                                                                         | *Optional[int]*                                                                                 | :heavy_minus_sign:                                                                              | The maximum number of Groups to return (default: 50) when listing Groups                        | 1                                                                                               |
| `offset`                                                                                        | *Optional[int]*                                                                                 | :heavy_minus_sign:                                                                              | The number of Groups to skip before starting to return results (default: 0) when listing Groups | 0                                                                                               |
| `retries`                                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                | :heavy_minus_sign:                                                                              | Configuration to override the default retry behavior of the client.                             |                                                                                                 |

### Response

**[models.GroupListResponse](../../models/grouplistresponse.md)**

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

Create a new Group

### Example Usage

<!-- UsageSnippet language="python" operationID="GroupCreate" method="post" path="/group" -->
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
        client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
    ),
) as m_client:

    res = m_client.groups.create(school_id="123e4567-e89b-12d3-a456-426614174000", title="1A", external={
        "source_id": "12345678",
    }, category="Education", types=[
        "Class",
    ], moderator_i_ds=[
        "123e4567-e89b-12d3-a456-426614174000",
    ], member_i_ds=[
        "123e4567-e89b-12d3-a456-426614174000",
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                                        | Type                                                                                                                                                                                                                             | Required                                                                                                                                                                                                                         | Description                                                                                                                                                                                                                      | Example                                                                                                                                                                                                                          |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `school_id`                                                                                                                                                                                                                      | *str*                                                                                                                                                                                                                            | :heavy_check_mark:                                                                                                                                                                                                               | The ID of the school the group belongs to                                                                                                                                                                                        | 123e4567-e89b-12d3-a456-426614174000                                                                                                                                                                                             |
| `title`                                                                                                                                                                                                                          | *str*                                                                                                                                                                                                                            | :heavy_check_mark:                                                                                                                                                                                                               | The title of the group, must be unique within the school.                                                                                                                                                                        | 1A                                                                                                                                                                                                                               |
| `external`                                                                                                                                                                                                                       | [Optional[models.GroupCreateExternal]](../../models/groupcreateexternal.md)                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                               | External is the External-object used on Update and Create operations, since it should only be allowed to set SourceID for the employee, the Source-field is not included.                                                        | {<br/>"sourceID": "12345678"<br/>}                                                                                                                                                                                               |
| `category`                                                                                                                                                                                                                       | [Optional[models.CategoryRequestBody]](../../models/categoryrequestbody.md)                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                               | If the category is Education, the ModeratorIDs have to be employees and the MemberIDs have to be students of the school. If the category is Other, it will not be possible to use the IsClass, IsChildcare and IsMentor fields.<br/> | Education                                                                                                                                                                                                                        |
| `types`                                                                                                                                                                                                                          | List[[models.GroupType](../../models/grouptype.md)]                                                                                                                                                                              | :heavy_minus_sign:                                                                                                                                                                                                               | The types of the group                                                                                                                                                                                                           | [<br/>"Class"<br/>]                                                                                                                                                                                                              |
| `moderator_i_ds`                                                                                                                                                                                                                 | List[*str*]                                                                                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                               | The IDs of the moderators of the group.  Can be any user type (Student, Employee, Guardian) if the Category is Other. If the Category is Education, the Moderators have to be employees of the school.<br/>                      | [<br/>"123e4567-e89b-12d3-a456-426614174000"<br/>]                                                                                                                                                                               |
| `member_i_ds`                                                                                                                                                                                                                    | List[*str*]                                                                                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                               | The IDs of the members of the group. Can be any user type (Student, Employee, Guardian) if the Category is Other. If the Category is Education, the Members have to be students of the school.<br/>                              | [<br/>"123e4567-e89b-12d3-a456-426614174000"<br/>]                                                                                                                                                                               |
| `retries`                                                                                                                                                                                                                        | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                                                               | Configuration to override the default retry behavior of the client.                                                                                                                                                              |                                                                                                                                                                                                                                  |

### Response

**[models.Group](../../models/group.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| errors.Error400ResponseBody            | 400                                    | application/json                       |
| errors.Error401ResponseBody            | 401                                    | application/json                       |
| errors.Error403ResponseBody            | 403                                    | application/json                       |
| errors.Error404ResponseBody            | 404                                    | application/json                       |
| errors.Error409ResponseBody            | 409                                    | application/json                       |
| errors.GroupCreate422ResponseBodyError | 422                                    | application/json                       |
| errors.Error429ResponseBody            | 429                                    | application/json                       |
| errors.Error500ResponseBody            | 500                                    | application/json                       |
| errors.MeitnerDefaultError             | 4XX, 5XX                               | \*/\*                                  |

## search

Search for `Groups` with filtering capabilities.

### Example Usage

<!-- UsageSnippet language="python" operationID="GroupSearch" method="post" path="/group/_search" -->
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

    res = m_client.groups.search(limit=1, offset=0, group_filter={
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
            "school_id": "123e4567-e89b-12d3-a456-426614174000",
            "title": "example",
            "moderator_i_ds": "123e4567-e89b-12d3-a456-426614174000",
            "member_i_ds": "123e4567-e89b-12d3-a456-426614174000",
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
            "school_id": "123e4567-e89b-12d3-a456-426614174000",
            "title": "example",
            "moderator_i_ds": "123e4567-e89b-12d3-a456-426614174000",
            "member_i_ds": "123e4567-e89b-12d3-a456-426614174000",
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
            "school_id": [
                "123e4567-e89b-12d3-a456-426614174000",
            ],
            "title": [
                "example",
            ],
            "moderator_i_ds": [
                "123e4567-e89b-12d3-a456-426614174000",
            ],
            "member_i_ds": [
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
            "school_id": [
                "123e4567-e89b-12d3-a456-426614174000",
            ],
            "title": [
                "example",
            ],
            "moderator_i_ds": [
                "123e4567-e89b-12d3-a456-426614174000",
            ],
            "member_i_ds": [
                "123e4567-e89b-12d3-a456-426614174000",
            ],
        },
        "like": {
            "external": {
                "source_id": "example",
                "source": "example",
            },
            "title": "example",
        },
        "not_like": {
            "external": {
                "source_id": "example",
                "source": "example",
            },
            "title": "example",
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
            "types": True,
            "moderator_i_ds": True,
            "member_i_ds": True,
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
            "types": True,
            "moderator_i_ds": True,
            "member_i_ds": True,
        },
        "or_condition": True,
    })

    while res is not None:
        # Handle items

        res = res.next()

```

### Parameters

| Parameter                                                                                         | Type                                                                                              | Required                                                                                          | Description                                                                                       | Example                                                                                           |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| `limit`                                                                                           | *Optional[int]*                                                                                   | :heavy_minus_sign:                                                                                | The maximum number of Groups to return (default: 50) when searching Groups                        | 1                                                                                                 |
| `offset`                                                                                          | *Optional[int]*                                                                                   | :heavy_minus_sign:                                                                                | The number of Groups to skip before starting to return results (default: 0) when searching Groups | 0                                                                                                 |
| `group_filter`                                                                                    | [Optional[models.GroupFilter]](../../models/groupfilter.md)                                       | :heavy_minus_sign:                                                                                | Request body                                                                                      |                                                                                                   |
| `retries`                                                                                         | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                  | :heavy_minus_sign:                                                                                | Configuration to override the default retry behavior of the client.                               |                                                                                                   |

### Response

**[models.GroupSearchResponse](../../models/groupsearchresponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| errors.Error400ResponseBody            | 400                                    | application/json                       |
| errors.Error401ResponseBody            | 401                                    | application/json                       |
| errors.Error403ResponseBody            | 403                                    | application/json                       |
| errors.Error404ResponseBody            | 404                                    | application/json                       |
| errors.Error409ResponseBody            | 409                                    | application/json                       |
| errors.GroupSearch422ResponseBodyError | 422                                    | application/json                       |
| errors.Error429ResponseBody            | 429                                    | application/json                       |
| errors.Error500ResponseBody            | 500                                    | application/json                       |
| errors.MeitnerDefaultError             | 4XX, 5XX                               | \*/\*                                  |

## get

Retrieves the `Group` with the given ID.

### Example Usage

<!-- UsageSnippet language="python" operationID="GroupGet" method="get" path="/group/{id}" -->
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
        client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
    ),
) as m_client:

    res = m_client.groups.get(id="123e4567-e89b-12d3-a456-426614174000")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | The unique identifier of the Group to retrieve                      | 123e4567-e89b-12d3-a456-426614174000                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.Group](../../models/group.md)**

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

Delete a Group

### Example Usage

<!-- UsageSnippet language="python" operationID="GroupDelete" method="delete" path="/group/{id}" -->
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
        client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
    ),
) as m_client:

    m_client.groups.delete(id="123e4567-e89b-12d3-a456-426614174000")

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | The unique identifier of the Group to delete                        | 123e4567-e89b-12d3-a456-426614174000                                |
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

Update a Group

### Example Usage

<!-- UsageSnippet language="python" operationID="GroupUpdate" method="patch" path="/group/{id}" -->
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
        client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
    ),
) as m_client:

    res = m_client.groups.update(id="123e4567-e89b-12d3-a456-426614174000", title="1A", external={
        "source_id": "12345678",
    }, types=[
        "Class",
    ], moderator_i_ds=[
        "123e4567-e89b-12d3-a456-426614174000",
    ], member_i_ds=[
        "123e4567-e89b-12d3-a456-426614174000",
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                               | Type                                                                                                                                                                                                    | Required                                                                                                                                                                                                | Description                                                                                                                                                                                             | Example                                                                                                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                                                                                                                    | *str*                                                                                                                                                                                                   | :heavy_check_mark:                                                                                                                                                                                      | The unique identifier of the Group to update                                                                                                                                                            | 123e4567-e89b-12d3-a456-426614174000                                                                                                                                                                    |
| `title`                                                                                                                                                                                                 | *str*                                                                                                                                                                                                   | :heavy_check_mark:                                                                                                                                                                                      | The title of the group, must be unique within the school.                                                                                                                                               | 1A                                                                                                                                                                                                      |
| `external`                                                                                                                                                                                              | [Optional[models.GroupUpdateExternal]](../../models/groupupdateexternal.md)                                                                                                                             | :heavy_minus_sign:                                                                                                                                                                                      | External is the External-object used on Update and Create operations, since it should only be allowed to set SourceID for the employee, the Source-field is not included.                               | {<br/>"sourceID": "12345678"<br/>}                                                                                                                                                                      |
| `types`                                                                                                                                                                                                 | List[[models.GroupType](../../models/grouptype.md)]                                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                      | The types of the group                                                                                                                                                                                  | [<br/>"Class"<br/>]                                                                                                                                                                                     |
| `moderator_i_ds`                                                                                                                                                                                        | List[*str*]                                                                                                                                                                                             | :heavy_minus_sign:                                                                                                                                                                                      | The IDs of the moderators of the group.  Can be any user type (Student, Employee, Guardian) if the Category is Other. If the Category is Education, the Moderators have to be employees of the school.<br/> | [<br/>"123e4567-e89b-12d3-a456-426614174000"<br/>]                                                                                                                                                      |
| `member_i_ds`                                                                                                                                                                                           | List[*str*]                                                                                                                                                                                             | :heavy_minus_sign:                                                                                                                                                                                      | The IDs of the members of the group. Can be any user type (Student, Employee, Guardian) if the Category is Other. If the Category is Education, the Members have to be students of the school.<br/>     | [<br/>"123e4567-e89b-12d3-a456-426614174000"<br/>]                                                                                                                                                      |
| `retries`                                                                                                                                                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                        | :heavy_minus_sign:                                                                                                                                                                                      | Configuration to override the default retry behavior of the client.                                                                                                                                     |                                                                                                                                                                                                         |

### Response

**[models.Group](../../models/group.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| errors.Error400ResponseBody            | 400                                    | application/json                       |
| errors.Error401ResponseBody            | 401                                    | application/json                       |
| errors.Error403ResponseBody            | 403                                    | application/json                       |
| errors.Error404ResponseBody            | 404                                    | application/json                       |
| errors.Error409ResponseBody            | 409                                    | application/json                       |
| errors.GroupUpdate422ResponseBodyError | 422                                    | application/json                       |
| errors.Error429ResponseBody            | 429                                    | application/json                       |
| errors.Error500ResponseBody            | 500                                    | application/json                       |
| errors.MeitnerDefaultError             | 4XX, 5XX                               | \*/\*                                  |