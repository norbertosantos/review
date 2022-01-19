FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /source

COPY Review.sln .
COPY Review.Web/Review.Web.csproj ./Review.Web/Review.Web.csproj
RUN dotnet restore

COPY Review.Web/. ./Review.Web/
WORKDIR /source/Review.Web
RUN dotnet publish -c release -o /source/bin/Review.Web --no-restore

FROM mcr.microsoft.com/dotnet/aspnet:5.0
WORKDIR /app
COPY --from=build /source/bin/Review.Web ./
ENTRYPOINT ["dotnet", "Review.Web.dll" ]
