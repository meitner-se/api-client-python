# meitner

Developer-friendly & type-safe Python SDK specifically catered to leverage *meitner* API.

<div align="left">
    <a href="https://www.speakeasy.com/?utm_source=meitner&utm_campaign=python"><img src="https://www.speakeasy.com/assets/badges/built-by-speakeasy.svg" /></a>
    <a href="https://opensource.org/licenses/MIT">
        <img src="https://img.shields.io/badge/License-MIT-blue.svg" style="width: 100px; height: 28px;" />
    </a>
</div>


<br /><br />
> [!IMPORTANT]
> This SDK is not yet ready for production use. To complete setup please follow the steps outlined in your [workspace](https://app.speakeasy.com/org/meitner-2u8/api). Delete this section before > publishing to a package manager.

<!-- Start Summary [summary] -->
## Summary

Directory API: Generated API documentation
<!-- End Summary [summary] -->

<!-- Start Table of Contents [toc] -->
## Table of Contents
<!-- $toc-max-depth=2 -->
* [meitner](https://github.com/meitner-se/api-client-python/blob/master/#meitner)
  * [SDK Installation](https://github.com/meitner-se/api-client-python/blob/master/#sdk-installation)
  * [IDE Support](https://github.com/meitner-se/api-client-python/blob/master/#ide-support)
  * [SDK Example Usage](https://github.com/meitner-se/api-client-python/blob/master/#sdk-example-usage)
  * [Authentication](https://github.com/meitner-se/api-client-python/blob/master/#authentication)
  * [Available Resources and Operations](https://github.com/meitner-se/api-client-python/blob/master/#available-resources-and-operations)
  * [Pagination](https://github.com/meitner-se/api-client-python/blob/master/#pagination)
  * [Retries](https://github.com/meitner-se/api-client-python/blob/master/#retries)
  * [Error Handling](https://github.com/meitner-se/api-client-python/blob/master/#error-handling)
  * [Server Selection](https://github.com/meitner-se/api-client-python/blob/master/#server-selection)
  * [Custom HTTP Client](https://github.com/meitner-se/api-client-python/blob/master/#custom-http-client)
  * [Resource Management](https://github.com/meitner-se/api-client-python/blob/master/#resource-management)
  * [Debugging](https://github.com/meitner-se/api-client-python/blob/master/#debugging)
* [Development](https://github.com/meitner-se/api-client-python/blob/master/#development)
  * [Maturity](https://github.com/meitner-se/api-client-python/blob/master/#maturity)
  * [Contributions](https://github.com/meitner-se/api-client-python/blob/master/#contributions)

<!-- End Table of Contents [toc] -->

<!-- Start SDK Installation [installation] -->
## SDK Installation

> [!TIP]
> To finish publishing your SDK to PyPI you must [run your first generation action](https://www.speakeasy.com/docs/github-setup#step-by-step-guide).


> [!NOTE]
> **Python version upgrade policy**
>
> Once a Python version reaches its [official end of life date](https://devguide.python.org/versions/), a 3-month grace period is provided for users to upgrade. Following this grace period, the minimum python version supported in the SDK will be updated.

The SDK can be installed with *uv*, *pip*, or *poetry* package managers.

### uv

*uv* is a fast Python package installer and resolver, designed as a drop-in replacement for pip and pip-tools. It's recommended for its speed and modern Python tooling capabilities.

```bash
uv add git+https://github.com/meitner-se/api-client-python.git
```

### PIP

*PIP* is the default package installer for Python, enabling easy installation and management of packages from PyPI via the command line.

```bash
pip install git+https://github.com/meitner-se/api-client-python.git
```

### Poetry

*Poetry* is a modern tool that simplifies dependency management and package publishing by using a single `pyproject.toml` file to handle project metadata and dependencies.

```bash
poetry add git+https://github.com/meitner-se/api-client-python.git
```

### Shell and script usage with `uv`

You can use this SDK in a Python shell with [uv](https://docs.astral.sh/uv/) and the `uvx` command that comes with it like so:

```shell
uvx --from meitner python
```

It's also possible to write a standalone Python script without needing to set up a whole project like so:

```python
#!/usr/bin/env -S uv run --script
# /// script
# requires-python = ">=3.9"
# dependencies = [
#     "meitner",
# ]
# ///

from meitner import Meitner

sdk = Meitner(
  # SDK arguments
)

# Rest of script here...
```

Once that is saved to a file, you can run it with `uv run script.py` where
`script.py` can be replaced with the actual file name.
<!-- End SDK Installation [installation] -->

<!-- Start IDE Support [idesupport] -->
## IDE Support

### PyCharm

Generally, the SDK will work well with most IDEs out of the box. However, when using PyCharm, you can enjoy much better integration with Pydantic by installing an additional plugin.

- [PyCharm Pydantic Plugin](https://docs.pydantic.dev/latest/integrations/pycharm/)
<!-- End IDE Support [idesupport] -->

<!-- Start SDK Example Usage [usage] -->
## SDK Example Usage

### Example

```python
# Synchronous Example
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
        client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
    ),
) as m_client:

    res = m_client.schools.list(limit=1, offset=0)

    while res is not None:
        # Handle items

        res = res.next()
```

</br>

The same SDK client can also be used to make asynchronous requests by importing asyncio.

```python
# Asynchronous Example
import asyncio
from meitner import Meitner, models
import os

async def main():

    async with Meitner(
        security=models.Security(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ) as m_client:

        res = await m_client.schools.list_async(limit=1, offset=0)

        while res is not None:
            # Handle items

            res = res.next()

asyncio.run(main())
```
<!-- End SDK Example Usage [usage] -->

<!-- Start Authentication [security] -->
## Authentication

### Per-Client Security Schemes

This SDK supports the following security schemes globally:

| Name                 | Type   | Scheme  | Environment Variable         |
| -------------------- | ------ | ------- | ---------------------------- |
| `client_credentials` | apiKey | API key | `MEITNER_CLIENT_CREDENTIALS` |
| `client_secret`      | apiKey | API key | `MEITNER_CLIENT_SECRET`      |

You can set the security parameters through the `security` optional parameter when initializing the SDK client instance. The selected scheme will be used by default to authenticate with the API for all operations that support it. For example:
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
        client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
    ),
) as m_client:

    res = m_client.schools.list(limit=1, offset=0)

    while res is not None:
        # Handle items

        res = res.next()

```
<!-- End Authentication [security] -->

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>

### [audit_events](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/auditevents/README.md)

* [list](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/auditevents/README.md#list) - List AuditEvents
* [search](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/auditevents/README.md#search) - Search AuditEvents
* [get](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/auditevents/README.md#get) - Get a AuditEvent

### [employee_placements](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/employeeplacements/README.md)

* [list](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/employeeplacements/README.md#list) - List EmployeePlacements
* [create](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/employeeplacements/README.md#create) - Create a new EmployeePlacement
* [search](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/employeeplacements/README.md#search) - Search EmployeePlacements
* [get](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/employeeplacements/README.md#get) - Get a EmployeePlacement
* [delete](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/employeeplacements/README.md#delete) - Delete a EmployeePlacement
* [update](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/employeeplacements/README.md#update) - Update a EmployeePlacement

### [employees](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/employees/README.md)

* [list](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/employees/README.md#list) - List Employees
* [create](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/employees/README.md#create) - Create a new Employee
* [search](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/employees/README.md#search) - Search Employees
* [get](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/employees/README.md#get) - Get a Employee
* [delete](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/employees/README.md#delete) - Delete a Employee
* [update](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/employees/README.md#update) - Update a Employee

### [groups](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/groups/README.md)

* [list](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/groups/README.md#list) - List Groups
* [create](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/groups/README.md#create) - Create a new Group
* [search](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/groups/README.md#search) - Search Groups
* [get](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/groups/README.md#get) - Get a Group
* [delete](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/groups/README.md#delete) - Delete a Group
* [update](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/groups/README.md#update) - Update a Group

### [guardians](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/guardians/README.md)

* [list](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/guardians/README.md#list) - List Guardians
* [create](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/guardians/README.md#create) - Create a new Guardian
* [search](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/guardians/README.md#search) - Search Guardians
* [get](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/guardians/README.md#get) - Get a Guardian
* [delete](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/guardians/README.md#delete) - Delete a Guardian
* [update](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/guardians/README.md#update) - Update a Guardian


### [schools](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/schools/README.md)

* [list](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/schools/README.md#list) - List Schools
* [create](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/schools/README.md#create) - Create a new School
* [search](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/schools/README.md#search) - Search Schools
* [get](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/schools/README.md#get) - Get a School
* [update](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/schools/README.md#update) - Update a School

### [student_placements](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/studentplacements/README.md)

* [list](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/studentplacements/README.md#list) - List StudentPlacements
* [create](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/studentplacements/README.md#create) - Create a new StudentPlacement
* [search](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/studentplacements/README.md#search) - Search StudentPlacements
* [get](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/studentplacements/README.md#get) - Get a StudentPlacement
* [delete](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/studentplacements/README.md#delete) - Delete a StudentPlacement
* [update](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/studentplacements/README.md#update) - Update a StudentPlacement
* [archive](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/studentplacements/README.md#archive) - Archive a student placement
* [restore](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/studentplacements/README.md#restore) - Restore an archived student placement

### [students](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/students/README.md)

* [list](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/students/README.md#list) - List Students
* [create](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/students/README.md#create) - Create a new Student
* [search](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/students/README.md#search) - Search Students
* [get](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/students/README.md#get) - Get a Student
* [delete](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/students/README.md#delete) - Delete a Student
* [update](https://github.com/meitner-se/api-client-python/blob/master/docs/sdks/students/README.md#update) - Update a Student

</details>
<!-- End Available Resources and Operations [operations] -->

<!-- Start Pagination [pagination] -->
## Pagination

Some of the endpoints in this SDK support pagination. To use pagination, you make your SDK calls as usual, but the
returned response object will have a `Next` method that can be called to pull down the next group of results. If the
return value of `Next` is `None`, then there are no more pages to be fetched.

Here's an example of one such pagination call:
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
        client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
    ),
) as m_client:

    res = m_client.schools.list(limit=1, offset=0)

    while res is not None:
        # Handle items

        res = res.next()

```
<!-- End Pagination [pagination] -->

<!-- Start Retries [retries] -->
## Retries

Some of the endpoints in this SDK support retries. If you use the SDK without any configuration, it will fall back to the default retry strategy provided by the API. However, the default retry strategy can be overridden on a per-operation basis, or across the entire SDK.

To change the default retry strategy for a single API call, simply provide a `RetryConfig` object to the call:
```python
from meitner import Meitner, models
from meitner.utils import BackoffStrategy, RetryConfig
import os


with Meitner(
    security=models.Security(
        client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
        client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
    ),
) as m_client:

    res = m_client.schools.list(limit=1, offset=0,
        RetryConfig("backoff", BackoffStrategy(1, 50, 1.1, 100), False))

    while res is not None:
        # Handle items

        res = res.next()

```

If you'd like to override the default retry strategy for all operations that support retries, you can use the `retry_config` optional parameter when initializing the SDK:
```python
from meitner import Meitner, models
from meitner.utils import BackoffStrategy, RetryConfig
import os


with Meitner(
    retry_config=RetryConfig("backoff", BackoffStrategy(1, 50, 1.1, 100), False),
    security=models.Security(
        client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
        client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
    ),
) as m_client:

    res = m_client.schools.list(limit=1, offset=0)

    while res is not None:
        # Handle items

        res = res.next()

```
<!-- End Retries [retries] -->

<!-- Start Error Handling [errors] -->
## Error Handling

[`MeitnerError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/meitnererror.py) is the base class for all HTTP error responses. It has the following properties:

| Property           | Type             | Description                                                                             |
| ------------------ | ---------------- | --------------------------------------------------------------------------------------- |
| `err.message`      | `str`            | Error message                                                                           |
| `err.status_code`  | `int`            | HTTP response status code eg `404`                                                      |
| `err.headers`      | `httpx.Headers`  | HTTP response headers                                                                   |
| `err.body`         | `str`            | HTTP body. Can be empty string if no body is returned.                                  |
| `err.raw_response` | `httpx.Response` | Raw HTTP response                                                                       |
| `err.data`         |                  | Optional. Some errors may contain structured data. [See Error Classes](https://github.com/meitner-se/api-client-python/blob/master/#error-classes). |

### Example
```python
from meitner import Meitner, errors, models
import os


with Meitner(
    security=models.Security(
        client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
        client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
    ),
) as m_client:
    res = None
    try:

        res = m_client.schools.list(limit=1, offset=0)

        while res is not None:
            # Handle items

            res = res.next()


    except errors.MeitnerError as e:
        # The base class for HTTP error responses
        print(e.message)
        print(e.status_code)
        print(e.body)
        print(e.headers)
        print(e.raw_response)

        # Depending on the method different errors may be thrown
        if isinstance(e, errors.Error400ResponseBody):
            print(e.data.error)  # models.Error400ResponseBodyError
```

### Error Classes
**Primary errors:**
* [`MeitnerError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/meitnererror.py): The base class for HTTP error responses.
  * [`Error400ResponseBody`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/error400responsebody.py): Bad Request - The request was malformed or contained invalid parameters. Status code `400`.
  * [`Error401ResponseBody`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/error401responsebody.py): Unauthorized - The request is missing valid authentication credentials. Status code `401`.
  * [`Error403ResponseBody`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/error403responsebody.py): Forbidden - Request is authenticated, but the user is not allowed to perform the operation. Status code `403`.
  * [`Error404ResponseBody`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/error404responsebody.py): Not Found - The requested resource does not exist. Status code `404`.
  * [`Error409ResponseBody`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/error409responsebody.py): Conflict - The request could not be completed due to a conflict. Status code `409`.
  * [`Error429ResponseBody`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/error429responsebody.py): Too Many Requests - When the rate limit has been exceeded. Status code `429`.
  * [`Error500ResponseBody`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/error500responsebody.py): Internal Server Error - An unexpected server error occurred. Status code `500`.

<details><summary>Less common errors (27)</summary>

<br />

**Network errors:**
* [`httpx.RequestError`](https://www.python-httpx.org/exceptions/#httpx.RequestError): Base class for request errors.
    * [`httpx.ConnectError`](https://www.python-httpx.org/exceptions/#httpx.ConnectError): HTTP client was unable to make a request to a server.
    * [`httpx.TimeoutException`](https://www.python-httpx.org/exceptions/#httpx.TimeoutException): HTTP request timed out.


**Inherit from [`MeitnerError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/meitnererror.py)**:
* [`SchoolCreate422ResponseBodyError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/schoolcreate422responsebodyerror.py): Validation error for School Create operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
* [`SchoolSearch422ResponseBodyError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/schoolsearch422responsebodyerror.py): Validation error for School Search operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
* [`SchoolUpdate422ResponseBodyError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/schoolupdate422responsebodyerror.py): Validation error for School Update operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
* [`GroupCreate422ResponseBodyError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/groupcreate422responsebodyerror.py): Validation error for Group Create operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
* [`GroupSearch422ResponseBodyError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/groupsearch422responsebodyerror.py): Validation error for Group Search operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
* [`GroupUpdate422ResponseBodyError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/groupupdate422responsebodyerror.py): Validation error for Group Update operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
* [`EmployeeCreate422ResponseBodyError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/employeecreate422responsebodyerror.py): Validation error for Employee Create operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
* [`EmployeeSearch422ResponseBodyError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/employeesearch422responsebodyerror.py): Validation error for Employee Search operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
* [`EmployeeUpdate422ResponseBodyError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/employeeupdate422responsebodyerror.py): Validation error for Employee Update operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
* [`EmployeePlacementCreate422ResponseBodyError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/employeeplacementcreate422responsebodyerror.py): Validation error for EmployeePlacement Create operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
* [`EmployeePlacementSearch422ResponseBodyError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/employeeplacementsearch422responsebodyerror.py): Validation error for EmployeePlacement Search operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
* [`EmployeePlacementUpdate422ResponseBodyError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/employeeplacementupdate422responsebodyerror.py): Validation error for EmployeePlacement Update operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
* [`GuardianCreate422ResponseBodyError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/guardiancreate422responsebodyerror.py): Validation error for Guardian Create operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
* [`GuardianSearch422ResponseBodyError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/guardiansearch422responsebodyerror.py): Validation error for Guardian Search operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
* [`GuardianUpdate422ResponseBodyError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/guardianupdate422responsebodyerror.py): Validation error for Guardian Update operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
* [`StudentCreate422ResponseBodyError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/studentcreate422responsebodyerror.py): Validation error for Student Create operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
* [`StudentSearch422ResponseBodyError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/studentsearch422responsebodyerror.py): Validation error for Student Search operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
* [`StudentUpdate422ResponseBodyError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/studentupdate422responsebodyerror.py): Validation error for Student Update operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
* [`StudentPlacementCreate422ResponseBodyError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/studentplacementcreate422responsebodyerror.py): Validation error for StudentPlacement Create operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
* [`StudentPlacementSearch422ResponseBodyError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/studentplacementsearch422responsebodyerror.py): Validation error for StudentPlacement Search operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
* [`StudentPlacementUpdate422ResponseBodyError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/studentplacementupdate422responsebodyerror.py): Validation error for StudentPlacement Update operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
* [`AuditEventSearch422ResponseBodyError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/auditeventsearch422responsebodyerror.py): Validation error for AuditEvent Search operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
* [`ResponseValidationError`](https://github.com/meitner-se/api-client-python/blob/master/./src/meitner/errors/responsevalidationerror.py): Type mismatch between the response data and the expected Pydantic model. Provides access to the Pydantic validation error via the `cause` attribute.

</details>

\* Check [the method documentation](https://github.com/meitner-se/api-client-python/blob/master/#available-resources-and-operations) to see if the error is applicable.
<!-- End Error Handling [errors] -->

<!-- Start Server Selection [server] -->
## Server Selection

### Select Server by Name

You can override the default server globally by passing a server name to the `server: str` optional parameter when initializing the SDK client instance. The selected server will then be used as the default on the operations that use it. This table lists the names associated with the available servers:

| Name         | Server                                        | Description                                     |
| ------------ | --------------------------------------------- | ----------------------------------------------- |
| `production` | `https://api.meitner.se/directory/v1`         | Server to use in production                     |
| `staging`    | `https://api.staging.meitner.se/directory/v1` | Server to use when building and testing the API |

#### Example

```python
from meitner import Meitner, models
import os


with Meitner(
    server="staging",
    security=models.Security(
        client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
        client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
    ),
) as m_client:

    res = m_client.schools.list(limit=1, offset=0)

    while res is not None:
        # Handle items

        res = res.next()

```

### Override Server URL Per-Client

The default server can also be overridden globally by passing a URL to the `server_url: str` optional parameter when initializing the SDK client instance. For example:
```python
from meitner import Meitner, models
import os


with Meitner(
    server_url="https://api.meitner.se/directory/v1",
    security=models.Security(
        client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
        client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
    ),
) as m_client:

    res = m_client.schools.list(limit=1, offset=0)

    while res is not None:
        # Handle items

        res = res.next()

```
<!-- End Server Selection [server] -->

<!-- Start Custom HTTP Client [http-client] -->
## Custom HTTP Client

The Python SDK makes API calls using the [httpx](https://www.python-httpx.org/) HTTP library.  In order to provide a convenient way to configure timeouts, cookies, proxies, custom headers, and other low-level configuration, you can initialize the SDK client with your own HTTP client instance.
Depending on whether you are using the sync or async version of the SDK, you can pass an instance of `HttpClient` or `AsyncHttpClient` respectively, which are Protocol's ensuring that the client has the necessary methods to make API calls.
This allows you to wrap the client with your own custom logic, such as adding custom headers, logging, or error handling, or you can just pass an instance of `httpx.Client` or `httpx.AsyncClient` directly.

For example, you could specify a header for every request that this sdk makes as follows:
```python
from meitner import Meitner
import httpx

http_client = httpx.Client(headers={"x-custom-header": "someValue"})
s = Meitner(client=http_client)
```

or you could wrap the client with your own custom logic:
```python
from meitner import Meitner
from meitner.httpclient import AsyncHttpClient
import httpx

class CustomClient(AsyncHttpClient):
    client: AsyncHttpClient

    def __init__(self, client: AsyncHttpClient):
        self.client = client

    async def send(
        self,
        request: httpx.Request,
        *,
        stream: bool = False,
        auth: Union[
            httpx._types.AuthTypes, httpx._client.UseClientDefault, None
        ] = httpx.USE_CLIENT_DEFAULT,
        follow_redirects: Union[
            bool, httpx._client.UseClientDefault
        ] = httpx.USE_CLIENT_DEFAULT,
    ) -> httpx.Response:
        request.headers["Client-Level-Header"] = "added by client"

        return await self.client.send(
            request, stream=stream, auth=auth, follow_redirects=follow_redirects
        )

    def build_request(
        self,
        method: str,
        url: httpx._types.URLTypes,
        *,
        content: Optional[httpx._types.RequestContent] = None,
        data: Optional[httpx._types.RequestData] = None,
        files: Optional[httpx._types.RequestFiles] = None,
        json: Optional[Any] = None,
        params: Optional[httpx._types.QueryParamTypes] = None,
        headers: Optional[httpx._types.HeaderTypes] = None,
        cookies: Optional[httpx._types.CookieTypes] = None,
        timeout: Union[
            httpx._types.TimeoutTypes, httpx._client.UseClientDefault
        ] = httpx.USE_CLIENT_DEFAULT,
        extensions: Optional[httpx._types.RequestExtensions] = None,
    ) -> httpx.Request:
        return self.client.build_request(
            method,
            url,
            content=content,
            data=data,
            files=files,
            json=json,
            params=params,
            headers=headers,
            cookies=cookies,
            timeout=timeout,
            extensions=extensions,
        )

s = Meitner(async_client=CustomClient(httpx.AsyncClient()))
```
<!-- End Custom HTTP Client [http-client] -->

<!-- Start Resource Management [resource-management] -->
## Resource Management

The `Meitner` class implements the context manager protocol and registers a finalizer function to close the underlying sync and async HTTPX clients it uses under the hood. This will close HTTP connections, release memory and free up other resources held by the SDK. In short-lived Python programs and notebooks that make a few SDK method calls, resource management may not be a concern. However, in longer-lived programs, it is beneficial to create a single SDK instance via a [context manager][context-manager] and reuse it across the application.

[context-manager]: https://docs.python.org/3/reference/datamodel.html#context-managers

```python
from meitner import Meitner, models
import os
def main():

    with Meitner(
        security=models.Security(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ) as m_client:
        # Rest of application here...


# Or when using async:
async def amain():

    async with Meitner(
        security=models.Security(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ) as m_client:
        # Rest of application here...
```
<!-- End Resource Management [resource-management] -->

<!-- Start Debugging [debug] -->
## Debugging

You can setup your SDK to emit debug logs for SDK requests and responses.

You can pass your own logger class directly into your SDK.
```python
from meitner import Meitner
import logging

logging.basicConfig(level=logging.DEBUG)
s = Meitner(debug_logger=logging.getLogger("meitner"))
```

You can also enable a default debug logger by setting an environment variable `MEITNER_DEBUG` to true.
<!-- End Debugging [debug] -->

<!-- Placeholder for Future Speakeasy SDK Sections -->

# Development

## Maturity

This SDK is in beta, and there may be breaking changes between versions without a major version update. Therefore, we recommend pinning usage
to a specific package version. This way, you can install the same version each time without breaking changes unless you are intentionally
looking for the latest version.

## Contributions

While we value open-source contributions to this SDK, this library is generated programmatically. Any manual changes added to internal files will be overwritten on the next generation. 
We look forward to hearing your feedback. Feel free to open a PR or an issue with a proof of concept and we'll do our best to include it in a future release. 

### SDK Created by [Speakeasy](https://www.speakeasy.com/?utm_source=meitner&utm_campaign=python)
