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

# Install dotnet-outdated (see
# https://github.com/dotnet-outdated/dotnet-outdated)
RUN runuser -l faker -c “dotnet tool install --global dotnet-outdated-tool”
# runuser installs it as if the non-root user was installing it.
# This makes it available to that non-root user
ENV PATH “$PATH:/home/faker/.dotnet/tools”
