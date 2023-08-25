# python-rule-engine

[![pypi](https://img.shields.io/pypi/v/python-rule-engine.svg)](https://pypi.python.org/pypi/python-rule-engine)
[![versions](https://img.shields.io/pypi/pyversions/python-rule-engine.svg)](https://github.com/santalvarez/python-rule-engine)
[![license](https://img.shields.io/github/license/pydantic/pydantic.svg)](https://github.com/pydantic/pydantic/blob/main/LICENSE)



A rule engine where rules are defined in JSON format. The syntax of the rules belongs to the [json-rules-engine](https://github.com/CacheControl/json-rules-engine) javascript library though it contains some changes to make it more powerfull.

## Installation
```
pip install python-rule-engine
```

## Quick Example

```python
from python_rule_engine import RuleEngine

rule = {
    "name": "basic_rule",
    "conditions": {
        "all": [
            {
                # JSONPath support
                "path": "$.person.name",
                "operator": "equal",
                "value": "Lionel"
            },
            {
                "path": "$.person.last_name",
                "operator": "equal",
                "value": "Messi"
            }
        ]
    }
}

obj = {
    "person": {
        "name": "Lionel",
        "last_name": "Messi"
    }
}

engine = RuleEngine([rule])

results = engine.evaluate(obj)

```

## Rule Format

Find more info about the rules [here](docs/rules.md).
