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

    Created project lhci-poc (3854b376-392a-4507-8675-5d1567b03878)!
    Use build token 0b1971cd-f533-49b0-a47d-aa5141ba6fc1 to add data.
    Use admin token PmKEPJDWx5HYDl947pfTmAcPRSPoMmyBHXu1pRGa to manage data. KEEP THIS SECRET!

## 4. Run LHCI to create data

    cd run
    lhci collect --url=http://localhost:8080
    lhci collect --staticDistDir=./../static-content

## 5. Run LHCI 

    lhci upload  --token=0b1971cd-f533-49b0-a47d-aa5141ba6fc1 --serverBaseUrl=http://localhost:9001

## 6. Destroy

    docker-clear-containers.sh
    docker-clear-volumes.sh
