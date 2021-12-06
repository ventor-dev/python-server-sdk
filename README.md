# DevCycle Python SDK

Welcome to the the DevCycle Python SDK, initially generated via the [DevCycle Bucketing API](https://docs.devcycle.com/bucketing-api/#tag/devcycle).

## Requirements.

Python 2.7 and 3.4+

## Installation

```sh
pip install devcycle-sdk
```
(you may need to run `pip` with root permission: `sudo pip install devcycle-sdk`)

Then import the package:
```python
import devcycle_python_sdk 
```

## Getting Started

```python
    from __future__ import print_function
    from devcycle_python_sdk import Configuration, DVCClient
    from devcycle_python_sdk.rest import ApiException
    configuration = Configuration()
    configuration.api_key['Authorization'] = 'your_server_key_here'

     # create an instance of the API class
     dvc = DVCClient(configuration)
    
     user = UserData(
        user_id='test',
        email='example@example.ca',
        country='CA'
    )
```

## Usage

### Getting All Features
```python
    try:
        # Get all features by key for user data
        api_response = dvc.all_features(user)
        print(api_response)
    except ApiException as e:
        print("Exception when calling DVCClient->all_features: %s\n" % e)
    
```

### Grabbing Variable Values
To get values from your Variables, `get_variables()` is used to fetch variable values using the identifier `key` coupled with a default value. The default value can be of type string, boolean, number, or object.
```python
    key = 'key-test' # str | Variable key
    
    try:
        # Get variable by key for user data
        api_response = dvc.variable(user, key, 'default-value')
        print(api_response)
    except ApiException as e:
         print("Exception when calling DVCClient->variable: %s\n" % e)
    
    try:
        # Get all variables for user data
        api_response = dvc.all_variables(user)
        print(api_response)
    except ApiException as e:
        print("Exception when calling DVCClient->all_variables: %s\n" % e)
    
```

### Track Event
To POST custom event for a user
```python

    event = Event(
        type="customEvent",
        target="somevariable.key"
    )
    try:
        # Post events to DevCycle for user
        api_response = dvc.track(user, event)
        print(api_response)
    except ApiException as e:
        print("Exception when calling DVCClient->track: %s\n" % e)
```
