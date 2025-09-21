---

````markdown
# as_envhelper Tutorial

This tutorial will guide you step-by-step on how to install, configure, and use **as_envhelper**, a simple and powerful Python environment variable loader.  

---

## 1. Installation

Install the library via `pip`:

```bash
pip install as_envhelper
````

Make sure you are using Python 3.7 or above.

---

## 2. Create a `.env` File

Create a `.env` file in your project root with your environment variables. Example:

```
DB_USER=myuser
DB_PASSWORD=mypassword
DB_PORT=3306
ENV_MODE=development
SECRET_KEY=abcd1234efgh5678ijkl9012mnop3456
```

> Tip: Keep your `.env` file secure and never commit it to public repositories.

---

## 3. Load Environment Variables in Python

```python
from as_envhelper import load_env, get_env

# Load variables from .env file
load_env(".env")

# Access variables
db_user = get_env("DB_USER")
db_password = get_env("DB_PASSWORD")
db_port = get_env("DB_PORT", type=int)
env_mode = get_env("ENV_MODE", choices=["development", "production"])
secret_key = get_env("SECRET_KEY", required=True)

print(f"DB_USER = {db_user}")
print(f"DB_PORT = {db_port}")
print(f"ENV_MODE = {env_mode}")
```

---

## 4. Get All Environment Variables as a Dictionary

```python
from as_envhelper import env_to_dict

env_dict = env_to_dict()
print(env_dict)
```

---

## 5. Flask Integration

```python
from flask import Flask
from as_envhelper import apply_to_flask

app = Flask(__name__)

# Load .env variables into Flask config
apply_to_flask(app, ".env")

# Access environment variables via app config
print(app.config["DB_USER"])
```

---

## 6. Django Integration

```python
import sys
from as_envhelper import apply_to_django_settings

# Apply .env variables to Django settings module
apply_to_django_settings(sys.modules[__name__], ".env")

# Access variables directly
print(DB_USER)
print(DB_PASSWORD)
```

---

## 7. Handling Missing or Required Variables

```python
from as_envhelper import get_env

# Raises an error if variable is missing
api_key = get_env("API_KEY", required=True)

# Provide a default value if missing
debug_mode = get_env("DEBUG_MODE", default=False, type=bool)
```

---

## 8. Advanced Features

* **Type Casting:** Convert values to `int`, `float`, `bool`, or `str`
* **Regex Validation:** Ensure variables match specific patterns
* **Choices Validation:** Restrict values to predefined options
* **Numeric Ranges:** Ensure values fall within `min_val` and `max_val`
* **Flask Integration:** Load variables into `Flask` app config
* **Django Integration:** Apply variables directly to `Django` settings

---

## 9. Best Practices

* Keep sensitive data in `.env` and never commit it to public repositories
* Use `required=True` for critical variables
* Use type casting and validation for safe usage
* Update `.env` carefully and reload environment variables in your app

---

> By following this tutorial, even **Python beginners** can securely manage environment variables across **Flask**, **Django**, and standard Python projects using **as_envhelper**.

```

---

