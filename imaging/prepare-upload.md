## Prepare Image For Upload
Preparing an image for upload involves creating a basic Windows installation, installing software on it, and customizing the look and feel of what will eventually be handed to your users. 
This topic has been vastly covered for many years by IT pros around the world and everybody has there own way of setting up their images, so it won't go into details.  This guide will provide some basic practices that are recommended for creating images with Theopenem.

### 1. Use Hyper-V
It is recommended to build your images by installing Windows in Hyper-V.  This isn't required, but makes keeping images up to date easier.  It also helps to fix issues with your image if something goes wrong by simply restoring to a checkpoint.
It is nice to be able to create a checkpoint before your final shutdown / upload to be able to go back and fix things if it doesn't deploy the way you hoped.

### 2. Use Audit Mode
When you first install Windows, before you go through the OOBE, you should press CTRL+SHIFT+F3.  This will skip the OOBE setup and take you directly to the desktop where you can install your software, run Windows Updates, and apply configuration changes.
It is recommended to make your image entirely from audit mode while never actually logging in as a user.

### 3. Use Sysprep
This should be obvious, yet many people still ask if Sysprep is required.  No it's not required, but definitely recommended.  You should be using Sysprep with an unattended answer file to through the OOBE automatically.  

### 4. Use Toec-ImagePrep
Toec Imageprep is a tool to make finalizing your image easier.  It is not required, but allows you to easily run your Sysprep workflow based on templates stored in Theopenem.  If you are installing Toec on your image before you upload, you must use Image Prep so 
that Toec will work properly after the image is deployed.  It should be the last thing you do before you upload the image.  More information about Toec Image Prep can be found in the next section.

