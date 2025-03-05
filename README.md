# Redis Helm chart for internal use

## Usage

TBD.

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
   