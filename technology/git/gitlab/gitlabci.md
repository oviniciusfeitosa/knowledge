# GitlabCI

## Multiline script

```text
script:
  - |
    echo \
        a \
        b \
        c
```

**or**

```text
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
```text
code_quality:
  image: docker:stable
  variables:
    DOCKER_DRIVER: overlay2
  allow_failure: true
  services:
    - docker:stable-dind
  script:
    - export SP_VERSION=$(echo "$CI_SERVER_VERSION" | sed 's/^\([0-9]*\)\.\([0-9]*\).*/\1-\2-stable/')
    - docker run
        --env SOURCE_CODE="$PWD"
        --volume "$PWD":/code
        --volume /var/run/docker.sock:/var/run/docker.sock
        "registry.gitlab.com/gitlab-org/security-products/codequality:$SP_VERSION" /code
  artifacts:
    paths: [gl-code-quality-report.json]

```
{% endcode %}

