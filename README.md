# Redis Helm chart

## Usage

To install as a dependency chart, add the following to your `requirements.yaml`, or `Chart.yaml`:

```yaml
dependencies:
  - name: redis
    repository: https://favish.github.io/helm-redis
    version: 1.1.0
```

Update the `values.yaml` for configuration options.

```yaml
redis:
  image:
    repository: redis
    tag: "4-alpine"
  redisExporter:
    image:
      repository: "oliver006/redis_exporter"
      tag: "v0.14"
  metrics:
    enabled: false
  resources:
    requests:
      cpu: 100m
      memory: 1G
  args: ["--maxmemory 50mb", "--maxmemory-policy allkeys-lfu"]
```

NOTE: make sure to pair Redis image version with appropriate Redis metrics export version. Visit https://github.com/oliver006/redis_exporter for more information.

By the way, if you want to use Redis 7, these images should fit:

```yaml
redis:
  image:
    repository: redis
    tag: "7-alpine"
  redisExporter:
    image:
      repository: "oliver006/redis_exporter"
      tag: "v1.67.0"
```

## Contributing

To update the chart, please follow the steps below:

1. Clone the project

```
git@github.com:favish/helm-redis.git
```

2. Make the changes, note down new version in [CHANGELOG.md](CHANGELOG.md) with the changes and commit them.
3. Tag new version and push the changes.

Example:
```
git tag -a 1.1.0 -m "Release 1.1.0"
git push origin 1.1.0

// or
git push origin --tags
```

4. Verify new chart version release.
Access the [`gh-pages`](https://github.com/favish/helm-redis/tree/gh-pages) branch to see the new chart package `redis-VERSION.tgz`

5. Draft a new release on GitHub with the new version and attach the chart package.

   1. Visit: https://github.com/favish/helm-redis/releases/new
   2. Choose the tag version you just created.
   3. Release title: put in the version
   4. Content, use following template, replace `PREV_VERSION` and `NEW_VERSION` with the actual version numbers.:
   ```
   ## What's Changed

   - Added values to config Redis image and version.
   - Added values to config Redis Metrics exporter image and version.
   
   **Full Changelog**: https://github.com/favish/helm-redis/compare/PREV_VERSION...NEW_VERSION
   ```
   5. Click on `Publish release`
   