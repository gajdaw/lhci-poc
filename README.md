# Lighthouse CI / POC

## 1. Start application to monitor:

    cd nginx
    docker-compose up -d

    http http://localhost:8080

## 2. Start LHCI server

    cd server
    docker-compose up -d

    http://localhost:9001


## 3. Run LHCI wizard:

    lhci wizard

    Which wizard do you want to run? new-project
    What is the URL of your LHCI server? http://localhost:9001
    What would you like to name the project? some-interesting-project
    Where is the project's code hosted? git@github.com:gajdaw/lhci-poc.git
    What branch is considered the repo's trunk or main branch? main

    Created project hello-world-project (e2ccdf45-301e-4032-b0a4-bc9f97a61469)!
    Use build token 1ae0d142-c7ab-4375-b358-9cbee85127ed to add data.
    Use admin token NEvJavbCo8hjUyRaMP8NJo1QfJnrbI3Qcp1hBdyR to manage data. KEEP THIS SECRET!

## 4. Run LHCI to create data

    cd run
    lhci collect --url=http://localhost:8080

## 5. Run LHCI 

    lhci upload  --token=1ae0d142-c7ab-4375-b358-9cbee85127ed --serverBaseUrl=http://localhost:9001

