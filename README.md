# fandom.js

A powerful library to interact with the Fandom + MediaWiki APIs.

[![npm version](https://img.shields.io/npm/v/fandom.js.svg)](https://www.npmjs.com/package/fandom.js)
[![License](https://img.shields.io/npm/l/fandom.js.svg)](LICENSE)

## Features

- **Page Management**: Fetch, edit, and manage wiki pages.
- **User Information**: Retrieve user details, groups, and contributions.
- **Revisions**: Access page history and recent changes.
- **Search**: Search for pages and content.
- **Categories**: List category members.
- **Events**: Listen for wiki events like page updates and creations.
- **TypeScript Support**: Fully typed for a better development experience.

## Installation

```bash
npm install fandom.js
# or
pnpm add fandom.js
# or
yarn add fandom.js
# or
bun add fandom.js
```

## Usage

Here is a simple example to get you started:

```javascript
import { Client } from "fandom.js";

const client = new Client({
  host: "https://sonic.fandom.com",
  apiPath: "/api.php", // API endpoint path (default: "/api.php")
  polling: true, // Enable polling for events (if activated, the client will run endlessly and listen for events until stopped manually)
});

client.events.on("ready", () => {
  console.log("Client is ready!");
});

async function main() {
  // Login (Optional, required for write operations)
  // await client.login("Username", "Password");

  // Fetch a page
  const page = await client.pages.fetch("Sonic_the_Hedgehog");
  console.log(`Title: ${page.title}`);
  console.log(`Extract: ${page.extract}`);

  const images = await page.images();
  console.log("Images:", images);

  // Search
  const results = await client.search.search("Tails");
  console.log("Search results:", results);
}

main();
```

## Documentation

For full documentation, visit [fandom.js.org](https://fandom.js.org).

## Contributing

Contributions are welcome! Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct, and the process for submitting pull requests.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
