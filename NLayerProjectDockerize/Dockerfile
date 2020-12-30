FROM mcr.microsoft.com/dotnet/core/sdk:3.1 as build
WORKDIR /app
COPY ./NLayerData/*.csproj ./NLayerData/
COPY ./NLayerDataAccess/*.csproj ./NLayerDataAccess/
COPY ./NLayerService/*.csproj ./NLayerService/
COPY ./NLayerService/*.csproj ./NLayerService/
COPY ./NLayerWeb/*.csproj ./NLayerWeb/
COPY *.sln .
RUN dotnet restore
COPY . .
RUN dotnet publish ./NLayerWeb/*.csproj -o /publish/
FROM mcr.microsoft.com/dotnet/core/sdk:3.1
WORKDIR /app
COPY --from=build /publish .
ENV ASPNETCORE_URLS="http://*:5000"
ENTRYPOINT [ "dotnet","NLayerWeb.dll" ]