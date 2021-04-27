#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS build-env
WORKDIR /app
EXPOSE 9001
EXPOSE 9000
#
#FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
#WORKDIR /src
COPY *.csproj .
#RUN dotnet restore "webapidemo/webapidemo.csproj"
RUN dotnet restore
COPY . ./
#WORKDIR "/src/webapidemo"
#RUN dotnet build "webapidemo.csproj" -c Release -o /app/build
#
#FROM build AS publish
#RUN dotnet publish "webapidemo.csproj" -c Release -o /app/publish
RUN dotnet publish --no-restore -c Release -o out
#
#FROM base AS final
WORKDIR /app
#COPY --from=publish /app/publish .
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "webapidemo.dll"]
