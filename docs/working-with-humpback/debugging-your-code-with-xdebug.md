# Debugging your code with Xdebug

Xdebug is the most commonly used debugging tool. In order to use it in Humpback, you should configure your IDE with default config values and adding the necessary PathMaps for your code (mapping between remote path: /var/www/html, and local path where your code is stored)

Then, you should run `ahoy docker setup-xdebug` and you'll be ready to go!!!

## Example VSCode launch.json

```
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Listen for XDebug",
            "type": "php",
            "request": "launch",
            "port": 9000,
            "pathMappings": {
                "/var/www/html": "${workspaceRoot}"
              }  
        }
    ]
}
```
