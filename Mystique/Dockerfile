FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build-env
WORKDIR /app

COPY Mystique ./Mystique/

WORKDIR /app/Mystique
RUN dotnet restore

RUN dotnet publish -c Release -o out

# ����Docker����
FROM mcr.microsoft.com/dotnet/core/runtime:3.1
WORKDIR /app/Mystique
COPY --from=build-env /app/Mystique/out .
ENV ASPNETCORE_URLS http://0.0.0.0:5000
ENTRYPOINT ["dotnet", "Mystqiue.dll"]