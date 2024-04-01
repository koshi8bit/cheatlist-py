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

