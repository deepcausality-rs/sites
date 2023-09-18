[//]: # (SPDX-License-Identifier: CC-BY-4.0)

# Project website

* Production: [www.deepcausality.com](https://deepcausality.com/)


## Contribute

1) Clone this repository
2) Modify the content as you see fit
3) Create a pull request 
4) Add the 🚀request-deploy label and wait for the CI to build the preview site (~1 minute)
5) Double check the deploy preview URL if your change looks good

## Preview (beta) site

Once you add the 🚀request-deploy label, the following happens:

1) Your fork will be cloned
2) NPM installs all dependencies
3) NPM builds the entire project
4) The site gets uploaded to cloudflare
5) If things are okay, you see a success message with a preview URL

<img src="https://github.com/deepcausality-rs/sites/blob/main/cf_success.png" width="60%" height="60%">

## Stack

* [Hugo](https://gohugo.io/)
* [Dot-Org Hugo Theme](https://github.com/cncf/dot-org-hugo-theme)
* [Cloudflare pages](https://pages.cloudflare.com/)

## Hugo

* [Getting Started](https://gohugo.io/getting-started/quick-start/)

## Cloudflare pages

* [Tutorial](https://www.nickersonj.com/posts/setting-up-hugo/)
* [Git integration (Publish page on push)](https://developers.cloudflare.com/pages/get-started/guide/)
* [Hugo config](https://developers.cloudflare.com/pages/framework-guides/deploy-a-hugo-site/)

## License

All software source code is licensed under the [MIT License](https://opensource.org/license/mit/).

All documentation is distributed under the [Creative Commons Attribution 4.0 International Licence.](https://creativecommons.org/licenses/by/4.0/)

This website uses the [Dot-Org Hugo Theme](https://github.com/cncf/dot-org-hugo-theme) licensed under the [MIT License](https://opensource.org/license/mit/).
