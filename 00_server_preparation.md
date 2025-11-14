# login
gcloud auth login

# progetto
gcloud projects create $PROJECT_ID
gcloud config set project $PROJECT_ID
gcloud beta billing projects link $PROJECT_ID --billing-account=BILLING_ID

# API
gcloud services enable compute.googleapis.com

# regione + zona
gcloud config set compute/region europe-west8
gcloud config set compute/zone europe-west8-b

# VM
gcloud compute instances create ai-stack --machine-type=e2-standard-4 \
    --image-family=ubuntu-2204-lts \
    --image-project=ubuntu-os-cloud \
    --boot-disk-size=50GB \
    --tags=allow-ssh

# firewall
gcloud compute firewall-rules create allow-ssh \
    --allow tcp:22 --target-tags allow-ssh

# SSH
gcloud compute ssh ai-stack


Pacchetti di base nella VM
```
sudo apt update
sudo apt upgrade -y

sudo apt install -y \
  build-essential \
  git \
  python3-venv \
  python3-pip \
  ffmpeg \
  curl \
  unzip \
  htop
```

Crea una cartella “progetto” dove teneremo tutto:

```
mkdir -p ~/ai-stack/{services,src,data}
cd ~/ai-stack
```
