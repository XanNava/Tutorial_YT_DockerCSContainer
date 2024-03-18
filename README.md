# YT_DockerCSContainer
https://www.youtube.com/watch?v=bg0QVTS4Q0c

Had to add a Publishing option named DefaultContainer, also had to disable AOT as it caused an error on publish<br>
"Cross-OS native compilation is not supported."<br>
https://github.com/dotnet/docs/issues/35445<br>
https://learn.microsoft.com/en-us/dotnet/core/deploying/native-aot/?tabs=net7%2Cwindows<br>

 cd C:\Users\Alexa\OneDrive\Documents\Projects\Personal\Learning\YT_DockerCSContainer\BackgroundDemo\BackgroundDemo<br>

dotnet publish --os linux --arch x64 -p:PublishProfile=DefaultContainer -c Release<br>
MSBuild version 17.8.3+195e7f5a3 for .NET<br>
