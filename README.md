# Sample project to demonstrate project mirroring using GitLab CI

If you host your main repository elsewhere and would like to use e.g.
GitLab-CI for testing, you would wish to have an option to mirror your
repository easily with your GitLab-instance. Unfortunately, the mirroring
feature is only integrated natively in the Enterprise Edition of GitLab
so far. One of the ways of setting up automated mirroring also in the Community
Edition is using GitLab-CI for it.

## How does it work

1. Create a new SSH key pair without a passphrase (Example: https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/)
2. Add the public key to your main repository hosting service as well as to GitLab.
3. Add the private key as a **Secret Variable** to your project in GitLab.
4. Add `.gitlab-ci.yml` to your project. Use the one you can find in this repository as an example.
5. Create your project in GitLab and mirror it once manually:

```bash
# Clone your repository
git clone --mirror git@example.com:<user>/<repository>
cd <path_to_your_repo>
# Push it to your GitLab instance
git push --mirror git@gitlab.example.com:<user>/<repository>
```

6. Set up a scheduled build, which runs e.g. every night.

Also have a look here https://docs.gitlab.com/ce/ci/ssh_keys/README.html for information
about how to use SSH keys in GitLab-CI.
