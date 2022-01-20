Developer Notes
===============

Release Checklist
-----------------

Perform the following tasks for every release:

  - Update version in README.md.
  - Update version in package.json.
  - Update copyright notice in LICENSE.md.
  - Update CHANGES.md.
  - Update minified script.

        npm run min

  - Stage changes.

        git status
        git add -p

  - Commit changes for new version.

        VERSION=<VERSION>
        git commit -em "Set version to $VERSION"
        git push

  - Update README.md with new screenshots.

  - Commit README.md

        VERSION=<VERSION>
        git commit -em "Add screenshots for version $VERSION"

  - Tag the release.

        VERSION=<VERSION>
        git tag $VERSION -m "SPCSS $VERSION"
        git push origin master $VERSION

  - Publish package.

        npm login
        npm publish


Post-Release Checklist
----------------------

Perform the following tasks after every release:

  - Update version in package.json to the next dev version (`X.Y.Z-dev` format).

  - Commit.

        git add -p
        git status

        VERSION=$(sed -n 's/.*version.*: "\(.*\)",/\1/p' package.json)
        echo VERSION: $VERSION

        git commit -em "Set version to $VERSION"
        git push origin master
