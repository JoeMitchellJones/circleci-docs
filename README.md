# CircleCI Documentation 

[![CircleCI Build Status](https://circleci.com/gh/circleci/circleci-docs.svg?style=shield)](https://circleci.com/gh/circleci/circleci-docs)
[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/circleci/circleci-docs/master/LICENSE)
[![CircleCi Community](https://img.shields.io/badge/community-CircleCI%20Discuss-343434.svg)](https://discuss.circleci.com)
[![ja translation](https://img.shields.io/badge/dynamic/json?color=blue&label=ja&style=flat&query=%24.progress.0.data.translationProgress&url=https%3A%2F%2Fbadges.awesome-crowdin.com%2Fstats-13528254-306408.json)](https://crowdin.com)

This is the public repository for [CircleCI Docs](https://circleci.com/docs/), a
static website generated by [Jekyll](https://jekyllrb.com/). If you find any
errors in our docs or have suggestions, please follow our [Contributing
Guide](docs/CONTRIBUTING.md) to submit an issue or pull request.

For minor changes like typos, you can click **Suggest an edit to this page**,
located at the bottom of each article. This will take you to the source file on
GitHub, where you can submit a pull request for your change through the UI.

For larger edits or new articles, you'll want to set up a local environment for
editing. Please see our [Local Development
document](./docs/local-development.md) to set that up.

If you have a question or need help debugging, please head to [CircleCI
Discuss](https://discuss.circleci.com/) where our support team will help you
out.

## Documentation Components

This repository houses and manages several arms of documentation for CircleCI.
This section will provide a brief overview of each "component" and how to get 
started with making changes.

### `/Jekyll` - Main Site

This is the main [CircleCI documentation site](https://circleci.com/docs/2.0/).
This is built with Jekyll and houses the majority of our documentation. Other
branches of documentation (`src-api`, `src-crg`, etc) eventually get moved into
this folder (in our build process) and integrated into the Jekyll Site. Follow
the [local development guide](./docs/local-development.md) to get started with
building the Jekyll site.

### `/src-api` - API v1.1 and v2 Build Tooling

Our API documentation source can be found in this folder.

**API v1** is written by hand, and compiled to work with
[Slate](https://github.com/slatedocs/slate). The compilation and deployment of
`v1` is handled by our `.circleci/config.yml`, which calls our `build_api_docs`
script. If you need to make changes to our V1 documentation, go to
`src-api/source/includes` and make changes as needed in the markdown files.

API v2 is compiled from an [OpenAPI
spec](https://github.com/OAI/OpenAPI-Specification). We use
[Redoc](https://github.com/Redocly/redoc) to compile our spec into a webpage. To
see the compilation process, refer to `build_api_docs.sh` and our
`.circleci/config.yml`. If you need to make changes to the output site, you will
likely need to make source code changes to the API, where the docs are generated
from.

This is the build folder we use for automatically generating documentation for
the CircleCI API v2. This uses [Slate](https://github.com/slatedocs/slate) and
[Widdershins](https://github.com/Mermade/widdershins) to create documentation
with a spec (that follows the Open API Spec) generated from the CircleCI code
base.

### `/src-js` - Javascript Files

Some JavaScript files that make use of Webpack  and bundles a Javascript
file that eventually gets loaded into Jekyll. Our JavaScript files are
splintered between Jekyll's assets folder and here. We should be navigating
toward one solution that will eventually aggregate all JS source code in one place.

### `/src-shared` - Shared Assets with circleci.com

This is a *git sub-module* for shared content with the main [CircleCI
website](https://circleci.com/docs/). The `js` folder within is symlinked into
Jekyll's assets folder for JavaScript. Eventually, the JS here could/should be
integrated with a better JS bundle solution per above. Please see the [local
development](./docs/local-development.md) guide for more information about
pulling in the updates for the sub-module.

### Server Documentation

Docs for CircleCI Server Administration are built in a slightly different way;
please refer to the [server build documentation](./docs/server-docs.adoc)
## License Information
Documentation (guides, references, and associated images) is licensed as
Creative Commons Attribution-NonCommercial-ShareAlike CC BY-NC-SA. The full
license can be found
[here](http://creativecommons.org/licenses/by-nc-sa/4.0/legalcode), and the
human-readable summary
[here](http://creativecommons.org/licenses/by-nc-sa/4.0/).

Everything in this repository not covered above is licensed under the [included
MIT license](./docs/licence.md).
