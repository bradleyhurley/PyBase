# PyBase

## Demo
![](demo.gif)

## Installation

Install Python Virtual Env and IPython
```bash
$ mkvirtualenv PyBase
$ workon PyBase
$ pip install ipython
```

Install PythonNet Dependencies
```bash
$ brew install pkg-config
$ brew cask install mono-mdk
```

Install PythonNet
- Mono Version
  - `$ ls /Library/Frameworks/Mono.framework/Versions/`
- pip install from /dist
  - `$ pip install --user dist/pythonnet-{ press tab key}`

```bash
$ git clone https://github.com/pythonnet/pythonnet
$ cd pythonnet/

$ PKG_CONFIG_PATH=/Library/Frameworks/Mono.framework/Versions/{Mono Version}/lib/pkgconfig python setup.py bdist_wheel

$ pip install --user dist/pythonnet-{pythonnet version}-{cpython version}-{mac version}.whl
```

Sample Usage
- If using IPython disable Jedi
  - %config IPCompleter.use_jedi=False

```python
import clr
clr.AddReference('/local/path/to/Hyland.Unity.dll')
clr.AddReference('/local/path/to/Hyland.Types.dll')

# Jedi silently encounters an auto completion error and crashes. Disabling reverts to the older implementation
%config IPCompleter.use_jedi=False

auth = Application.CreateOnBaseAuthenticationProperties('app_server_url', 'user', 'password', 'data_source')

app = Application.Connect(auth)
app.SessionID
```
