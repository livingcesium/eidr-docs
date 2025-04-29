# Documentation for `party_query.py`

## Class: `PartyQuery`


**Description:**

Represents a service for querying party information.

This service allows querying party details using various parameters such as
ID, display name, organization ID, and more. It extends the `NoOperationRequest`
base class.


### Method: `__init__`


**Description:**

Initializes the PartyQuery service with optional query parameters.



**Parameters:**

|Name|Type|Description|
|----|----|-----------|
| expression | Optional[str] | The query expression. |
| page_number | Optional[int] | The page number for pagination. Defaults to 1. |
| page_size | Optional[int] | The number of results per page. Defaults to 1. |
| continuation_token | Optional[str] | Token for continuing a previous query. |

---

### Method: `validate`


**Description:**

Validates the query parameters.



**Returns:**

|Type|Description|
|----|-----------|
| bool | Always returns True as validation is not implemented. |


---
### Method: `objectify`


**Description:**

Converts the query parameters into the internal representation.

This method creates a `FindServices` object using the provided arguments.


**Raises:**

- ValueError: If invalid arguments are provided.

---

### Method: `party_expression`


**Description:**

Builds a query expression for party parameters.



**Parameters:**

|Name|Type|Description|
|----|----|-----------|
| id | str or None | The party ID. |
| display_name | str or None | The display name of the party. |
| sort_name | str or None | The sort name of the party. |
| organization_id | str or None | The organization ID of the party. |
| id_type | str or None | The type of the party ID. |
| alternate_party_name | str or None | Alternate name of the party. |
| contact_name | str or None | Contact name of the party. |
| primary_email | str or None | Primary email of the party. |
| alternate_email | str or None | Alternate email of the party. |
| contact_address | str or None | Contact address of the party. |
| contact_phone | str or None | Contact phone number of the party. |
| active | bool or None | Whether the party is active. |
| party_account_name | str or None | Account name of the party. |
| allowed_roles | str or None | Allowed roles for the party. |

**Returns:**

|Type|Description|
|----|-----------|
| str | A query expression string combining all provided parameters. |

---
