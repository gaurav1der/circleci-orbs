# Anchore CircleCi Orbs [![CircleCI](https://circleci.com/gh/anchore/circleci-orbs/tree/master.svg?style=svg)](https://circleci.com/gh/anchore/circleci-orbs/tree/master)

All orbs are tested with .circleci/config.yaml of this repo. Finished orbs will be published to the public CircleCi orb repository under the anchore namespace.

* Orb testing will be initiated upon pushing to repo
* If orb passes linting & packing it will be published using `@dev:alpha`

After the `@dev:alpha` orb is successfully published, integration tests will be triggered. Once all tests have passed, the dev orb can be promoted to production.

The major, minor, or patch version of the Orb will be published based on version tag pushed to the git repository.
  * Push a git tag with the following naming convention (major|minor|patch)-release-vX.X.X - orb will automatically be published w/ major, minor or patch version depending on what was specified in tag (the actual version in tag is just for reference)
  * Final testing will be performed when this tag is pushed, the publish to production will happen upon manual job approval within the CircleCi WorkFlows UI.
    * For the anchore-engine orb - the `custom_policy_fail` job should always fail, double check that policy evaluation to ensure custom policy was activated. Then go into the failed workflow and approval publish to prod.
