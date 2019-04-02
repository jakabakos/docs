# Process of creating own challenges

### 1. Create a challenge on the Avatao platform

After logging in, click to **Dashboard** \(1.\) on the Avatao platform, then there will be a **Create a challenge** \(2.\) menu on the left \(if you can’t see this, please contact to us\). Here, all you have to do is to give the repository name \(3.\). If you would have a challenge with name „Integer overflow” in C\#, the repo name could be integer-overflow-csharp. Please use only lowercase characters and hyphens instead of spaces. The repo name of course should be associative with the name of the challenge. Your registered username and the date will be automaticall concatened to the repo’s name. 

![](../.gitbook/assets/kep%20%284%29.png)

### Creating a new branch

After all, you will be redirected to a page where you can find the URL of the created GitHub repository. Your next task is to create a new branch with name `staging` \(see the image on the right\). It is needed because you can’t write to the `master` branch due to security reasons. You have to clone this repo to your local:

```
$ git clone -b staging <repo-url.git>
```

![](../.gitbook/assets/kep%20%283%29.png)

### Choose an existing challenge

As your next step it is recommended to choose an existing challenge similar to your ideas \(for example the deploy mechanism in the event handler is mostly matching with your ideas\), rewrite the parts you need and change the related files.

### Implement the application itself

You should place this application to the `solvable/src/` or `solvable/src/webservice/` directory.

### Dream the scenario

Think about the scenario of the challenge: what and how to show the related \(security\) issue. This needs some routine, so if you are a newbie you can ask a more experinced colleague. Please solve as much challenge in the Avatao platform as many you can to get some XP!

### Modifying the necessary files

You will also have to rewrite the following files \(see details later\):

* `metadata/description.md`: the description of the challenge that will be seen in the platform. As you can see it is supported by Markdown markup language
* `metadata/summary.md`: one or two sentence for summarizing what the challenge is about
* `metadata/writeup.md`: you will need a writeup only in the attack challenges
* `config.yml`: contains the configuration of the challenge
* `solvable/Dockerfile`: contains the instructions for building the solvable challenge’s image
* `solvable/frontend/src/app/config.ts`: you can find the Angular frontend’s configs here
* `solvable/supervisor`: directory for the process manager. Each processes will be run with .conf extension here
* `solvable/sr`c: directory for the webservice and other application-related source files 
* `solvable/src/tfw_server.py`: the server app 
* `solvable/supervisor/tfw_server.conf`: to set up the server to run 
* `solvable/src/event_handler_main.py`: the event handler 
* `solvable/src/test_fsm.py`: a final state machine that describes the actions triggered at several states

### Upload your files

You can push your files to the remote repository during the development and - of course - after completing the challenge, too. For this, you can use the following commands:

`git add .   
git commit –m”<message>”   
git push origin staging`

If you want to see the challenge at the platform, you also have to ask for a merge `staging` branch to the `master` branch by clicking to „New pull request” on the GitHub repo. After it, the build of the project will be automatically start. If the challenge has built successfully and the merge is done, you will find it in the Avatao platform by searching. At this stage this can be seen by the Avatao staff only.   
Before uploading your challenge to the plarform it is recommended tor un the `check-format.py` in the `challenge-toolbox` repo. As a paramter you should add the local route of your repo.

![](../.gitbook/assets/kep%20%286%29.png)

