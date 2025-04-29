# Documentation for `util.py`

### Function: `attempt`


**Description:**

A Go-like attempt function that returns a tuple of the result and an exception if it occurs.


**Parameters:**

|Name|Description|
|----|-----------|
| func | function to attempt |

**Returns:**

|Description|
|-----------|
| tuple of (result, exception) |


---
### Function: `default_dataclass`


**Description:**

Create an instance of a dataclass with default values, including for nested dataclasses.


**Parameters:**

|Name|Description|
|----|-----------|
| cls | The dataclass to create an instance of. |
| default_enums | If True, use the first value of the enum as the default value. |

**Returns:**

|Description|
|-----------|
| An instance of the dataclass with default values. |


---
### Function: `instance_to_dict`


**Description:**

Convert a dataclass to a dict representation.


**Parameters:**

|Name|Description|
|----|-----------|
| obj | dataclass instance |

**Returns:**

|Description|
|-----------|
|  |

---
- dict representation of the dataclass

### Function: `dict_to_instance`


**Description:**

Convert a dict representation of a dataclass to an instance of the dataclass.


**Parameters:**

|Name|Description|
|----|-----------|
| d | dict representation of the dataclass |

**Returns:**

|Description|
|-----------|
|  |

---
- instance of the dataclass

### Function: `create_record_config`


**Description:**

Create a new record config file in the given file path.

Record types:
    - basic
    - series
    - interactive
    - episode
    - season
    - manifestation
    - clip
    - composite
    - edit
    - compilation


**Parameters:**

|Name|Description|
|----|-----------|
| file_name | name of the newly created file |
| record_type | record type |


## Missing docstrings

- **Function** `is_optional_type`
- **Function** `get_optional_inner_type`
- **Function** `get_type_name`
- **Function** `to_field_dict`
- **Function** `extract_union`
- **Function** `generate_default`
- **Function** `generate_xml`
- **Function** `filter_type_info`
- **Function** `repr_non_serials`
