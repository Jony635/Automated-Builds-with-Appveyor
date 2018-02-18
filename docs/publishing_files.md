### ZIP Files + Github Releases

---

To achieve publishing a Github Release through Appveyor, we have to learn some new concepts.
First of all, Environments. They are the sites where you are going to publish the files to.
<br> 
#### 1. Go [HERE](https://ci.appveyor.com/environments) and add a new one.
#### 2. Select your provider. In our case, Github Releases.
#### 3. Choose a name for the Environment, in order to you can understand easily which repository are you sending the files in.
#### 4. Add your environment.
<br>
Now your new environment will appear in the environment tag. After clicking on it, you will see 2 tags: Deployments and Settings.
We will come back to deployment later, this is the way we publish files. But we have to configure the environment first, so click on Settings.<br><br>

![Environment Settings](https://github.com/Jony635/Automated-Builds-with-Appveyor/blob/master/docs/images/environmentsettings.png?raw=true)

Same as projects, feel free to explore this tag and configure your settings the way you like more.
**Tags name** and **Release name** will be the version and the title of your release in github when each build is published.
The most important field is **GitHub authentication token**, we need this in order to Appveyor can access to our repositories.
To obtain one, go to [GitHub](https://github.com/) and click on your account at the top-right of your screen. Go to Settings->Developer_Settings->Personal_Access_Tokens->Generate_new_token. Select the repo checkboxes and generate a token. 
This is what you have to set in **GitHub authentication token** field.

###### *(If you are using Appveyor with a GitHub Organization, go [HERE](https://jony635.github.io/Automated-Builds-with-Appveyor/organizations))* <br> <br>

![Github Settings](https://github.com/Jony635/Automated-Builds-with-Appveyor/blob/master/docs/images/githubsettings.png?raw=true)<br> <br>

![Token](https://github.com/Jony635/Automated-Builds-with-Appveyor/blob/master/docs/images/token.png?raw=true)<br> <br>

![Token Example](https://github.com/Jony635/Automated-Builds-with-Appveyor/blob/master/docs/images/tokenexample.png?raw=true)<br> <br>

Now we can publish files as Releases, but how can we build a Zip with all the necessary files if they are on Appveyor server?
That is what we are going to learn now. <br> <br>


### [Appveyor.yml](https://www.appveyor.com/docs/appveyor-yml/) 
is a file that has to be in the root of our repository and contains all instructions Appveyor will do before, during or after the build process. Obtain it from YourProject=>Settings=>Export YAML, and this will contain all the settings you have established.
You can become really crazy with this feature, which has a lot of utilities you can made use.
Here I will show you how to build a zip file from multiple files in different locations of Appveyor server.

In your Appveyorproject->Settings->Environment->CloneDirectory field will be detailed the address where Appveyor will clone and build your project. By default it is c:\projects\nameofyourproject. You can access to that address by %APPVEYOR_BUILD_FOLDER% Appveyor variable. <br> <br>

Below I show you an example of the script I use to create the zip file with my example project:
```
after_build:
- 7z a SpikeFromAppveyor.zip "%APPVEYOR_BUILD_FOLDER%\Spike Project\Debug\Spike_FlanStudio.exe"
- 7z a SpikeFromAppveyor.zip "%APPVEYOR_BUILD_FOLDER%\Spike Project\Resources"
- 7z a SpikeFromAppveyor.zip "%APPVEYOR_BUILD_FOLDER%\Spike Project\*.dll"
- 7z a SpikeFromAppveyor.zip "%APPVEYOR_BUILD_FOLDER%\README.md"
```
after_build: It means all the commands written below with - will only execute after the build is completed.
7z a NameofZipArchive "Address" takes the files of this address (\*.dll means all dll files), which can be an unic file or even a full folder, and creates a zip file with it. If a file with the same name exists, 7z upgrade it adding the new files.

After executing the script above, we will have an SpikeFromAppveyor.zip in %APPVEYOR_BUILD_FOLDER% (the root of the build) with all the .dll, the Resources folder, the executable and the README file. Now we have to declare this zip an *Artifact*, which is the way Appveyor has to declare files as *Deployable*. To do that, use the following syntax:
```
artifacts:
  - path: SpikeFromAppveyor.zip 
```
After this step, we have all the neccesary stuff to publish Releases.

### How to publish manually a new Release from last Build
From Appveyor, go to Environments=>TheEnvironmentYouCreatedBefore. Click on it, select the new deployment option, your desired project and the build you want to publish. After clicking on deploy all artifacts of this build will be published on GitHub as a new Release.
