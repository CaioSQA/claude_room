# claude_room — workspace isolado do Claude (Debian 12)
# Ferramentas: git, gh, PowerShell 7, Python 3, Java 17 (headless), Node + Claude Code, Chromium (PDF)
FROM debian:12-slim

ARG PWSH_VERSION=7.4.6
ENV DEBIAN_FRONTEND=noninteractive LANG=C.UTF-8

RUN apt-get update && apt-get install -y --no-install-recommends \
      ca-certificates curl git gh openssh-client jq unzip less nano \
      python3 python3-pip python3-venv \
      openjdk-17-jdk-headless \
      nodejs npm \
      chromium fonts-liberation \
      libicu72 libssl3 \
    && rm -rf /var/lib/apt/lists/*

# PowerShell 7 (tarball oficial, versão fixa)
RUN curl -fsSL -o /tmp/pwsh.tgz \
      "https://github.com/PowerShell/PowerShell/releases/download/v${PWSH_VERSION}/powershell-${PWSH_VERSION}-linux-x64.tar.gz" \
    && mkdir -p /opt/microsoft/powershell/7 \
    && tar -xzf /tmp/pwsh.tgz -C /opt/microsoft/powershell/7 \
    && chmod +x /opt/microsoft/powershell/7/pwsh \
    && ln -s /opt/microsoft/powershell/7/pwsh /usr/local/bin/pwsh \
    && rm /tmp/pwsh.tgz

# Claude Code
RUN npm install -g @anthropic-ai/claude-code

# Usuário sem privilégios
RUN useradd -m -s /bin/bash claude
USER claude
WORKDIR /home/claude/claude_room
