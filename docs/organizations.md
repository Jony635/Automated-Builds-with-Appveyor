### Appveyor for GitHub Organizations <br>

***Important: You need to have a Personal Access Token registered in your GitHub Account before following these steps. 
If you do not have one, go [HERE](https://jony635.github.io/Automated-Builds-with-Appveyor/publishing_files) and come back later***

You will need to grant aditional permissions from GitHub in order to Appveyor can access your organization commits and releases.

#### 1. Go to **Settings** from GitHub (Remember, click on your account icon, select Settings)
#### 2. Select **Applications** tag
#### 3. Select **Authorized OAuth Apps** tag

There you will see two Appveyor applications: Appveyor and Appveyor CI. Click on **Appveyor** and at the bottom of the page you will see all the organizations you are a member of. 
At the right of each organization you will see one of two options: Grant Access, if you are an owner in this organization, or Request access. In the first case clicking it will grant access immediately, and all repositories in this organization will be able to be added as projects in Appveyor. Otherwise, this organization owners will receive an email asking for permissions. 
<br> <br>

![Organizations](https://github.com/Jony635/Automated-Builds-with-Appveyor/blob/master/docs/images/organizations.png?raw=true)

