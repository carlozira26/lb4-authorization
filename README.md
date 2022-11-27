# lb4-authorization

This application is generated using [LoopBack 4 CLI](https://loopback.io/doc/en/lb4/Command-line-interface.html) with the
[initial project layout](https://loopback.io/doc/en/lb4/Loopback-application-layout.html).

## Install dependencies

By default, dependencies were installed when this application was generated.
Whenever dependencies in `package.json` are changed, run the following command:

```sh
npm install
```

To only install resolved dependencies in `package-lock.json`:

```sh
npm ci
```

## Run the application

```sh
npm start
```

You can also run `node .` to skip the build step.

Open http://127.0.0.1:3000 in your browser.

## Tutorial

When you already have the authentication or you can grab it here: https://github.com/carlozira26/lb4-authorization
1. You can start by creating the jwt.service. We will bind this to Loopback 4 JWTService of our application. 
 (Sample Code: https://github.com/carlozira26/lb4-authorization/blob/main/src/services/jwt.service.ts)
2. To bind the JWTService to our application.
  a. import the jwt.service
      import {JWTService} from './services/jwt.service';
  b. bind to class
      this.bind(TokenServiceBindings.TOKEN_SERVICE).toClass(JWTService);
3. Create the basicAuthorizor (Sample Code: https://github.com/carlozira26/lb4-authorization/blob/main/src/services/basic.authorizor.ts)
4. We need to import the basic authorizor to our endpoint.
    import {basicAuthorization} from '../services/basic.authorizor';
5. We can now use the @authorize to our endpoint. @authorize should be after the @authenticate('jwt')
  (Sample Code: https://github.com/carlozira26/lb4-authorization/blob/main/src/controllers/user.controller.ts)
  
   @authenticate('jwt')
   @authorize({allowedRoles: ['admin'], voters: [basicAuthorization]})
   @get('/users/list', 
    {...}
   )

## Rebuild the project

To incrementally build the project:

```sh
npm run build
```

To force a full build by cleaning up cached artifacts:

```sh
npm run rebuild
```

## Fix code style and formatting issues

```sh
npm run lint
```

To automatically fix such issues:

```sh
npm run lint:fix
```

## Other useful commands

- `npm run migrate`: Migrate database schemas for models
- `npm run openapi-spec`: Generate OpenAPI spec into a file
- `npm run docker:build`: Build a Docker image for this application
- `npm run docker:run`: Run this application inside a Docker container

## Tests

```sh
npm test
```

## What's next

Please check out [LoopBack 4 documentation](https://loopback.io/doc/en/lb4/) to
understand how you can continue to add features to this application.

[![LoopBack](https://github.com/loopbackio/loopback-next/raw/master/docs/site/imgs/branding/Powered-by-LoopBack-Badge-(blue)-@2x.png)](http://loopback.io/)
