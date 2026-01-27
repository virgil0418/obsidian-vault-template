---
up:
  - "[[Mac]]"
related:
date: 2026-01-18
---

右CMD+AWSD控制方向键盘
```
{
    "description": "arrow keys",
    "manipulators": [
        {
            "from": {
                "key_code": "a",
                "modifiers": {
                    "mandatory": ["right_command"],
                    "optional": ["any"]
                }
            },
            "to": [{ "key_code": "left_arrow" }],
            "type": "basic"
        },
        {
            "from": {
                "key_code": "s",
                "modifiers": {
                    "mandatory": ["right_command"],
                    "optional": ["any"]
                }
            },
            "to": [{ "key_code": "down_arrow" }],
            "type": "basic"
        },
        {
            "from": {
                "key_code": "w",
                "modifiers": {
                    "mandatory": ["right_command"],
                    "optional": ["any"]
                }
            },
            "to": [{ "key_code": "up_arrow" }],
            "type": "basic"
        },
        {
            "from": {
                "key_code": "d",
                "modifiers": {
                    "mandatory": ["right_command"],
                    "optional": ["any"]
                }
            },
            "to": [{ "key_code": "right_arrow" }],
            "type": "basic"
        }
    ]
}

```