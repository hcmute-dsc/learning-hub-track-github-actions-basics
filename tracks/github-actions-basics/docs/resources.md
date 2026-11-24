## Tài liệu chính thức của GitHub Actions

- [GitHub Actions documentation](https://docs.github.com/en/actions): trang gốc, đọc mục "Get started" nếu muốn ôn lại chương 1.
- [Understanding GitHub Actions](https://docs.github.com/en/actions/get-started/understand-github-actions): event, workflow, job, step, runner (chương 1).
- [Workflow syntax](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax): tra cứu mọi khóa trong file workflow.
- [Events that trigger workflows](https://docs.github.com/en/actions/reference/workflows-and-actions/events-that-trigger-workflows): mọi event, kể cả `pull_request` và `pull_request_target`.
- [Contexts reference](https://docs.github.com/en/actions/reference/workflows-and-actions/contexts) và [Expressions](https://docs.github.com/en/actions/reference/workflows-and-actions/expressions): `github`, `env`, `vars`, `secrets`, `matrix`, `hashFiles`, `always()`.

## Theo chương

- Chương 2: [Using custom workflows with GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages); công cụ kiểm tra link [lychee](https://github.com/lycheeverse/lychee) và [lychee-action](https://github.com/lycheeverse/lychee-action).
- Chương 3: [Building and testing Node.js](https://docs.github.com/en/actions/tutorials/build-and-test-code/nodejs); [About rulesets](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets); [Node.js test runner](https://nodejs.org/api/test.html).
- Chương 4: [Variables](https://docs.github.com/en/actions/how-tos/write-workflows/choose-what-workflows-do/use-variables); [Using secrets in GitHub Actions](https://docs.github.com/en/actions/how-tos/write-workflows/choose-what-workflows-do/use-secrets); [Managing environments for deployment](https://docs.github.com/en/actions/how-tos/deploy/configure-and-manage-deployments/manage-environments).
- Chương 5: [Running variations of jobs (matrix)](https://docs.github.com/en/actions/how-tos/write-workflows/choose-what-workflows-do/run-job-variations); [Dependency caching](https://docs.github.com/en/actions/reference/workflows-and-actions/dependency-caching); [Storing workflow data as artifacts](https://docs.github.com/en/actions/tutorials/store-and-share-data); [actions/cache](https://github.com/actions/cache), [actions/upload-artifact](https://github.com/actions/upload-artifact), [actions/download-artifact](https://github.com/actions/download-artifact).
- Chương 6: [Reusing workflows](https://docs.github.com/en/actions/how-tos/reuse-automations/reuse-workflows); [Creating a composite action](https://docs.github.com/en/actions/tutorials/create-actions/create-a-composite-action); [Keeping your actions up to date with Dependabot](https://docs.github.com/en/code-security/dependabot/working-with-dependabot/keeping-your-actions-up-to-date-with-dependabot).
- Chương 7: [Secure use reference](https://docs.github.com/en/actions/reference/security/secure-use) (permissions, secret, script injection, ghim SHA); [GITHUB_TOKEN](https://docs.github.com/en/actions/concepts/security/github_token); [Script injections](https://docs.github.com/en/actions/concepts/security/script-injections).

## Công cụ

- [actionlint](https://github.com/rhysd/actionlint): kiểm tra file workflow trên máy, bắt cả một số lỗi bảo mật.
- [zizmor](https://github.com/zizmorcore/zizmor): công cụ quét lỗi bảo mật chuyên cho GitHub Actions, cho ai muốn đi sâu hơn chương 7.
- [Extension GitHub Actions cho VS Code](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-github-actions).

## Đọc thêm về bảo mật

- [GitHub Advisory GHSA-mrrh-fwg8-r2c3](https://github.com/advisories/GHSA-mrrh-fwg8-r2c3): vụ `tj-actions/changed-files` năm 2025 nhắc ở chương 6.
- [Keeping your GitHub Actions and workflows secure: Preventing pwn requests](https://securitylab.github.com/resources/github-actions-preventing-pwn-requests/) của GitHub Security Lab (chương 7).

## Track liên quan

- [GitHub Actions và Docker: từ portfolio đến pipeline](https://learn.hcmute-dsc.io.vn/tracks/actions-docker): chương 1–2 và phần bảo mật của track này lấy từ đó; track kia đi tiếp sang Docker, Docker Compose và đẩy image lên GHCR.
- [Tự động hoá với Discord](https://learn.hcmute-dsc.io.vn/tracks/discord-webhook-automation): dùng secrets và workflow chạy theo lịch để gửi tin vào Discord.
