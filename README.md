# AWS Dev Day

## Supabase MCP

### Getting started

#### Create free Supabase project

Head over to [👉 database.new](database.new) and create a free account - make sure you set the region close to your geographical location.

#### Create a Next.js project

1. Create a project

```
npx create-next-app -e with-supabase aws-dev-day
```

2. Update environment variables

```
mv .env.example .env.local
```

Update environment variable values to connect to [your project](https://supabase.com/dashboard/project/_?showConnect=true).

#### Configure Supabase MCP

Check out [the docs](https://supabase.com/docs/guides/getting-started/mcp) for more settings and configuring Supabase MCP for other tools.

1. Create a Personal Access Token

Head over to your [Supabase Settings](https://supabase.com/dashboard/account/tokens) and create a new access token.

2. Configure MCP for Cursor

Create a file called `.cursor/mcp.json` and configure it to use your project.

```
{
  "mcpServers": {
    "supabase": {
      "command": "npx",
      "args": [
        "-y",
        "@supabase/mcp-server-supabase@latest",
        "--read-only", // remove this for workshop, but a good one to default to
        "--project-ref=<project-ref>"
      ],
      "env": {
        "SUPABASE_ACCESS_TOKEN": "<personal-access-token>"
      }
    }
  }
}
```

3. Enable MCP Server

Head over to `Cursor's Settings > Tools and Integrations` and enable `supabase` under `MCP Tools`.

4. Add to .gitignore

Add `.cursor/mcp.json` to the bottom of `.gitignore`.

#### Create a test user

Head over to [your project's Auth Settings](https://supabase.com/dashboard/project/_/auth/users), and create a new user.

![Create new user](/create-user.png)

Make sure "Auto Confirm User" is checked.

![Auto Confirm User](/auto-confirm-user.png)

### Create blog page

```
Here is a starting Next.js + Supabase template. I want you to build a simple blog post app that shows a list of blog posts. These blog posts should come from my Supabase database. Use a black + green colour scheme.

Create a `posts` table and insert some example content. Make sure you write an RLS policy that allows everyone to view our blog posts.

I've already setup the Supabase client and environment variables. Assume that the environment variables are setup correctly. Don't worry about generating database types. Write all the code in a new page - recipes/page.tsx. Use the Supabase server client in from ~/lib/supabase/server.
```

### Create blog details page

```
Add a page to view the contents of each blog post.
```

### Add comments

```
Let's now add a commenting feature on each post.

A user should be able to view and add comments at the bottom of each blog post page. As before, you should setup a comments table with RLS policies that allow anyone to read comments and signed in users only to create comments. Use the users email as the commenter name.

Use a Next.js server action for the form and make sure to call `revalidatePath` so the UI updates after creating a comment.

Also, add the number of comments for each blog post on the blog post's card in `/posts` page.
```

### Extensions

- Add [social auth](https://supabase.com/docs/guides/auth/social-login) with GitHub or Google
- Implement [Realtime Subscriptions](https://supabase.com/docs/guides/realtime/subscribing-to-database-changes)
- Configure [Branching](https://supabase.com/docs/guides/deployment/branching)
