### Ali Cloud Deployment
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
docker login --username=siemensspa registry.cn-hangzhou.aliyuncs.com
docker tag a6f9992e6510 registry.cn-hangzhou.aliyuncs.com/spa1/spa-mf-test:1.0.0
docker push registry.cn-hangzhou.aliyuncs.com/spa1/spa-mf-test:1.0.0
```
* * *
### Commands
```
docker image list
```
