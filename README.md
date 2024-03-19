# Tutorial_YT_DockerCSContainer
https://www.youtube.com/watch?v=bg0QVTS4Q0c

Had to add a Publishing option named DefaultContainer, also had to disable AOT as it caused an error on publish<br>
"Cross-OS native compilation is not supported."<br>
https://github.com/dotnet/docs/issues/35445<br>
https://learn.microsoft.com/en-us/dotnet/core/deploying/native-aot/?tabs=net7%2Cwindows<br>
```
cd C:\Users\Alexa\OneDrive\Documents\Projects\Personal\Learning\YT_DockerCSContainer\BackgroundDemo\BackgroundDemo<br>

dotnet publish --os linux --arch x64 -p:PublishProfile=DefaultContainer -c Release<br>
MSBuild version 17.8.3+195e7f5a3 for .NET<br>
```
Didn't push image to local registery for docker. So added Dockerfile.
```
# Use the official .NET SDK image as a build environment
FROM mcr.microsoft.com/dotnet/sdk:8.0.100 AS build-env

# Set the working directory in the container
WORKDIR /app

# Copy the project file and restore dependencies
COPY *.csproj ./
RUN dotnet restore

# Copy the remaining source code
COPY . ./

# Build the application
RUN dotnet publish -c Release -o out

# Build the runtime image
FROM mcr.microsoft.com/dotnet/runtime:8.0
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "BackgroundDemo.dll"]
```
and then built
```
docker build -t background-demo .
```
and then pushed the image
```
docker push background-demo
```
Got error
denied: requested access to the resource is denied

Instead I went to docker Desktop and found it under images.
Then in the image selected run.
