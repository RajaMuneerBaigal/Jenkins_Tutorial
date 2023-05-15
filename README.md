## This is my first tutorial of Jenkins


### What is jenkins?
  - Jenkins is an automation platform that allows us to build, test and deploy softwares using pipelines. Jenkins provide a web gui where we can create jobs and customize functionality such as source control management pre and post build actions as well as build triggers.

### Jenkins Infrastructure
  - Jenkins infrastructure consists of two servers
     - Master Server  : control the pipeline and schedules builds to agents
     - Agents         : which runs the build in the workspace

  - Example workflow can be a developer commits a code to github the master server is aware of this commit and triggers the appropriate pipeline and distributes the build to one of the agents to run. It selects the appropriate agent based on labels which is configured by us using jenkins UI.
    The agent then runs the build which is usually a bunch of linux commands to build test and distribute the code.


### Types of Jenkins Agents:
   - Usually two types of jenkins agents:
      - Pernament Agents    :   standalone linux or window servers that are configured to run jenkins jobs. The only real setup includes java installed and ssh is setup as master server makes connections over ssh and build tools need to be installed on these servers
      - Cloud Agents        :   Dynamic agents spun up on demand examples include docker, kubernetes or aws fleet manager. Spun up dynamically depend on agent templates you configure.


### Build Types
   - Usually two types of popular Build Types
       - Freestyle build    
             -  simplest method to create a build 
             -  simply shell scripts will be run on a server that can be triggered by specific events 

       - Pipelines: 
             -  Uses the jenkins files written in the groovy syntax to specify what happends during the build. 
             -  Pipelins are usually broken into different stages .i.e clone, build, test, deply


### Jenkins UI
    - Jenkins UI has several components:
        - menubar 
              - A top bar with Jenkins title and a search button on the right to search on jenkins jobs, username and logout button
        - sidebar 
              - new item         :   its the way we create new item and jobs in jenkins.
              - people	         :   its where we manage user accounts
              - build history    :   gives us history of all our run jobs
              - manage jenkins   :   has all management stuff. this is where we will setup agents and install plugins.
              - myviews	         :   just a way to organize jobs and have things displayed nicely
              - open blue ocean  :   just enhaces our cicd pipelines
              - new views        :   just like myviews. We can create our own views for jenkins UI.




#### Build Triggers Section comes up with several options. 

   1. Trigger builds remotely                :     we can build jobs remotely from scripts using this option. it gives us a url with secret token which we can use by giving the jobname and secret token along with the url.  we can run the job by using curl command in the script with username and pass. i.e curl -u RajaMuneerBaigal:SecretToken jenkinsurl
   2. Build after other projects are built   :     this option is used when we want to run one job after other job is successfull or unsuccessfull. it comes with 4-5 options. build the second job after first job is successfull, unsuccessfull or unstable. we can unstable a project by giving an error code in shell script.
   3. Build periodically                     :     Build periodically means we can build a job every one hour, one minute or two minutes depending upon our need. 
   4. Poll SCM				     :     Poll SCM is used when we have a code on github/gitlab and pull scm looks for any changes in the github depending upon the cron job or time we have set.
   5. GitHub hook trigger for GITScm polling :     triggers job if it sees any change in the github repo without any time set like poll scm.
 

#### Build Environments section under freestyle project comes up with several options:

   1. Delete workspace before build starts :     by checking this option it will delete the workspace/folder which exists and then start working in the directory. i.e if we have a cloned a github repo and we have not removed the folder then on second build it will give us an error as the folder will already exsist there. so we need to remoe the folder first or we need to select this option.

#### Jenkins by default provides some environment variables which we can use in our job. But these variables have scope only under single job we cannot use the the same variable in another job. For that we can set global variables and use global variables across different jobs. To set the global variables we can go to configure jenkins and then configure system and under global properties we can see environment variables and set them 



