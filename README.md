# Student-Registry-App


# Used to practice Jenkins

## Jenkins Notes:

1. In order to setup CI proccess with jenkins and to start my jobs on jenkins everytime i commit in my github repo i need:
    - To create in Github webhook which is going to allow external services to be allowed when event happens in my git repo

    ```ru
        http://localhost:8080/ => is tipically my default jenkins url. (change if u have another one)
        PAYLOAD_URL = http://localhost:8080/github-webhook/
        Content Type = application/json
        Secret = Optionally, secret token for additional security

    ```