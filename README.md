Template to initialize a backend project using Node.js, Express, TypeScript, and related libraries:

### Step 1: Install Dependencies

```bash
# Install TypeScript, Express, and related dependencies
yarn add express ts-node tsconfig-paths
yarn add --dev typescript ts-node-dev @types/node @types/express
npx tsc --init
yarn add cors
yarn add --dev @types/cors
```

### Step 2: Create .gitignore

Create a `.gitignore` file and add the following lines:

```
node_modules
.env
yarn-error.log
```

### Step 3: Update package.json

Update your `package.json` with the project details and scripts:

```json
{
  "name": "workshop-backend",
  "version": "1.0.0",
  "scripts": {
    "dev": "ts-node-dev -r tsconfig-paths/register src/main.ts",
    "start": "ts-node -r tsconfig-paths/register src/main"
  },
  // ...other package.json settings
}
```

### Step 4: Create src/main.ts

Create a `src/main.ts` file for your main application code.

### Step 5: Start the Project

You can start the project using either of the following commands:

```bash
# Development mode with auto-reload
yarn dev

# Production mode
yarn start
```

### Step 6: Install Validation Library

```bash
# Install validation libraries
yarn add io-ts io-ts-extra fp-ts
```

### Step 7: Install PostgreSQL Connection

```bash
# Install PostgreSQL and its types
yarn add pg
yarn add --dev @types/pg
```

### Step 8: Install Prisma ORM

```bash
# Install Prisma and initialize it
yarn add --dev prisma
yarn add @yarnpkg/pnpify
npx prisma init --datasource-provider postgresql
```

### Step 9: Create .env File

Create a `.env` file and add your environment variables:

```
DATABASE_URL="postgresql://postgres:password@localhost:5432/postgres?schema=xxxxxxx"
```

### Step 10: Create Prisma Schema Files

Create Prisma schema files (e.g., `index.prisma` and `test.prisma`) based on your project requirements.

### Step 11: Update package.json Scripts

Add the following scripts to your `package.json`:

```json
"scripts": {
    // ...other scripts
    "prisma:merge": "cat prisma/schema/**.prisma > prisma/schema.prisma",
    "prisma:format": "npx prisma format",
    "prisma:migrate": "yarn pnpify migrate dev --name init --schema prisma/schema.prisma",
    "prisma:generate": "yarn pnpify prisma generate --schema=prisma/schema.prisma"
}
```

### Explanation of Prisma Scripts:

- `prisma:merge`: Combines code from `index.prisma` and `test1.prisma` together and adds them to `schema.prisma`.
- `prisma:format`: Formats and checks Prisma code.
- `prisma:migrate`: Migrates the new schema to the database.
- `prisma:generate`: Generates code for connections built with Prisma (e.g., creating connections).

These scripts should be run in this order every time you change the schema.

### Step 12: Install Jest for Unit Testing

```bash
# Install Jest and related libraries for unit testing
yarn add --dev jest ts-jest @types/jest
```

### Step 13: Create jest.config.ts

Create a `jest.config.ts` file for Jest configuration.

### Step 14: Update package.json Scripts for Testing

Add the following scripts for running tests:

```json
"scripts": {
    // ...other scripts
    "test": "jest --verbose",
    "test:xxxx": "jest -- src/xxxx"
}
```

Replace `xxxx` with your project name or specific test suite names.

### Step 15: Project Structure

Your project structure should include the following:

- `routes.ts`: Collects paths for all APIs.
- `test1API` folder containing:
  - `resolver.ts`: Connects to the database via Prisma.
  - `handler.ts`: Handles API requests, checks input codecs, and manages responses.
  - `interface.ts`: Declares types/interfaces.
  - `spec.ts`: Contains tests for each API response.

When cloning the project, make the following changes:

1. Update the schema in `test.prisma` by changing the file name and adding schema details.
2. In the `.env` file, change `DATABASE_URL` to your own database URL.
3. In `package.json`, change `"test:xxxxx"` to your project name or specific test suite names.
4. Start by writing code in the resolver file to connect to the database, then create an interface to manage input, followed by the handler, route.ts, and finally spec.ts to test the APIs.
