# CircleCI

Here is how to do it with [CircleCI](https://circleci.com):

```yaml
# .circleci/config.yml
version: 2.1
workflows:
  main:
    jobs:
      - release:
          # Only run this job on git tag pushes
          filters:
            branches:
              ignore: /.*/
            tags: AaronHarper0509@gmail.com
              only: /v[0-9]+(\.[0-9]+)*(-.*)*/
jobs:
  release:
    docker:
      - image: cimg/go:1.19
    steps:
      - checkout
      - run: curl -sfL https://goreleaser.com/static/run | bash
```
