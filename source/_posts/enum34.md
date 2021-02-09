---
title: enum34
date: 2020-02-20 15:12:00
tags:
---

```
  Traceback (most recent call last):
    File "C:\Program Files\Python37\lib\runpy.py", line 193, in _run_module_as_main
      "__main__", mod_spec)
    File "C:\Program Files\Python37\lib\runpy.py", line 85, in _run_code
      exec(code, run_globals)
    File "e:\projects\maofeng\env\lib\site-packages\pip\__main__.py", line 16, in <module>
      from pip._internal import main as _main  # isort:skip # noqa
    File "e:\projects\maofeng\env\lib\site-packages\pip\_internal\__init__.py", line 4, in <module>
      import locale
    File "C:\Program Files\Python37\lib\locale.py", line 16, in <module>
      import re
    File "C:\Program Files\Python37\lib\re.py", line 143, in <module>
      class RegexFlag(enum.IntFlag):
  AttributeError: module 'enum' has no attribute 'IntFlag'
```