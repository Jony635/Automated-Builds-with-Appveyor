### Manual Builds with Appveyor

---

#### 1. Sign in Appveyor and go [HERE](https://ci.appveyor.com/projects)
#### 2. Click on New Project
#### 3. Select the repository where you want to generate a new build and choose Add
#### 4. Now we have to configure your project before starting builds. Choose settings option
#### 5. In this page you can configure the project. Do it the way you like more, but here we are interested in the Environment tab. Click it.
#### 6. Select the right Build worker image. In my case I use Visual Studio 2017.
#### 7. Now you can compile virtually in Appveyor servers and check if your project has some errors.

---

![Environment](https://github.com/Jony635/Automated-Builds-with-Appveyor/blob/master/docs/images/environmentcircled.png?raw=true)
![Build Worker Image](https://github.com/Jony635/Automated-Builds-with-Appveyor/blob/master/docs/images/buildworkerimage2.png?raw=true)

---

After following those steps you will have all your project compiled in the Appveyor's servers. 

How can you build the .zip file and publish it on Github Releases? Go [HERE](https://jony635.github.io/Automated-Builds-with-Appveyor/publishing_files)
