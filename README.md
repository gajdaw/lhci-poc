# Lighthouse CI / POC


## 1. In a nutshell

- start the server
- run the wizard
- work in main branch: create a web page, analyze it and upload data to server

Steps for one iteration (i.e. one run of LHCI for a webpage):

1. Create first web page `index-0.html` in `static-content/`
2. Commit the page in main branch
3. Analyze the page with:

```
lhci collect --staticDistDir=./../static-content
```

4. Upload results:

```
lhci upload  --token=0b1971cd-f533-49b0-a47d-aa5141ba6fc1 --serverBaseUrl=http://localhost:9001

```

Repeat the above steps for: `index-0.html`, `index-1.html`, `index-2.html`, etc.


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
    lhci collect --staticDistDir=./../static-content

## 5. Run LHCI to upload data

    lhci upload  --token=0b1971cd-f533-49b0-a47d-aa5141ba6fc1 --serverBaseUrl=http://localhost:9001

## 6. Destroy

    docker-clear-containers.sh
    docker-clear-volumes.sh

## 7. How to use served website?

Start:

    cd nginx
    docker-compose up -d

Test:

    http http://localhost:8080


Run analysis:

    lhci collect --url=http://localhost:8080

