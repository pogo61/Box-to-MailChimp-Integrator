# Akana API HOOK
![Image of Akana] 
(https://www.akana.com/img/formerlyLOGO8.png) 
[Akana.com](http://akana.com)

## Box the MailChimp API Integrator
### About the API
- This API retreives the contents of a file on Box (this should be a CSV with the email address, first name, last name on each line) and then loads the lines as prospects into MailChimp. *note:* the email addresses must be real as MailChimp will send an invite to subscribe to the list to those addresses. Until the owners accept the invitations the details will not be added to the List. *also note:* that the list must be created via the MailChimp Web Interface. You cannot create a list via the API. 

### Pre-Reqs
- You must have installed and verified, via the HelloWorld integration, the Box API Hook. 
You must have installed and verified, via the HelloWorld integration, the MailChimp API Hook.

### Getting Started Instructions
#### Download and Import
- Download BoxtoMailChimpIntegrator.zip
- Download the migrations.properties file, and edit it to replace the <replace this with your key> text with the "Container Key" of the ND or ND cluster in your target PM.
    - the container key is found by going to the "Deatils Tab" of the ND cluster, or ND defined in the Policy Manager Console, then looking at the " Container Overview" tab on that page, and copying the "Container Key:" value. ![container key screenshot](https://github.com/pogo61/Google-Sheets-API-Integration/blob/master/Screen%20Shot%202015-03-18%20at%2011.24.45%20am.png "ND Container Key")
- Login to PolicyManager  example: http://localhost:9900
- Select the root "Registry" organisation and click on the "Import Package" from the Actions navigation window on the right side of the screen
  - click on button to browse for the BoxtoMailChimpIntegrator.zip archive file 
  - make sure select the migrations.properties file 
  - click Okay to start the importation of the hook.
- this will create a Box to MailChimp Integrator Organisation with the requisite artefacts needed to run the API.

#### Verify Import
- Expand the services folder in the Box to MailChimp Integrator you imported and find CBox_to_MailChimp_Integrator VS

#### Activate Anonymous Contract
- Expand the contracts folder in the Google Sheets API Hook you imported and find the "Anonymous" contract under the "Provided Contracts" folder
- click on the "Activate Contract" workflow activity in the righ-hand Activities portlet
- ensure that the status changes to "Workflow Is Completed"

#### Configure Security
- Nil.

#### Verify Connectivity
- Using ```curl -X POST -d '{"apikey": "7e4027a513ad1f8f66f770920cc7a537-us10","file": "mailchimp/mailchimp_test.csv","listname":"MailChimp Hook Integration"}' http://ec2-107-21-253-123.compute-1.amazonaws.com:9905/mailchimp_int/prospects --header "Content-Type:application/json" --header "boxAuthKey:702gbme46kw" --header "mailAuthKey:pznb4ygps5r" ```
-  the response should be similar to the below, listing of the first email, of the first folder, of the first email account found in your Context.io account:  
```{"add_count":0,"adds":[],"update_count":4,"updates":[{"email":"paul.pogonoski@akana.com","euid":"16cd1c3ef0","leid":"84881365"},{"email":"paul.pogonoski@akana.com","euid":"16cd1c3ef0","leid":"84881365"},{"email":"paulpog@japarasolutions.com","euid":"e0a5f08e1c","leid":"86095949"},{"email":"paulpog@mac.com","euid":"1fdc4c754a","leid":"86095953"}],"error_count":0,"errors":[]}```
  

### Modify and Build
In the event you need to change the API Hook.   Here are the instructions to do so. 

### License
Put a link to an open source license

