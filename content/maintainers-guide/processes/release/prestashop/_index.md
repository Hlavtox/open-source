---
title: How to release a new PrestaShop version
menuTitle: Releasing a new PS version
aliases:
  - /maintainers-guide/releasing-prestashop/
---

# How to release a new PrestaShop version

This section describes the release process, step by step. A PrestaShop version release requires all these steps to be completed.

## Prerequisites

To perform a build, you will need the following:

- [Git][git-scm], so you can clone [the project's Git repository][github-repository] on your computer.
- The [PHP CLI][php] executable (within the [compatible version range][compatible-php-versions] of the PrestaShop version you will be building), so you can create a build.
- The [Composer][get-composer] executable, to fetch PHP dependencies.
- The [NodeJs CLI][nodejs] executable (within the [compatible version range][nodejs-requirements]) and NPM, to compile assets.

{{% notice note %}}
Some of steps will require special tools or access rights which are currently not accessible for maintainers outside the PrestaShop Company. A notice indicates when this is the case.
{{% /notice %}}

## Different types of releases

We currently have 4 kind of new releases for PrestaShop:

- security patch releases
- regular patch releases
- minor releases
- major releases

Security patch releases contain security fixes for major security issues. Please read [about them][security-releases].

## Process overview

1. **[Perform preliminary tasks][preliminary-tasks]**: (click to see the full step)

   Short summary:

   - **Update the version number in the Core.**

   - **Make sure the default translation catalogue has been updated and pushed to Crowdin.**  
   _To make any new wordings translatable._

   - **Lock the theme version.**  

   - **Make sure to trigger the release of the Upgrade module if necessary.**  

   - **Perform manual verifications.**  
   _To make sure that the project is ready to be built._

   - **Set up the new version on the PrestaShop Addons Marketplace and update native modules' compatibility.**  
   _To allow the PrestaShop Addons Marketplace and its API to serve modules compatible with this new PrestaShop version._

2. **[Create a new build][create-build]**: (click to see the full step)

   Short summary:

   - **Merge security PRs locally.**  
     _Any security PRs must be merged on a local branch before making them public._

   - **Update the Changelog and Contributors list.**  
     _These files must be included in the build._

   - **Push your work into a build branch.**  
     _Allows the base branch to continue receiving merges while your build is being validated._

   - **Build and store the zip archive.**  
     _The ZIP archive contains the software (including third party dependencies) and compiled assets (Javascript and CSS), but not the development sources, dev dependencies & tests._

   - **Deliver to QA team.**

3. **[Release the version publicly][release-publicly]**: (click to see the full step)

   Short summary:

   - **Merge security PRs on GitHub.**  
     _And publish the security advisories._

   - **Merge the updated Changelog and Contributors list on GitHub.**

   - **Tag the version using Git and publish the release on GitHub.**

   - **Communicate.**

4. **[Final steps][final-steps]**: (click to see the full step)

   Short summary:

   - **Update API stream for 1-click upgrade.**  
     _So that the 1-Click Upgrade (autoupgrade) module becomes aware of the new release._

   - **Create Docker images for the new version.**

   - **Go through the checklist.**  
     _To make sure everything went all right._

   - **Store the ZIP archive.**  
     _To keep track of all published versions._

   - **Improve the process.**

[git-scm]: https://git-scm.com/
[github-repository]: https://github.com/prestashop/prestashop
[php]: https://www.php.net/
[compatible-php-versions]: {{< devdocs "basics/installation/system-requirements.md#php-requirements" >}}
[get-composer]: <https://getcomposer.org/>
[nodejs]: <https://nodejs.org/>
[nodejs-requirements]: {{< devdocs "development/compile-assets.md#requirements" >}}

[preliminary-tasks]: {{< relref "preliminary-tasks.md" >}}
[create-build]: {{< relref "create-build.md" >}}
[release-publicly]: {{< relref "release-publicly.md" >}}
[final-steps]: {{< relref "final-steps.md" >}}
[security-releases]: {{< relref "security.md" >}}
