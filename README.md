# 头像定制
- 用户将自己的个人头像上传后，可借助 Stable Diffusion 模型进行训练，并生成一款拥有不同风格的个人头像。


# Photoshot

[![Twitter](https://img.shields.io/twitter/url/https/twitter.com/photoshot_ai.svg?style=social&label=Follow%20%40photoshot_ai)](https://twitter.com/photoshot_ai)

An open-source AI avatar generator web app

[![Photoshot](https://photoshot.app/og-cover.jpg)
](https://user-images.githubusercontent.com/1102595/206658000-d349ef06-e4f2-4626-9deb-6c8a246f7553.mp4)

Try it out at [photoshot.app](https://photoshot.app)

## Stack

- ▲ [Next.js](https://nextjs.org/) for webapp
- 🖼 [Chakra UI](https://chakra-ui.com/) for UI components
- 📦 [Prisma](https://www.prisma.io/) for database
- 🧠 [Replicate](https://replicate.com/), a platform for running machine learning models in the cloud
- 💰 [Stripe](https://stripe.com/) for payments
- 👩‍🎨 [Stable Diffusion](https://replicate.com/stability-ai/stable-diffusion) an open-source text-to-image generation model

## Getting Started

Install dependencies:

```bash
yarn install
```

You can use Docker to run a local postgres database and maildev server (accessible at http://localhost:1080):

```bash
docker-compose up -d
```

Create .env.local:

```bash
cp .env.example .env.local
```

Update environment variable values:

```
// Database connection string of your database (postgresql here)
DATABASE_URL=postgresql://photoshot:photoshot@localhost:5432/photoshot
// https://next-auth.js.org/configuration/options#nextauth_url
NEXTAUTH_URL=http://localhost:3000

// AWS S3 bucket info (for storing pictures)
S3_UPLOAD_KEY=
S3_UPLOAD_SECRET=
S3_UPLOAD_BUCKET=
S3_UPLOAD_REGION=

// Replicate API token / username
REPLICATE_API_TOKEN=
REPLICATE_USERNAME=
REPLICATE_MAX_TRAIN_STEPS=3000
REPLICATE_NEGATIVE_PROMPT=
REPLICATE_HD_VERSION_MODEL_ID=

// Replicate instance token (should be rare)
NEXT_PUBLIC_REPLICATE_INSTANCE_TOKEN=

// Random secret for NextAuth
SECRET=

// SMTP server and email address to send emails from
EMAIL_FROM=
EMAIL_SERVER=smtp://localhost:25

// Stripe API key
STRIPE_SECRET_KEY=

// Price of a studio in cents (ie: 1000 = $10)
NEXT_PUBLIC_STRIPE_STUDIO_PRICE=

// Amount of allowed shots per studio
NEXT_PUBLIC_STUDIO_SHOT_AMOUNT=

// Prompt wizard
OPENAI_API_KEY=
OPENAI_API_SEED_PROMPT=
```

Please note that if you want to use the provided `docker-compose` setup you have to disable `TLS` in your `.env.local` by adding:

```
NODE_TLS_REJECT_UNAUTHORIZED = "0"
```

Run migrations

```bash
yarn prisma:migrate:dev
```

Run the development server:

```bash
npm run dev
# or
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.
