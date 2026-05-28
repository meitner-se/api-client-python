# GradeElementaries

## Overview

### Available Operations

* [list](#list) - List GradeElementaries
* [create](#create) - Create a new GradeElementary
* [get](#get) - Get a GradeElementary
* [delete](#delete) - Delete a GradeElementary
* [update](#update) - Update a GradeElementary

## list

Returns a paginated list of all `GradeElementaries` in your organization.

### Example Usage

<!-- UsageSnippet language="python" operationID="GradeElementaryList" method="get" path="/grade-elementary" example="responseExample" -->
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        option1=models.SecurityOption1(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ),
) as m_client:

    res = m_client.grade_elementaries.list(limit=1, offset=0)

    while res is not None:
        # Handle items

        res = res.next()

```

### Parameters

| Parameter                                                                                                             | Type                                                                                                                  | Required                                                                                                              | Description                                                                                                           | Example                                                                                                               |
| --------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| `limit`                                                                                                               | *Optional[int]*                                                                                                       | :heavy_minus_sign:                                                                                                    | The maximum number of GradeElementaries to return (default: 50) when listing GradeElementaries                        | 1                                                                                                                     |
| `offset`                                                                                                              | *Optional[int]*                                                                                                       | :heavy_minus_sign:                                                                                                    | The number of GradeElementaries to skip before starting to return results (default: 0) when listing GradeElementaries | 0                                                                                                                     |
| `retries`                                                                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                      | :heavy_minus_sign:                                                                                                    | Configuration to override the default retry behavior of the client.                                                   |                                                                                                                       |

### Response

**[models.GradeElementaryListResponse](../../models/gradeelementarylistresponse.md)**

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

Create a new GradeElementary

### Example Usage: errorExample

<!-- UsageSnippet language="python" operationID="GradeElementaryCreate" method="post" path="/grade-elementary" example="errorExample" -->
```python
from datetime import date
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        option1=models.SecurityOption1(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ),
) as m_client:

    res = m_client.grade_elementaries.create(student_id="123e4567-e89b-12d3-a456-426614174000", school_id="123e4567-e89b-12d3-a456-426614174000", subject_code="MA", academic_year="2024/2025", term="HT", school_year="9", final_grade=True, is_ended=True, external={
        "source_id": "12345678",
    }, language_code="SV", teacher1_employee_id="123e4567-e89b-12d3-a456-426614174000", teacher2_employee_id="123e4567-e89b-12d3-a456-426614174000", grade="A", grade_date=date.fromisoformat("2025-01-15"), school_comment="Utmärkt arbete under hela terminen.")

    # Handle response
    print(res)

```
### Example Usage: requestExample

<!-- UsageSnippet language="python" operationID="GradeElementaryCreate" method="post" path="/grade-elementary" example="requestExample" -->
```python
from datetime import date
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        option1=models.SecurityOption1(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ),
) as m_client:

    res = m_client.grade_elementaries.create(student_id="123e4567-e89b-12d3-a456-426614174000", school_id="123e4567-e89b-12d3-a456-426614174000", subject_code="MA", academic_year="2024/2025", term="HT", school_year="9", final_grade=True, is_ended=True, external={
        "source_id": "12345678",
    }, language_code="SV", teacher1_employee_id="123e4567-e89b-12d3-a456-426614174000", teacher2_employee_id="123e4567-e89b-12d3-a456-426614174000", grade="A", grade_date=date.fromisoformat("2025-01-15"), school_comment="Utmärkt arbete under hela terminen.")

    # Handle response
    print(res)

```
### Example Usage: responseExample

<!-- UsageSnippet language="python" operationID="GradeElementaryCreate" method="post" path="/grade-elementary" example="responseExample" -->
```python
from datetime import date
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        option1=models.SecurityOption1(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ),
) as m_client:

    res = m_client.grade_elementaries.create(student_id="123e4567-e89b-12d3-a456-426614174000", school_id="123e4567-e89b-12d3-a456-426614174000", subject_code="MA", academic_year="2024/2025", term="HT", school_year="9", final_grade=True, is_ended=True, external={
        "source_id": "12345678",
    }, language_code="SV", teacher1_employee_id="123e4567-e89b-12d3-a456-426614174000", teacher2_employee_id="123e4567-e89b-12d3-a456-426614174000", grade="A", grade_date=date.fromisoformat("2025-01-15"), school_comment="Utmärkt arbete under hela terminen.")

    # Handle response
    print(res)

```
### Example Usage: validationError

<!-- UsageSnippet language="python" operationID="GradeElementaryCreate" method="post" path="/grade-elementary" example="validationError" -->
```python
from datetime import date
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        option1=models.SecurityOption1(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ),
) as m_client:

    res = m_client.grade_elementaries.create(student_id="123e4567-e89b-12d3-a456-426614174000", school_id="123e4567-e89b-12d3-a456-426614174000", subject_code="MA", academic_year="2024/2025", term="HT", school_year="9", final_grade=True, is_ended=True, external={
        "source_id": "12345678",
    }, language_code="SV", teacher1_employee_id="123e4567-e89b-12d3-a456-426614174000", teacher2_employee_id="123e4567-e89b-12d3-a456-426614174000", grade="A", grade_date=date.fromisoformat("2025-01-15"), school_comment="Utmärkt arbete under hela terminen.")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                      | Type                                                                                                                                                           | Required                                                                                                                                                       | Description                                                                                                                                                    | Example                                                                                                                                                        |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `student_id`                                                                                                                                                   | *str*                                                                                                                                                          | :heavy_check_mark:                                                                                                                                             | The ID of the student the grade belongs to. Must reference a student within the organization who has an active placement at the school referenced by SchoolID. | 123e4567-e89b-12d3-a456-426614174000                                                                                                                           |
