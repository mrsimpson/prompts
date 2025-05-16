- If you need to understand what this project is about, check the docs folder
  - The PDD (Product Design Description) is stored in (docs/pdd.md) and describes the functional specification about what we want to develop
  - The target architecture is documented in docs/arc42.md
- After each change in the code,
  - type check the code (by running pm run typecheck in the bash)
  - lint the code (by running npm run lint in the bash)
- After each **major** change in the code, in this order perform
  - type check the code (by running npm run typecheck in the bash)
  - lint the code (by running npm run lint in the bash)
  - run the automated tests (by running npm run test in the bash)
  - run the end-to-end-test (by running npm run test:e2e:fast in the bash)
  - adapt the implementation plan and check the boxes. Don't change anything except the progress ou've been working on unless explicitly requested
  - use the git git_add tool to add the changes to the staging area and the git_commit tool with a message of the following pattern:

  ```text
  > {{The last prompt by the user, if it's already written in an imperative style. Else or if multiple user commands were involved an imperative version of the user's intention}}

  {{A summary of the changes you performed after the last prompt and what was the reasoning behind those changes}}
  ```
