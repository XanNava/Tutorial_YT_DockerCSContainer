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