# Hackathon - Capture Image For AI

This repo provides a template for a Python/Flask app that streams images from teh users webcam to a video player on an HTML page. Then when the use clicks a button, it will capture the image and POST it to a route in the Flask app.

## To use this repo

* Select the **Use this template** button at the top of the page. This will create a new GitHub repo in your account using the code from here as the basic template.
* Clone the new repo
* Open it in [Visual Studio Code](https://code.visualstudio.com/?WT.mc_id=hackathoncaptureimageforai-github-jabenn)
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
  #
  # Add your AI call here
  #
  #
  ##############################################
  ```

  The code you add here should create the Cognitive Services client using the keys stored in the `.env` file, accessed as environment variables.

You can see an example of a similar app that uses the Face API to identify emotions and create a game in [this GitHub repo](https://github.com/jimbobbennett/HappySadAngryWorkshop).
