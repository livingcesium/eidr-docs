
## Class: `GraphTraversal`


**Description:**

A class to handle graph traversal operations for a given DOI.


### Method: `find_ancestors`


**Description:**

Retrieve the ancestors of a given DOI.


**Parameters:**

|Name|Type|Description|
|----|----|-----------|
| doi | Optional[Union[str, AssetDoitype]] | The DOI to search for. If not provided, it will be validated. |
| referent_type_filter | list[ReferentType] | A list of referent types to filter by. |
| relationship_type_filter | list[RelationshipType] | A list of relationship types to filter by. |
| structural_type_filter | list[CreationStructuralType] | A list of structural types to filter by. |
| find_ancestors | FindAncestorsType | An instance of FindAncestorsType containing the search criteria. |

**Returns:**

| Type                                                  | Description                                                                                                                                                                                |
|-------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Tuple[Optional[ResponseReader], Optional[ValueError]] | A tuple where the first element is the ResponseReader instance containing relationship data, and the second is an optional ValueError indicating any issues with the response status code. |


---
### Method: `get_remotest_ancestor`


**Description:**

Retrieves remotest ancestor of a Digital Object


**Returns:**

| Type                                                  | Description                                                                                                                                                                                |
|-------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Tuple[Optional[ResponseReader], Optional[ValueError]] | A tuple where the first element is the ResponseReader instance containing relationship data, and the second is an optional ValueError indicating any issues with the response status code. |

---
```python
print("AAAAAAAAA")
```


### Method: `find_descendants`


**Description:**

Retrieve the descendants of a given DOI.



**Parameters:**

| Name                     | Type                               | Description                                                        |
|--------------------------|------------------------------------|--------------------------------------------------------------------|
| doi                      | Optional[Union[str, AssetDoitype]] | The DOI to search for. If not provided, it will be validated.      |
| extended_family          | Optional[bool]                     | Whether to include extended family members in the result.          |
| referent_type_filter     | list[ReferentType]                 | A list of referent types to filter by.                             |
| relationship_type_filter | list[RelationshipType]             | A list of relationship types to filter by.                         |
| structural_type_filter   | list[CreationStructuralType]       | A list of structural types to filter by.                           |
| find_descendants         | FindDescendantsType                | An instance of FindDescendantsType containing the search criteria. |

**Returns:**

| Type                                                  | Description                                                                                                                                                                                |
|-------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Tuple[Optional[ResponseReader], Optional[ValueError]] | A tuple where the first element is the ResponseReader instance containing relationship data, and the second is an optional ValueError indicating any issues with the response status code. |
| str                                                   | The serialized XML representation of the request.                                                                                                                                          |


---
### Method: `get_leaf_descendants`


**Description:**

Retrieve the leaf descendants of a given DOI.


**Returns:**

| Type                                                  | Description                                                                                                                                                                                |
|-------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Tuple[Optional[ResponseReader], Optional[ValueError]] | A tuple where the first element is the ResponseReader instance containing relationship data, and the second is an optional ValueError indicating any issues with the response status code. |


---
### Method: `get_lightweight_relationships`


**Description:**

Retrieves lightweight relationships of a Digital Object.



**Returns:**

| Type                                                  | Description                                                                                                                                                                                |
|-------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Tuple[Optional[ResponseReader], Optional[ValueError]] | A tuple where the first element is the ResponseReader instance containing relationship data, and the second is an optional ValueError indicating any issues with the response status code. |


---
### Method: `get_dependants`


**Description:**

Retrieves all dependents of a Digital Object.


**Returns:**

| Type                                                  | Description                                                                                                                                                                                |
|-------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Tuple[Optional[ResponseReader], Optional[ValueError]] | A tuple where the first element is the ResponseReader instance containing dependent objects, and the second is an optional ValueError indicating any issues with the response status code. |

**Notes:**

    - Dependants are objects upon which the given object depends.

---


### Method: `get_children`


**Description:**

Retrieves immediate dependents (children) of a Digital Object.



**Returns:**

| Type                                                  | Description                                                                                                                                                                            |
|-------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Tuple[Optional[ResponseReader], Optional[ValueError]] | A tuple where the first element is the ResponseReader instance containing child objects, and the second is an optional ValueError indicating any issues with the response status code. |

**Notes:**

    - Children are direct dependents in the object's dependency tree.

---

