# Vue Cli Environment Variable

## Mode

Under the default situation, the Vue CLI project has `three` modes:

- `development` mode used in `vue-cli-service serve`
- `test` mode used in `vue-cli-service test:unit`
- `production` mode used in `vue-cli-service build` and `vue-cli-service test:e2e`

可以通过传递 `--mode` 选项参数为命令行覆写默认的模式。例如，如果你想要在构建命令中使用开发环境变量：

```bash
    vue-cli-service build --mode development
```

当运行 `vue-cli-service` 命令时，所有的环境变量都从对应的 环境文件 中载入。如果文件内部不包含
`NODE_ENV` 变量，它的值将取决于模式，例如，在 `production` 模式下被设置为 `"production"` ，在 `test` 模式下被设置为 `"test"` ，默认则是 `"development"` 。

## Environment Variables

we can create below these files to identify the environment variables under project root folder:

```bash
    .env                # 在所有的环境中被载入
    .env.local          # 在所有的环境中被载入，但会被 git 忽略
    .env.[mode]         # 只在指定的模式中被载入
    .env.[mode].local   # 只在指定的模式中被载入，但会被 git 忽略
```

One environment file only include `"key=value"` format for each environment variable.

```bash
    FOO=bar
    VUE_APP_NOT_SECRET_CODE=some_value
```

## Access the Environment Variables in .js .ts or .vue

We can through the `process.env` to access the Environment Variable.

```js
const base_url = process.env.VUE_APP_BASE_URL;
```
