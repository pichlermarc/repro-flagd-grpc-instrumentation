# Bug reproduction repository

## How to run

```
npm install 
npm run docker:start
npm run start
```

Go to `http://localhost:16686`, the trace should start at the `js-client` service and continue to `flagd`, however, the trace is broken and two different trace-ids are used, and no grpc spans can be seen.

The OpenFeature `FlagdProvider` is using `@grpc/grpc-js` to communicate with `flagd`, so the trace should be connected, the same trace-id should be used across all serivces, and a span should be created for the service call.