| `school_id`                                                                                                                                                    | *str*                                                                                                                                                          | :heavy_check_mark:                                                                                                                                             | The ID of the school where the student received the grade. Must reference a school within the organization.                                                    | 123e4567-e89b-12d3-a456-426614174000                                                                                                                           |
| `subject_code`                                                                                                                                                 | *str*                                                                                                                                                          | :heavy_check_mark:                                                                                                                                             | The subject code as defined by the Swedish school authorities (e.g. "MA" for Mathematics, "SV" for Swedish).                                                   | MA                                                                                                                                                             |
| `academic_year`                                                                                                                                                | *str*                                                                                                                                                          | :heavy_check_mark:                                                                                                                                             | The academic year in which the grade was awarded, in the format YYYY/YYYY (e.g. "2024/2025").                                                                  | 2024/2025                                                                                                                                                      |
| `term`                                                                                                                                                         | [models.GradeElementaryCreateTerm](../../models/gradeelementarycreateterm.md)                                                                                  | :heavy_check_mark:                                                                                                                                             | The school term in which the grade was awarded.                                                                                                                | HT                                                                                                                                                             |
| `school_year`                                                                                                                                                  | [models.GradeElementaryCreateSchoolYear](../../models/gradeelementarycreateschoolyear.md)                                                                      | :heavy_check_mark:                                                                                                                                             | The school year of the student at the time the grade was awarded.                                                                                              | 9                                                                                                                                                              |
| `final_grade`                                                                                                                                                  | *bool*                                                                                                                                                         | :heavy_check_mark:                                                                                                                                             | Whether this is the final grade for the student in this subject. A final grade is the official grade used on the student's grade certificate.                  | true                                                                                                                                                           |
| `is_ended`                                                                                                                                                     | *bool*                                                                                                                                                         | :heavy_check_mark:                                                                                                                                             | Whether the grading period has ended for this student in this subject.                                                                                         | true                                                                                                                                                           |
| `external`                                                                                                                                                     | [Optional[models.GradeElementaryCreateExternal]](../../models/gradeelementarycreateexternal.md)                                                                | :heavy_minus_sign:                                                                                                                                             | ExternalRequest is the External-object used on Create and Update operations. Only SourceID can be set — the Source field is derived from the API key.          | {<br/>"sourceID": "12345678"<br/>}                                                                                                                             |
| `language_code`                                                                                                                                                | *OptionalNullable[str]*                                                                                                                                        | :heavy_minus_sign:                                                                                                                                             | The language code for the grade, used when the subject is taught in a specific language (e.g. mother tongue instruction).                                      | **Example 1:** SV<br/>**Example 2:** null                                                                                                                      |
| `teacher1_employee_id`                                                                                                                                         | *OptionalNullable[str]*                                                                                                                                        | :heavy_minus_sign:                                                                                                                                             | The ID of the primary teacher responsible for the grade. Must reference an Employee who has an active placement at the school referenced by SchoolID.          | **Example 1:** 123e4567-e89b-12d3-a456-426614174000<br/>**Example 2:** null                                                                                    |
| `teacher2_employee_id`                                                                                                                                         | *OptionalNullable[str]*                                                                                                                                        | :heavy_minus_sign:                                                                                                                                             | The ID of the secondary teacher responsible for the grade. Must reference an Employee who has an active placement at the school referenced by SchoolID.        | **Example 1:** 123e4567-e89b-12d3-a456-426614174000<br/>**Example 2:** null                                                                                    |
| `grade`                                                                                                                                                        | [OptionalNullable[models.GradeElementaryCreateGrade]](../../models/gradeelementarycreategrade.md)                                                              | :heavy_minus_sign:                                                                                                                                             | The grade awarded to the student.                                                                                                                              | **Example 1:** A<br/>**Example 2:** null                                                                                                                       |
| `grade_date`                                                                                                                                                   | [datetime](https://docs.python.org/3/library/datetime.html#datetime-objects)                                                                                   | :heavy_minus_sign:                                                                                                                                             | The date the grade was awarded.                                                                                                                                | **Example 1:** 2025-01-15<br/>**Example 2:** null                                                                                                              |
| `school_comment`                                                                                                                                               | *OptionalNullable[str]*                                                                                                                                        | :heavy_minus_sign:                                                                                                                                             | A comment from the school about the grade, visible to the student and guardians.                                                                               | **Example 1:** Utmärkt arbete under hela terminen.<br/>**Example 2:** null                                                                                     |
| `retries`                                                                                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                               | :heavy_minus_sign:                                                                                                                                             | Configuration to override the default retry behavior of the client.                                                                                            |                                                                                                                                                                |

### Response

**[models.GradeElementaryCreateResponse](../../models/gradeelementarycreateresponse.md)**

### Errors

| Error Type                                       | Status Code                                      | Content Type                                     |
| ------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------ |
| errors.Error400ResponseBody                      | 400                                              | application/json                                 |
| errors.Error401ResponseBody                      | 401                                              | application/json                                 |
| errors.Error403ResponseBody                      | 403                                              | application/json                                 |
| errors.Error404ResponseBody                      | 404                                              | application/json                                 |
| errors.Error409ResponseBody                      | 409                                              | application/json                                 |
| errors.GradeElementaryCreate422ResponseBodyError | 422                                              | application/json                                 |
| errors.Error429ResponseBody                      | 429                                              | application/json                                 |
| errors.Error500ResponseBody                      | 500                                              | application/json                                 |
| errors.MeitnerDefaultError                       | 4XX, 5XX                                         | \*/\*                                            |

## get

Retrieves the `GradeElementary` with the given ID.

### Example Usage

<!-- UsageSnippet language="python" operationID="GradeElementaryGet" method="get" path="/grade-elementary/{id}" example="responseExample" -->
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        option1=models.SecurityOption1(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ),
) as m_client:

    res = m_client.grade_elementaries.get(id="123e4567-e89b-12d3-a456-426614174000")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | The unique identifier of the GradeElementary to retrieve            | 123e4567-e89b-12d3-a456-426614174000                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.GradeElementaryGetResponse](../../models/gradeelementarygetresponse.md)**

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

