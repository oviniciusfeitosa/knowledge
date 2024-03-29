# GitlabCI

## Multiline script

```
script:
  - |
    echo \
        a \
        b \
        c
```

**or**

```
script:
  - >
    echo
        a
        b
        c
```

## Code Quality

It is possible to use the source code of the code-climate project to provide one of the tools for code quality for the continuous integration process of Gitlab.

{% code title=".gitlab-ci.yml" %}
```
code_quality:
  stage: codeQuality
  image: docker:stable
  variables:
    DOCKER_DRIVER: overlay2
  allow_failure: true
  services:
    - docker:stable-dind
  script:
    - export SP_VERSION=$(echo "$CI_SERVER_VERSION" | sed 's/^\([0-9]*\)\.\([0-9]*\).*/\1-\2-stable/')
    - docker run 
        --interactive --rm 
        --env CODECLIMATE_CODE="$PWD"
        --volume "$PWD":/code
        --volume /var/run/docker.sock:/var/run/docker.sock
        --volume /tmp/cc:/tmp/cc
        codeclimate/codeclimate analyze -f html > codeclimate.html
  artifacts:
    paths: [codeclimate.html]
  tags:
    - gitlab-runner-tag

```
{% endcode %}
