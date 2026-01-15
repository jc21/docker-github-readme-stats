FROM node:slim AS builder

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

RUN apt-get update && apt-get install -y wget unzip && apt-get clean
RUN mkdir -p /workspace
WORKDIR /workspace
RUN wget "https://github.com/anuraghazra/github-readme-stats/archive/refs/heads/master.zip" -O master.zip
RUN unzip master.zip
RUN rm -f master.zip
WORKDIR /workspace/github-readme-stats-master
RUN yarn install

#############
# Final Image
#############

FROM node:slim
LABEL maintainer="Jamie Curnow <jc@jc21.com>"

COPY --from=builder /workspace/github-readme-stats-master /app
WORKDIR /app
EXPOSE 9000

CMD ["node", "express.js"]

LABEL org.label-schema.schema-version="1.0" \
	org.label-schema.license="MIT" \
	org.label-schema.name="github-readme-stats" \
	org.label-schema.url="https://github.com/jc21/docker-github-readme-stats" \
	org.label-schema.vcs-url="https://github.com/jc21/docker-github-readme-stats.git" \
	org.label-schema.cmd="docker run --rm -ti jc21/github-readme-stats:latest"
