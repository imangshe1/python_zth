# str
Immutable sequence of unicode codepoints
- immutable - means you can't modify str content
- sequence - follows the sequence protocol
## str literals
```python
'this is a literal string'
"this is a literal string too"

# multiline str
"this is a\n multiline str"

"""this is a
multiline str too"""

'''this is a
multiline str too'''
```

> ***'\n'*** is a universal newline in python - io in text mode will automatically translate ***'\n'*** to/from native newline
> https://pythonconquerstheuniverse.wordpress.com/2011/05/08/newline-conversion-in-python-3/
```python
# escape char in literals
"say \"hello\""
'say "hello" better'

# raw str
"instead of C:\\foo\\goo"
r"C:\foo\goo"
```
```python
# format strings (f-string)
today = datatime.now()
f"today is {today} tomorrow is {today + datetime.timedelta(days=1)}"

# raw f-string
folder = "foo"
rf"C:\tmp\{folder}"
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTMxNDgzMTYwMSwtMzE2MTI3NDY1LC0xMz
Y3Nzk2MDA3LDE4MDM2MDM5NDhdfQ==
-->