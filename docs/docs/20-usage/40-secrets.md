# Secrets

Woodpecker provides the ability to store named parameters external to the YAML configuration file, in a central secret store. These secrets can be passed to individual steps of the pipeline at runtime.

Secrets are exposed to your pipeline steps and plugins as uppercase environment variables and can therefore be referenced in the commands section of your pipeline.

Woodpecker provides three different levels to add secrets to your pipeline. The following list shows the priority of the different levels. If a secret is defined in multiple levels, will be used following this priorities: Repository secrets > Organization secrets > Global secrets.

1. **Repository secrets**: They are available to all pipelines of an repository.
2. **Organization secrets**: They are available to all pipelines of an organization.
3. **Global secrets**: Can be configured by an instance admin.
   They are available to all pipelines of the **whole** Woodpecker instance and should therefore **only** be used for secrets that are allowed to be read by **all** users.

## Usage

```diff
steps:
  docker:
    image: docker
    commands:
+     - echo $DOCKER_USERNAME
+     - echo $DOCKER_PASSWORD
+   secrets: [ docker_username, docker_password ]
```

Alternatively, you can get a `setting` from secrets using the `from_secret` syntax.
In this example, the secret named `secret_token` would be passed to the pipeline as `PLUGIN_TOKEN`.

**NOTE:** the `from_secret` syntax only works with the newer `settings` block.

```diff
steps:
  docker:
    image: my-plugin
    settings:
+     token:
+       from_secret: secret_token
```


Please note parameter expressions are subject to pre-processing. When using secrets in parameter expressions they should be escaped.

```diff
steps:
  docker:
    image: docker
    commands:
-     - echo ${DOCKER_USERNAME}
-     - echo ${DOCKER_PASSWORD}
+     - echo $${DOCKER_USERNAME}
+     - echo $${DOCKER_PASSWORD}
    secrets: [ docker_username, docker_password ]
```

## Adding Secrets

Secrets are added to the Woodpecker in the UI or with the CLI.

## Alternate Names

There may be scenarios where you are required to store secrets using alternate names. You can map the alternate secret name to the expected name using the below syntax:

```diff
steps:
  docker:
    image: plugins/docker
    repo: octocat/hello-world
    tags: latest
+   secrets:
+     - source: docker_prod_password
+       target: docker_password
```

## Pull Requests

Secrets are not exposed to pull requests by default. You can override this behavior by creating the secret and enabling the `pull_request` event type.

```diff
woodpecker-cli secret add \
  -repository octocat/hello-world \
  -image plugins/docker \
+ -event pull_request \
+ -event push \
+ -event tag \
  -name docker_username \
  -value <value>
```

Please be careful when exposing secrets to pull requests. If your repository is open source and accepts pull requests your secrets are not safe. A bad actor can submit a malicious pull request that exposes your secrets.

## Image filter

To prevent abusing your secrets with malicious pull requests, you can limit a secret to a list of images. They are not available to any other container. In addition, you can make the secret available only for plugins (steps without user-defined commands).

:::warning
If you enable the option "Only available for plugins", always set an image filter too. Otherwise, the secret can be accessed by a very simple self-developed plugin and is thus *not* safe.
If you only set an image filter, you could still access the secret using the same image and by specifying a command that prints it.
:::

## CLI Examples

Create the secret using default settings. The secret will be available to all images in your pipeline, and will be available to all push, tag, and deployment events (not pull request events).

```diff
woodpecker-cli secret add \
  -repository octocat/hello-world \
  -name aws_access_key_id \
  -value <value>
```

Create the secret and limit to a single image:

```diff
woodpecker-cli secret add \
  -repository octocat/hello-world \
+ -image plugins/s3 \
  -name aws_access_key_id \
  -value <value>
```

Create the secrets and limit to a set of images:

```diff
woodpecker-cli secret add \
  -repository octocat/hello-world \
+ -image plugins/s3 \
+ -image peloton/woodpecker-ecs \
  -name aws_access_key_id \
  -value <value>
```

Create the secret and enable for multiple hook events:

```diff
woodpecker-cli secret add \
  -repository octocat/hello-world \
  -image plugins/s3 \
+ -event pull_request \
+ -event push \
+ -event tag \
  -name aws_access_key_id \
  -value <value>
```

Loading secrets from file using curl `@` syntax. This is the recommended approach for loading secrets from file to preserve newlines:

```diff
woodpecker-cli secret add \
  -repository octocat/hello-world \
  -name ssh_key \
+ -value @/root/ssh/id_rsa
```
