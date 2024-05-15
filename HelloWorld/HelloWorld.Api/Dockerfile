FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /build

COPY . ./

RUN dotnet restore
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=build /build/out .

EXPOSE 8080
ENTRYPOINT ["dotnet", "HelloWorld.Api.dll"]