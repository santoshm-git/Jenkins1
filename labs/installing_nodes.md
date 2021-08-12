### Enable JNLP port
1. Go to Manage Jenkin http://18.237.87.185:8080/manage
2. Select Configure Global Security
3. Under Agents, select Fixed and add 50000. Click Save

### Install agant using 'Launch agent by connecting it to the master'
1. Go to Jenkins dashboard http://18.237.87.185:8080/
2. click 'Build Executer Status''
3. Select New Node
4. Add Node Name as windows_node & Select Permanent Agent. Click OK
5. Add Description as This is Windows Node, Number of executors as 1, Remote root directory as C:\Jenkins, Labels as windows
6. Add Usage as Only build jobs with labels expression matching this node
7. Add Launch Method as Launch agent by connecting it to the master
8. Keep other options as Deafult. Click Save

### Once Completed one offline node is available under 'Build Executer Status'
1. select 'Windows Nodes' which is showing offline
2. Ensure Java is installed on the node
3. Access 'http://18.237.87.185:8080/jnlpJars/agent.jar' to download 'agent.jar' and place it in agent remote directory which is 'C:\Windows\'
4. Open CMD & Run cd c:\Jenkins
5. Copy command under Run from agent command line: and Runthe same from CMD

### Install agent using SSH Connection
1. Login to server and run 'sudo hostnamectl set-hostname jenkins_node, bash, sudo apt-get update -y && sudo apt-get install -y default-jre, & mkdir /home/ubuntu/jenkins
2. Select Build Executor Status on Jenkins Dashboard
3. Select New Node.
4. Add Node Name as Linux Node and select Permanent Node. Click OK
5. Add Description as This is Linux Node, Number of executors as 2, Remote root directory as /home/ubuntu/jenkins, Labels as linux
6. Add Launch Method as Launch agent via SSH
7. Under Launch Method. Add Host as your second machine public IP, select Credentials as ubuntu and Host Key Verification Strategy as No verifying verification strategy. Click Save'
