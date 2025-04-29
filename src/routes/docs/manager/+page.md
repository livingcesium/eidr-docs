# Documentation for `manager.py`

## Class: `SessionManager`

**Description:**

A class to manage a session with the EIDR API, using a config file.  
Maintains a list of tokens for the session, and exposes methods to interact with the API.

### Method: `from_default`

**Description:**

Create a `SessionManager` instance using the default config file.

**Returns:**

| Type           | Description                                                |
|----------------|------------------------------------------------------------|
| SessionManager | An instance of `SessionManager` with the default `API_Driver`. |

---

### Method: `post`

**Description:**

Post a request to the EIDR API.

**Parameters:**

| Name     | Description                        |
|----------|------------------------------------|
| req      | The request to post.               |
| res_type | _Unused._                          |
| params   | Extra HTTP parameters to pass over |

**Returns:**

| Type           | Description                                           |
|----------------|-------------------------------------------------------|
| ResponseReader | The response from the API wrapped in a helper class.  |

---

### Method: `resolve`

**Description:**

Resolve an ID to a `FullMeta` object (will be streamlined into file paradigm).

**Parameters:**

| Name         | Description                  |
|--------------|------------------------------|
| resolve_mode | The type of response desired |
| id           | The ID to resolve            |

**Returns:**

| Type     | Description                        |
|----------|------------------------------------|
| FullMeta | The resolved `FullMeta` object.    |

---

### Method: `query`

**Description:**

Query the EIDR API with a query request.

**Parameters:**

| Name    | Description                                                           |
|---------|-----------------------------------------------------------------------|
| q       | A `RegistryRequest` of type **Query**.                                |
| as_file | Whether to save results to `query_results.json`.                      |

**Returns:**

| Type                                | Description                                                                                                |
|-------------------------------------|------------------------------------------------------------------------------------------------------------|
| Tuple[List\[SimpleMetadata\], str]  | A list of `SimpleMetadata` objects plus a continuation token.                                             |
| Tuple[List\[str\], str]             | A list of EIDR IDs plus a continuation token (when IDs are requested instead).                            |

---

### Method: `status`

**Description:**

Get the status of an operation using the provided service.

**Parameters:**

| Name | Description                 |
|------|-----------------------------|
| s    | The status request to post. |

**Returns:**

| Type                   | Description                                                   |
|------------------------|---------------------------------------------------------------|
| Tuple[List[dict], str] | A list of operation-status dicts and a continuation token.    |

---

### Method: `future_status`

**Description:**

Get the status of an operation, for use in an async pipeline.

**Parameters:**

| Name    | Description                       |
|---------|-----------------------------------|
| s       | The status request to post.       |
| wait    | Seconds to wait between retries.  |
| retries | Number of retries to attempt.     |

**Returns:**

| Type           | Description                                                      |
|----------------|------------------------------------------------------------------|
| List\[Future\] | Futures representing the eventual status of the operation.       |

---

### Method: `service_resolve`

**Description:**

Resolve a service to a `ServiceMeta` object.

**Parameters:**

| Name        | Description                                         |
|-------------|-----------------------------------------------------|
| id          | ID of the service in the EIDR registry.             |
| service_doi | DOI of the service (if different from `id`).        |
| followAlias | Whether to follow the alias of the service.         |

**Returns:**

| Type        | Description                         |
|-------------|-------------------------------------|
| ServiceMeta | The resolved `ServiceMeta` object.  |

---

### Method: `service_query`

**Description:**

Query the EIDR API with a service-query request.

**Parameters:**

| Name | Description                                   |
|------|-----------------------------------------------|
| s    | The service-query (or queries) request to post |

**Returns:**

| Type                | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| List\[ServiceMeta\] | A list of `ServiceMeta` objects representing the matched services.          |

---

### Method: `party_resolve`

**Description:**

Resolve a party to a `PartyMeta` object.

**Parameters:**

| Name         | Description                          |
|--------------|--------------------------------------|
| party_id     | The ID of the party to resolve.      |
| resolve_mode | The type of response desired.        |

**Returns:**

| Type      | Description                       |
|-----------|-----------------------------------|
| PartyMeta | The resolved `PartyMeta` object.  |

---

### Method: `user_resolve`

**Description:**

Resolve a user.

**Parameters:**

| Name        | Description                       |
|-------------|-----------------------------------|
| user_doi    | The DOI of the user to resolve.   |
| resolve_mode| The type of response desired.     |

**Returns:**

| Type           | Description                                           |
|----------------|-------------------------------------------------------|
| ResponseReader | The response from the API wrapped in a helper class.  |

---

### Method: `change_user_password`

**Description:**

Change a user’s password (current credentials must be in the config).

**Parameters:**

| Name     | Description                                     |
|----------|-------------------------------------------------|
| user_doi | The DOI of the user to change the password for. |
| password | The new password                                |

**Returns:**

| Type | Description |
|------|-------------|
| None | —           |

---

### Method: `party_query`

**Description:**

Query the EIDR API with a party-query request.

**Parameters:**

| Name | Description                                 |
|------|---------------------------------------------|
| p    | The party-query request to post.            |
| full | Return full metadata (`True`) or just IDs.  |

**Returns:**

| Type               | Description                                                    |
|--------------------|----------------------------------------------------------------|
| List\[PartyMeta\]  | List of `PartyMeta` objects (when `full=True`).                |
| List\[str\]        | List of party IDs (when `full=False`).                         |

---

### Method: `permissions`

**Description:**

Get the list of parties that have permission for an operation.

**Parameters:**

| Name      | Description                       |
|-----------|-----------------------------------|
| object_id | The ID of the object.             |
| acl_type  | The type of permissions to query. |

**Returns:**

| Type        | Description                                              |
|-------------|----------------------------------------------------------|
| List\[str\] | Party IDs that have the specified permission.            |

---

### Method: `modification_base`

**Description:**

Get the base metadata required to perform a modification.

**Parameters:**

| Name              | Description                              |
|-------------------|------------------------------------------|
| object_id         | The object ID to get base metadata for.  |
| modification_type | The type of modification to perform.     |

**Returns:**

| Type | Description                                      |
|------|--------------------------------------------------|
| dict | Dictionary containing the base metadata for edit |

---

## Missing docstrings

- **Class** `AdminResponseError`
- **Function** `check_err`
- **Function** `test_permissions`
- **Function** `test_query`
- **Function** `test_modification_base`
- **Method** `SessionManager.__init__`
