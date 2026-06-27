# invidious-mirror

Automated, **unmodified** mirror of the official [Invidious](https://github.com/iv-org/invidious)
container images from Quay (`quay.io/invidious/*`) to Docker Hub (`docker.io/sirfergy/*`), so they can be
pulled alongside everything else on Docker Hub.

A scheduled [GitHub Action](.github/workflows/mirror.yml) runs `skopeo copy --all` daily (06:00 UTC),
mirroring each image's `:latest` tag and preserving every architecture in the upstream manifest.

- **Upstream project & source:** https://github.com/iv-org/invidious

## Mirrored images

Each is a drop-in replacement for its `quay.io/invidious/<name>` counterpart:

| Docker Hub mirror | Source (Quay) |
| --- | --- |
| [`sirfergy/invidious`](https://hub.docker.com/r/sirfergy/invidious) | `quay.io/invidious/invidious` |
| [`sirfergy/invidious-companion`](https://hub.docker.com/r/sirfergy/invidious-companion) | `quay.io/invidious/invidious-companion` |
| [`sirfergy/invidious-redirect`](https://hub.docker.com/r/sirfergy/invidious-redirect) | `quay.io/invidious/invidious-redirect` |
| [`sirfergy/inv-sig-helper`](https://hub.docker.com/r/sirfergy/inv-sig-helper) | `quay.io/invidious/inv-sig-helper` |
| [`sirfergy/youtube-trusted-session-generator`](https://hub.docker.com/r/sirfergy/youtube-trusted-session-generator) | `quay.io/invidious/youtube-trusted-session-generator` |
| [`sirfergy/smart-ipv6-rotator`](https://hub.docker.com/r/sirfergy/smart-ipv6-rotator) | `quay.io/invidious/smart-ipv6-rotator` |
| [`sirfergy/lsquic-compiled`](https://hub.docker.com/r/sirfergy/lsquic-compiled) | `quay.io/invidious/lsquic-compiled` |
| [`sirfergy/instances`](https://hub.docker.com/r/sirfergy/instances) | `quay.io/invidious/instances` |
| [`sirfergy/invidious.io`](https://hub.docker.com/r/sirfergy/invidious.io) | `quay.io/invidious/invidious.io` |
| [`sirfergy/docs.invidious.io`](https://hub.docker.com/r/sirfergy/docs.invidious.io) | `quay.io/invidious/docs.invidious.io` |

```
docker pull sirfergy/invidious:latest
```

To add or remove images, edit the `REPOS` list in [.github/workflows/mirror.yml](.github/workflows/mirror.yml).

## Manual run

Trigger the **Mirror Invidious to Docker Hub** workflow from the Actions tab, or:

```
gh workflow run mirror.yml -R sirfergy/invidious-mirror
```

## Setup

One secret is required:

```
gh secret set DOCKERHUB_TOKEN -R sirfergy/invidious-mirror
```

Use a Docker Hub **access token** (Account Settings → Personal access tokens) with Read/Write/Delete
scope — not your account password.

## License & attribution

Invidious is licensed under the **GNU AGPL-3.0**. This repository only re-publishes the *unmodified*
upstream images; all copyright and license notices baked into the images are preserved, and the
corresponding source is available upstream at the link above (satisfying AGPL-3.0 §6).

This is a personal mirror and is **not affiliated with or endorsed by the Invidious project**.
