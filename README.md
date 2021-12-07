# gh-action-triggers-circleci [![cron](https://github.com/bahmutov/gh-action-triggers-circleci/actions/workflows/cron.yml/badge.svg?branch=main)](https://github.com/bahmutov/gh-action-triggers-circleci/actions/workflows/cron.yml)
> Example GH Action that periodically triggers the CircleCI Pipeline that uses context variables

By default the scheduled CircleCI workflows cannot use security contexts, [bug](https://circleci.canny.io/cloud-feature-requests/p/allow-restricted-contexts-within-scheduled-workflows). Which is very frustrating. As a workaround, this repo uses GH Actions to trigger the pipelines periodically.

The GH Action [.github/workflows/cron.yml](./.github/workflows/cron.yml) runs periodically and triggers the CircleCI pipeline in [.circleci/config.yml](./.circleci/config.yml) using the [trigger-circleci-pipeline](https://github.com/bahmutov/trigger-circleci-pipeline) utility. The trigger uses the `CIRCLE_CI_API_TOKEN` token to know which user is the "author" of the cron job, thus the CircleCI pipeline can use the [security context](https://circleci.com/docs/2.0/contexts/) variables.
