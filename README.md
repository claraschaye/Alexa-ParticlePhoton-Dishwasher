# Alexa-ParticlePhoton-Dishwasher

Creating a Lambda Function

Go to https://console.aws.amazon.com/lambda
Click “Functions”
Click “Create a Lambda function”
Select blueprint
Select runtime “Node.js 6.10” (This means we are coding in the most recent version of JavaScript, if a newer version is available select that option)
Click “Blank function”
Configure triggers
Click the dashed line box
Select “Alexa Skills Kit” (this allows us to create a ‘Skill’)
Click Next
Configure function
Give function a name, for example “Particle”
Select code entry type “Upload a .ZIP file”
Upload the .zip file created using the steps dictated in “Creating a .zip file for your Lambda Function”
Leave Handler as “index.handler” (index refers to the code, somewhere in the code it should say exports.handler)
Select Role “Create new role from template(s)’
Give role a name, for example “SimplePermission”
Select policy template “Simple Microservice permissions”
Click Next
Review
 Click “Create function”

Creating an Alexa Skill
Log in to https://developer.amazon.com
Click “Alexa” tab
Click “Get Started” under Alexa Skills Kit
Click “Add a new skill”
Skill Information
Select Skill Type “Custom Interaction Model” (building a custom skill)
Give skill a name, for example “Particle”
Give skill an invocation name, for example “particle” (this is what you would say to Alexa to activate the skill)
For information on naming and invoking custom skills go to https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/choosing-the-invocation-name-for-an-alexa-skill#invocation-name-requirements
Click “No” next to Audio Player
Click “Save”
Click “Interaction Model”
Interaction Model
Under Intent Schema copy and paste “Intent_Schema” located  in UIUC_IoT → Alexa_Skill
Do not enter anything under Custom Slot Types
Under Sample Utterances copy and paste “Sample_Utterances” located  in UIUC_IoT → Alexa_Skill
Click “Save”
Click “Configuration”
Configuration
Select Service Endpoint Type “AWS Lambda ARN”
Select “North America”
Copy and paste the ARN for your Lambda function
Go to https://console.aws.amazon.com/lambda
Click “Functions”
Click on your function, for example “Particle”
Copy the ARN found in the upper right hand corner of the screen
Go back to your skill configuration and paste the ARN under where it says “North America”
Select “No” under account linking
Do not select anything under permissions
Click “Save”
Click “Publishing Information”
Publishing Information
Select Category “Smart Home”
Enter Testing Instructions, for example “turn on green/red light”
Enter a Short Skill Description, for example “turn on green/red light”
Enter a Full Skill Description, for example “turn on green/red light”
Enter Example Phrases, for example “Alexa, tell Particle to turn on red light”
Upload Small/Large Icon Images
Click “Save”
Click “Privacy & Compliance”
Privacy & Compliance
Select “No” for all questions under Privacy
Click the checkbox next to Export Compliance
Click “Save”
Click “Back to all skills”

Setting up Echo Dot
Go to http://echo.amazon.com/#skills
Click “Begin Setup”
Click “Echo Dot”
Select “English”
Follow the instructions given on the Alexa app and by your Echo Dot to set up Wifi
Select “No speakers”
Click “Next” until the screen says “All done!”
Click “Go to Home”

Setting up Photon Particle
The setup is shown in the diagram below

NOTE: Make sure the diodes are not reversed, the bent side should be connected to the resistor.
Plug the USB cable into your computer
Hold down the SETUP button on your device and it should start blinking blue
Go to setup.particle.io
Make an account
Click “Setup a photon”
Click “Next”
Click “Continue with Local File”
Open file that just downloaded called photosetup.html
Connect to wifi network “Photon-XXXX” on your computer
Enter your wifi information on the webpage
Reconnect to your wifi network on your computer
Click “Name your device”
Enter name, for example uiuc-particle

Uploading Firmware to Photon Particle
Go to https://build.particle.io/build
Click “Code” tab
Name app “alexa”
A tab at the top named alexa.ino should show up
Copy and paste code from the alexa.ino Sublime Text file located in UIUC_IoT → Particle_Firmware
Click plus button in the upper right hand corner
Two new tabs should show up, one .cpp file and one .h file
Name both of these files “DHT”
Copy and paste code from the DHT.cpp and DHT.h Sublime Text files located in UIUC_IoT → Particle_Firmware
Click “Save” located in the upper left hand corner
Click “Verify”  located in the upper left hand corner
Click “Flash” located in the upper left hand corner

NOTE: You must go through the setup again if connecting on a different wifi network. Photon particle can save up to 5 networks.

Changing the Code to work with your Devices
Go to your Particle Lambda function
Select “Edit code inline”
Locate the following three parts of code
var APP_ID = undefined
var deviceid = “<<deviceid>>”;
var accessToken = “<<accesstoken>>”;
Finding the Application ID (Alexa Skill)
Go to https://developer.amazon.com/edw/home.html#/skills
Click “View Skill ID” under the name of your skill
The Application ID should be displayed
Replace undefined in the code with your Application ID in quotation marks
Finding the Action Device ID (Photon Particle)
Go to https://build.particle.io
Click “Devices”
Click the arrow next to your device
The device ID should be displayed
Finding the access token (Photon Particle)
Go to https://build.particle.io
Click “Settings”
Access token should be displayed

Creating a .zip file for your Lambda Function
Downloading node modules
Go to command prompt
Create a folder called node_modules
Make node_modules your current directory using the cd command
Type npm install request
Creating a .zip file
Open 7zip
Navigate to the folder containing node_modules, index.js, and AlexaSkill.js and select all of the files in this folder
Click Add
Change the archive format to .zip
Click OK
A .zip folder should show up in the same folder as the other files