Delete a GradeElementary

### Example Usage

<!-- UsageSnippet language="python" operationID="GradeElementaryDelete" method="delete" path="/grade-elementary/{id}" -->
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        option1=models.SecurityOption1(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ),
) as m_client:

    res = m_client.grade_elementaries.delete(id="123e4567-e89b-12d3-a456-426614174000")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | The unique identifier of the GradeElementary to delete              | 123e4567-e89b-12d3-a456-426614174000                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.GradeElementaryDeleteResponse](../../models/gradeelementarydeleteresponse.md)**

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

Update a GradeElementary

### Example Usage: errorExample

<!-- UsageSnippet language="python" operationID="GradeElementaryUpdate" method="patch" path="/grade-elementary/{id}" example="errorExample" -->
```python
from datetime import date
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        option1=models.SecurityOption1(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ),
) as m_client:

    res = m_client.grade_elementaries.update(id="123e4567-e89b-12d3-a456-426614174000", academic_year="2024/2025", term="HT", school_year="9", final_grade=True, is_ended=True, external={
        "source_id": "12345678",
    }, language_code="SV", teacher1_employee_id="123e4567-e89b-12d3-a456-426614174000", teacher2_employee_id="123e4567-e89b-12d3-a456-426614174000", grade="A", grade_date=date.fromisoformat("2025-01-15"), school_comment="Utmärkt arbete under hela terminen.")

    # Handle response
    print(res)

```
### Example Usage: requestExample

