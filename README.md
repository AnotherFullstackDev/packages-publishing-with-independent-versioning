# Publishing steps

1. Bump packages version;
2. Generate changelog;
3. Push changes to the repo;
4. Create a PR with packages release;
5. Do correction to PR if necesarry;
6. Merge the PR into the main branch;
7. Release packages based on the version published to the registry and the ones in the repository;

## Notes

Lerna seems to use tags to identify released/unreleased changes in packages. If the tags creation skipped Lerna will increment version of all the packages it manages. While with tags only packages that have commited changes will be updated.

Command to update packages version. By adding/removing the `--no-git-tag-version` parameter the creation of git tags is controlled.

```bash
npx lerna version --no-push --no-git-tag-version --no-private
```

IMPORTANT! Not sure about the behavior of the publishing in case when a version bump is made but there are additional changed made before the publish command runs.

- With `publish from-package` a package is published even if it got a change after the version bump had been made. That creates a chance of publishing a version with unexpected changes;


Publishing might be done in several ways. The most convenient seems to be the option to publish packages depending on whether the version in the NPM repository or not.

Publishing with synchronization to the registry

```bash
npx lerna publish from-package --no-private
```
