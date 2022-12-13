# UAS-Deep-RL-Landing
Using Deep Q-Network for UAS Autonomous Landing

## Setup
Requires a Linux machine. We use Ubuntu 20.04.
1. Use `ssh -Y test@161253.73.97`, when connecting, so that Unreal Engine 4 windows are forwarded through SSH.
2. Setup AirSim and Unreal Engine 4 by following [these instructions](https://microsoft.github.io/AirSim/build_linux). 
   1. Follow "Build Unreal Engine".
   2. Follow "Build AirSim". I had to remove `sudo apt-get update` from `./setup.sh` in AirSim because some GPG keys were'nt working on my computer.
   3. After that, the steps for "How to Use AirSim" are broken. (Was getting "Build would modify the following engine files" on AirSim plugin files. Tried [these](https://community.gamedev.tv/t/unable-to-run-bull-and-cow-game-on-linux-ubuntu/155138) [solutions](https://stackoverflow.com/questions/69829601/i-cannot-open-c-projects-in-linux-unrealengine-4-27))
3. Go to the [releases](https://github.com/microsoft/AirSim/releases) sections of AirSim and download the `Blocks.zip` for v1.8.1 - Linux.
4. Unzip it. And run the ./Blocks.sh
   ```
   unzip ~/Downloads/Blocks.zip
   cd ~/Downloads/LinuxBlocks1.8.1/LinuxNoEditor
   ./Blocks.sh
   ```
   UE4 will prompt the user to select either the car or multirotor simulation. Sometimes the buttons do not work, so to set it on start up, modify the `settings.json` file in `~/Documents/AirSim/settings.json` to include
   ```
   "SimMode": "Multirotor"
   ```
   To prompt the user, set `"SimMode": ""`. Additional settings can be found [here](https://microsoft.github.io/AirSim/settings/).
5. If that is not working. You might have to start UnrealEngine manually using the following.
   ```
   cd ~/UnrealEngine
   ./Engine/Binaries/Linux/UE4Editor
   ```
6. Once AirSim is running in UE4, you can connect a PythonClient. If AirSim is not running from the previous steps, you will see an error like
   ```
   WARNING:tornado.general:Connect error on fd 6: WSAECONNREFUSED
   ```
   I used the instructions for the [python API](https://microsoft.github.io/AirSim/apis/), but this is what I ran:
   ```
   cd ~/AirSim/PythonClient/multirotor
   python hello_drone.py
   ```
7. Make any code changes to `~/AirSim/PythonClient/multirotor/hello_drone.py`
   Images taken by the drone's camera will be save in `/tmp/airsim_drone`.
8. AirSim has [documentation](https://microsoft.github.io/AirSim/reinforcement_learning/) for running the multirotor with DQN training.


## Running
We can run the `hello_drone.py` script and take pictures. There are 2 steps.
Start AirSim environment in UE4
1. `ssh -Y test@161.253.73.97`
2. `cd ~/Downloads/LinuxBlocks1.8.1/LinuxNoEditor`
3. `./Blocks.sh`
4. A new window should pop up showing the drone
Run Client hello_drone.py script
1. Log into test using MobaXTerm VNC session
2. `cd ~/AirSim/PythonClient/multirotor`
3. `python hello_drone.py` 
Images get saved to `/tmp/airsim_drone`

