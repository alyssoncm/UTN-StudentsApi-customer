FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src

COPY UTN-StudentsApi/Students.Api/Students.Api.csproj .
RUN dotnet restore

COPY . .
WORKDIR "/src/Students.Api"
RUN dotnet build -c Release -o /app/build

FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS final
WORKDIR /app
COPY --from=build /app/build .

ENV ASPNETCORE_URLS=http://+:5099
ENV ASPNETCORE_ENVIRONMENT=Development

ENTRYPOINT ["dotnet", "Students.Api.dll"]
