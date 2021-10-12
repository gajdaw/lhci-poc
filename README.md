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
    What would you like to name the project? lhci-poc
    Where is the project's code hosted? https://github.com/gajdaw/lhci-poc
    What branch is considered the repo's trunk or main branch? main

    Created project lhci-poc (83f850b5-2bbf-4184-8671-a6eb78273155)!
    Use build token 4e372fc5-85b5-4b1d-977b-77ccbefd46bb to add data.
    Use admin token Ah3S4ec5srCk7aljUh5BrRUinrf8vrtl13HAClgH to manage data. KEEP THIS SECRET!

## 4. Run LHCI to create data

    cd run
    lhci collect --url=http://localhost:8080
    lhci collect --staticDistDir=./../static-content

## 5. Run LHCI 

    lhci upload  --token=4e372fc5-85b5-4b1d-977b-77ccbefd46bb --serverBaseUrl=http://localhost:9001

## 6. Destroy

    docker-clear-containers.sh
    docker-clear-volumes.sh
