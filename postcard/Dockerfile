FROM mcr.microsoft.com/dotnet/sdk:7.0 AS hackathon_postcard
WORKDIR /postcard

# Copy everything
COPY . ./
# Restore as distinct layers
RUN dotnet restore
# Build and publish a release
RUN dotnet publish -c Release -o out

# Build runtime image
FROM mcr.microsoft.com/dotnet/aspnet:7.0
WORKDIR /postcard
COPY --from=build-env /postcard/out .
ENTRYPOINT ["postcard", "postcard.dll"]