<!-- UsageSnippet language="python" operationID="GradeElementaryUpdate" method="patch" path="/grade-elementary/{id}" example="requestExample" -->
```python
from datetime import date
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        option1=models.SecurityOption1(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ),
) as m_client:

    res = m_client.grade_elementaries.update(id="123e4567-e89b-12d3-a456-426614174000", academic_year="2024/2025", term="HT", school_year="9", final_grade=True, is_ended=True, external={
        "source_id": "12345678",
    }, language_code="SV", teacher1_employee_id="123e4567-e89b-12d3-a456-426614174000", teacher2_employee_id="123e4567-e89b-12d3-a456-426614174000", grade="A", grade_date=date.fromisoformat("2025-01-15"), school_comment="Utmärkt arbete under hela terminen.")

    # Handle response
    print(res)

```
### Example Usage: responseExample

<!-- UsageSnippet language="python" operationID="GradeElementaryUpdate" method="patch" path="/grade-elementary/{id}" example="responseExample" -->
```python
from datetime import date
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        option1=models.SecurityOption1(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ),
) as m_client:

    res = m_client.grade_elementaries.update(id="123e4567-e89b-12d3-a456-426614174000", academic_year="2024/2025", term="HT", school_year="9", final_grade=True, is_ended=True, external={
        "source_id": "12345678",
    }, language_code="SV", teacher1_employee_id="123e4567-e89b-12d3-a456-426614174000", teacher2_employee_id="123e4567-e89b-12d3-a456-426614174000", grade="A", grade_date=date.fromisoformat("2025-01-15"), school_comment="Utmärkt arbete under hela terminen.")

    # Handle response
    print(res)

```
### Example Usage: validationError

