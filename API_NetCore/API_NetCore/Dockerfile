# Rest of your Dockerfile instructions...
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build

# Set the working directory inside the container
WORKDIR /app

# Copy the project files to the container
COPY . .

# Restore the project dependencies
RUN dotnet restore

# Build the project
RUN dotnet publish -c Release -o out

# Use a smaller base image for runtime
FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS runtime

# Set the working directory inside the container
WORKDIR /app

# Copy the published output from the build stage to the runtime stage
COPY --from=build /app/out .

# Expose the port that the application listens on
EXPOSE 80

# Start the application
CMD ["dotnet", "API_NetCore.dll"]
