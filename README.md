# Run Microservice On Docker Locally
Running microservices and web on Docker Locally :star_struck:

-----

- We will be practically implementing [Build your first microservice with .NET](https://learn.microsoft.com/en-us/training/paths/create-microservices-with-dotnet/)
- We will be using our [Indepth-microservices code template](https://github.com/vivekmvp/indepth-microservices) to begin with. :+1:

----

# High-level Architecture of Application

![image](https://user-images.githubusercontent.com/30829678/192071871-fdd7c8d2-2f9a-4262-a1cd-d32afe211ff1.png)

----

# Creating a Docker File

## Creating a Docker File for Frontend web

```
  FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
  WORKDIR /src
  COPY frontend.csproj .
  RUN dotnet restore
  COPY . .
  RUN dotnet publish -c release -o /app

  FROM mcr.microsoft.com/dotnet/aspnet:6.0
  WORKDIR /app
  EXPOSE 80
  EXPOSE 443
  COPY --from=build /app .
  ENTRYPOINT ["dotnet", "frontend.dll"]
```



## Creating a Docker File for Backend Api

And similarly add Docker file code for Backend api

----

# Build and Run the Docker Image locally

## Build Docker Image

Go to Backend code directory and build the docker image.

```
docker build -t onlinestorebackend .
```

![image](https://user-images.githubusercontent.com/30829678/192160212-4ac722a6-852f-4d6f-8454-4e7e60ff4368.png)


And similarly for Frondend


```
docker build -t onlinestorefrontend .
```

![image](https://user-images.githubusercontent.com/30829678/192160277-dcd08a32-9d1f-4123-9ce1-f230becae11f.png)


You can verify that image was build successfully in Docker Desktop locally



