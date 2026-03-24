# nextjs-webpack-vs-turbopack-sass

Hey! 👋🏼

This a reproduction repository for showcasing Next.js Turbopack vs Webpack rounding precision difference when compiling Sass. 

## Steps to reproduce

1. Build the project using Webpack:

```sh
npm run build:webpack
```

2. Copy generated CSS into a `webpack.css` file:

```sh
find .next -name '*.css' -exec cat {} + > ./webpack.css
```

3. Build the project using Turbopack:

```sh
npm run build:turbopack
```

4. Copy generated CSS into a `turbopack.css` file:

```sh
find .next -name '*.css' -exec cat {} + > ./turbopack.css
```

5. Do a `diff` of both files (look at `line-height` property):

- Webpack `line-height`: `1.4705882353` (10 digits of precision)
- Turbopack `line-height`: `1.47059` (5 digits of precision)

```sh
diff webpack.css turbopack.css
```

### Visual reproduction

You can also reproduce it by building and opening the project in two separate tabs:

1. Build with webpack and start the server:

```sh
npm run build:webpack && npm run start -- -p 3001
```

2. Open http://localhost:3001 in a Safari
3. Stop the server (without closing browser tab)
4. Build with turbopack and start the server:

```sh
npm run build:turbopack && npm run start -- -p 3002
```

5. Open http://localhost:3002 in Safari
6. Compare both tabs

https://github.com/user-attachments/assets/2bf93c06-f5a4-4c4d-b6f1-e953a269b29a
