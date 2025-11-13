# Turborepo starter

This Turborepo starter is maintained by the Turborepo core team.

## Using this example

Run the following command:

```sh
npx create-turbo@latest
```

## What's inside?

This Turborepo includes the following packages/apps:

### Apps and Packages

- `docs`: a [Next.js](https://nextjs.org/) app
- `web`: another [Next.js](https://nextjs.org/) app
- `@repo/ui`: a stub React component library shared by both `web` and `docs` applications
- `@repo/eslint-config`: `eslint` configurations (includes `eslint-config-next` and `eslint-config-prettier`)
- `@repo/typescript-config`: `tsconfig.json`s used throughout the monorepo

Each package/app is 100% [TypeScript](https://www.typescriptlang.org/).

### Utilities

This Turborepo has some additional tools already setup for you:

- [TypeScript](https://www.typescriptlang.org/) for static type checking
- [ESLint](https://eslint.org/) for code linting
- [Prettier](https://prettier.io) for code formatting

### Build

To build all apps and packages, run the following command:

```
cd my-turborepo

# With [global `turbo`](https://turborepo.com/docs/getting-started/installation#global-installation) installed (recommended)
turbo build

# Without [global `turbo`](https://turborepo.com/docs/getting-started/installation#global-installation), use your package manager
npx turbo build
yarn dlx turbo build
pnpm exec turbo build
```

You can build a specific package by using a [filter](https://turborepo.com/docs/crafting-your-repository/running-tasks#using-filters):

```
# With [global `turbo`](https://turborepo.com/docs/getting-started/installation#global-installation) installed (recommended)
turbo build --filter=docs

# Without [global `turbo`](https://turborepo.com/docs/getting-started/installation#global-installation), use your package manager
npx turbo build --filter=docs
yarn exec turbo build --filter=docs
pnpm exec turbo build --filter=docs
```

### Develop

To develop all apps and packages, run the following command:

```
cd my-turborepo

# With [global `turbo`](https://turborepo.com/docs/getting-started/installation#global-installation) installed (recommended)
turbo dev

# Without [global `turbo`](https://turborepo.com/docs/getting-started/installation#global-installation), use your package manager
npx turbo dev
yarn exec turbo dev
pnpm exec turbo dev
```

You can develop a specific package by using a [filter](https://turborepo.com/docs/crafting-your-repository/running-tasks#using-filters):

```
# With [global `turbo`](https://turborepo.com/docs/getting-started/installation#global-installation) installed (recommended)
turbo dev --filter=web

# Without [global `turbo`](https://turborepo.com/docs/getting-started/installation#global-installation), use your package manager
npx turbo dev --filter=web
yarn exec turbo dev --filter=web
pnpm exec turbo dev --filter=web
```

### Remote Caching

> [!TIP]
> Vercel Remote Cache is free for all plans. Get started today at [vercel.com](https://vercel.com/signup?/signup?utm_source=remote-cache-sdk&utm_campaign=free_remote_cache).

Turborepo can use a technique known as [Remote Caching](https://turborepo.com/docs/core-concepts/remote-caching) to share cache artifacts across machines, enabling you to share build caches with your team and CI/CD pipelines.

By default, Turborepo will cache locally. To enable Remote Caching you will need an account with Vercel. If you don't have an account you can [create one](https://vercel.com/signup?utm_source=turborepo-examples), then enter the following commands:

```
cd my-turborepo

# With [global `turbo`](https://turborepo.com/docs/getting-started/installation#global-installation) installed (recommended)
turbo login

# Without [global `turbo`](https://turborepo.com/docs/getting-started/installation#global-installation), use your package manager
npx turbo login
yarn exec turbo login
pnpm exec turbo login
```

This will authenticate the Turborepo CLI with your [Vercel account](https://vercel.com/docs/concepts/personal-accounts/overview).

Next, you can link your Turborepo to your Remote Cache by running the following command from the root of your Turborepo:

```
# With [global `turbo`](https://turborepo.com/docs/getting-started/installation#global-installation) installed (recommended)
turbo link

# Without [global `turbo`](https://turborepo.com/docs/getting-started/installation#global-installation), use your package manager
npx turbo link
yarn exec turbo link
pnpm exec turbo link
```

## Useful Links

Learn more about the power of Turborepo:

- [Tasks](https://turborepo.com/docs/crafting-your-repository/running-tasks)
- [Caching](https://turborepo.com/docs/crafting-your-repository/caching)
- [Remote Caching](https://turborepo.com/docs/core-concepts/remote-caching)
- [Filtering](https://turborepo.com/docs/crafting-your-repository/running-tasks#using-filters)
- [Configuration Options](https://turborepo.com/docs/reference/configuration)
- [CLI Usage](https://turborepo.com/docs/reference/command-line-reference)


# LMS Monorepo პროექტი (IT კოლეჯისთვის)

ეს არის Full-Stack აპლიკაცია, რომელიც შექმნილია IT კოლეჯის მენტორებისა და სტუდენტებისთვის. პროექტი აგებულია Turborepo-სა და pnpm-ის გამოყენებით.

## 📚 პროექტის სტრუქტურა

ჩვენ ვიყენებთ Monorepo არქიტექტურას, რომელიც მოიცავს:

* `apps/client`: **Frontend** აპლიკაცია (Next.js 14, React, TypeScript)
* `apps/api`: **Backend** აპლიკაცია (Nest.js, TypeScript)
* `packages/db`: **საერთო პაკეტი** (Prisma), რომელიც შეიცავს მონაცემთა ბაზის სქემას და კლიენტს.

---

## ⚙️ ეტაპი 0: ფუნდამენტის აწყობა

ამ ეტაპზე მოხდა პროექტის სრული ინიციალიზაცია:

1.  **Monorepo:** დაყენდა `pnpm` და `Turborepo` სამართავად.
2.  **აპლიკაციები:** შეიქმნა `client` (Next.js) და `api` (Nest.js) აპლიკაციები.
3.  **მონაცემთა ბაზა:**
    * შეიქმნა `packages/db` პაკეტი Prisma-სთვის.
    * პროექტი დაუკავშირდა Supabase PostgreSQL ბაზას.
    * გამოსწორდა IPv4/IPv6 კავშირის პრობლემა **Session Pooler**-ის გამოყენებით.
    * დაყენდა `dotenv-cli`, რათა სკრიპტებმა სწორად წაიკითხონ `.env` ფაილი.
4.  **პორტები:**
    * Frontend (`client`) მუშაობს `http://localhost:3000`-ზე.
    * Backend (`api`) მუშაობს `http://localhost:3001`-ზე.

## 🔑 ეტაპი 1: ავთენტიფიკაციის ფუნდამენტი

ამ ეტაპზე მოვამზადეთ ყველაფერი მომხმარებლების მართვისთვის:

1.  **ბაზის სქემა:** `schema.prisma`-ში შეიქმნა `User` მოდელი და `Role` enum-ი (`STUDENT`, `ASSISTANT`, `MENTOR`, `ADMIN`).
2.  **იერარქია:** `User` მოდელს დაემატა თვით-მიმთითებელი კავშირი (self-relation), რათა მენტორებს შეეძლოთ ასისტენტების ყოლა.
3.  **მიგრაცია:** `prisma migrate dev` ბრძანებით ბაზაში შეიქმნა `User` ცხრილი.
4.  **Backend-ის მომზადება:**
    * `api` აპლიკაციაში დაყენდა `bcrypt`, `passport`, `passport-jwt`, `@nestjs/jwt` და ვალიდაციის პაკეტები.
    * `nest g` ბრძანებით დაგენერირდა `AuthModule`, `AuthService` და `AuthController`.

---

## 🚀 როგორ გავუშვათ პროექტი

1.  **დააინსტალირეთ დამოკიდებულებები:**
    ```bash
    pnpm install
    ```
2.  **დააგენერირეთ Prisma Client:**
    ```bash
    pnpm --filter @lms/db db:generate
    ```
3.  **გაუშვით დეველოპმენტ სერვერები:**
    ```bash
    pnpm turbo run dev
    ```

    