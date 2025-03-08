# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2021-11-19
### Added
- Initial release.

## [1.0.3] - 2025-02-11
### Fix monitoring
- Use modern PodMonitor CRD for discoverabilioty by prometheus. 

## [1.1.0]  - 2025-03-05
### Added
- Parameterized the Redis container image and version. Default to `redis:4-alpine` for backward compatibility.
- Parameterized the Redis exporter container image and version. Default to `oliver006/redis_exporter:v0.14` for backward compatibility.

## [1.1.1] - 2025-03-07
### Added
- Added values to enable/disable init containers.

## [1.1.2] - 2025-03-07
### Added
- Fixed issue with `PodMonitor` is created when installing Redis chart on cluster not having Prometheus release installed.
  - The known issue message with this issue is `Error: unable to build kubernetes objects from release manifest: resource mapping not found for name: "redis" namespace: "" from "": no matches for kind "PodMonitor" in version "monitoring.coreos.com/v1"`
