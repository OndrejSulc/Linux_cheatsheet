# VS Code configs

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
