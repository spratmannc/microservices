FROM microsoft/dotnet:2.1-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 54030
EXPOSE 44304

# copy to /src directory
FROM microsoft/dotnet:2.1-sdk AS build
WORKDIR /src
COPY . .

# build and publish to /app directory
RUN dotnet publish "DockApi.csproj" -c Release -o /app

# copy from /app directory in build to /app directory
FROM base AS final
WORKDIR /app
COPY --from=build /app .
ENTRYPOINT ["dotnet", "DockApi.dll"]