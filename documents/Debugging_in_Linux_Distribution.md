# Debugging

## Debugging with a Python path:

This function checks the python environment in the current user.

```
python3 -c "import sys; print(sys.path)"
```

This is the source of local user 
```
cd /home/tod/.local/lib/python3.9/site-packages
```

This command start gunicorn proxy server
```
gunicorn --bind 0.0.0.0:5000 wsgi:app
```
