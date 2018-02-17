### ZIP Files + Github Releases

---

To achieve publishing a Github Release through Appveyor, we have to learn some new concepts.
First of all, Environments. They are the sites where you are going to publish the files to.

#### 1. Go [HERE](https://ci.appveyor.com/environments) and add a new one.
#### 2. Select your provider. In our case, Github Releases.
#### 3. Choose a name for the Environment, in order to you can understand easily which repository are you sending the files in.
#### 4. Add your environment.

Now your new environment will appear in the environment tag. After clicking on it, you will see 2 tags: Deployments and Settings.
We will come back to deployment later, this is the way we publish files. But we have to configure the environment first, so click on Settings.

Same as projects, feel free to explore this tag and configure your settings the way you like more.
**Tags name** and **Release name** will be the version and the title of your release in github when each build is published.
The most important field is **GitHub authentication token**, we need this in order to Appveyor can access to our repositories.
To obtain one, go to [GitHub](https://github.com/) and click on your account at the top-right of your screen. Go to Settings->Developer_Settings->Personal_Access_Tokens->Generate_new_token. Select the repo checkboxes and generate a token. 
This is what you have to set in **GitHub authentication token** field.

![Github Settings](https://github.com/Jony635/Automated-Builds-with-Appveyor/blob/master/docs/images/githubsettings.png?raw=true)

![Token](https://github.com/Jony635/Automated-Builds-with-Appveyor/blob/master/docs/images/token.png?raw=true)

![Token Example](https://github.com/Jony635/Automated-Builds-with-Appveyor/blob/master/docs/images/tokenexample.png?raw=true)

![Environment Settings](https://github.com/Jony635/Automated-Builds-with-Appveyor/blob/master/docs/images/environmentsettings.png?raw=true)
