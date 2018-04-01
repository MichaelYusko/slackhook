# slackhook
Simple, slack's webhook integration for a Flask application.

First what do you need, create a Webhook for you a slack application follow the link [Outgoing Webhooks](https://api.slack.com/custom-integrations/outgoing-webhooks) After that, you able to playing with a Webhook.

[![Build Status](https://travis-ci.org/MichaelYusko/slackhook.svg?branch=master)](https://travis-ci.org/MichaelYusko/slackhook)
[![PyPI version](https://badge.fury.io/py/slackhook.svg)](https://badge.fury.io/py/slackhook)


Installation
```
pip install slackhook
```


Example of usage
```python
from flask import Flask, jsonify
from slackhook.hook import SlackWebHook

# :NOTE:
# When you initialize an application
# By default you will be have a POST /slack-webhook route
# If you want change the route name
# Add endpoint argument to the SlackWebHook class
# For example, app = SlackWebHook(app, endpoint='/my-name')

app = Flask(__name__)
slack = SlackWebHook(app)


@slack.hook()
def slack_hook(data):
    message = 'links in order to solve an problems(firecode.io, leetcode.com)'
    if data == 'algos-resources':
        return jsonify(text=message)

if __name__ == '__main__':
    app.run()
```


Result of the code above

![example](https://user-images.githubusercontent.com/13191999/38173932-251cdd34-35ce-11e8-8e34-63c448f117a4.png)