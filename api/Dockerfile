# Build Stage
FROM microsoft/aspnetcore-build:2 as build-env

WORKDIR /api
COPY *.csproj .
RUN dotnet restore
COPY . .
RUN dotnet publish -c Release -o /publish

# Runtime Image Stage
FROM microsoft/aspnetcore:2 as runtime-env
COPY --from=build-env /publish . 
WORKDIR /publish
ENTRYPOINT ["dotnet", "/api.dll"]