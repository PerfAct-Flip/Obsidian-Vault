## Linked Note
[[Imp points MERN]]


```bash
npx tsc --init
```

```bash
npm install --save-dev typescript ts-node nodemon
```

	nodemon.json
```json
{
  "watch": ["src"],
  "ext": "ts",
  "exec": "ts-node ./src/index.ts"
}



my current
{
  "watch": ["src", "server.ts"],
  "ext": "ts,js,json",
  "exec": "npx ts-node-esm server.ts"
}
```

	package.json
```json
"scripts": {
  "dev": "nodemon"
}
```
