```python
def modules(cls):

    import importlib, pkgutil

    ls = []
    gen = pkgutil.walk_packages(cls.__path__, cls.__name__ + ".")

    for each in gen:
        try:
            mod = importlib.import_module(each.name)
        except:
            continue
        
        ls.extend(map((lambda x: each.name+'.'+x), dir(mod)))

    return set(ls)

```
