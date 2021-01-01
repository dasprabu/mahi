FROM mcr.microsoft.com/dotnet/sdk:5.0.101

RUN apt-get update && \
    apt-get install -y procps

RUN useradd -m -s $(which bash) mahi

RUN mkdir /app && chown mahi:mahi /app

USER mahi
