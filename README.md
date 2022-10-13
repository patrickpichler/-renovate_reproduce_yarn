# renovate_reproduce_yarn

When running renovate bot with `binarysource=install` and enalbed `lockFileMaintenance` against this repo, it fails as
it tries to install yarn version 3.2.2 via `install-tool`.


## Command used to test
```
docker run --rm -it \
      -e RENOVATE_TOKEN=$GH_TOKEN \
      -e RENOVATE_BINARY_SOURCE=install \
      -e RENOVATE_LOCK_FILE_MAINTENANCE='{"enabled":true}' \
      -e RENOVATE_PLATFORM=github \
      -e LOG_LEVEL=debug \
      renovate/renovate:slim patrickpichler/renovate_reproduce_yarn
```

## Config
```
{
  "binarySource": "install",
  "platform": "github",
  "token": "***********",
  "lockFileMaintenance": {"enabled": true},
  "repositories": ["patrickpichler/renovate_reproduce_yarn"]
}
```
## Error from logs
```
{
     "name": "ExecError",
     "cmd": "/bin/sh -c install-tool yarn-slim 3.2.4",
     "stderr": "",
     "stdout": "installing v2 tool yarn-slim v3.2.4\nnpm ERR! code ETARGET\nnpm ERR! notarget No matching version found for yarn@3.2.4.\nnpm ERR! notarget In most cases you or one of your dependencies are requesting\nnpm ERR! notarget a package version that doesn't exist.\n\nnpm ERR! A complete log of this run can be found in:\nnpm ERR! /tmp/tmp.6Bfg8VkfJs/_logs/2022-10-13T10_43_13_911Z-debug-0.log\n",
     "options": {
       "cwd": "/tmp/renovate/repos/github/patrickpichler/renovate_reproduce_yarn",
       "encoding": "utf-8",
       "env": {
         "NPM_CONFIG_CACHE": "/tmp/renovate/cache/others/npm",
         "npm_config_store": "/tmp/renovate/cache/others/pnpm",
         "HOME": "/home/ubuntu",
         "PATH": "/home/ubuntu/bin:/home/ubuntu/.npm-global/bin:/home/ubuntu/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
         "LC_ALL": "C.UTF-8",
         "LANG": "C.UTF-8",
         "BUILDPACK_CACHE_DIR": "/tmp/renovate/cache/containerbase",
         "CONTAINERBASE_CACHE_DIR": "/tmp/renovate/cache/containerbase"
       },
       "maxBuffer": 10485760,
       "timeout": 900000
     },
     "exitCode": 1,
     "message": "Command failed: install-tool yarn-slim 3.2.4\n",
     "stack": "ExecError: Command failed: install-tool yarn-slim 3.2.4\n\n    at ChildProcess.<anonymous> (/usr/src/app/node_modules/renovate/lib/util/exec/common.ts:99:11)\n    at ChildProcess.emit (node:events:525:35)\n    at ChildProcess.emit (node:domain:489:12)\n    at Process.ChildProcess._handle.onexit (node:internal/child_process
:293:12)"
```
