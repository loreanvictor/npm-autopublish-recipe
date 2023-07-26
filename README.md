```
┳┓┏┓┳┳┓             ┓ ┓• ┓ 
┃┃┃┃┃┃┃  ┏┓┓┏╋┏┓┏┓┓┏┣┓┃┓┏┣┓
┛┗┣┛┛ ┗  ┗┻┗┻┗┗┛┣┛┗┻┗┛┗┗┛┛┗
                ┛          
```
A [tmplr](https://github.com/loreanvictor/tmplr) recipe to 
add an NPM autopublish Github action. The action will automatically check the
code and publish to NPM when there is a version bump (in `package.json`).

## Usage

This recipe should be used by some other [tmplr recipe](https://github.com/loreanvictor/tmplr):

```yml
# .tmplr.yml
steps:
  # ...

  - use: loreanvictor/npm-autopublish-recipe

  # ...
```

<br>

This recipe requires a few arguments. If not provided, it will prompt the user for them:

- `auto_publish`: Whether to add the workflow or not. A notice should be given to user if they choose to add the workflow, as they need to add a specific environment variable. If passed, then won't ask the user.
- `test_command`: The command to test the code before publishing. Default is `npm test`, but I'd recommend using a command that also checks coverage.
- `lint_command`: The command to check code quality before publishing.

```yml
# .tmplr.yml
use: loreanvictor/npm-autopublish-recipe
with:
  auto_publish: yes
  test_command: npm run coverage
  lint_command: npm run lint
```

<br>

Repositories using this recipe MUST add `NPM_AUTH_TOKEN` secret to allow GitHub to publish to NPM on their behalf.

👉 [How to generate access tokens](https://docs.npmjs.com/creating-and-viewing-access-tokens) \
👉 [How to add secrets for GitHub Actions](https://docs.github.com/en/actions/security-guides/encrypted-secrets)

<br><br>

