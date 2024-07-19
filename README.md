Created based on a comment by ImpeccableChicken: https://stackoverflow.com/questions/78764500/configuration-file-of-python-app-shared-across-sub-packages

```
stackoverflow_imports/
    main.py
    devices/
        __init__.py
        CONFIG.py
        motors/
            __init__.py
            one_kind_of_motor.py
```

### CONFIG.py
```python
globals()['one_setting'] = 1.2345
```
### main.py
```python
from devices import CONFIG

print(CONFIG.one_setting)
```
Result:
```
1.2345
```
### one_kind_of_motor.py
```python
from .. import CONFIG

print(CONFIG.one_setting)
```
Result:
```
Traceback (most recent call last):
  File "c:\...\stackoverflow_imports\devices\motors\one_kind_of_motor.py", line 1, in <module>
    from .. import CONFIG
ImportError: attempted relative import with no known parent package
```
