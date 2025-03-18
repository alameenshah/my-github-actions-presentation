# https://hub.docker.com/_/microsoft-dotnet
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /source
EXPOSE 80
EXPOSE 443

# copy everything else and build app
COPY . ./
RUN dotnet publish -c Release -o /app my-web-app.csproj

# final stage/image
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=build /app ./
ENTRYPOINT ["dotnet", "my-web-app.dll"]