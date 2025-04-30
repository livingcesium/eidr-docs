
## 🚀 Quick Start

A short guide showing how to use the basic functionality of the EIDR Python SDK

---

## 🛠️ Configuration

### Option A — XML file

1. Copy the provided `config.xml` into `./config/config.xml`.
2. Open the file and replace the placeholders:

```xml
<EndpointConfig>
  <BaseURL>https://sandbox2.eidr.org:443/EIDR/</BaseURL>
  <Party>10.5237/XXXX‑XXXX</Party>
  <User>10.5238/youruser</User>
  <Passwd>supers3cret</Passwd>
</EndpointConfig>
```

### Option B—Python dict (great for CLI)

```python
config = {
    "endpoint": {
        "base_url": "https://sandbox2.eidr.org:443/EIDR/",
        "party":    "10.5237/XXXX-XXXX",
        "user":     "10.5238/youruser",
        "password": "supers3cret"
    }
}
```

Create the session from either source:

```python
from app.manager import SessionManager

# XML‑based (auto‑discovered)
session = SessionManager.from_default()

# Dict‑based
session = SessionManager.from_dict(config)
```

---

## 🚀 Quick-Start

Below are the **three most common operations** you will perform with the SDK.

## 1) Resolve

```python
meta = session.resolve("10.5240/8B55-F9AA-007F-B18E-C000-6")
print(meta.base_meta.resource_name, meta.base_meta.release_date)
```

---

## 2) Query

```python
from app.services import Query
from app.eidr_request import RegistryRequest

expr = Query.base_obj_expression(release_date="2005")
q = Query(
    response_type = Query.QueryResponseType.ID,
    expression    = expr,
    page_num      = 1,
    page_size     = 50
)

ids, token = session.query(RegistryRequest([q]))
print("First 5 IDs:", ids[:5])
```

---

## 3) Create (Basic Record)

#### 3.1 Generate a Template

```python
from pathlib import Path
from app.scheme.org.eidr.schema import CreationType

# This writes JSON stubs to ./records/
session.generate_templates(Path("records"), [CreationType.CREATE_BASIC])
print("Template created at records/create_basic.json — open it in your editor ✏️")
```

#### 3.2 Edit the Generated JSON
Open ```records/create_basic.json``` and fill in the blanks. A minimal example looks like:
```json
{
  "BaseObjectData": {
    "StructuralType": "Abstraction",
    "Mode": "Audio",
    "ReferentType": "Movie",
    "ResourceName": {
      "value": "SDK Demo Movie",
      "titleClass": "release",
      "lang": "en"
    },
    "ReleaseDate": "2025-04-30",
    "Administrators": {
      "Registrant": {
        "value": ""
      }
    }
  }
}
```

#### 3.3 Finish Up the Script
```python
import json
from pathlib import Path
from app.services.registration.create import Create
from app.eidr_request import RegistryRequest
from app.scheme.org.eidr.schema import CreateBasicDataType
from util import dict_to_instance

# Load your edited file
raw = json.loads(Path("records/create_basic.json").read_text())

# Default the Registrant value to your Party DOI if still empty
if not raw["BaseObjectData"]["Administrators"]["Registrant"]["value"]:
    raw["BaseObjectData"]["Administrators"]["Registrant"]["value"] = session.driver.config.party

record    = dict_to_instance(raw, CreateBasicDataType)
create_op = Create(record=record)
status, _ = session.register(RegistryRequest([create_op]), immediate_resp=True)

print("Create status:", status)
```

And now you're cooking with EIDR! Check out the documentation for more details and for other services

