This is a demo repo for a weird Check Run behavior.

### 1. Bad case - Check run manually created for a commit pushed with GITHUB_TOKEN does not trigger `check_run` event

Steps to reproduce:

1. Run [commit-push](https://github.com/kyanny-corp-enterprise-cloud-testing/zd-3456357-check-run/actions/workflows/commit-push.yml) workflow. It creates a new commit and push it to the `main`. GITHUB_TOKEN is used.
2. Run [create-check-run](https://github.com/kyanny-corp-enterprise-cloud-testing/zd-3456357-check-run/actions/workflows/create-check-run.yml) workflow. It creates a check run for the HEAD commit. GitHub App installation token is used.
3. Check [Actions](https://github.com/kyanny-corp-enterprise-cloud-testing/zd-3456357-check-run/actions) tab. You don't see [pong](https://github.com/kyanny-corp-enterprise-cloud-testing/zd-3456357-check-run/actions/workflows/pong.yml) workflow ran. Pong workflow listens `check_run` trigger.

### 2. Good case - Check run manually created for a commit pushed without GITHUB_TOKEN triggers `check_run` event

1. Commit and push through the web browser or Git client. Make sure you use credentials other than GITHUB_TOKEN.
2. Run [create-check-run](https://github.com/kyanny-corp-enterprise-cloud-testing/zd-3456357-check-run/actions/workflows/create-check-run.yml) workflow. It creates a check run for the HEAD commit. GitHub App installation token is used.
3. [Actions](https://github.com/kyanny-corp-enterprise-cloud-testing/zd-3456357-check-run/actions) tab. You will see [pong](https://github.com/kyanny-corp-enterprise-cloud-testing/zd-3456357-check-run/actions/workflows/pong.yml) workflow ran. Pong workflow listens `check_run` trigger.
