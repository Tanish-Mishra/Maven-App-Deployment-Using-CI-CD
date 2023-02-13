<h1 align="center">Maven Webapp Deployment Using Continuous Integration and Continuous Deployment Infrastructure</h1>
<br/>
<table width="100%" align="center" style=" border-collapse: collapse;">
  <trstyle=" border-collapse: collapse;">
    <th style=" border-collapse: collapse;">
        <a href="https://github.com/">
            <img src="https://github.githubassets.com/images/modules/logos_page/Octocat.png" height="60px" width="90px" alt="Github" />         
        </a>
    </th>  
    <th> 
        <a href="https://www.jenkins.io/">
            <img src="https://www.jenkins.io/images/logos/cute/cute.png" height="60px" width="90px"  alt="Jenkins" />       
        </a>
    </th>
    <th>
        <a href="https://www.ansible.com/">
            <img src="https://logos-download.com/wp-content/uploads/2016/10/Ansible_logo-700x700.png" height="60px" width="90px" alt="Ansible" />
        </a>
    </th>
    <th>
        <a href="https://www.docker.com/">
            <img src="https://www.clipartmax.com/png/full/146-1469802_logo-logo-docker.png" height="60px" width="90px"  alt="Docker" />
        </a>
    </th>
    <th>
        <a href="https://tomcat.apache.org/">
            <img src="https://www.seekpng.com/png/full/640-6408917_apache-tomcat-logo-png-clipart-apache-tomcat-web.png" height="60px" width="90px"  alt="Tomcat" />
        </a>
    </th>
  </tr>
</table>

  <h3>👨‍💻Live Version</h3>

