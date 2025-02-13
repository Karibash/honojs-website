# Pretty JSON Middleware

Pretty JSON middleware enables "_JSON pretty print_" for JSON response body.
Adding `?pretty` to url query param, the JSON strings are prettified.

```js
// GET /
{"project":{"name":"Hono","repository":"https://github.com/honojs/hono"}}
```

will be:

```js
// GET /?pretty
{
  "project": {
    "name": "Hono",
    "repository": "https://github.com/honojs/hono"
  }
}
```

## Import

::: code-group

```ts [npm]
import { Hono } from 'hono'
import { prettyJSON } from 'hono/pretty-json'
```

```ts [Deno]
import { Hono } from 'https://deno.land/x/hono/mod.ts'
import { prettyJSON } from 'https://deno.land/x/hono/middleware.ts'
```

:::

## Usage

```ts
const app = new Hono()

app.use('*', prettyJSON()) // With options: prettyJSON({ space: 4 })
app.get('/', (c) => {
  return c.json({ message: 'Hono!' })
})
```

## Options

- `space`
  - Number of spaces for indentation. Default is `2`.
