# Get Started with Azure AI Services

Credits: Skillabe Lab - Azure AI 102

## 1. Clone the repository in Visual Studio Code

You'll develop your code using Visual Studio Code. The code files for your app have been provided in a GitHub repo.

1. Start Visual Studio Code.

2. Open the palette (SHIFT+CTRL+P) and run a Git: Clone command to clone the https://github.com/MicrosoftLearning/mslearn-ai-services repository to a local folder (it doesn't matter which folder).

![image](https://github.com/moniquecardoso25/Azure-AI102/assets/140358716/15675c4f-452e-4b59-8da2-dfbc1e429c40)

3. When the repository has been cloned, open the folder in Visual Studio Code.

4. Wait while additional files are installed to support the C# code projects in the repo, if necessary

5. Expand the Labfiles/01-use-azure-ai-services folder.

![image](https://github.com/moniquecardoso25/Azure-AI102/assets/140358716/11321f12-7761-431f-b711-5e21586d6c08)

## 2. Provision an Azure AI Services 

Azure AI Services are cloud-based services that encapsulate artificial intelligence capabilities you can incorporate into your applications. You can provision individual Azure AI services resources for specific APIs (for example, Language or Vision), or you can provision a single Azure AI Services resource that provides access to multiple Azure AI services APIs through a single endpoint and key. In this case, you'll use a single Azure AI Services resource.

1. Open the Azure portal at https://portal.azure.com, and sign in using the Microsoft account associated with your Azure subscription.
   
2. In the top search bar, search for Azure AI services, select Azure AI Services, and create an Azure AI services multi-service account resource with the following settings:
- Subscription: Your Azure subscription
- Resource group: Choose or create a resource group (if you are using a restricted subscription, you may not have permission to create a new resource group - use the one provided)
- Region: Choose any available region
- Name: Enter a unique name
- Pricing tier: Standard S0
- 
![image](https://github.com/moniquecardoso25/Azure-AI102/assets/140358716/8cfb6ce8-3a96-4576-b50e-0a7f07e57926)
  
3. Select the required checkboxes and create the resource.
4. Wait for deployment to complete, and then view the deployment details.
5. Go to the resource and view its Keys and Endpoint page. This page contains the information that you will need to connect to your resource and use it from applications you develop. Specifically:
- An HTTP endpoint to which client applications can send requests.
- Two keys that can be used for authentication (client applications can use either key to authenticate).
- The location where the resource is hosted. This is required for requests to some (but not all) APIs.

![image](https://github.com/moniquecardoso25/Azure-AI102/assets/140358716/dfa8304d-4e81-4521-a79a-6f871e99f041)

## 3. Use a REST Interface

The Azure AI services APIs are REST-based, so you can consume them by submitting JSON requests over HTTP. In this example, you'll explore a console application that uses the Language REST API to perform language detection; but the basic principle is the same for all of the APIs supported by the Azure AI Services resource.

1. In Visual Studio Code, expand the C-Sharp or Python folder depending on your language preference.

2. View the contents of the rest-client folder, and note that it contains a file for configuration settings:

- C#: appsettings.json
- Python: .env
Open the configuration file and update the configuration values it contains to reflect the endpoint and an authentication key for your Azure AI services resource. Save your changes.

![image](https://github.com/moniquecardoso25/Azure-AI102/assets/140358716/18003d8c-4455-4cd9-9530-cad2973bb3e0)

3. Note that the rest-client folder contains a code file for the client application:

- C#: Program.cs
- Python: rest-client.py
Open the code file and review the code it contains, noting the following details:

Various namespaces are imported to enable HTTP communication
- Code in the Main function retrieves the endpoint and key for your Azure AI services resource - these will be used to send REST requests to the Text Analytics service.
- The program accepts user input, and uses the GetLanguage function to call the Text Analytics language detection REST API for your Azure AI services endpoint to detect the language of the text that was entered.
- The request sent to the API consists of a JSON object containing the input data - in this case, a collection of document objects, each of which has an id and text.
- The key for your service is included in the request header to authenticate your client application.
- The response from the service is a JSON object, which the client application can parse.
5. Right click on the rest-client folder, select Open in Integrated Terminal and run the following command:

![image](https://github.com/moniquecardoso25/Azure-AI102/assets/140358716/0ab0ced1-dd35-4737-b655-4c656d9f7f82)

Python

'''pip install python-dotenv
python rest-client.py'''

![image](https://github.com/moniquecardoso25/Azure-AI102/assets/140358716/19577466-77b4-4530-bc21-63ff1c7882c9)

![image](https://github.com/moniquecardoso25/Azure-AI102/assets/140358716/22be36e6-2ea0-49a3-bd0b-6879b3faa00c)

5. When prompted, enter some text and review the language that is detected by the service, which is returned in the JSON response. For example, try entering "Hello", "Bonjour", and "Gracias".

6. When you have finished testing the application, enter "quit" to stop the program.

![image](https://github.com/moniquecardoso25/Azure-AI102/assets/140358716/187ce90f-84c6-425d-9105-e4319588d049)



![image](https://github.com/moniquecardoso25/Azure-AI102/assets/140358716/e18611fb-710d-41fb-9bf4-e7a6c46ed132)

![image](https://github.com/moniquecardoso25/Azure-AI102/assets/140358716/d381b821-637a-46d4-a401-9002e95e121d)

![image](https://github.com/moniquecardoso25/Azure-AI102/assets/140358716/ad46ed3e-5424-414a-9325-1d89606ac477)

![image](https://github.com/moniquecardoso25/Azure-AI102/assets/140358716/93cbaf5d-777c-4a56-817a-d698e55dbc38)



## 4. Use an SDK
You can write code that consumes Azure AI services REST APIs directly, but there are software development kits (SDKs) for many popular programming languages, including Microsoft C#, Python, Java, and Node.js. Using an SDK can greatly simplify development of applications that consume Azure AI services.

1. In Visual Studio Code, expand the sdk-client folder under the C-Sharp or Python folder, depending on your language preference. Then run cd ../sdk-client to change into the relevant sdk-client folder.

2. Install the Text Analytics SDK package by running the appropriate command for your language preference:

'''pip install azure-ai-textanalytics==5.3.0'''

3. View the contents of the sdk-client folder, and note that it contains a file for configuration settings:

Python: .env
Open the configuration file and update the configuration values it contains to reflect the endpoint and an authentication key for your Azure AI services resource. Save your changes.
Note that the sdk-client folder contains a code file for the client application:

Python: sdk-client.py
Open the code file and review the code it contains, noting the following details:

- The namespace for the SDK you installed is imported
- Code in the Main function retrieves the endpoint and key for your Azure AI services resource - these will be used with the SDK to create a client for the Text Analytics service.
- The GetLanguage function uses the SDK to create a client for the service, and then uses the client to detect the language of the text that was entered.
4. Return to the terminal, ensure you are in the sdk-client folder, and enter the following command to run the program:

Python

'''python sdk-client.py'''

5. When prompted, enter some text and review the language that is detected by the service. For example, try entering "Goodbye", "Au revoir", and "Hasta la vista".

6. When you have finished testing the application, enter "quit" to stop the program.

Note: Some languages that require Unicode character sets may not be recognized in this simple console application.

![image](https://github.com/moniquecardoso25/Azure-AI102/assets/140358716/834db128-2268-4794-888f-5cdcce9751af)

![image](https://github.com/moniquecardoso25/Azure-AI102/assets/140358716/7bb22d1f-2e1d-4763-b646-1dd50810d651)

![image](https://github.com/moniquecardoso25/Azure-AI102/assets/140358716/902c45e0-229b-401b-b407-e190c76cb9d6)

