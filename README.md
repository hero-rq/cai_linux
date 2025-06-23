
cai linux within all kali linux attack tools

## A. Enable WSL & Virtual Machine Platform

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

dism.exe /online /enable-feature /featurename:VirtualMachinePlatform           /all /norestart

wsl --set-default-version 2
````

## B. Install Kali Linux

```powershell
wsl --install -d kali-linux
wsl -d kali-linux
sudo passwd root
exit
```

## C. Prepare Kali Environment

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y git python3 python3-venv python3-pip build-essential
```

## D. Restore Kali Signing Keyring

```bash
sudo apt update
sudo apt install -y kali-archive-keyring
sudo apt update
wget -qO- https://archive.kali.org/archive-key.asc | sudo apt-key add -
sudo apt update
```

## E. Switch to the Rolling Repository

```bash
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
sudo sed -i 's|kali-last-snapshot|kali-rolling|g' /etc/apt/sources.list
sudo apt update
```

## F. Install CAI Prerequisites

```bash
sudo apt install -y python3-venv python3-pip git pipx
pipx ensurepath
```

## G. Install CAI via pipx

```bash
pipx install cai-framework
```

## H. Clone CAI Repo & Setup `.env`

```bash
cd ~
git clone https://github.com/aliasrobotics/cai.git
cd cai
cp .env.example .env
```

## I. Persist PATH & OpenAI Key

```bash
echo 'export PATH="$HOME/.local/bin:$PATH"'      >> ~/.bashrc
echo 'export OPENAI_API_KEY="sk-<your-openai-key>"' >> ~/.bashrc
source ~/.bashrc
```

## J. Smoke Test CAI

```bash
which cai
cai --help
cai agents list
```

## K. Install Kali Tooling

```bash
sudo apt update
sudo apt install -y \
  nmap masscan \
  gobuster ffuf dirb \
  nikto sqlmap \
  hydra medusa john \
  enum4linux smbclient smbmap ldapsearch cifer \
  dnsenum amass \
  seclists \
  metasploit-framework
```

## L. Verify Installed Tools

```bash
which nmap gobuster ffuf nikto hydra sqlmap amass
```

and 

```bash
   cd ~/cai
   ```

```bash
  cai
 ```
