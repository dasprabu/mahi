FROM mcr.microsoft.com/dotnet/core/sdk:3.1

RUN useradd -m -s $(which bash) mahi

RUN mkdir /app && chown mahi:mahi /app

USER mahi
