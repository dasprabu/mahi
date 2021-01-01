FROM mcr.microsoft.com/dotnet/sdk:5.0.101

RUN apt-get update && \
    apt-get install -y procps

RUN groupadd -g 1001 -r mahi && \
    useradd -u 1001 -r -g mahi -m -s $(which bash) mahi

# Create working directory. Ownership will be changed in entrypoint.sh which
# executes *after* the volume has been mounted.
RUN mkdir /app
# Copy entrypoint script into container, make it executable, then execute it:
COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]
