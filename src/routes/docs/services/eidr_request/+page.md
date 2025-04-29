# Documentation for `eidr_request.py`

## Class: `RegistryRequest`


**Description:**

A class representing a registry request that is one or many operations of the same type.

Attributes:
    response_type (Query.QueryResponseType | Enum | str): The type of response expected from the request.
Methods:
    __init__(operations: List[ServiceBase]):
        Initializes the RegistryRequest with a list of operations.
    objectify():
        Converts the operations into a Request object.
    add(other: ServiceBase):
        Adds another operation to the batch, ensuring it is of the same type.
    validate() -> bool:
        Validates the request.


### Method: `__init__`


**Description:**

Initializes the RegistryRequest with a list of operations.



**Parameters:**

|Name|Type|Description|
|----|----|-----------|
| operations | List[ServiceBase] | A list of ServiceBase operations. |

**Raises:**

- ValueError: If the first operation is a RegistryRequest or if operations are of mixed types.

---

### Method: `objectify`


**Description:**

Converts the operations into a Request object.

---

### Method: `add`


**Description:**

Adds another operation to the batch.



**Parameters:**

|Name|Type|Description|
|----|----|-----------|
| other | ServiceBase | The operation to add. |

**Raises:**

- ValueError: If the operation type does not match the existing batch type.

---

### Method: `validate`


**Description:**

Validates the request.



**Returns:**

|Type|Description|
|----|-----------|
| bool | Always returns True. |

---
