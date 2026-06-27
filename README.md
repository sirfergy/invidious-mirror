# invidious-mirror

Automated, **unmodified** mirror of the official [Invidious](https://github.com/iv-org/invidious)
container image from Quay to Docker Hub, so it can be pulled alongside everything else on Docker Hub.

- **Source image:** `quay.io/invidious/invidious`
- **Mirror:** [`docker.io/sirfergy/invidious`](https://hub.docker.com/r/sirfergy/invidious)
- **Upstream source code:** https://github.com/iv-org/invidious

A scheduled [GitHub Action](.github/workflows/mirror.yml) runs `skopeo copy --all` daily (06:00 UTC) to
keep the mirror in sync, preserving every architecture in the upstream manifest.

## Usage

```
docker pull sirfergy/invidious:latest
```

This is a drop-in replacement for `quay.io/invidious/invidious:latest`.

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
upstream image; all copyright and license notices baked into the image are preserved, and the
corresponding source is available upstream at the link above (satisfying AGPL-3.0 §6).

This is a personal mirror and is **not affiliated with or endorsed by the Invidious project**.