Check out the website: [Webapp Maven Application](http://44.206.13.42:8080/webapp/)
<ol>
  <li>Project Description
        <p>Hi 👋, This Project is about Maven Webapp Deployment by using the Continuous Integration and Continuous Deployment Infrastructure settled on the Jenkins Automation Server!.We are going to Build,Test and Deploy the Application on the Deployment Server which can be further modified by Anyone by forking the repository and make the changes to it then after raise the Pull Request which will be inspected to be merged after being merged(Steps Described Ahead in additon to do the changes to the Project) we will be able to see the Jenkins Job be triggered up by the github webhook In order to actually montior the Jenkins Job visit <a href = "http://18.234.209.199:8080"> Click Here </a> Login by Credentials given as follows -
    <div> 
      <b> Username - </b> <em> guest </em>
      <br>
      <b> Password - </b> <em> IamGuest </em>
 </div>
    1.Click on the Application Deployment Job 
    <br>
    <img src="/jobs/Job1.PNG" height="80px" width="100%">
    <p> <b> As the Job Completes It triggers the Continuous Deployment Job </b> </p>
    2.Click on the Continuous Deployment Job
    <img src="/jobs/Job2.PNG" height="80px" width="100%">
    <p> <b> Eventually,This Job Deploys the Application on the Tomcat Container Deployment Server </b> </p>
    <hr>
        This application consists of the following components:
        <ul>
        <li>A single-AWS-Linux-instance used as a Jenkins Automation Server to Build,Test and Deploy the Applicaion</li>
        <li>A single-AWS-Linux-instance used as a Ansible App Deployment Server</li>
        <li>A single-AWS-Linux-instance used as a Tomcat-Deployment Server where our Maven App will be Deployed</li>
        </ul>
        </p>  </li>

       An elastic IP is allocated to the Deployment Server and Jenkins Automation Server so NO Worries about the IP being changed even after the unfortunate restart or shutdown! Visit the address with ease which are provided at required places!
  <li>Tools and Technology
    <ul>
        <li><a href="https://www.jenkins.io/">Jenkins</a></li>
        <li><a href="https://www.docker.com/">Docker</a></li>
        <li><a href="https://www.ansible.com/">Ansible</a></li>
        <li><a href="https://maven.apache.org/">Maven</a></li>
        <li><a href="https://tomcat.apache.org/">Tomcat</a></li>
      <li><a href="https://aws.amazon.com/">Amazon Web Services(AWS)</a></li>
    </ul>
  </li>
  <li>Stages
    <ul>
        <li><p>The project includes three Stages for Maven Application Deployment. The modules are Building and Testing, shiping the artifact on Dockerhub and Deployment on Tomcat Docker Container on the Deployment Sever.</p>
        <ul>
            <li><b>Building the Artifact and Testing Automatically by Maven </b>
                <ul><p>First stage is about creation of Artifact and Testing Automatically by maven.Basically,Jenkins hold the charge and starts our Continuous Integration Process(know more about CI and CD here <a href="https://www.infoworld.com/article/3271126/ci-cd/what-is-cicd-continuous-integration-and-continuous-delivery-explained.html">Know more</a>) of building and Testing the application by Its plugin called Maven Integration Plugin which provides us the ease of Building the application and Testing it!</p>
                <li><b>Docker image Creation:</b><p>Again,Jenkins holds the charge and by using the plugin called publish over ssh the webapp artifact is sent to the ansible server where it is built as a Docker image by using the Dockerfile and the meaningfull ansible playbook which is triggerd by the Publish over ssh plugin as the webapp artifact is Successfully Publish over the ssh to the ansible Application Deployment Server!</p></li>
                </ul>
            </li>
            <li><b>Shipping to the Dockerhub</b>
                <ul><p>Shipping is the process of pushing docker image to the repo where it is stored for the further use at any enviroment despite of the configuration mess.Here,Dockerhub is used as the service for the having the docker images</p>
                <li><b>Tagging and Pushing </b><p>By using the same Ansible Playbook responsible for the creation of the Docker Image further Modules does the tagging and Pushing to the DockerHub!</p></li>
                </ul>
            </li>
            <li><b>Deploying To The Tomcat Container on the Host Server</b>
                <ul><p>Deloyment is done via the Approach of the Continuous Deployment where no Human Intervention is Required to make the configurations Ready to deploy the Application our Automated Pipeline reduces human efforts at <b>massive</b> extent.</p>
                <li><b>Process of Deployment:  </b><p>Ansible Playbook lying on the Ansible Application Deployment Server is triggered by our Automation Server Jenkins and Ansible playbook starts the Process of Deploying the Application on The Tomcat Application Deployment Server by pulling the Application Image on the Deployment server and Creates the Container out of it with proper configuration and removes any older version of the image,removes any older running tomcat container with the older configuration and Deploys Fresh Application on the Server.Basically,If the Application does not exist on the Deployment server then the our playbook ignores the error caused by it and goes through the futher process defined.</p></li>
                </ul>
            </li>
        </ul>
        </li>
    </ul>
  </li>
</ol> 

## How to make changes to the Project (overall process)

1. Fork the project using the gray `Fork` button in the top right of this page.
2. Make any changes in your forked repository.
3. On this repo, click `Pull Requests` (which is the third option at the top of this page after the options `Code` and `Issues`) and raise a Pull Request by clicking the green `New Pull Request` button and selecting your fork from the right dropdown field.

You can ask questions by raising an [issue](https://github.com/Tanish-Mishra/Maven-App-Deployment-Using-CI-CD/issues/new).

## How to clone the repository and make changes locally

- Click on the green `Code` button, then either the HTTPS or SSH option and, click the icon to copy the URL. Now you have a copy of the project. Thus, you can play around with it locally on your computer.

- Run the following commands into a terminal window (Command Prompt, Powershell, Terminal, Bash, ZSH). Do this to download the forked copy of this repository to your computer.

```bash
  git clone https://github.com/Tanish-Mishra/Maven-App-Deployment-Using-CI-CD.git
```

- Switch to the cloned folder. You can paste this command into the same terminal window.

```bash
  cd Maven-App-Deployment-Using-CI-CD
```

- Make a new branch. Your username would make a good branch because it's unique.

```bash
  git checkout -b <name-of-new-branch>
```

- Open the `/webapp/src/main/webapp/index.jsp` file

- Do changes.
  `It can be a simple HTML element addition`

- Stage your changes.

```bash
  git add .
```

- Commit the changes.

```bash
  git commit -m "YOUR-NAME"
```

- Check the status of your repository.

```bash
  git status
```

- The response should be like this:

```bash
On branch <name-of-your-branch>
nothing to commit, working tree clean
```

- Pushing your repository to GitHub.

```bash
  git push origin <name-of-your-branch>
```

or

```bash
  git branch -M main
  git push -u origin main
```

If you get an error message like the one below, you probably forgot to fork the repository before cloning it. It is best to start over and fork the project repository first.

```bash
ERROR: Permission to Tanish-Mishra/Maven-App-Deployment-Using-CI-CD denied to <your-github-username>.
fatal: Could not read from remote repository.
Please make sure you have the correct access rights and the repository exists.
```

- On the GitHub website, navigate to your forked repo - on the top of the files section, you'll notice a new section containing a `Compare & Pull Request` button!

- Click on that button, this will load a new page, comparing the local branch in your forked repository against the main branch in the Tanish-Mishra Maven-App-Deployment-Using-CI-CD repository. Accept the default values in the dropdown boxes and click the green `Create Pull Request` button. After creating the PR (Pull Request).
  Note: A pull request allows us to merge your changes with the original project repo.

- Your pull request will be reviewed and then eventually merged.

Hurray! You successfully have made your Changes and also pushed them; Now you may,visit <a href="http://44.206.13.42:8080/webapp/">Click Here</a> to see your changes! 🎉
### NOTE: You will be Informed with a message that at what time your changes are going to be merged so that you can visit and see the Jenkins Job working in the Console Output ! Till then  Please Be Patient:) !

---



