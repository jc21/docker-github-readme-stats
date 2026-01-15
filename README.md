# docker-github-readme-stats

This is a docker image that wraps the [github-readme-stats](https://github.com/anuraghazra/github-readme-stats)
project, for self hosting.

## Usage

Refer to the [official repo](https://github.com/anuraghazra/github-readme-stats?tab=readme-ov-file#available-environment-variables)
for env var usage and instructions on setting up your `PAT_1` personal github token.

```yml
services:
  github-readme-stats:
    container_name: github-readme-stats
    image: jc21/github-readme-stats:latest
    ports:
      - '9000:9000'
    environment:
      PAT_1: 'github_pat_11A....'
	  WHITELIST: 'jc21'
	  GIST_WHITELIST: ''
    restart: unless-stopped
```


## Building

```bash
./scripts/buildx --push -t jc21/github-readme-stats:latest
```
