### 1. Ali Cloud Deployment
##### Install Core Images
```
docker pull mcr.microsoft.com/dotnet/aspnet:3.1
```
##### Create Dockerfile
```
FROM mcr.microsoft.com/dotnet/aspnet:3.1
WORKDIR /app
COPY ./publish .
EXPOSE 80
CMD ["dotnet", "DigitalFactoryWebApp.dll"]
```

##### Publish Solution to folder

##### Build App Image
```
docker build -t digitalfactory .
```
##### Push Image to Ali Cloud
```
//阿里云
docker login --username=siemensspa registry.cn-hangzhou.aliyuncs.com
docker tag a6f9992e6510 registry.cn-hangzhou.aliyuncs.com/spa1/spa-mf-test:1.0.0
docker push registry.cn-hangzhou.aliyuncs.com/spa1/spa-mf-test:1.0.0
```
```
//Azure
docker login spamftestmscontainer.azurecr.io
docker tag 3e58988d5ae4 spamftestmscontainer.azurecr.io/digitalfactory:1.0.1
docker push spamftestmscontainer.azurecr.io/digitalfactory:1.0.1
```
* * *
### 2. Commands
```
docker image ls
```
```
//run in the backend
docker container run -d --name web -p 8000:8080

//run iteractive way
docker container run -it --name test alpine sh
```
```
docker container stop web
docker container start web
```
```
docker container rm web
```
