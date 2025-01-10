# J.A.R.V.I.S System Overview
The full J.A.R.V.I.S. operating system, beta testing Mark 5. The full suystem is designed and tested to be ran on the WINDOWS 11 OS

JARVIS is one of the first fully integrated systems that can be spoken to and run locally or through an API, right before speaking it's response back to you and running the command given to it. Using OpenAI's Whisper model for the speech-to-text, either OpenAI's ChatGPT API or Ollama's Gemma2 model for local running, and either OpenAI's, elevenlabs, or microsoft's text-to-speech, there are many different ways to customize your experience. This os is designed to be fully run on any computer system, regardless of processing power(However more processing power always helps). 

FOLLOW THIS GUIDE CLOSELY. It will be a full walkthrough on exactly how the program is to be used.

## Features

There are many features of JARVIS installed, and if running locally, these features are sent to the model via the 
\caches and calls\System_call.txt 
text file. To learn in detail how each function works, reveiw that text file. 

CLICK HERE to watch a demonstration regarding every feature's abilities and how to use them effectively in my patreon.

A basic overveiw is also included below:

- Control Volume with hand gestures - Use OpenCV and media pipe technology to control the volume on a WINDOWS operating system, must have a webcam included for opencv to find. JARVIS function will still work if no camera is to be found

- full intent recognition - JARVIS can offer ideas and then follow up with commands based on what he believes to be the user's intentions

- GUI - A full graphical user interface to be able to interact JARVIS in a clean enviornment(terminals will run in the background as well for those who are interested)

- Muting - In order to make it so JARVIS is not always listening and responding, tell him to mute! If spotify is playing in the background, JARVIS has the capabilities to stop the playback while he is speaking. Once he mutes, the playback will continue as normal.

- Vision - JARVIS can use this function to see through the camera and answer any questions regarding what he sees

- Spotify - Has full spotify control, can play, pause, skip, previous, and tell you what song is playing. Song searching through JARVIS coming in future installments

- save text - can save text files in the "J.A.R.V.I.S log files" folder based on what you ask him to save

- google image search and text search - JARVIS can search google for specific images and can parse through websites to find specific data. This is a very effective function for research, as it allows you to parse through many websites in a very short time.

- DALLE3 generated images - JARVIS can also generate images through OpenAI's DALLE3. Be warned that DALLE3 is not good at text generation.

- analyze image files - JARVIS can take input image files (.png, .jpg tested and supported) and analyze them based on what the user is looking to analyze. PDF analyzation coming in future installments.

- IOS mode - Currently in the beta testing stages, JARVIS can use your phone provider and send free SMS messages through gmail. Any text sent back through IOS is sent to the gmail inbox, which is monitored by JARVIS. Any input from the IOS message will send it through gmail to JARVIS, where he can then parse the text and send it back to the user. THIS IS CURRENTLY IN BETA TESTING, DO NOT EXPECT PERFECT RESULTS. Regardless of testing, the sending of messages through IOS is perfectly encrypted through gmail, so data leaks are not a problem.

## Cost of Operation

The main purpose of this project was to keep the cost of operation as low as possible. Therefore, lots of different methods and options have been used in place of more expensive ones through my research. A few options that do still have costs are as follows:

- OpenAI chatGPT API - If you decide to use the ChatGPT API as your LLM model, Based on which API model you use, expenses can vary. The GPT-3.5 model, however, is incredibly inexpensive, and you can go through an entire conversation with JARVIS(around 500 words generated by the LLM) and only spend around 1 CENT.

- Local LLM through Ollama - This model is completely FREE to use, but does require a significant amount of processing power to run. In terms of processing power, the standard gemma2 model is best fit with a GPU of RTX 4060 to run effectively, but different models have different requirements. I have found through testing that the gemma2 standard model is the best overall, and will be the default for this project. But play around with different models on the ollama website, and see which one is best for you.

- text-to-speech options - There are 3 main ways to use the text-to-speech options. The first being the completely FREE option of microsoft's pyttsx3, which has two options, boy and girl, and are quite robotic. They are the default for this project, but support for elevenlabs and OpenAI's tts are available as well. Pricing varies based on useage, visit the websites for more info on pricing, linked here:

elevenlabs link
OpenAI tts link

- Vision, Analyze, Image generation - These functions are all ran through the OpenAI API, and have varying costs for the Vision and Analyze functions. For these the project uses GPT-4o, which upon using either function has an API cost of about 1 CENT per function call. The DALLE3 image generator has an API cost of about 4 CENTS per call. 

# Imports and Installs
There are many, many, many things to install, so let's get started. This setup process is only required once.

I have included a basic tutorial below, but for the full in-depth look on how to install all of these dependencies the correct way, while also getting a look on how to create the API keys and set up google cloud in order to effectively use all of the functions, head to my patreon here: CLICK HERE

1. Firstly, download all of the files into the directory you wish to use JARVIS in. Then open a terminal and run the following command:

pip install -r requirements.txt

This will install all of the imports needed to run JARVIS

2. Next, we need to input all of the API keys that will be used for the different functions. The API keys that are needed are as follows:

- OpenAI API key
- OpenAI assistants ID
- OpenAI thread ID
- Pvporcupine API key
- Serpapi google search API key
- Elevenlabs API(optional but for speech to text)

Take these API keys and place them in their respective variables in \Utilities\constants.py

3. Next, we need to input all of the credentials needed for the Spotify and IOS functions to work. All the spots to put the credentials are in "\Utilities\constants.py". For IOS authentication, you will need to input the following in their respective variables:

- phone number
- phone provider
- gmail you wish to send messages from and recieve to
- the password given to you by the sms messaging system to authenticate

For spotify autentication, you will need to input these credentials in their respective variables:

- username(not actual username, but the spotify given one)
- client Id
- client secret
- redirect_uri

4. After all this setup, we should be ready to run JARVIS! The last thing we need to do is make it so that JARVIS can run on startup of our computer.

- Head to task scheduler on the start menu of your windows machine.
- Create a new task.
- In the "Triggers" section, Allow the task to run on the "at startup", "on workstation unlock", "At log on", "on connection to user session". These can be changed based on your preferences
- In the "Actions" section, add a new action, that will "start a program"
- Find the path to your python executable file, and in this new action, paste the path into the "program/script".
- In the "Add arguments" section, put the executable file we want to run, in this case would be "Mark_5.py"
- In the "Start in" section, put the path to the directory that the executable file (i.e. Mark_5.py) is run in.
- Change any other settings based on your preferences, and save the new action.
- Repeat this process for the exectuable file "GUI.py"

5. Enjoy!! If there are any bugs or software issues, please leave a comment on the github or head to my patreon to get access to the tutorial videos on how to set up this program, as well as access to a discord community chat room: CLICK HERE

# User Customization
Thare are lots of different ways to customize your JARVIS bot, here are a few starters:

- Speech-to-text - have full control over what voice to give your JARVIS bot, weather it is OpenAI, elevenlabs, or microsoft.

- LLM model type - The user has access to the OpenAI API for talking through a wifi connection, or through an ollama model if you want to go offline

- Adding new functions - take the reigns and add your own functions to the bot. To add new functions, its as simple as adding a definition in the main executable that does the action, hook it up in the executable_functions definiton, and add a description in the \caches and calls\System_call.txt file!

# Drawbacks and Limitations(for now)
- Upon first startup the model has a slower response time -
- Whisper hallucenations -
- Beta testing of the IOS mode - 
- Memory does not pass through instances -
- analyze function can only accept (.png and .jpg) image files- 

# Future installments
- Analyze function accepts pdf format and .heic files
- MAC OS accessability
- IOS mode stability
- Much more!

# License
Etext functionalities provided by AlfredoSequeida (c) 2021

Distributed under the MIT license, see LICENSE for more information

# Contact
I am going to try my absolute very best to provide as much help to people as possible, but please understand that I am not always available to do so. There are many different ways to contact me:

- Instagram @ hacker.industries
- Github comments
- Discord community chat - available through patreon HERE.
