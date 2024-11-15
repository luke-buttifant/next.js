# create-next-app-no-deps

Create Next.js applications without automatically installing dependencies. This is a modified version of `create-next-app` that skips the dependency installation step, allowing you to review and customize dependencies before installing them.

## Usage

```bash
npx create-next-app-no-deps@latest my-app
```

## Features

- Creates Next.js project structure
- Skips automatic dependency installation
- Supports TypeScript and JavaScript templates
- Configurable project settings
- Includes all standard create-next-app templates and configurations

## Why use this?

- Review dependencies before installation
- Customize package.json before running npm install
- Faster initial project creation
- Better control over dependency versions
- Useful in environments with strict dependency requirements

## After Creation

1. Review your package.json
2. Modify dependencies as needed
3. Run `npm install` manually

## License

MIT

## Credits

Based on the official create-next-app by Vercel
