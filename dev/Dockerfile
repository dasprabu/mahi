FROM mcr.microsoft.com/dotnet/sdk:5.0.101

RUN apt-get update && \
    apt-get install -y procps

RUN groupadd -g 1001 -r mahi && \
    useradd -u 1001 -r -g mahi -m -s $(which bash) mahi

RUN mkdir /app && chown mahi:mahi /app

USER mahi
