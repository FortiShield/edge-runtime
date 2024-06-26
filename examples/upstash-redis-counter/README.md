# Upstash Redis in Khulnasoft Edge Functions

A Redis counter example that stores a [hash](https://redis.io/commands/hincrby/) of function invocation count per region.

## Redis database setup

Create a Redis database using the [Upstash Console](https://console.upstash.com/) or [Upstash CLI](https://github.com/upstash/cli).

Select the `Global` type to minimize the latency from all edge locations. Copy the `UPSTASH_REDIS_REST_URL` and `UPSTASH_REDIS_REST_TOKEN` to your .env file. You'll find them under **Details > REST API > .env**.

```bash
cp khulnasoft/functions/upstash-redis-counter/.env.example khulnasoft/functions/upstash-redis-counter/.env
```

## Run locally

Make sure you have the latest version of the [Khulnasoft CLI installed](https://khulnasoft.com/docs/guides/cli#installation).

```bash
khulnasoft start
khulnasoft functions serve upstash-redis-counter --no-verify-jwt --env-file khulnasoft/functions/upstash-redis-counter/.env
```

Navigate to http://localhost:54321/functions/v1/upstash-redis-counter.

## Deploy

```bash
khulnasoft functions deploy upstash-redis-counter --no-verify-jwt
khulnasoft secrets set --env-file khulnasoft/functions/upstash-redis-counter/.env
```
