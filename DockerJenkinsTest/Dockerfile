FROM mcr.microsoft.com/dotnet/core/sdk:6.0 AS base
WORKDIR /app

COPY *.csproj .

RUN dotnet restore

COPY . ./

RUN dotnet publish --no-restore -c Realse -o out

FROM mcr.microsoft.com/dotnet/sdk:6.0
WORKDIR /app
COPY --from=base /app/out .
ENTRYPOINT ["dotnet", "DockerJenkinsTest.dll"]