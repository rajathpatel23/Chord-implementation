# Chord_implementation
As part of the Advance Operating System 

### Prerequisites


```
Go language needs to be installed on your Windows or Linux OS
You can install go directly on Linux using following commands
sudo apt-get install golang

while on Windows system download the programming language executable from following link
https://golang.org/dl/
```

### Function Description

The Function below provide the description of their working in the program
```
func read_from_channels(Node_Pointer *map[int]Node, input_channel <-chan []byte, output_channel chan<- []byte, key int)
Description: This function provides interface between our main program and the commnand function which are present in form of json messages. This function also helps in starting and continuing our go routines
 ```
 ```
func node_commands(n_1 Node, input_channel <-chan []byte, output_channel chan<- []byte)
Description: The function node_commands has the switch case commands to perform different function for the nodes present in the Deployment
```
```
func (n_1 Node) join_chord_deployment(sponsor_node int, key int)
Description: The function helps in joining a new node to deployment with the help of the sponsor nodes
```
```
func (n_1 Node) build_finger_table(target_node int, response_node int)
Description: The function helps in building the finger table for the newly joined Nodes
```
```
func (n_1 Node) find_successor(target_node int, response_node int)
Description: The function helps in finding the successor of the given target node using the node n_1 and send the data back to the response node who has requested for it.
```
```
func (n_1 Node) closest_preceding_node(target_node int)
Description: The function helps in finding the closest predecessor in the finger table of the node n_1
```
```
func (n_1 Node) find_predecessor(target_node int)
Description: The function find predecessor helps in finding the predecessor of the target node using the node n_1
```
```
func (n_1 Node) notify(target_node int)
Description: The function notify helps in notifyon the target node about it own predecessor
```
```
func (n_1 Node) stabilize()
Description: The function stabilize helps in stabilizing the state of each whenever a new node enters the deployment or leaves the current deployment
```
```
func (n_1 Node) store_data(target_node int, Communication_holder Data)
Description: The function helps in storing the data in form of key value pair using the node n_1 in the target node
```
```
func (n_1 Node) retrieve_data(target_node int, Communication_holder Data)
Description: The function helps in retrieving the data from the target node using node n_1
```
```
func (n_1 Node) leave_deployment(target_node int, Communication_holder Data)
Description: The function helps in removing a node from the current chord deployment
```
```
func (n_1 Node) remove_data(target_node int, Communication_holder Data)
Description: Function removes the data from the target node using the node n_1
```

```
func (n_1 Node) fix_finger_table()
Description: The function helps in fixing the entries of the finger tables of the nodes whenever a new node enters the system Deployment
```
```
func run_stabilize()
Description: The function run through go routine enabled in the main and run the stabilize, fix_finger_table and notify functions for each active node in the system periodically
```

```
func sending_request(ex Exchange)
Description: The helps in forming a json message that is send to the command function to execute the required messages from the nodes
```
```
func sending_reply(message_to int, channel_key int)
Description: Function sending reply helps in sending the outcome of the action functions to the response Nodes, using the output channels
```
```
func send_node_data)(n_1 Node, channel_key int)
Description: The function helps in sending back the node data across the channels
```

### Testing the Program
Kindly enter the commands in the format below for testing and running the program,please do note the we have few commented code for testing in the program itself which might help you in testing the functions.

```
ex2 := Exchange{"find-ring-successor", 1, 1, 1, "EMPTY", Communication_holder, 0}
sending_request(ex2)
time.Sleep(1 * time.Second)
err := json.Unmarshal(<-output_channel[1], &node_data)
if err != nil {
	panic(err)
}
x := *node_data
fmt.Println("The successor of the node is:", x)
 
 
ex4 := Exchange{"join-ring", 8, 8, 1, "EMPTY", Communication_holder, 0}
sending_request(ex4)
time.Sleep(1 * time.Second)
ex5 := Exchange{"join-ring", 14, 14, 8, "EMPTY", Communication_holder, 0}
sending_request(ex5)
time.Sleep(1 * time.Second)
 
 
Communication_holder.Key_1 = 1
Communication_holder.Values = "Rajat"
ex8 := Exchange{"put-data", 21, 1, 21, "EMPTY", Communication_holder, 0}
sending_request(ex8)
time.Sleep(1 * time.Second)
Communication_holder.Key_1 = 1
ex9 := Exchange{"get-data", 21, 1, 21, "EMPTY", Communication_holder, 0}
sending_request(ex9)
time.Sleep(1 * time.Second)

 ```


## Authors

* **Rajat Patel**
* **Sowmya Rampatruni**