<!-- UsageSnippet language="python" operationID="GradeElementaryUpdate" method="patch" path="/grade-elementary/{id}" example="validationError" -->
```python
from datetime import date
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        option1=models.SecurityOption1(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ),
) as m_client:

    res = m_client.grade_elementaries.update(id="123e4567-e89b-12d3-a456-426614174000", academic_year="2024/2025", term="HT", school_year="9", final_grade=True, is_ended=True, external={
        "source_id": "12345678",
    }, language_code="SV", teacher1_employee_id="123e4567-e89b-12d3-a456-426614174000", teacher2_employee_id="123e4567-e89b-12d3-a456-426614174000", grade="A", grade_date=date.fromisoformat("2025-01-15"), school_comment="Utmärkt arbete under hela terminen.")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                               | Type                                                                                                                                                    | Required                                                                                                                                                | Description                                                                                                                                             | Example                                                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                                                                    | *str*                                                                                                                                                   | :heavy_check_mark:                                                                                                                                      | The unique identifier of the GradeElementary to update                                                                                                  | 123e4567-e89b-12d3-a456-426614174000                                                                                                                    |
| `academic_year`                                                                                                                                         | *str*                                                                                                                                                   | :heavy_check_mark:                                                                                                                                      | The academic year in which the grade was awarded, in the format YYYY/YYYY (e.g. "2024/2025").                                                           | 2024/2025                                                                                                                                               |
| `term`                                                                                                                                                  | [models.GradeElementaryUpdateTerm](../../models/gradeelementaryupdateterm.md)                                                                           | :heavy_check_mark:                                                                                                                                      | The school term in which the grade was awarded.                                                                                                         | HT                                                                                                                                                      |
| `school_year`                                                                                                                                           | [models.GradeElementaryUpdateSchoolYear](../../models/gradeelementaryupdateschoolyear.md)                                                               | :heavy_check_mark:                                                                                                                                      | The school year of the student at the time the grade was awarded.                                                                                       | 9                                                                                                                                                       |
| `final_grade`                                                                                                                                           | *bool*                                                                                                                                                  | :heavy_check_mark:                                                                                                                                      | Whether this is the final grade for the student in this subject. A final grade is the official grade used on the student's grade certificate.           | true                                                                                                                                                    |
| `is_ended`                                                                                                                                              | *bool*                                                                                                                                                  | :heavy_check_mark:                                                                                                                                      | Whether the grading period has ended for this student in this subject.                                                                                  | true                                                                                                                                                    |
| `external`                                                                                                                                              | [Optional[models.GradeElementaryUpdateExternal]](../../models/gradeelementaryupdateexternal.md)                                                         | :heavy_minus_sign:                                                                                                                                      | ExternalRequest is the External-object used on Create and Update operations. Only SourceID can be set — the Source field is derived from the API key.   | {<br/>"sourceID": "12345678"<br/>}                                                                                                                      |
| `language_code`                                                                                                                                         | *OptionalNullable[str]*                                                                                                                                 | :heavy_minus_sign:                                                                                                                                      | The language code for the grade, used when the subject is taught in a specific language (e.g. mother tongue instruction).                               | **Example 1:** SV<br/>**Example 2:** null                                                                                                               |
| `teacher1_employee_id`                                                                                                                                  | *OptionalNullable[str]*                                                                                                                                 | :heavy_minus_sign:                                                                                                                                      | The ID of the primary teacher responsible for the grade. Must reference an Employee who has an active placement at the school referenced by SchoolID.   | **Example 1:** 123e4567-e89b-12d3-a456-426614174000<br/>**Example 2:** null                                                                             |
| `teacher2_employee_id`                                                                                                                                  | *OptionalNullable[str]*                                                                                                                                 | :heavy_minus_sign:                                                                                                                                      | The ID of the secondary teacher responsible for the grade. Must reference an Employee who has an active placement at the school referenced by SchoolID. | **Example 1:** 123e4567-e89b-12d3-a456-426614174000<br/>**Example 2:** null                                                                             |
| `grade`                                                                                                                                                 | [OptionalNullable[models.GradeElementaryUpdateGrade]](../../models/gradeelementaryupdategrade.md)                                                       | :heavy_minus_sign:                                                                                                                                      | The grade awarded to the student.                                                                                                                       | **Example 1:** A<br/>**Example 2:** null                                                                                                                |
| `grade_date`                                                                                                                                            | [datetime](https://docs.python.org/3/library/datetime.html#datetime-objects)                                                                            | :heavy_minus_sign:                                                                                                                                      | The date the grade was awarded.                                                                                                                         | **Example 1:** 2025-01-15<br/>**Example 2:** null                                                                                                       |
| `school_comment`                                                                                                                                        | *OptionalNullable[str]*                                                                                                                                 | :heavy_minus_sign:                                                                                                                                      | A comment from the school about the grade, visible to the student and guardians.                                                                        | **Example 1:** Utmärkt arbete under hela terminen.<br/>**Example 2:** null                                                                              |
| `retries`                                                                                                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                        | :heavy_minus_sign:                                                                                                                                      | Configuration to override the default retry behavior of the client.                                                                                     |                                                                                                                                                         |

### Response

**[models.GradeElementaryUpdateResponse](../../models/gradeelementaryupdateresponse.md)**

### Errors

| Error Type                                       | Status Code                                      | Content Type                                     |
| ------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------ |
| errors.Error400ResponseBody                      | 400                                              | application/json                                 |
| errors.Error401ResponseBody                      | 401                                              | application/json                                 |
| errors.Error403ResponseBody                      | 403                                              | application/json                                 |
| errors.Error404ResponseBody                      | 404                                              | application/json                                 |
| errors.Error409ResponseBody                      | 409                                              | application/json                                 |
| errors.GradeElementaryUpdate422ResponseBodyError | 422                                              | application/json                                 |
| errors.Error429ResponseBody                      | 429                                              | application/json                                 |
| errors.Error500ResponseBody                      | 500                                              | application/json                                 |
| errors.MeitnerDefaultError                       | 4XX, 5XX                                         | \*/\*                                            |