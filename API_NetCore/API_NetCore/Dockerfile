# Rest of your Dockerfile instructions...
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build

# Set the working directory inside the container
WORKDIR /app

# Copy the project files to the container
COPY . .

# Restore the project dependencies
RUN dotnet restore


# Set the working directory inside the container
WORKDIR /app

# Copy the published output from the build stage to the runtime stage
COPY --from=build /app/out .

# Build the project
RUN dotnet build 

# Expose the port that the application listens on
EXPOSE 80

# Start the application
CMD ["dotnet", "API_NetCore.dll"]
