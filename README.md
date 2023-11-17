# ansible-podman-play-host

This was an interesting experiment on how `podman` and `systemd` could be used in tandem with `ansible` to completely replace
`docker-compose`.

In the end, I found [what I've tried here](https://codeberg.org/fourstepper/ansible-podman-containers/src/branch/main/tasks/containers.yml) unsuitable, due to the following issues:

- applications from the internet often come pre-packages as `docker-compose` files - rewriting them into a custom format is quite a burden
- trying to take advantage of rootless podman seems a bit futile in this case
  - we still have to manage stuff centrally and holistically, thus connect over root
  - I am a single tenant - perhaps if one was to set up an actual multi-tenant podman host, maybe with a central proxy like `traefik`, rootless podman would become way more useful
    - at the same time, the setup complexity and adoption complexity would start nearing running and offering something like `k0s` with some OpenID connect integration
