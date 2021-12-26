# CODE SNIPPETS

## create new env

1. bikin folder project, misal 'pythonapp' kemudian `cd pythonapp`
2. jalankan `python3.9 -m venv pythonapp-env`, dimana `pythonapp-env` adalah nama environment pada project tersebut
3. jalankan `source pythonapp-env/bin/activate` untuk aktifkan environment tersebut


## python-golang comparison

| python | golang |
|--------|-------|
| _venv_ | _go modules_ |
| _requirement.txt_ | _go.mod_ |
| `pip install -r requirement.txt` | `go mod tidy` |
| `pip freeze > requirement.txt` | `go mod init project_name` |
 