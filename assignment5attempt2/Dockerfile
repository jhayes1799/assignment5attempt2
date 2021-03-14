FROM mcr.microsoft.com/dotnet/core/aspnet:3.0-buster-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.0-buster AS build
WORKDIR /src
COPY ["assignment5attempt2/assignment5attempt2.csproj", "assignment5attempt2/"]
RUN dotnet restore "assignment5attempt2/assignment5attempt2.csproj"
COPY . .
WORKDIR "/src/assignment5attempt2"
RUN dotnet build "assignment5attempt2.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "assignment5attempt2.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "assignment5attempt2.dll"]