# VS Code configs

## Key shortcuts

collapse all ranges of specified indent
```
ctrl + k + 0..3
```

uncollapse all ranges
```
ctrl + k + j
```


## Config
.vscode/settings.json
```
"files.exclude": {
      "**/node_modules/**": true,
      "**/dist/**": true
  }
```


.vscode/launch.json
```
{
    "version": "0.2.0",
    "configurations": [
      {
        "name": "Mocha (Test single file)",
        "type": "node",
        "request": "launch",
        "runtimeArgs": [
          "${workspaceRoot}/node_modules/.bin/mocha",
          "--inspect-brk",
          "${relativeFile}",
          "--timeout 0"
        ],
        "console": "integratedTerminal",
        "internalConsoleOptions": "neverOpen",
    }]
}
```
