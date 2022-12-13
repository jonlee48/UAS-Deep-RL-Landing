# UAS-Deep-RL-Landing
Using Deep Q-Network for UAS Autonomous Landing

## Setup
Requires a Linux machine. We use Ubuntu 20.04.
1. Setup AirSim and Unreal Engine 4 by following [these instructions](https://microsoft.github.io/AirSim/build_linux).
2. Had to remove `sudo apt-get update` from `./setup.sh` in AirSim because some GPG keys were'nt working.
3. Use `ssh -Y test@161253.73.97`
4. ```
   cd ~/UnrealEngine
   ./Engine/Binaries/Linux/UE4Editor
   ```
6. Then setup a python environment using the [python API](https://microsoft.github.io/AirSim/apis/)

