# Introduction📔

BlockAssist is an AI assistant that learns from its user’s actions in Minecraft. The assistant appears in-game with you, starting with only basic knowledge of the game’s commands. As you play, it learns how to assist you in building, learning directly from your actions. It shows an early demo of assistance learning - a new paradigm for aligning agents to human preferences across domains.


# <h1 align="center">👨🏻‍💻 Gensyn BlockAssist Guide 👨🏻‍💻 </h1>
![image](https://github.com/sarjil15/-BlockAssist-Guide-/blob/44a1002ca10e6527f9fee3210d8b7c4fc9823f00/image_2025-10-14_17-58-16.png)

## Device/System Requirements 💻

- Minimum RAM = 8GB
- 50-100 GB disk space
- Multi-core CPU
- Wont work in VPS (Cpu based) , GPU require

- Installation for Mac user: Follow https://docs.gensyn.ai/testnet/blockassist/getting-started They dont need to install VcXsrv: just install these dependencies and all the process is same to play the game. just your start command is diff:

# Pre-Requirements 🛠

Install dependencies
```
sudo apt-get update -y && sudo apt-get install -y make build-essential gcc libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev curl git unzip zip mesa-utils x11-apps x11-xserver-utils libxi6 libxrender1 libxtst6 libxrandr2 libglu1-mesa libopenal1
```

Install node.js
```
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash - && sudo apt update && sudo apt install -y nodejs
```

Version
```
node -v
```

## Install Game Ready Driver {IMPORTANT}

For nvidia:

- Go To: https://www.nvidia.com/Download/index.aspx
- Select your GPU, Window Version & Press Find
- Click on View & Download the GeForce Game Ready Driver
- After Dow, Open it & Do all the processes to Install it into Your Machine:
- Restart Your PC to make changes

## For AMD

- Go to the official AMD driver page: https://www.amd.com/en/support

- On that page, you can:

- Use the Auto-Detect and Install option (easiest).

- Or manually select your GPU by choosing:

- Graphics → Integrated Graphics (if it’s built into your CPU, e.g., Ryzen with Radeon Graphics)

- Then select your specific series (like Ryzen 5 5600U with Radeon Graphics).

- Download and install the latest driver.


## Install VcXsrv Windows X Server

- Download VcXsrv: https://sourceforge.net/projects/vcxsrv/
- Now open the XLaunch (VcXsrv) From Start icon:
- Check Multiple windows ✔️
- Check Start no client ✔️
- Check Disable access control ✔️
- Next & Finish: It gonna run on background
- ❗Whenever you are going to play the game, you need to open XLaunch everytime and do all the above process:

![image](https://github.com/sarjil15/-BlockAssist-Guide-/blob/44a1002ca10e6527f9fee3210d8b7c4fc9823f00/479251875-8f63ac81-b4eb-4b3b-9d80-3198a5928708.png)

## Set DISPLAY and Audio to ~/.bashrc
```
echo -e '\n# WSL2 VcXsrv display setup\nexport DISPLAY=$(ip route | grep -m1 default | awk '"'"'{print $3}'"'"'):0.0\nexport LIBGL_ALWAYS_INDIRECT=0\nexport LIBGL_DEBUG=verbose' >> ~/.bashrc
```

Reload ~/.bashrc
```
source ~/.bashrc
```

Test VcXsrv
```
xeyes
```
  - If a New Tab got pop-up with EYES, Than VcXsrv has set-up perfectly
  
![image](https://github.com/sarjil15/-BlockAssist-Guide-/blob/44a1002ca10e6527f9fee3210d8b7c4fc9823f00/479519827-3e48848c-73be-45a4-9602-130a1ac6614e.png)

## Get Hugging Face API token
1. Go To: https://huggingface.co & Sign Up with Mail
2. Verify Your Email
3. Generate a New Access Token
   - Click your profile icon (top right corner)
   - Select “Access Tokens” from the dropdown
   - Click “New token”
   - Name: something like “BlockAssist”
   - Role: choose Write
   - Click “Create”
4. Copy & Save the token immediately - you won’t be able to see it again
5. 📋 Lost it? Just delete the token and create a new one


## Clone & move to blockassist Repo:
```
git clone https://github.com/gensyn-ai/blockassist.git
cd blockassist
```
- Install Java 1.8.0_152
```
./setup.sh
```
- Install pyenv
```
curl -fsSL https://pyenv.run | bash
```

- Add pyenv to your shell
```
cat <<'EOF' >> ~/.bashrc

# Pyenv setup
export PYENV_ROOT="$HOME/.pyenv"
[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init - bash)"
eval "$(pyenv virtualenv-init -)"
EOF
```

- Reload
```
source ~/.bashrc
```

## Install Python 3.10, psutil & readchar
```
pyenv install 3.10
```
```
pip install psutil readchar rich
```

## Run BlockAssist 🚀
1. Move to modal-login Directory & install yarn packages
   - Why? To prevent future terminated error
```
cd ~/blockassist/modal-login
```
```
yarn install && yarn dev
```

2. Gensyn Testnet login
   - You will be prompted to log in through your browser:
```
http://localhost:3000
```
  - open & Login with your mail (Better to use old mail which u are running rl-swarm)

3. CTRL + C After the login & move to blockassist repo
```
cd ~/blockassist
```

4. Make sure XLaunch (VcXsrv) running in background
5. Start the BlockAssist
```
python run.py
```

6. Enter Huggingface Token
7. Play Minecraft
   - After login, two Minecraft windows will be pop-up (could take a while to open)
   - After that Press ENTER in your UBUNTU/WSL
   - Now go to first Minecraft window & Press Enter twice & move your player with wasd keys on keyboard
   
![image](https://github.com/sarjil15/-BlockAssist-Guide-/blob/44a1002ca10e6527f9fee3210d8b7c4fc9823f00/487757921-ff20d555-b499-4634-8045-6ce834217040%20(1).png)
8. How to play? 
- watch video: https://www.youtube.com/watch?v=bASaYW0n13w


Check logs:
   - If your node does not start & got terminated while starting then check logs in new tab & debug it:
```
tail -f blockassist/logs/malmo.log
```

<h1 align="center">FAQ❓</h1>

## 1️⃣ How to start next Day:


1. Move to blockassist directory
```
cd blockassist
```
2. Make sure XLaunch (VcXsrv) running in background
3. Run Script & Follow all the process which u did previously ✔️
```
python run.py
```

<h1 align="center">Grab Block Role 🦾</h1>

## 1. First of all your have to take SWARM Role: Follow https://github.com/sarjil15/Gensyn-Rl-Swarm_Guide
## 2. Go to `🐝@The Swarm` channel in DC
## 3. Type & send `/block-verify`
## 4. Now a Form will pop-up
![image](https://github.com/sarjil15/-BlockAssist-Guide-/blob/44a1002ca10e6527f9fee3210d8b7c4fc9823f00/481320540-f3f352e1-c191-4ed1-b4f3-d03e3d1d822b.png)
## 5. Enter your Huggingface Block model URL from your Profile
![image](https://github.com/sarjil15/-BlockAssist-Guide-/blob/44a1002ca10e6527f9fee3210d8b7c4fc9823f00/481320727-aa7b68e4-8dd2-4cbb-a878-ee13c7c25e6c.png)
## 6. Enter Huggingface URL FROM HERE
## DONE:✔️✔️✔️

<h1 align="center">📈 Upgrade to new release {v0.1.0}</h1>

We wont directly upgrade to v0.1.0 through git pull, instead we will remove the repo and will clone from scratch to optimized full changes

1. Remove blockassist & pyenv Repo
```
sudo rm -rf ~/blockassist
```
```
sudo rm -rf ~/.pyenv
```
2. Now follow all the process from Clone & move to blockassist Repo
Done✔️✔️


`Thank U! 👨🏻‍💻    IF YOU FACE ANY PROBLEM YOU CAN TAG ME IN GENSYN DISCORD: @sarjil`
