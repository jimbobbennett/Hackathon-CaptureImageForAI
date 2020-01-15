# Hackathon - Capture Image For AI

This repo provides a template for a Python/Flask app that streams images from the users webcam to a video player on an HTML page. Then when the use clicks a button, it will capture the image and POST it to a route in the Flask app.

## To use this repo

* Select the **Use this template** button at the top of the page. This will create a new GitHub repo in your account using the code from here as the basic template.
* Clone the new repo
* Open it in [Visual Studio Code](https://code.visualstudio.com/?WT.mc_id=hackathoncaptureimageforai-github-jabenn). You will need the [Python extension](https://marketplace.visualstudio.com/itemdetails?itemName=ms-python.python&WT.mc_id=hackathoncaptureimageforai-github-jabenn) installed in Visual Studio Code.
* Open the terminal and install the pip packages from the `requirements.txt` file:

  ```sh
  pip3 install requirements.txt
  ```

## Running the app

THe app will contain configuration to allow you to debug it as a Flask app from inside Visual Studio Code.

## The structure of the code

* `app.py` - this file contains the Flask app. It has two routes:
  * `/` - this loads the `home.html` template, passing in an empty dictionary of data
  * `/process_image` - this receives the image as a JSON document containing the image as Base64 encoded data.

## Adding AI capabilities

This is a great starter project for capturing an image ready to run through AI services such as face recognition or an image classifier. To add AI capabilities:

* If you don't already have an Azure account, you will need to create one:

  * Students can sign up at [aka.ms/FreeStudentAzure](https://azure.microsoft.com/free/students/?WT.mc_id=hackathoncaptureimageforai-github-jabenn) using a valid higher education email address. You won't need a credit card and will get US$100 to use for 12 months, as well as 12 months of free services. After 12 months if you are still a student you can renew for another 12 months and get another $100 and free services, and so on each year you are still a student.

  * If you are not a student you can sign up at [aka.ms/FreeAz](https://azure.microsoft.com/free/?WT.mc_id=hackathoncaptureimageforai-github-jabenn). You will need a credit card to verify you are not a bot (you won't be charged anything), and wil get US$200 for 30 days, as well as 12 months of free services.

* Browse the vision based Cognitive Services on the [product page](https://azure.microsoft.com/services/cognitive-services/?WT.mc_id=hackathoncaptureimageforai-github-jabenn) and select the service you want.

* Create a resource for the service that you want. For a lot of these services you can create a single **Cognitive Services** resource and use that key for multiple services.

* Add a file called `.env` to the app to store application keys. Add key/value pairs for the endpoint and API key

* Add the relevant Python package to the `requirements.txt` file for the service you want to use, and install the packages from this file

* Add code to the `/process_image` route, replacing this comment inside the function:

  ```python
  ##############################################
  #                                            #
  # Add your AI call here                      #
  #                                            #
  ##############################################
  ```

  The code you add here should create the Cognitive Services client using the keys stored in the `.env` file, accessed as environment variables.

You can see an example of a similar app that uses the Face API to identify emotions and create a game in [this GitHub repo](https://github.com/jimbobbennett/HappySadAngryWorkshop).

## Deploying to Azure

Once your app is complete, you can deploy it to an [Azure App Service](https://azure.microsoft.com/services/app-service/?WT.mc_id=hackathoncaptureimageforai-github-jabenn). There is an [Azure App Service extension for Visual Studio Code](https://marketplace.visualstudio.com/itemdetails?itemName=ms-azuretools.vscode-azureappservice&WT.mc_id=hackathoncaptureimageforai-github-jabenn) that you can use to allow you to deploy from inside Visual Studio Code.

> Deploying apps from VS Code is not recommended for production apps, but is great for development or a hackathon

* Open the command palette:
  * On Windows, press Ctrl+Shift+P
  * On MacOS, press Cmd+Shift+P

* Select *Azure App Service: Deploy to Web App...*
  
  ![The command palette showing the Azure App Service: Deploy to Web App option](https://raw.githubusercontent.com/jimbobbennett/HappySadAngryWorkshop/master/images/CommandPaletteDeployAppService.png)

* You will be asked what code you want to deploy. This option will automatically select the folder with your code in it, so select that.

  ![The command palette showing the deployment source option](https://raw.githubusercontent.com/jimbobbennett/HappySadAngryWorkshop/master/images/SelectDeployFolder.png)

* If you have never signed into Azure from Visual Studio Code before, you will be asked to sign in.
  * Select *Sign in to Azure...*
  * Your browser will be launched, and you can sign in with your Azure account.
  * Once signed in from the browser, you can close the web page that was launched.

* Select the Azure subscription you want to use.
  
  ![The command palette showing the select subscription option](https://raw.githubusercontent.com/jimbobbennett/HappySadAngryWorkshop/master/images/SelectDeploySubscription.png)

* Select *+ Create New Web App*

  There are 2 *Create New Web App* options, one marked as *Advanced*. You want the normal one, **not** the *Advanced* one.

  ![The command palette showing the create web app option](https://raw.githubusercontent.com/jimbobbennett/HappySadAngryWorkshop/master/images/CreateNewWebApp.png)

* Give your web app a name. This will be part of the public web site address, so needs to be unique across the world. For example, I might use `jimspythonwebapp2019`.

  ![The command palette showing the new web app name option](https://raw.githubusercontent.com/jimbobbennett/HappySadAngryWorkshop/master/images/SelectWebAppName.png)

* Select the runtime for your App Service App. This is a Python app, so select the latest version of the Python runtime, such as *Python 3.7*

  ![The command palette showing the select runtime option](https://raw.githubusercontent.com/jimbobbennett/HappySadAngryWorkshop/master/images/SelectPythonRuntime.png)

* The App Service will start being created. You will see a progress bar on the bottom right, and this will show you once it is complete. You can monitor the progress from the *Output* window by selecting *View -> Output* and selecting *Azure App Service* from the window selector..

  ![The create app service progress bar](https://raw.githubusercontent.com/jimbobbennett/HappySadAngryWorkshop/master/images/CreateWebAppProgress.png)

* Some popups wil appear asking if you want to make configuration changes to speed up deployment and always deploy this web app. Select **Yes** for both.
  
  ![The update workspace configuration dialog](https://raw.githubusercontent.com/jimbobbennett/HappySadAngryWorkshop/master/images/UpdateWorkspaceConfigDialog.png)
  
  ![The always deploy to the web app configuration dialog](https://raw.githubusercontent.com/jimbobbennett/HappySadAngryWorkshop/master/images/AlwaysDeployDialog.png)

* A popup will appear showing the deployment progress. You can monitor the progress from the *Output* window by selecting *View -> Output* and selecting *Azure App Service* from the window selector.
  
  ![The deploy progress dialog](https://raw.githubusercontent.com/jimbobbennett/HappySadAngryWorkshop/master/images/DeployProgress.png)

* Once the code has been deployed, you will be able to view the code over the internet. Launch your browser and open your web site. The address will be `https://<web app name>.azurewebsites.net/`. For example, for my web site this is `https://jimspythonwebapp2019.azurewebsites.net/`.

> These steps will create a Free tier App Service and deploy your app to it. You can only have one Free tier per subscription, so if you have already got a free app service running, use the *Create New Wep App Advanced* option, and create using a paid tier.