### Method: `get_parent`


**Description:**

Retrieves the immediate ancestor (parent) of a Digital Object.



**Returns:**

| Type                                                  | Description                                                                                                                                                                                 |
|-------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Tuple[Optional[ResponseReader], Optional[ValueError]] | A tuple where the first element is the ResponseReader instance containing parent information, and the second is an optional ValueError indicating any issues with the response status code. |

**Notes:**

    - The parent is the direct ancestor in the object's lineage.

---


### Method: `get_series_ancestry`


**Description:**

Retrieves all ancestors of a Digital Object, tracing its lineage.



**Returns:**

| Type                                                  | Description                                                                                                                                                                                   |
|-------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Tuple[Optional[ResponseReader], Optional[ValueError]] | A tuple where the first element is the ResponseReader instance containing ancestor information, and the second is an optional ValueError indicating any issues with the response status code. |

**Notes:**

    - Series ancestry provides a complete lineage of the object.

---


### Method: `video_service_get_children`


**Description:**

Retrieves the children of a given Digital Object using the video service.



**Parameters:**

| Name         | Type                               | Description                                                   |
|--------------|------------------------------------|---------------------------------------------------------------|
| doi          | Optional[Union[str, AssetDoitype]] | The DOI to search for. If not provided, it will be validated. |
| all_children | bool                               | Whether to include all children in the result.                |

**Returns:**

| Type                                                                 | Description                                                                                                                                                                                |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Tuple[Optional[ResponseReader.ResponseReader], Optional[ValueError]] | A tuple where the first element is the ResponseReader instance containing child information, and the second is an optional ValueError indicating any issues with the response status code. |


---
### Method: `video_service_get_parent`


**Description:**

Retrieves the parent of a given Digital Object using the video service.



**Parameters:**

| Name | Type                               | Description                                                   |
|------|------------------------------------|---------------------------------------------------------------|
| doi  | Optional[Union[str, AssetDoitype]] | The DOI to search for. If not provided, it will be validated. |

**Returns:**

| Type                                                                 | Description                                                                                                                                                                                 |
|----------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Tuple[Optional[ResponseReader.ResponseReader], Optional[ValueError]] | A tuple where the first element is the ResponseReader instance containing parent information, and the second is an optional ValueError indicating any issues with the response status code. |


---
### Method: `validate_response`


**Description:**

Validates and processes the response from a server request.
    validates response if request is not provided


**Parameters:**

| Name    | Type    | Description                    |
|---------|---------|--------------------------------|
| request | Request | The request object to be sent. |

**Returns:**

| Type                                                  | Description                                                                                                                                                                     |
|-------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Tuple[Optional[ResponseReader], Optional[ValueError]] | A tuple containing the ResponseReader instance if successful, or None if an error occurs. The second element is a ValueError if there's an issue with the response status code. |

**Notes:**

    - Sends the request using POST.
    - Converts the response content to pretty-formatted XML.
    - Uses ResponseReader to parse the XML and check the status code.
    - Raises specific errors based on status codes 18 and 19.

---


### Method: `validate_doi`


**Description:**

Validate the DOI and convert it to an AssetDoitype.



**Parameters:**

| Name | Type                     | Description          |
|------|--------------------------|----------------------|
| doi  | Union[str, AssetDoitype] | The DOI to validate. |

**Raises:**

Value Error If doi is Not a string or AssetDOIType

**Raises:**

Value Error if doi is None/Empty

**Returns:**

| Type         | Description        |
|--------------|--------------------|
| AssetDoitype | The validated DOI. |


---
### Method: `create_operations`


**Description:**

Create a Request object from a list of OperationType objects.



**Parameters:**

| Name      | Type                | Description                                                |
|-----------|---------------------|------------------------------------------------------------|
| operation | list[OperationType] | A list of OperationType objects to include in the request. |

**Returns:**

| Type    | Description                 |
|---------|-----------------------------|
| Request | The created Request object. |


---
### Method: `serialize`


**Description:**

Serialize the given Request object into an XML string using the configured serializer.



**Parameters:**

| Name | Type    | Description                      |
|------|---------|----------------------------------|
| req  | Request | The Request object to serialize. |

**Returns:**

| Type | Description                                       |
|------|---------------------------------------------------|
| str  | The serialized XML representation of the request. |



---
## Missing docstrings

- **Method** `GraphTraversal.__init__`
