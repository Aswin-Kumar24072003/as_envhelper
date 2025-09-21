---

````markdown
# as_envhelper Examples

This file provides practical examples of using **as_envhelper**, a simple and powerful Python environment variable loader.  

---

## 1. Basic Usage

Load variables from a `.env` file and access them:

```python
from as_envhelper import load_env, get_env

# Load environment variables from a .env file
load_env(".env")

# Access a variable
db_user = get_env("DB_USER")
print("Database User:", db_user)

# Access a variable with type casting and default value
port = get_env("DB_PORT", default=3306, type=int)
print("Database Port:", port)
````

---

## 2. Get All Environment Variables as a Dictionary

```python
from as_envhelper import env_to_dict

env_dict = env_to_dict()
for key, value in env_dict.items():
    print(f"{key} = {value}")
```

---

## 3. Using Optional Validation

```python
from as_envhelper import get_env

# Must be one of the allowed choices
env_mode = get_env("ENV_MODE", choices=["development", "production"])
print("Environment Mode:", env_mode)

# Must match a regex pattern
api_key = get_env("API_KEY", regex=r"^[A-Za-z0-9]{32}$")
print("API Key:", api_key)

# Must be within a numeric range
max_users = get_env("MAX_USERS", type=int, min_val=1, max_val=100)
print("Max Users:", max_users)
```

---

## 4. Flask Integration

```python
from flask import Flask
from as_envhelper import apply_to_flask

app = Flask(__name__)

# Load .env variables into Flask config
apply_to_flask(app, ".env")

# Access environment variable in Flask config
print(app.config["DB_USER"])
```

---

## 5. Django Integration

```python
import sys
from as_envhelper import apply_to_django_settings

# Apply .env variables to Django settings module
apply_to_django_settings(sys.modules[__name__], ".env")

# Access the variables directly
print(DB_USER)
print(DB_PASSWORD)
```

---

## 6. Handling Missing or Required Variables

```python
from as_envhelper import get_env

# Raises an error if the variable is missing
secret_key = get_env("SECRET_KEY", required=True)
print("Secret Key:", secret_key)

# Provide a default value if missing
debug_mode = get_env("DEBUG_MODE", default=False, type=bool)
print("Debug Mode:", debug_mode)
```

---

## 7. Advanced Features

* Type casting: int, float, bool, str
* Regex validation for string patterns
* Choices validation for allowed values
* Numeric range validation (min\_val, max\_val)
* Flask and Django integration

---

> These examples cover most use cases for **as_envhelper**. For more details, see the [tutorial](tutorial.md) or the [README](../README.md).

```

---


```

