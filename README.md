# Python cheatlist

## main
```py
import os
import logging


def check_env_variables():
    variables = [
        "VITA_LIFE_SPREADSHEET_ID",
        "VITA_LIFE_SPREADSHEET_YEAR",
    ]

    for variable in variables:
        if variable not in os.environ:
            raise EnvironmentError(f"OS variable '{variable}' not found")


if __name__ == '__main__':
    logging.basicConfig(level=logging.WARNING,
                        format="%(asctime)s - %(levelname)s - %(message)s")
    load_dotenv()
    check_env_variables()
    logging.warning('init ok')
    
```

## env
`pip3 install python-dotenv`
```py
from dotenv import load_dotenv


if __name__ == '__main__':
    load_dotenv()
```

## flask
`pip3 install flask waitress`
```py
from flask import Flask, request
from waitress import serve


app = Flask(__name__)


@app.route("/")
def hello_world():
    return f"<h1>" \
           f"I'm alive!" \
           f"</h1>"


if __name__ == '__main__':
    # app.run(host='0.0.0.0', port=3000)       # debug
    # serve(app, host='0.0.0.0', port=3000)    # release
```

## JSON

```py
import json

with open("conf.json") as f:
    d = json.load(f)
    print(d)
    print(json.dumps(d, indent=4))
```

```json
{
    "a": [1,3,"asdf",true],
    "b": {
        "Hello": "world"
    }
}
```

## args

```py
import argparse


if __name__ == "__main__":
    parser = argparse.ArgumentParser()
    parser = argparse.ArgumentParser(prog='ProgramName',
                                     description='What the program does',
                                     epilog='Text at the bottom of help')


    parser.add_argument('filename', help="some help text")          # positional argument
    parser.add_argument('-c', '--count')                            # option that takes a value
    parser.add_argument('-v', '--verbose', action='store_true')     # on/off flag
    
    args = parser.parse_args()

    print(args.filename, args.count, args.verbose)

```
