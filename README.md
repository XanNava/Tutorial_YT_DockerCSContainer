# YT_DockerCSContainer

Had to add a Publishing option named DefaultContainer, also had to disable AOT as it caused an error on publish
"Cross-OS native compilation is not supported."
https://github.com/dotnet/docs/issues/35445
https://learn.microsoft.com/en-us/dotnet/core/deploying/native-aot/?tabs=net7%2Cwindows

 cd C:\Users\Alexa\OneDrive\Documents\Projects\Personal\Learning\YT_DockerCSContainer\BackgroundDemo\BackgroundDemo

dotnet publish --os linux --arch x64 -p:PublishProfile=DefaultContainer -c Release
MSBuild version 17.8.3+195e7f5a3 for .NET
