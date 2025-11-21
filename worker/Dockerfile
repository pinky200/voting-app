# Build
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src

COPY Worker.csproj .
RUN dotnet restore Worker.csproj

COPY . .
RUN dotnet publish Worker.csproj -c Release -o /app

# Runtime
FROM mcr.microsoft.com/dotnet/runtime:7.0
WORKDIR /app
COPY --from=build /app .

CMD ["dotnet", "Worker.dll"]

