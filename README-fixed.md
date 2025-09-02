command to run

docker-compose up --build -d -V

this will expose rugplay on port 80
you still need to change the .env file stuff to match the docker services

btw... this also needs to be run behind HTTPS.

below is an example of what it should look like, ... needs to be filled in with your own credentials.
You also need to setup Google OAuth and set the redirect URI to: `https://my-domain/api/auth/callback/google`

this version doesn't run replicas, so you will need to configure that yourself using nginx proxy in front, with tls/ssl certs or whatever.

you also need to ensure that the schemas are run by running the following commands inside the `website` directory, this might need you to temporarily change the host in the postgres .env variable to point to localhost while u run these commands.

- npx drizzle-kit push
- npx drizzle-kit migrate

enjoy!

```
# Rugplay Environment Configuration
# Copy this file to .env and fill in your actual values

# Database Configuration
DATABASE_URL=postgresql://postgres:password@postgres:5432/postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=password
POSTGRES_DB=rugplay

# Redis Configuration
REDIS_URL=redis://redis:6379

# Authentication
PRIVATE_BETTER_AUTH_SECRET=your_super_secret_auth_key_here_i_hope_this_is_longer_than_64
PUBLIC_BETTER_AUTH_URL=https://my-domain

# Google OAuth (optional - for social login)
GOOGLE_CLIENT_ID=...
GOOGLE_CLIENT_SECRET=...

# AWS S3/B2 Storage (for file uploads)
PRIVATE_B2_KEY_ID=...
PRIVATE_B2_APP_KEY=...
PUBLIC_B2_BUCKET=rugplay
PUBLIC_B2_ENDPOINT=http://minio:9000
PUBLIC_B2_REGION=us-east-1

# OpenAI (for AI features)
OPENROUTER_API_KEY=your_openrouter_api_key

# Websocket URL
PUBLIC_WEBSOCKET_URL=https://my-domain:8080
```

