## CI/CD

There will be two main parts:
- `Setup Wizard` - setsup the vps and its tech stack
- `CI/CD pipline` - creates a pipeline so every main branch push is pushed to prod

This is an extension on the basic CI/CD implementation. Once a push happens to a repo it will:
- Pull the latest code on the VPS.
- Install dependencies (like Python packages if needed).
- Restart Gunicorn (your application server).
- Reload Nginx (your web server) if configuration changes are needed.

## Setup Wizard

...

## CI/CD Pipeline

...
