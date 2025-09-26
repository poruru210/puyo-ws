# syntax=docker/dockerfile:1
ARG NODE_VERSION=20
FROM node:${NODE_VERSION}-bookworm

# AWS CLI v2（公式zip方式）
RUN apt-get update && apt-get install -y unzip curl less groff jq python3 && rm -rf /var/lib/apt/lists/* \
 && curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "/tmp/awscliv2.zip" \
 && unzip /tmp/awscliv2.zip -d /tmp \
 && /tmp/aws/install \
 && rm -rf /tmp/aws /tmp/awscliv2.zip

# root のままグローバルnpmを入れる（EACCES回避）
RUN npm i -g aws-cdk http-server

# 作業ユーザー
USER node
WORKDIR /workspaces/puyo-ws
