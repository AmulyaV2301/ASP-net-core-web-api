FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY WebApi1.csproj .
RUN dotnet restore "WebApi1.csproj"
COPY . .
RUN dotnet publish "WebApi1.csproj" -c Release -o /publish

FROM mcr.microsoft.com/dotnet/aspnet:6.0 as final
WORKDIR /app
COPY --from=build /publish .

ENTRYPOINT ["dotnet", "WebApi1.dll"]