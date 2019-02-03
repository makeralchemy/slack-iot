# Python script for sending IOT messages to Slack

## Overview
*slack.py* is a Python script used to send IOT messages via slack to users.

*slack.py* will run under both Python 2 and Python 3.  It was tested on Python 2.7.13 and Python 3.5.3.

## Usage Instructions

*slack.py* can be executed from the command line, inside a shell script, or imported into another Python script.

### Command Line Usage:

    $ python slack.py -h
    usage: slack.py [-h] [-d] message

    positional arguments:
      message

    optional arguments:
      -h, --help   show this help message and exit
      -d, --debug  in debug mode messages are printed and not sent to slack

### Command Line Examples
Send a IOT message to slack:

     $ python slack.py -m "Test Message"

Simulate sending a message to slack:

     $ python slack.py -m "Test Message" -d

or

     $ python slack.py -m "Test Message" --debug

### Python script usage

    import slack

    # Get the slack credentials using all the defaults
    slack_webhook = slack.Iot()

    # Send the message to slack
    slack_webhook.post_message("Test Message")

    # If failure, print the status code, exit with non-zero return code
    if slack_webhook.status_code != 200:
        print("Failed to send slack message. Status code: {}".format(slack_webhook.status_code))

### Instantiating the slack Iot object:

Three parameters can be specified when instantiating the slack Iot object:
- url: the slack webhooks URL
- credentials_file: the file name for the slack credentials
- debug: set to False if messages are to be sent to slack; set to True if messages are to
be printed rather than sent.

Below is an example of instantiating a slack Iot object with all parameters specified.
The values below are the default values. Parameters only need to be specified when 
overriding these defaults.

    slack_webhook = slack.Iot(url="https://hooks.slack.com/services/",
                              credentials_file="slack.credentials",
                              debug=False,
                              )


