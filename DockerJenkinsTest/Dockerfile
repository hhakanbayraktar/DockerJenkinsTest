FROM mcr.microsoft.com/dotnet/sdk:6.0 AS base
WORKDIR /app
EXPOSE 7000

COPY *.csproj .

RUN dotnet restore

COPY . ./

RUN dotnet publish --no-restore -c Realse -o out

FROM mcr.microsoft.com/dotnet/sdk:6.0
WORKDIR /app
COPY --from=base /app/out .
ENV ASPNETCORE_URLS http://*:7000
ENTRYPOINT ["dotnet", "DockerJenkinsTest.dll"]