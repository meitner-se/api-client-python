# GradeUpperSecondaries

## Overview

### Available Operations

* [list](#list) - List GradeUpperSecondaries
* [create](#create) - Create a new GradeUpperSecondary
* [get](#get) - Get a GradeUpperSecondary
* [delete](#delete) - Delete a GradeUpperSecondary
* [update](#update) - Update a GradeUpperSecondary

## list

Returns a paginated list of all `GradeUpperSecondaries` in your organization.

### Example Usage

<!-- UsageSnippet language="python" operationID="GradeUpperSecondaryList" method="get" path="/grade-upper-secondary" example="responseExample" -->
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

    res = m_client.grade_upper_secondaries.list(limit=1, offset=0)

    while res is not None:
        # Handle items

        res = res.next()

```

### Parameters

| Parameter                                                                                                                     | Type                                                                                                                          | Required                                                                                                                      | Description                                                                                                                   | Example                                                                                                                       |
| ----------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| `limit`                                                                                                                       | *Optional[int]*                                                                                                               | :heavy_minus_sign:                                                                                                            | The maximum number of GradeUpperSecondaries to return (default: 50) when listing GradeUpperSecondaries                        | 1                                                                                                                             |
| `offset`                                                                                                                      | *Optional[int]*                                                                                                               | :heavy_minus_sign:                                                                                                            | The number of GradeUpperSecondaries to skip before starting to return results (default: 0) when listing GradeUpperSecondaries | 0                                                                                                                             |
| `retries`                                                                                                                     | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                              | :heavy_minus_sign:                                                                                                            | Configuration to override the default retry behavior of the client.                                                           |                                                                                                                               |

### Response

**[models.GradeUpperSecondaryListResponse](../../models/gradeuppersecondarylistresponse.md)**

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

Create a new GradeUpperSecondary

### Example Usage: errorExample

<!-- UsageSnippet language="python" operationID="GradeUpperSecondaryCreate" method="post" path="/grade-upper-secondary" example="errorExample" -->
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

    res = m_client.grade_upper_secondaries.create(student_id="123e4567-e89b-12d3-a456-426614174000", school_id="123e4567-e89b-12d3-a456-426614174000", course_code="MATMAT01a", include_on_final_grade=True, external={
        "source_id": "12345678",
    }, language_code="SV", teacher1_employee_id="123e4567-e89b-12d3-a456-426614174000", teacher2_employee_id="123e4567-e89b-12d3-a456-426614174000", grade="A", grade_date=date.fromisoformat("2025-01-15"), grade_comment="Eleven har visat goda kunskaper i algebra.", extent="Normal", school_year="2", section="Program", teacher_comment="Eleven deltar aktivt och visar stort engagemang.", program_title="Teknikprogrammet", start_date=date.fromisoformat("2024-08-19"), end_date=date.fromisoformat("2025-01-17"))

    # Handle response
    print(res)

```
### Example Usage: requestExample

<!-- UsageSnippet language="python" operationID="GradeUpperSecondaryCreate" method="post" path="/grade-upper-secondary" example="requestExample" -->
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

    res = m_client.grade_upper_secondaries.create(student_id="123e4567-e89b-12d3-a456-426614174000", school_id="123e4567-e89b-12d3-a456-426614174000", course_code="MATMAT01a", include_on_final_grade=True, external={
        "source_id": "12345678",
    }, language_code="SV", teacher1_employee_id="123e4567-e89b-12d3-a456-426614174000", teacher2_employee_id="123e4567-e89b-12d3-a456-426614174000", grade="A", grade_date=date.fromisoformat("2025-01-15"), grade_comment="Eleven har visat goda kunskaper i algebra.", extent="Normal", school_year="2", section="Program", teacher_comment="Eleven deltar aktivt och visar stort engagemang.", program_title="Teknikprogrammet", start_date=date.fromisoformat("2024-08-19"), end_date=date.fromisoformat("2025-01-17"))

    # Handle response
    print(res)

```
### Example Usage: responseExample

<!-- UsageSnippet language="python" operationID="GradeUpperSecondaryCreate" method="post" path="/grade-upper-secondary" example="responseExample" -->
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

    res = m_client.grade_upper_secondaries.create(student_id="123e4567-e89b-12d3-a456-426614174000", school_id="123e4567-e89b-12d3-a456-426614174000", course_code="MATMAT01a", include_on_final_grade=True, external={
        "source_id": "12345678",
    }, language_code="SV", teacher1_employee_id="123e4567-e89b-12d3-a456-426614174000", teacher2_employee_id="123e4567-e89b-12d3-a456-426614174000", grade="A", grade_date=date.fromisoformat("2025-01-15"), grade_comment="Eleven har visat goda kunskaper i algebra.", extent="Normal", school_year="2", section="Program", teacher_comment="Eleven deltar aktivt och visar stort engagemang.", program_title="Teknikprogrammet", start_date=date.fromisoformat("2024-08-19"), end_date=date.fromisoformat("2025-01-17"))

    # Handle response
    print(res)

```
### Example Usage: validationError

<!-- UsageSnippet language="python" operationID="GradeUpperSecondaryCreate" method="post" path="/grade-upper-secondary" example="validationError" -->
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

    res = m_client.grade_upper_secondaries.create(student_id="123e4567-e89b-12d3-a456-426614174000", school_id="123e4567-e89b-12d3-a456-426614174000", course_code="MATMAT01a", include_on_final_grade=True, external={
        "source_id": "12345678",
    }, language_code="SV", teacher1_employee_id="123e4567-e89b-12d3-a456-426614174000", teacher2_employee_id="123e4567-e89b-12d3-a456-426614174000", grade="A", grade_date=date.fromisoformat("2025-01-15"), grade_comment="Eleven har visat goda kunskaper i algebra.", extent="Normal", school_year="2", section="Program", teacher_comment="Eleven deltar aktivt och visar stort engagemang.", program_title="Teknikprogrammet", start_date=date.fromisoformat("2024-08-19"), end_date=date.fromisoformat("2025-01-17"))

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                      | Type                                                                                                                                                           | Required                                                                                                                                                       | Description                                                                                                                                                    | Example                                                                                                                                                        |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `student_id`                                                                                                                                                   | *str*                                                                                                                                                          | :heavy_check_mark:                                                                                                                                             | The ID of the student the grade belongs to. Must reference a student within the organization who has an active placement at the school referenced by SchoolID. | 123e4567-e89b-12d3-a456-426614174000                                                                                                                           |
| `school_id`                                                                                                                                                    | *str*                                                                                                                                                          | :heavy_check_mark:                                                                                                                                             | The ID of the school where the student received the grade. Must reference a school within the organization.                                                    | 123e4567-e89b-12d3-a456-426614174000                                                                                                                           |
| `course_code`                                                                                                                                                  | *str*                                                                                                                                                          | :heavy_check_mark:                                                                                                                                             | The national course code as defined by the Swedish school authorities (e.g. "MATMAT01a" for Mathematics 1a).                                                   | MATMAT01a                                                                                                                                                      |
| `include_on_final_grade`                                                                                                                                       | *bool*                                                                                                                                                         | :heavy_check_mark:                                                                                                                                             | Whether this course grade should be included when calculating the student's final grade certificate.                                                           | true                                                                                                                                                           |
| `external`                                                                                                                                                     | [Optional[models.GradeUpperSecondaryCreateExternal]](../../models/gradeuppersecondarycreateexternal.md)                                                        | :heavy_minus_sign:                                                                                                                                             | ExternalRequest is the External-object used on Create and Update operations. Only SourceID can be set — the Source field is derived from the API key.          | {<br/>"sourceID": "12345678"<br/>}                                                                                                                             |
| `language_code`                                                                                                                                                | *OptionalNullable[str]*                                                                                                                                        | :heavy_minus_sign:                                                                                                                                             | The language code for the grade, used when the course is taught in a specific language.                                                                        | **Example 1:** SV<br/>**Example 2:** <nil>                                                                                                                     |
| `teacher1_employee_id`                                                                                                                                         | *OptionalNullable[str]*                                                                                                                                        | :heavy_minus_sign:                                                                                                                                             | The ID of the primary teacher responsible for the grade. Must reference an Employee who has an active placement at the school referenced by SchoolID.          | **Example 1:** 123e4567-e89b-12d3-a456-426614174000<br/>**Example 2:** <nil>                                                                                   |
| `teacher2_employee_id`                                                                                                                                         | *OptionalNullable[str]*                                                                                                                                        | :heavy_minus_sign:                                                                                                                                             | The ID of the secondary teacher responsible for the grade. Must reference an Employee who has an active placement at the school referenced by SchoolID.        | **Example 1:** 123e4567-e89b-12d3-a456-426614174000<br/>**Example 2:** <nil>                                                                                   |
| `grade`                                                                                                                                                        | [OptionalNullable[models.GradeUpperSecondaryCreateGrade]](../../models/gradeuppersecondarycreategrade.md)                                                      | :heavy_minus_sign:                                                                                                                                             | The grade awarded to the student.                                                                                                                              | **Example 1:** A<br/>**Example 2:** <nil>                                                                                                                      |
| `grade_date`                                                                                                                                                   | [datetime](https://docs.python.org/3/library/datetime.html#datetime-objects)                                                                                   | :heavy_minus_sign:                                                                                                                                             | The date the grade was awarded.                                                                                                                                | **Example 1:** 2025-01-15<br/>**Example 2:** <nil>                                                                                                             |
| `grade_comment`                                                                                                                                                | *OptionalNullable[str]*                                                                                                                                        | :heavy_minus_sign:                                                                                                                                             | A comment about the grade from the teacher.                                                                                                                    | **Example 1:** Eleven har visat goda kunskaper i algebra.<br/>**Example 2:** <nil>                                                                             |
| `extent`                                                                                                                                                       | [OptionalNullable[models.GradeUpperSecondaryCreateExtent]](../../models/gradeuppersecondarycreateextent.md)                                                    | :heavy_minus_sign:                                                                                                                                             | The extent of the course for this student.                                                                                                                     | **Example 1:** Normal<br/>**Example 2:** <nil>                                                                                                                 |
| `school_year`                                                                                                                                                  | [OptionalNullable[models.GradeUpperSecondaryCreateSchoolYear]](../../models/gradeuppersecondarycreateschoolyear.md)                                            | :heavy_minus_sign:                                                                                                                                             | The school year of the student at the time the grade was awarded.                                                                                              | **Example 1:** 2<br/>**Example 2:** <nil>                                                                                                                      |
| `section`                                                                                                                                                      | [OptionalNullable[models.GradeUpperSecondaryCreateSection]](../../models/gradeuppersecondarycreatesection.md)                                                  | :heavy_minus_sign:                                                                                                                                             | The section/type of the course in the student's study plan.                                                                                                    | **Example 1:** Program<br/>**Example 2:** <nil>                                                                                                                |
| `teacher_comment`                                                                                                                                              | *OptionalNullable[str]*                                                                                                                                        | :heavy_minus_sign:                                                                                                                                             | A comment from the teacher about the student's performance.                                                                                                    | **Example 1:** Eleven deltar aktivt och visar stort engagemang.<br/>**Example 2:** <nil>                                                                       |
| `program_title`                                                                                                                                                | *OptionalNullable[str]*                                                                                                                                        | :heavy_minus_sign:                                                                                                                                             | The title of the program this course belongs to. Used to associate the course with a specific educational program.                                             | **Example 1:** Teknikprogrammet<br/>**Example 2:** <nil>                                                                                                       |
| `start_date`                                                                                                                                                   | [datetime](https://docs.python.org/3/library/datetime.html#datetime-objects)                                                                                   | :heavy_minus_sign:                                                                                                                                             | The date the student started the course.                                                                                                                       | **Example 1:** 2024-08-19<br/>**Example 2:** <nil>                                                                                                             |
| `end_date`                                                                                                                                                     | [datetime](https://docs.python.org/3/library/datetime.html#datetime-objects)                                                                                   | :heavy_minus_sign:                                                                                                                                             | The date the student finished the course.                                                                                                                      | **Example 1:** 2025-01-17<br/>**Example 2:** <nil>                                                                                                             |
| `retries`                                                                                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                               | :heavy_minus_sign:                                                                                                                                             | Configuration to override the default retry behavior of the client.                                                                                            |                                                                                                                                                                |

### Response

**[models.GradeUpperSecondaryCreateResponse](../../models/gradeuppersecondarycreateresponse.md)**

### Errors

| Error Type                                           | Status Code                                          | Content Type                                         |
| ---------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- |
| errors.Error400ResponseBody                          | 400                                                  | application/json                                     |
| errors.Error401ResponseBody                          | 401                                                  | application/json                                     |
| errors.Error403ResponseBody                          | 403                                                  | application/json                                     |
| errors.Error404ResponseBody                          | 404                                                  | application/json                                     |
| errors.Error409ResponseBody                          | 409                                                  | application/json                                     |
| errors.GradeUpperSecondaryCreate422ResponseBodyError | 422                                                  | application/json                                     |
| errors.Error429ResponseBody                          | 429                                                  | application/json                                     |
| errors.Error500ResponseBody                          | 500                                                  | application/json                                     |
| errors.MeitnerDefaultError                           | 4XX, 5XX                                             | \*/\*                                                |

## get

Retrieves the `GradeUpperSecondary` with the given ID.

### Example Usage

<!-- UsageSnippet language="python" operationID="GradeUpperSecondaryGet" method="get" path="/grade-upper-secondary/{id}" example="responseExample" -->
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

    res = m_client.grade_upper_secondaries.get(id="123e4567-e89b-12d3-a456-426614174000")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | The unique identifier of the GradeUpperSecondary to retrieve        | 123e4567-e89b-12d3-a456-426614174000                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.GradeUpperSecondaryGetResponse](../../models/gradeuppersecondarygetresponse.md)**

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

Delete a GradeUpperSecondary

### Example Usage

<!-- UsageSnippet language="python" operationID="GradeUpperSecondaryDelete" method="delete" path="/grade-upper-secondary/{id}" -->
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

    res = m_client.grade_upper_secondaries.delete(id="123e4567-e89b-12d3-a456-426614174000")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | The unique identifier of the GradeUpperSecondary to delete          | 123e4567-e89b-12d3-a456-426614174000                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.GradeUpperSecondaryDeleteResponse](../../models/gradeuppersecondarydeleteresponse.md)**

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

Update a GradeUpperSecondary

### Example Usage: errorExample

<!-- UsageSnippet language="python" operationID="GradeUpperSecondaryUpdate" method="patch" path="/grade-upper-secondary/{id}" example="errorExample" -->
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

    res = m_client.grade_upper_secondaries.update(id="123e4567-e89b-12d3-a456-426614174000", include_on_final_grade=True, external={
        "source_id": "12345678",
    }, language_code="SV", teacher1_employee_id="123e4567-e89b-12d3-a456-426614174000", teacher2_employee_id="123e4567-e89b-12d3-a456-426614174000", grade="A", grade_date=date.fromisoformat("2025-01-15"), grade_comment="Eleven har visat goda kunskaper i algebra.", extent="Normal", school_year="2", section="Program", teacher_comment="Eleven deltar aktivt och visar stort engagemang.", program_title="Teknikprogrammet", start_date=date.fromisoformat("2024-08-19"), end_date=date.fromisoformat("2025-01-17"))

    # Handle response
    print(res)

```
### Example Usage: requestExample

<!-- UsageSnippet language="python" operationID="GradeUpperSecondaryUpdate" method="patch" path="/grade-upper-secondary/{id}" example="requestExample" -->
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

    res = m_client.grade_upper_secondaries.update(id="123e4567-e89b-12d3-a456-426614174000", include_on_final_grade=True, external={
        "source_id": "12345678",
    }, language_code="SV", teacher1_employee_id="123e4567-e89b-12d3-a456-426614174000", teacher2_employee_id="123e4567-e89b-12d3-a456-426614174000", grade="A", grade_date=date.fromisoformat("2025-01-15"), grade_comment="Eleven har visat goda kunskaper i algebra.", extent="Normal", school_year="2", section="Program", teacher_comment="Eleven deltar aktivt och visar stort engagemang.", program_title="Teknikprogrammet", start_date=date.fromisoformat("2024-08-19"), end_date=date.fromisoformat("2025-01-17"))

    # Handle response
    print(res)

```
### Example Usage: responseExample

<!-- UsageSnippet language="python" operationID="GradeUpperSecondaryUpdate" method="patch" path="/grade-upper-secondary/{id}" example="responseExample" -->
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

    res = m_client.grade_upper_secondaries.update(id="123e4567-e89b-12d3-a456-426614174000", include_on_final_grade=True, external={
        "source_id": "12345678",
    }, language_code="SV", teacher1_employee_id="123e4567-e89b-12d3-a456-426614174000", teacher2_employee_id="123e4567-e89b-12d3-a456-426614174000", grade="A", grade_date=date.fromisoformat("2025-01-15"), grade_comment="Eleven har visat goda kunskaper i algebra.", extent="Normal", school_year="2", section="Program", teacher_comment="Eleven deltar aktivt och visar stort engagemang.", program_title="Teknikprogrammet", start_date=date.fromisoformat("2024-08-19"), end_date=date.fromisoformat("2025-01-17"))

    # Handle response
    print(res)

```
### Example Usage: validationError

<!-- UsageSnippet language="python" operationID="GradeUpperSecondaryUpdate" method="patch" path="/grade-upper-secondary/{id}" example="validationError" -->
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

    res = m_client.grade_upper_secondaries.update(id="123e4567-e89b-12d3-a456-426614174000", include_on_final_grade=True, external={
        "source_id": "12345678",
    }, language_code="SV", teacher1_employee_id="123e4567-e89b-12d3-a456-426614174000", teacher2_employee_id="123e4567-e89b-12d3-a456-426614174000", grade="A", grade_date=date.fromisoformat("2025-01-15"), grade_comment="Eleven har visat goda kunskaper i algebra.", extent="Normal", school_year="2", section="Program", teacher_comment="Eleven deltar aktivt och visar stort engagemang.", program_title="Teknikprogrammet", start_date=date.fromisoformat("2024-08-19"), end_date=date.fromisoformat("2025-01-17"))

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                               | Type                                                                                                                                                    | Required                                                                                                                                                | Description                                                                                                                                             | Example                                                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                                                                    | *str*                                                                                                                                                   | :heavy_check_mark:                                                                                                                                      | The unique identifier of the GradeUpperSecondary to update                                                                                              | 123e4567-e89b-12d3-a456-426614174000                                                                                                                    |
| `include_on_final_grade`                                                                                                                                | *bool*                                                                                                                                                  | :heavy_check_mark:                                                                                                                                      | Whether this course grade should be included when calculating the student's final grade certificate.                                                    | true                                                                                                                                                    |
| `external`                                                                                                                                              | [Optional[models.GradeUpperSecondaryUpdateExternal]](../../models/gradeuppersecondaryupdateexternal.md)                                                 | :heavy_minus_sign:                                                                                                                                      | ExternalRequest is the External-object used on Create and Update operations. Only SourceID can be set — the Source field is derived from the API key.   | {<br/>"sourceID": "12345678"<br/>}                                                                                                                      |
| `language_code`                                                                                                                                         | *OptionalNullable[str]*                                                                                                                                 | :heavy_minus_sign:                                                                                                                                      | The language code for the grade, used when the course is taught in a specific language.                                                                 | **Example 1:** SV<br/>**Example 2:** <nil>                                                                                                              |
| `teacher1_employee_id`                                                                                                                                  | *OptionalNullable[str]*                                                                                                                                 | :heavy_minus_sign:                                                                                                                                      | The ID of the primary teacher responsible for the grade. Must reference an Employee who has an active placement at the school referenced by SchoolID.   | **Example 1:** 123e4567-e89b-12d3-a456-426614174000<br/>**Example 2:** <nil>                                                                            |
| `teacher2_employee_id`                                                                                                                                  | *OptionalNullable[str]*                                                                                                                                 | :heavy_minus_sign:                                                                                                                                      | The ID of the secondary teacher responsible for the grade. Must reference an Employee who has an active placement at the school referenced by SchoolID. | **Example 1:** 123e4567-e89b-12d3-a456-426614174000<br/>**Example 2:** <nil>                                                                            |
| `grade`                                                                                                                                                 | [OptionalNullable[models.GradeUpperSecondaryUpdateGrade]](../../models/gradeuppersecondaryupdategrade.md)                                               | :heavy_minus_sign:                                                                                                                                      | The grade awarded to the student.                                                                                                                       | **Example 1:** A<br/>**Example 2:** <nil>                                                                                                               |
| `grade_date`                                                                                                                                            | [datetime](https://docs.python.org/3/library/datetime.html#datetime-objects)                                                                            | :heavy_minus_sign:                                                                                                                                      | The date the grade was awarded.                                                                                                                         | **Example 1:** 2025-01-15<br/>**Example 2:** <nil>                                                                                                      |
| `grade_comment`                                                                                                                                         | *OptionalNullable[str]*                                                                                                                                 | :heavy_minus_sign:                                                                                                                                      | A comment about the grade from the teacher.                                                                                                             | **Example 1:** Eleven har visat goda kunskaper i algebra.<br/>**Example 2:** <nil>                                                                      |
| `extent`                                                                                                                                                | [OptionalNullable[models.GradeUpperSecondaryUpdateExtent]](../../models/gradeuppersecondaryupdateextent.md)                                             | :heavy_minus_sign:                                                                                                                                      | The extent of the course for this student.                                                                                                              | **Example 1:** Normal<br/>**Example 2:** <nil>                                                                                                          |
| `school_year`                                                                                                                                           | [OptionalNullable[models.GradeUpperSecondaryUpdateSchoolYear]](../../models/gradeuppersecondaryupdateschoolyear.md)                                     | :heavy_minus_sign:                                                                                                                                      | The school year of the student at the time the grade was awarded.                                                                                       | **Example 1:** 2<br/>**Example 2:** <nil>                                                                                                               |
| `section`                                                                                                                                               | [OptionalNullable[models.GradeUpperSecondaryUpdateSection]](../../models/gradeuppersecondaryupdatesection.md)                                           | :heavy_minus_sign:                                                                                                                                      | The section/type of the course in the student's study plan.                                                                                             | **Example 1:** Program<br/>**Example 2:** <nil>                                                                                                         |
| `teacher_comment`                                                                                                                                       | *OptionalNullable[str]*                                                                                                                                 | :heavy_minus_sign:                                                                                                                                      | A comment from the teacher about the student's performance.                                                                                             | **Example 1:** Eleven deltar aktivt och visar stort engagemang.<br/>**Example 2:** <nil>                                                                |
| `program_title`                                                                                                                                         | *OptionalNullable[str]*                                                                                                                                 | :heavy_minus_sign:                                                                                                                                      | The title of the program this course belongs to. Used to associate the course with a specific educational program.                                      | **Example 1:** Teknikprogrammet<br/>**Example 2:** <nil>                                                                                                |
| `start_date`                                                                                                                                            | [datetime](https://docs.python.org/3/library/datetime.html#datetime-objects)                                                                            | :heavy_minus_sign:                                                                                                                                      | The date the student started the course.                                                                                                                | **Example 1:** 2024-08-19<br/>**Example 2:** <nil>                                                                                                      |
| `end_date`                                                                                                                                              | [datetime](https://docs.python.org/3/library/datetime.html#datetime-objects)                                                                            | :heavy_minus_sign:                                                                                                                                      | The date the student finished the course.                                                                                                               | **Example 1:** 2025-01-17<br/>**Example 2:** <nil>                                                                                                      |
| `retries`                                                                                                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                        | :heavy_minus_sign:                                                                                                                                      | Configuration to override the default retry behavior of the client.                                                                                     |                                                                                                                                                         |

### Response

**[models.GradeUpperSecondaryUpdateResponse](../../models/gradeuppersecondaryupdateresponse.md)**

### Errors

| Error Type                                           | Status Code                                          | Content Type                                         |
| ---------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- |
| errors.Error400ResponseBody                          | 400                                                  | application/json                                     |
| errors.Error401ResponseBody                          | 401                                                  | application/json                                     |
| errors.Error403ResponseBody                          | 403                                                  | application/json                                     |
| errors.Error404ResponseBody                          | 404                                                  | application/json                                     |
| errors.Error409ResponseBody                          | 409                                                  | application/json                                     |
| errors.GradeUpperSecondaryUpdate422ResponseBodyError | 422                                                  | application/json                                     |
| errors.Error429ResponseBody                          | 429                                                  | application/json                                     |
| errors.Error500ResponseBody                          | 500                                                  | application/json                                     |
| errors.MeitnerDefaultError                           | 4XX, 5XX                                             | \*/\*                                                |