# Azure Defender

## Container Registry

~~~ bash
az account show
prefix=cptcdcr
location=eastus
az group create -n $prefix -l $location
az acr create --sku Standard -g $prefix -l $location -n $prefix
az acr login --name $prefix
docker pull elastic/logstash:7.13.3 # Pull the image from docker hub
docker images 
docker tag elastic/logstash:7.13.3 ${prefix}.azurecr.io/logstash:7.13.3 # rename/tag
docker images
docker push ${prefix}.azurecr.io/logstash:7.13.3 # Push the image to our own Container registry
az acr repository list -n $prefix -g $prefix
~~~

## Misc

### github
~~~ bash
git init
git add *
gh repo create $prefix --public
git remote add origin https://github.com/cpinotossi/${prefix}.git
git commit -m"init"
git push origin main
~~~