{
  "github": {
    "silent": true
  }
}
{
  "$schema": "https://turborepo.org/schema.json",
  "globalDependencies": [".env", "./secrets/**"],
  "pipeline": {
    "build": {
      "dependsOn": ["^build"],
      "outputs": [
        "dist/**",
        ".next/**",
        "!.next/cache/**",
        "storybook-static/**"
      ]
    },

    "start": {
      "persistent": true,
      "cache": false
    },
    "lint": {},
    "lint:fix": {},
    "storybook": {},
    "storybook:build": {},
    "clean": {
      "cache": false
    },
    "dev": {
      "persistent": true,
      "cache": false,
      "env": [".env.bartio"]
    },
    "check-types": {
      "dependsOn": ["^build"],
      "cache": false,
      "outputs": ["storybook-static/**"]
    }
  },
  "globalEnv": ["CI", "NODE_ENV", "SKIP_ENV_VALIDATION", "VERCEL", "VERCEL_ENV"]
}
{
  "compilerOptions": {
    "target": "es2020",
    "lib": ["dom", "dom.iterable", "esnext"],
    "allowJs": true,
    "checkJs": true,
    "skipLibCheck": true,
    "strict": true,
    "forceConsistentCasingInFileNames": true,
    "noEmit": true,
    "esModuleInterop": true,
    "module": "esnext",
    "moduleResolution": "Bundler",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "jsx": "preserve",
    "incremental": true,
    // "noUncheckedIndexedAccess": true,
    // "sourceMap": true
  },
  "exclude": ["**/auth/*"],
  "include": [
    "src",
    "index.ts",
    "transformer.ts",
    ".eslintrc.js",
    ".prettierrc.js"
  ]
}
{
  "compilerOptions": {
    "moduleResolution": "Bundler",
    "module": "ESNext",
    "target": "ES2021", // Setting this to `ES2021` enables native support for `Node v16+`: https://github.com/microsoft/TypeScript/wiki/Node-Target-Mapping.
    "lib": [
      "ES2022", // By using ES2022 we get access to the `.cause` property on `Error` instances.
      "DOM" // We are adding `DOM` here to get the `fetch`, etc. types. This should be removed once these types are available via DefinitelyTyped.
    ]
  }
}
packages:
  - packages/config/*
  - packages/b-sdk
  - packages/graphql
  - packages/berajs
  - packages/wagmi
  - packages/proto
  - packages/ui
  - packages/shared-ui
  - apps/hub
  - apps/honey
  - apps/lend
  - apps/perp
  - apps/berajs-docs
  - apps/storybook
