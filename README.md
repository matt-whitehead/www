# www
This repository powers my personal website: [matt-whitehead.com](https://www.matt-whitehead.com).

It is based on the [Identity](https://html5up.net/identity) template provided by HTML5 UP under the [Creative Commons Attribution 3.0 License](https://creativecommons.org/licenses/by/3.0/). The site serves as merely a landing page for now, but I hope to expand it in the future. 

The main purpose of the site is to dive into Continuious Deployment. This repo powers an [AWS Amplify](https://aws.amazon.com/amplify/) workflow. Commits to the prod branch automatically trigger a build and deploy workflow which pushes changes live to [CloudFront](https://aws.amazon.com/cloudfront/) within minutes.

A pretty fun little side project and a nice intro to CI/CD :)

## Continuous Deployment Workflow
The pipeline from GitHub to prod looks something like this:

1. Commits are pushed to the prod branch
2. AWS detects the changes and launches a docker container with the build enviornment (I'm using the default one)
3. The docker container reads **amplify.yml** and builds the site
4. Automated tests are run after the build succeeds
5. The site is deployed to CloudFront after the tests pass
6. AWS renders the site on a bunch of devices and takes screenshots as a final validation. (This doesn't work well at the moment because it takes the screenshots before the site has a chance to load fully.)
