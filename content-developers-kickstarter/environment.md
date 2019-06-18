# Environment

  
We highly recommend to use a UNIX-based operation system like **Linux** or **MacOS**. Ubuntu 18.04.01 is preferred the most.

There is an **install script** written in bash \(`install-apps-gui.sh`\) to install all the applications and tools needed for developing, furthermore some others that makes your work easier: you can set the keyboard input layout, generate and set an SSH key for your GitHub account, set your favorites, etc. This script was tested in Ubuntu 18.04.

The must-have tools you will need: **bash, Git, Docker, yarn, Angular CLI, GNU coreutils**.

Remember, in UNIX there is a way to define aliases. For this, you have to open as root the ~/.bashrc and define them. See my favorite aliases:

`alias buildonly="python3 ~/Desktop/tools/challenge-toolbox-master/build.py ."   
alias startonly="python3 ~/Desktop/tools/challenge-toolbox-master/start.py ."   
alias aliases="sudo gedit ~/.bashrc"   
alias cpnode="sudo cp -R ~/Desktop/tools /frontend-tutorial-framework/node_modules ."   
alias hack="./hack/tfw.sh start"  
alias getin="docker exec -it $(docker ps | grep 8888 | head -c 12) /bin/bash"   
alias getintocontroller="docker exec -it $(docker ps | grep opt | head -c 12) /bin/bash"  
alias godmode="sudo chmod 777 ./* -R"  
function buildandstart(){   
    python3 ~/Desktop/tools/challenge-toolbox-master/build.py .   
    python3 ~/Desktop/tools/challenge-toolbox-master/start.py .   
}`

After the installation you can use this script to set up a development environment:

`bash -c "$(curl -fsSL https://git.io/vxBfj)"`

Note that your SSH public key must be added to your GitHub user for this to work, or you must select HTTPS remotes when prompted.

This will set up a dev environment based on [test-tutorial-framework](https://github.com/avatao-content/test-tutorial-framework) just for you:

-  it builds the latest release of the framework Docker baseimage locally  
-  it pins solvable/Dockerfile to use this image  
-  it includes the latest frontend in solvable/frontend with dependencies installed

By default your IDE will fail to autocomplete code and will complain about missing dependencies. To fix this you should install the tfw pip package in your dev virtualenv:

`pip install git+ssh://git@github.com/avatao-content/baseimage-tutorial-framework.git (SSH) pip install git+https://github.com/avatao-content/baseimage-tutorial-framework.git (HTTPS`

