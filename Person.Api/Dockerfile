FROM mcr.microsoft.com/dotnet/sdk:6.0 AS base
WORKDIR /app

COPY Person.Api.csproj ./
RUN dotnet restore

COPY . ./
RUN dotnet publish "Person.Api.csproj" -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /app
EXPOSE 80
COPY --from=base /app/publish .

ENTRYPOINT ["dotnet", "Person.Api.dll"]

