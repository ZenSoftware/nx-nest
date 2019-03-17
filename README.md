### Minimum bug reproduction for Nx & @nestjs v6.0.0

Running `ng build` with the `--prod` flag fails to build.

```
ng build --prod
... or ...
npm run build:prod
```

#### How this repo was produced

```
npm install npx -g
npx create-nx-workspace nx-nest
ng g node-app api --framework nestjs
... upgrade @nestjs from v5 to v6
npm install @nestjs/platform-express@6.0.0 reflect-metadataG
```

#### Environment

```
- Nest: 6.0.0
- Node: 10.15.3
- Nx: 7.7.1
- Platform: Linux
```

#### Commands that work

```
npm run start
npm run build
```

Also regressing to nestjs@5.7.4 will compile with `ng build --prod`

#### Error log

```
$ ng build --prod
Starting type checking service...
Using 6 workers with 2048MB memory limit
Hash: de380795417288d36cc2
Version: webpack 4.29.0
Time: 13666ms
Built at: 03/17/2019 12:50:11 PM
      Asset      Size  Chunks  Chunk Names
    main.js  1.14 MiB       0  main
main.js.map  1.65 MiB       0  main
Entrypoint main = main.js main.js.map
  [0] ./node_modules/tslib/tslib.es6.js 10.1 KiB {0} [built]
 [16] ./node_modules/@nestjs/common/index.js 695 bytes {0} [built]
 [81] ./node_modules/@nestjs/core/constants.js 486 bytes {0} [built]
 [88] ./apps/api/src/app/app.service.ts 395 bytes {0} [built]
[145] ./node_modules/@nestjs/core/helpers/index.js 236 bytes {0} [built]
[149] ./node_modules/@nestjs/core/nest-application-context.js 10.9 KiB {0} [built]
[151] ./node_modules/reflect-metadata/Reflect.js 50 KiB {0} [built]
[302] ./node_modules/@nestjs/core/services/index.js 236 bytes {0} [built]
[307] ./node_modules/@nestjs/core/nest-application.js 14.5 KiB {0} [built]
[313] ./node_modules/@nestjs/core/index.js 972 bytes {0} [built]
[329] ./apps/api/src/app/app.module.ts 485 bytes {0} [built]
[330] ./apps/api/src/app/app.controller.ts 913 bytes {0} [built]
[331] multi ./apps/api/src/main.ts 28 bytes {0} [built]
[332] ./apps/api/src/main.ts 992 bytes {0} [built]
[333] ./node_modules/@nestjs/core/adapters/index.js 231 bytes {0} [built]
    + 555 hidden modules

WARNING in ./node_modules/@nestjs/common/utils/load-package.util.js 8:39-59
Critical dependency: the request of a dependency is an expression
 @ ./node_modules/@nestjs/core/nest-application.js
 @ ./node_modules/@nestjs/core/index.js
 @ ./apps/api/src/main.ts
 @ multi ./apps/api/src/main.ts

WARNING in ./node_modules/@nestjs/core/helpers/load-adapter.js 8:15-39
Critical dependency: the request of a dependency is an expression
 @ ./node_modules/@nestjs/core/nest-factory.js
 @ ./node_modules/@nestjs/core/index.js
 @ ./apps/api/src/main.ts
 @ multi ./apps/api/src/main.ts

WARNING in ./node_modules/optional/optional.js 6:15-30
Critical dependency: the request of a dependency is an expression
 @ ./node_modules/@nestjs/core/nest-application.js
 @ ./node_modules/@nestjs/core/index.js
 @ ./apps/api/src/main.ts
 @ multi ./apps/api/src/main.ts

ERROR in ./node_modules/@nestjs/core/nest-application.js
Module not found: Error: Can't resolve '@nestjs/microservices' in '/home/z/Work/nx-nest/node_modules/@nestjs/core'
 @ ./node_modules/@nestjs/core/nest-application.js 148:124-156
 @ ./node_modules/@nestjs/core/index.js
 @ ./apps/api/src/main.ts
 @ multi ./apps/api/src/main.ts

ERROR in ./node_modules/@nestjs/core/nest-factory.js
Module not found: Error: Can't resolve '@nestjs/microservices' in '/home/z/Work/nx-nest/node_modules/@nestjs/core'
 @ ./node_modules/@nestjs/core/nest-factory.js 56:136-168
 @ ./node_modules/@nestjs/core/index.js
 @ ./apps/api/src/main.ts
 @ multi ./apps/api/src/main.ts

ERROR in ./node_modules/@nestjs/common/cache/cache.providers.js
Module not found: Error: Can't resolve 'cache-manager' in '/home/z/Work/nx-nest/node_modules/@nestjs/common/cache'
 @ ./node_modules/@nestjs/common/cache/cache.providers.js 10:116-140
 @ ./node_modules/@nestjs/common/cache/cache.module.js
 @ ./node_modules/@nestjs/common/cache/index.js
 @ ./node_modules/@nestjs/common/index.js
 @ ./apps/api/src/app/app.module.ts
 @ ./apps/api/src/main.ts
 @ multi ./apps/api/src/main.ts

ERROR in ./node_modules/@nestjs/common/pipes/validation.pipe.js
Module not found: Error: Can't resolve 'class-transformer' in '/home/z/Work/nx-nest/node_modules/@nestjs/common/pipes'
 @ ./node_modules/@nestjs/common/pipes/validation.pipe.js 52:119-147
 @ ./node_modules/@nestjs/common/pipes/index.js
 @ ./node_modules/@nestjs/common/index.js
 @ ./apps/api/src/app/app.module.ts
 @ ./apps/api/src/main.ts
 @ multi ./apps/api/src/main.ts

ERROR in ./node_modules/@nestjs/common/serializer/class-serializer.interceptor.js
Module not found: Error: Can't resolve 'class-transformer' in '/home/z/Work/nx-nest/node_modules/@nestjs/common/serializer'
 @ ./node_modules/@nestjs/common/serializer/class-serializer.interceptor.js 33:131-159 34:8-36
 @ ./node_modules/@nestjs/common/serializer/index.js
 @ ./node_modules/@nestjs/common/index.js
 @ ./apps/api/src/app/app.module.ts
 @ ./apps/api/src/main.ts
 @ multi ./apps/api/src/main.ts

ERROR in ./node_modules/@nestjs/common/pipes/validation.pipe.js
Module not found: Error: Can't resolve 'class-validator' in '/home/z/Work/nx-nest/node_modules/@nestjs/common/pipes'
 @ ./node_modules/@nestjs/common/pipes/validation.pipe.js 51:115-141
 @ ./node_modules/@nestjs/common/pipes/index.js
 @ ./node_modules/@nestjs/common/index.js
 @ ./apps/api/src/app/app.module.ts
 @ ./apps/api/src/main.ts
 @ multi ./apps/api/src/main.ts
```
