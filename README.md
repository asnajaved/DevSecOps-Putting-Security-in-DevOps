# DevSecOps-Putting-Security-in-DevOps

In this workshop you will learn how to create a toolchain on IBM Cloud using contineous delivery service and detect vulnerabilities in your code before pushing it to git repository. 

## Step 1: Create IBM Cloud account

Signup/Sign-in on IBM Cloud account

## Step 2: Create Toolchain

To create toolchain first Create contineous delivery service. Go to Catalog -> select services from left hand side -> scroll down -> click on contineous delivery service 

<img width="488" alt="1" src="https://media.github.ibm.com/user/246450/files/308d9c80-6578-11eb-895d-8f0ee6f2a67f">

<img width="606" alt="2" src="https://media.github.ibm.com/user/246450/files/2ff50600-6578-11eb-8ce4-ca636b70459b">


## Step 3: Clone git repository

After creating toolchain, clone your sample app in your local machine 

<img width="509" alt="3" src="https://media.github.ibm.com/user/246450/files/f45c3b00-657b-11eb-9e1e-ec3680947c13">

<img width="591" alt="4" src="https://media.github.ibm.com/user/246450/files/f4f4d180-657b-11eb-85a6-5606a5221ff8">

<img width="567" alt="5" src="https://media.github.ibm.com/user/246450/files/c0354a00-657c-11eb-9a08-b5611583310b">

     git clone <link of your repository>

To check all connections are working, modify the readme file and push it to your repository
    
     git commit -am "modified readme"
     git push 
    
## Step 4: Create Snyk account

To create snyk account to go https://snyk.io/

## Step 5: Connect Snyk with your repository 

     npm install
     npm install -g snyk

Authorize snyk

     snyk auth 

Run below commands for snyk setup

     snyk monitor (Snyk uses monitoring to regularly test your code and notify you when new vulnerabilities are introduced)
     snyk test (The snyk test command tests a local project for known vulnerabilities.)
     snyk wizard (this will create a .snyk file) (snyk wizard configures your policy file to update, auto patch and ignore vulnerabilities in npm & yarn projects.)

update your gitrepository 

     git add .snyk
     git commit -am "added .snyk"
     git push
    
 ## Step 6: Vulnerabilities test 
 
 Downgrade your express.js to 4.4.5 in package.json file to introduce vulnerabilities in your code.
 
 again run the below commands 
 
    npm install
    snyk test
 
 Now you can see how snyk monitors vulnerabilities.
 
 ## Step 7: Add SAST file in your toolchain 
 
 to test vulnerabilities in toolchain add SAST testing stage in your git repository 
 
<img width="421" alt="6" src="https://media.github.ibm.com/user/246450/files/579b9c80-657f-11eb-8d7d-6a5b33679739">

<img width="439" alt="7" src="https://media.github.ibm.com/user/246450/files/566a6f80-657f-11eb-9013-a84d951eabb4">

<img width="525" alt="9" src="https://user-images.githubusercontent.com/16270682/106631611-588bf880-6596-11eb-9cec-c7421e04488f.PNG">

now push the vulnerable code, you will notice SAST stage failed.

     git commit -am "modified package.json"
     git push

to wrap up, remove SAST stage, upgrade your express.js to latest version and push the changes. 
   




