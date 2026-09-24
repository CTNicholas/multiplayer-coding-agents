https://github.com/user-attachments/assets/8f1d8567-f9fb-41bb-a6a0-b2ff98a13f25

## Multiplayer coding agents

This demo shows you how to implement a multiplayer coding agent tool, with [Liveblocks](https://liveblocks.io/).

- **Shared chats**: Each chat is a multiplayer Liveblocks Feed.
- **Queue and merge**: Messages posted while the agent is busy are queued and handled as a follow-up.
- **Jev triage**: TypeSafe AI chooses whether a response to each message is needed—a coding agent, or just a regular AI.
- **Quick answers**: Questions are answered with read-only tools to browse the repository.
- **Coding sessions**: A Cursor agent commits, pushes, and opens a pull request of requested changes.
- **Changes and PR tabs**: Side panel shows the PR's diff rendered with `@pierre/diffs`.
- **Multiplayer documents**: Write Markdown documents as well as code, and edit them in a multiplayer markdown editor.
- **Skills**: Place skils into the `/skills` folder, load them with `/`.
- **Notifications**: Participants receieve a notification when the agent has completed coding.
- **Access control**: Members of your GitHub organization, and users on the allow-list, can talk to the agent.

### Set up

- Install all dependencies with `npm install`
- Create an account on [liveblocks.io](https://liveblocks.io/dashboard)
- Copy your **secret** key from the
  [dashboard](https://liveblocks.io/dashboard/apikeys)
- Create an `.env.local` file at the root (see `.env.example`) and add your
  **secret** key as the `LIVEBLOCKS_SECRET_KEY` environment variable
- Create a Cursor API key in the
  [Cursor dashboard](https://cursor.com/dashboard) and add it as
  `CURSOR_API_KEY` (use a team **service account** key so runs aren't tied to
  one person)
- In the Cursor dashboard, connect GitHub under **Integrations** and grant the
  Cursor GitHub App access to the repositories your team will work on
- Create a [GitHub OAuth App](https://github.com/settings/developers) with the
  callback URL `http://localhost:3000/api/auth/callback/github`, and add its
  client id and secret as `AUTH_GITHUB_ID` and `AUTH_GITHUB_SECRET`
- Set `AUTH_SECRET` to a random string (`openssl rand -base64 32`)
- Set `GITHUB_ALLOWED_ORG` to your GitHub organization, or list logins in
  `GITHUB_ALLOWED_USERS`; leave both empty locally to let anyone who signs in
  take part
- Create an account on [vercel.com](https://vercel.com)
- Copy your **AI gateway key** from the
  [dashboard](https://vercel.com/ai-gateway) into the `AI_GATEWAY_API_KEY`
  environment variable (this enables Jev triage and quick answers; without it,
  every message goes to the coding agent)
- Optionally set `GITHUB_TOKEN` to a read-only fine-grained token so private
  repositories' branches and files can be read, `CURSOR_MODEL` to change the
  default model, or `NEXT_PUBLIC_LOCKED_REPO` to pin every chat to one
  repository
- Run `npm run dev` and go to [http://localhost:3000](http://localhost:3000)
