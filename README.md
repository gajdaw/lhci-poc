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

    Created project lhci-poc (72825ba9-9576-4fb7-ad5f-ef06578e25b2)!
    Use build token ad4ddd4a-be8d-441e-ac5e-ca9741b3339b to add data.
    Use admin token h1TnomIwI8xV2q5KQiVmfaO97tbc6gdfhV4eDgHm to manage data. KEEP THIS SECRET!

## 4. Run LHCI to create data

    cd run
    lhci collect --url=http://localhost:8080

## 5. Run LHCI 

    lhci upload  --token=ad4ddd4a-be8d-441e-ac5e-ca9741b3339b --serverBaseUrl=http://localhost:9001

## 6. Destroy

    docker-clear-containers.sh
    docker-clear-volumes.sh
