#build stage
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src
# COPY *.csproj ./
COPY *.csproj ./
RUN dotnet restore
COPY . .
RUN dotnet publish -c release -o output

#final stage
FROM mcr.microsoft.com/dotnet/aspnet:7.0
WORKDIR /app
EXPOSE 80
COPY --from=build /src/output .
ENTRYPOINT ["dotnet", "WebApi.dll"]