# edu-node-ts

## instruktioner

```bash
cd ~
cd ws
mkdir edu-node-ts-intro
cd edu-node-ts-intro
npm init -y
npm pkg set main="service.js"
npm pkg set scripts.build="npx tsc"
npm pkg set scripts.start="node service.js"
npm pkg set scripts.dev="concurrently \"npx tsc --watch\" \"nodemon -q service.js\""
npm install -D typescript
npm install -D @types/express 
npm install -D @types/node
npm install -D concurrently nodemon
npx tsc --init
npm install express
npm install dotenv
touch service.ts
touch server.ts
```

## DoD

```bash
npm run build
npm start
```

## service.ts

```ts
import {app} from './server';
import dotenv from 'dotenv';

dotenv.config();
const PORT = process.env.PORT || 3000;

app.listen(PORT, () => {
    console.log(`Server is running at https://localhost:${PORT}`);
});
```


## server.ts

```ts
import express, { Express, Request, Response } from 'express';

export const app: Express = express();

app.get('/', (req: Request, res: Response) => {
    res.send('Express + TypeScript Server');
});
