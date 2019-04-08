# Communication with TFW

![](../.gitbook/assets/kep%20%285%29.png)

Event handlers connect to the TFW server using **ZMQ**. They receive messages on their `SUB`\(scribe\) sockets, which are connected to the `PUB`\(lish\) socket of the server. Event handlers reply on their PUSH socket, then their messages are received on the `PULL` socket of the server. 

The TFW server is basically just a fancy proxy. It's behaviour is quite simple: it proxies every message received from the fontend to the event handlers and vice versa. 

The framework uses **JSON** messages internally and in exposed APIs as well. These messages must comply with some rules. Don't worry, we are not too fond of rules around these parts. 

The TFW message format:

`{   
  "key: " some identifier used for addressing ",  
  "data": {   
    . . .  
    JSON object carrying anything...   
  },  
  "trigger": "FSM action optioinal"  
}`

* The `key` field is used by TFW for addressing and every message must have one \(it can be an empty string though\) 
* The `data` object can contain anything you might want to send 
* The `trigger` key is an optional field that triggers an FSM action with that name from the current state \(whatever that might be\)

## TerminalEventHandler

#### Writing to the terminal

`{ 'key': 'shell', 'data': { 'command': 'write', 'value': 'curl http://www.trynerr.com' } }`

#### Writing to the console

`{ 'key': 'console', 'data': { 'command': 'write', 'content': message } }`

#### Changing between terminal and console

`{ 'key': 'dashboard', 'data': { 'command': 'terminalMenuItem', 'value': 'terminal'  } }`

#### Read terminal command history

`{ 'key': 'shell', 'data': { 'command': 'read', 'content': ..number.. } }`

## IdeEventHandler

#### Select a file in the IDE

`{ 'key': 'ide', 'data': { 'command': 'select', 'filename': 'change-js.sh' } }` 

#### Read the content of the currently selected file

`{ 'key': 'ide', 'data': { 'command': 'read' } }`

#### Switch to a new working directory using this message \(note that the directory must be in `allowed_directories`\)

`{ 'key': 'ide', 'data': { 'command': 'selectdir', 'directory': '/home/user/workdir2' } }`

#### Overwrite the content of the currently selected file

`{ 'key': 'ide', 'data': { 'command': write, 'content': 'string' } }`

#### Overwriting the current list of excluded file patterns

`{ "key": "ide", "data": { "command": "exclude", "exclude": ...array of strings... } }` 

## LogMonitoringEventHandler

#### Setting the tail length of logs \(the monitor will send back the last value characters of the log\)

`{ "key": "logmonitor", "data": { "command": "log_tail", "value": ...number... } }` 

#### Change which supervisor process is monitored use

`{ "key": "logmonitor", "data" : { "command": "process_name", "value": ...string... } } 4.` 

## ProcessManagingEventHandler

#### Starting, stopping and restarting supervisor processes can be done using similar messages \(where command is start, stop or restart\):

`{ "key": "processmanager", "data": { "command": ...string..., "process_name": ...string... } }` 

#### I.e to restart the webservice:

`{ 'key': 'processmanager', 'data': { 'command': 'restart', 'process_name': 'webservice'} }`

## FSMManagingEventHandler

#### Attempt executing a trigger on the FSM \(this will also generate an FSM update message\):

`{ "key": "fsm", "data" : { "command": "trigger", "value": ...string... } }` 

## OTHER

####  Changing layout at the frontend

`{ "key": "dashboard", "data": {"command": "layout", "value": "terminal-ide-horizontal"} }`

#### You can also hide and show the messages component

`{ "key": "dashboard", "data": { "command": "hideMessages", "value": ...boolean... } }`

