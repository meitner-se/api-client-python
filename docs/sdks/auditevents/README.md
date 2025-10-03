# AuditEvents
(*audit_events*)

## Overview

### Available Operations

* [list](#list) - List AuditEvents
* [search](#search) - Search AuditEvents
* [get](#get) - Get a AuditEvent

## list

Returns a paginated list of all `AuditEvents` in your organization.

### Example Usage

<!-- UsageSnippet language="python" operationID="AuditEventList" method="get" path="/audit-event" -->
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
        client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
    ),
) as m_client:

    res = m_client.audit_events.list(limit=1, offset=0)

    while res is not None:
        # Handle items

        res = res.next()

```

### Parameters

| Parameter                                                                                                 | Type                                                                                                      | Required                                                                                                  | Description                                                                                               | Example                                                                                                   |
| --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| `limit`                                                                                                   | *Optional[int]*                                                                                           | :heavy_minus_sign:                                                                                        | The maximum number of AuditEvents to return (default: 50) when listing AuditEvents                        | 1                                                                                                         |
| `offset`                                                                                                  | *Optional[int]*                                                                                           | :heavy_minus_sign:                                                                                        | The number of AuditEvents to skip before starting to return results (default: 0) when listing AuditEvents | 0                                                                                                         |
| `retries`                                                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                          | :heavy_minus_sign:                                                                                        | Configuration to override the default retry behavior of the client.                                       |                                                                                                           |

### Response

**[models.AuditEventListResponse](../../models/auditeventlistresponse.md)**

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

## search

Search for `AuditEvents` with filtering capabilities.

### Example Usage

<!-- UsageSnippet language="python" operationID="AuditEventSearch" method="post" path="/audit-event/_search" -->
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

    res = m_client.audit_events.search(limit=1, offset=0, audit_event_filter={
        "equals": {
            "id": "123e4567-e89b-12d3-a456-426614174000",
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "created_by": "123e4567-e89b-12d3-a456-426614174000",
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_by": "123e4567-e89b-12d3-a456-426614174000",
            },
            "timestamp": parse_datetime("2024-01-15T10:30:00Z"),
            "resource_id": "123e4567-e89b-12d3-a456-426614174000",
        },
        "not_equals": {
            "id": "123e4567-e89b-12d3-a456-426614174000",
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "created_by": "123e4567-e89b-12d3-a456-426614174000",
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_by": "123e4567-e89b-12d3-a456-426614174000",
            },
            "timestamp": parse_datetime("2024-01-15T10:30:00Z"),
            "resource_id": "123e4567-e89b-12d3-a456-426614174000",
        },
        "greater_than": {
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
            },
            "timestamp": parse_datetime("2024-01-15T10:30:00Z"),
        },
        "smaller_than": {
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
            },
            "timestamp": parse_datetime("2024-01-15T10:30:00Z"),
        },
        "greater_or_equal": {
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
            },
            "timestamp": parse_datetime("2024-01-15T10:30:00Z"),
        },
        "smaller_or_equal": {
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
            },
            "timestamp": parse_datetime("2024-01-15T10:30:00Z"),
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
            "resource_id": [
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
            "resource_id": [
                "123e4567-e89b-12d3-a456-426614174000",
            ],
        },
        "null": {
            "meta": {
                "created_by": True,
                "updated_at": True,
                "updated_by": True,
            },
        },
        "not_null": {
            "meta": {
                "created_by": True,
                "updated_at": True,
                "updated_by": True,
            },
        },
        "or_condition": True,
    })

    while res is not None:
        # Handle items

        res = res.next()

```

### Parameters

| Parameter                                                                                                   | Type                                                                                                        | Required                                                                                                    | Description                                                                                                 | Example                                                                                                     |
| ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| `limit`                                                                                                     | *Optional[int]*                                                                                             | :heavy_minus_sign:                                                                                          | The maximum number of AuditEvents to return (default: 50) when searching AuditEvents                        | 1                                                                                                           |
| `offset`                                                                                                    | *Optional[int]*                                                                                             | :heavy_minus_sign:                                                                                          | The number of AuditEvents to skip before starting to return results (default: 0) when searching AuditEvents | 0                                                                                                           |
| `audit_event_filter`                                                                                        | [Optional[models.AuditEventFilter]](../../models/auditeventfilter.md)                                       | :heavy_minus_sign:                                                                                          | Request body                                                                                                |                                                                                                             |
| `retries`                                                                                                   | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                            | :heavy_minus_sign:                                                                                          | Configuration to override the default retry behavior of the client.                                         |                                                                                                             |

### Response

**[models.AuditEventSearchResponse](../../models/auditeventsearchresponse.md)**

### Errors

| Error Type                                  | Status Code                                 | Content Type                                |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| errors.Error400ResponseBody                 | 400                                         | application/json                            |
| errors.Error401ResponseBody                 | 401                                         | application/json                            |
| errors.Error403ResponseBody                 | 403                                         | application/json                            |
| errors.Error404ResponseBody                 | 404                                         | application/json                            |
| errors.Error409ResponseBody                 | 409                                         | application/json                            |
| errors.AuditEventSearch422ResponseBodyError | 422                                         | application/json                            |
| errors.Error429ResponseBody                 | 429                                         | application/json                            |
| errors.Error500ResponseBody                 | 500                                         | application/json                            |
| errors.MeitnerDefaultError                  | 4XX, 5XX                                    | \*/\*                                       |

## get

Retrieves the `AuditEvent` with the given ID.

### Example Usage

<!-- UsageSnippet language="python" operationID="AuditEventGet" method="get" path="/audit-event/{id}" -->
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
        client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
    ),
) as m_client:

    res = m_client.audit_events.get(id="123e4567-e89b-12d3-a456-426614174000")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | The unique identifier of the AuditEvent to retrieve                 | 123e4567-e89b-12d3-a456-426614174000                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.AuditEvent](../../models/auditevent.md)**

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