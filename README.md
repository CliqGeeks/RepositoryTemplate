# RepositoryTemplate 📔
This is the Template Repository in which the Github Action can perform well on cloning itself

Users can easily utilise the CliqInformer :speech_balloon: by cloning the repository using the commands
```
git clone https://<GITHUB PERSONAL ACCESS TOKEN>@github.com/CliqGeeks/RepositoryTemplate
```

## Generating Personal Access Token 🗝️
The **Personal Access Token** can be created 
  - from the Tokens Section of Settings at https://github.com/settings/tokens
  - or Click Profile -> Settings -> Developer Settings -> Personal Access Tokens -> Tokens (classic)

and Click on Generate new Token and select the Expiration Period and Select the Scope Required.

Since we will be pushing Code to the Repository, A Scope 🛡️ of **public_repo** is required for public repositories and **repo** is required for all (private and public) repositories

Once Cloned , you are all ready to utilise the Github Action of CliqGeeks 💬 .

## Custom Event Messages ⚙️

We have added few custom messages you can try with by removing the comment which is as simple as removing the **hash (#)**

Suppose if you need a Notification in Cliq 💬 for only selected Events or Actions, 
  - you may change the **_on_** key of the YAML File where the Action is called.
  - or additionally you can set all the required messages and declare the input '__*set-message-if-none*__' as **false** to avoid messages from events that you don't want messages from

You provide default messages to all kind of actions that triggers a Workflow.

The Messages can be customized to your own message using the inputs _'**event**-message'_ where event is the Event for which you would like to customize the message.

For e,g. : To set a Custom Message for a Pull Request Event, you must define the input as
```yaml
  pull-request-message: 'A Pull Request has been Opened'
```

## Default Message 📓

If you wish to add a Single Custom Message for all Kind of Events, then you may use the '**default-message**' which would set the message to all kind of events.
For e.g. : To set a Default Custom Message , you must define the _default-message_ as
```yaml
  default-message: 'A (event) has been (action)'
```

## Shortcuts ⏩

We also provide several shortcuts ⏩ to obtain the Variables that you want to insert in the Message such as
  - **(event)** : which will be replaced with the Event that the Workflow is triggered by
  - **(action)** : whiich will be replaced by the Action the Event is performing with
  - **(me)** : which will be replaced with the Github User who is performing the Action.
  - **(repo)** : which will be replaced by the Repository where the Github Action is Performed
  - **(ref)** : which will be replaced by the Branch/Tag where the Github Action is Performed
  - **(workflow)** : which will be replaced by the Workflow on which the Github Action is Performed
  - **(rule)** : which will be replaced by the Branch Protection Rule (if the Event is Branch Protection Rule)
  - **(run)** : which will be replaced by the Check Run (if the Event is Check Run)
  - **(branch)** : which will be replaced by the Branch/Tag which is Created/Deleted (if the Event is Create / Delete)
  - **(deployment)** : which will be replaced by the Deployment (if the Event is Deployment or Deployment Status)
  - **(discussion)** : which will be replaced by the Discussion which is worked on
  - **(category)** : which will be replaced by the Category Name to which the Discussion is changed to 
  - **(issue)** : which will be replaced by the Issue (if the Event is Issue or Issue Comment)
  - **(label)** : which will be replaced by the Label that is being worked on or being added to
  - **(milestone)** : which will be replaced by the Milestone that is being worked on or being added to
  - **(assignee)** : which will be replaced by the User Assigned to the Issue or Pull Request
  - **(pull)** : which will be replaced by the Pull Request that is worked on
  - **(package)** : which will be replaced the Registry Package that is worked on
  - **(release)** : which will be replaced by the Release that is worked on
  - **(status)** : which will be replaced by the Status of the Event (if the Event is Deployment Status or Status)

## Github Secret for Channel Endpoint 🔗
You must add a Github Secrets which contains the Channel Endpoint in the format in the Name of ENDPOINT
```
<Cliq Channel Endpoint>?zapikey=<Cliq Webhook Token>
```

You must create a Github Secret for providing the Channel Endpoint 🔗 by
  - Go to the Repository where the CliqInformer 💬 is to be added and go to '**Settings**' Tab
  - Select '**Secrets and variables**' and Click on **Actions** in the Dropdown.
  - Click on '**New repository secret**' and Enter the Name as '**ENDPOINT**' and Enter the Cliq 💬 Channel Endpoint 🔗 as the Secret (in above mentioned format)

## Base YAML Code 🗒

But don't worry 😉 you don't need to remember that much, Here is the minimal code required to start with 🗒️
```yaml
name : Communicating with Cliq

on:
  #you may add the events you like to get notified
  push:
    
jobs:
  test_name:
    runs-on: ubuntu-latest
    steps:
      - uses: CliqGeeks/CliqInformer@v1
        with:
          channel-endpoint: ${{ secrets.ENDPOINT }}
```

That's all, you will start getting notified for each event occuring in Github through the Github Action. You may view the Actions Tab of the Repository to view the Status of Message.
