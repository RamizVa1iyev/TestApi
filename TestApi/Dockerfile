FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build-env
WORKDIR /app

USER root

COPY *.csproj .

RUN dotnet restore

COPY . ./


RUN dotnet publish --no-restore -c Release -o out


FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "TestApi.dll"]