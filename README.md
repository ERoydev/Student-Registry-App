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

2. Since my jenkis is running locally i cannot create webhook with local host since github cannot access private network.
    - use additionaly software named **ngrock**
    - It downloads ngrock.exe file which opens my terminal and there i nee to run
    ```bash
        ngrok http 8080
    ```
    - On the Forwarding => I have url link which is redirecting to my jenkins. I am going to use it as PAYLOAD_URL for git webhook
    ```ru
        PAYLOAD_URL = https://ac63-77-78-30-58.ngrok-free.app/github-webhook/
        Content Type = application/json
        Secret = Optionally, secret token for additional security

    ```

3. In my jenkins i need on my Job => Configure to set Triggers to **GitHub hook trigger for GITScm polling** => Active

4. Have in mind if you are testing .Net apps you should install MSBuild and .NET SDK SUPPORT plugins inside jenkins

5. I solve the problem of dotnet not found in jenkins with these commands:

5.1 First i enter into docker into my terminal
```bash
    docker exec -u root -it myjenkins bash
```
5.2 I install dotnet
```bash
    apt-get update
    apt-get install -y wget apt-transport-https software-properties-common
    wget https://packages.microsoft.com/config/debian/12/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
    dpkg -i packages-microsoft-prod.deb
    apt-get update
    apt-get install -y dotnet-sdk-6.0
```

## Errors:

1. If error occurs.
    - I can check in Manage Jenkins => System Log - to see if jenkins has received POST request from Github webhook
    - If it does likely my issue is somewhere from Configuration of the Job 


