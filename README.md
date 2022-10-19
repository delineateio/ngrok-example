[![PRs Welcome][pr-welcome-shield]][pr-welcome-url]
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]

<!-- PROJECT LOGO -->
<br />
<p align="center">
  <img alt="delineate.io" src="https://github.com/delineateio/.github/blob/master/assets/logo.png?raw=true" height="75" />
  <h2 align="center">delineate.io</h2>
  <p align="center">portray or describe (something) precisely.</p>

  <h3 align="center">Using ngrok Examples</h3>

  <p align="center">
    This repo contains some repeatable examples using ngrok to create secure tunnels to expose local endpoints on the internet
    <br />
    <a href="https://github.com/delineateio/ngrok-example"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/delineateio/ngrok-example/issues">Report Bug</a>
    ·
    <a href="https://github.com/delineateio/ngrok-example/issues">Request Feature</a>
  </p>
</p>

## Table of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [About The Project](#about-the-project)
- [Built With](#built-with)
- [Getting Started](#getting-started)
- [Usage Examples](#usage-examples)
  - [Auth Token for `ngrok`](#auth-token-for-ngrok)
  - [Standard Examples](#standard-examples)
  - [File Examples](#file-examples)
  - [Agent Examples](#agent-examples)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgements](#acknowledgements)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

<!-- ABOUT THE PROJECT -->
## About The Project

This repo was created to experiment with [ngrok](https://dashboard.ngrok.com/) to better understand it's functionality and use cases.  It is not meant to be a replica of the official documentation :laughing:.

## Built With

![pre-commit](https://img.shields.io/badge/precommit-%235835CC.svg?style=for-the-badge&logo=precommit&logoColor=white)
![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)

<!-- GETTING STARTED -->
## Getting Started

This repo follows the principle of minimal manual setup of the local development environment.  A `task` target has been provided for simplicity ```task init```, the `taskfile.yaml` file can be inspected for more details.

<!-- USAGE EXAMPLES -->
## Usage Examples

### Auth Token for `ngrok`

To use `ngrok` you must have a valid authentication token.  If you need to create an account get an auth token you should follow the simple sign up steps at [ngrok.com/signup](https://dashboard.ngrok.com/signup).

Once you have a token it must be added to `.env` using `NGROK_AUTH_TOKEN=[YOUR TOKEN]`.

### Standard Examples

To use the following examples you must first start the simple non-production web server using `task example:web` command, this will start serving a "hello, world!" website on `http://localhost:8000`.

For the `domain` & `oauth` examples you will need to register custom domain on the `ngrok` edge platform follow the instructions at [ngrok domains](https://dashboard.ngrok.com/cloud-edge/domains), as part of this it will be necessary to to setup DNS entries in your domain registrar.

Once this is running you can use the following commands to start an `ngrok` tunnel.

| Example | Task | Description |
| --- | --- | --- |
| basic | `task example:basic` | This example exposes the website running at `localhost:8000` on a non-stable grok generated sub-domain.|
| domain | `task example:domain` | This example exposes the website using a custom pre-owned domain.  See below for more details . |
| oauth | `task example:oauth` | This example exposes the website on a custom domain and secures authentication using an OAuth provider (e.g. Google) |

Once you have finished with each example you can stop the web server using `task example:kill` to stop the web server.

### File Examples

This example shows ngrok being used to run a file server.

| Example | Task | Description |
| --- | --- | --- |
| File | `task example:files` | This example serves the files that are located in [examples/files](examples/files). |

### Agent Examples

`ngrok` can also be run as a background service, this example uses a configuration file [ngrok.yaml](examples/ngrok.yaml) and enables the configured `ngrok` tunnels.  For simplicity this example mirrors the tunnel created using `task example:oauth`.  This is a great way to run multiple tunnels easily.

The ngrok auth token must be written to the config file.  To reduce the risk committing secret with `git` the `ngrok.yaml` file is copied to `ngrok.processed.yaml` and the token added to `ngrok.processed.yaml`, while `ngrok.processed.yaml` is excluded via `.gitignore`.

```shell
# starts the configured tunnels
task example:service:start

# stops the configured tunnels
task example:service:stop
```

> Also note that the above commands will require admin privileges and therefore it's highly likely that you will need to enter your password to complete these tasks.

<!-- ROADMAP -->
## Roadmap

See the [open issues](https://github.com/delineateio/ngrok-example/issues) for a list of proposed features (and known issues).

<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to be learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

If you would like to contribute to any delineate.io OSS projects please read:

* [Code of Conduct](https://github.com/delineateio/.github/blob/master/CODE_OF_CONDUCT.md)
* [Contributing Guidelines](https://github.com/delineateio/.github/blob/master/CONTRIBUTING.md)

<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE` for more information.

<!-- ACKNOWLEDGEMENTS -->
## Acknowledgements

* [Best README Template](https://github.com/othneildrew/Best-README-Template)
* [Markdown Badges](https://github.com/Ileriayo/markdown-badges)
* [DocToc](https://github.com/thlorenz/doctoc)

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->

[pr-welcome-shield]: https://img.shields.io/badge/PRs-welcome-ff69b4.svg?style=for-the-badge&logo=github
[pr-welcome-url]: https://github.com/delineateio/ngrok-example/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue
[contributors-shield]: https://img.shields.io/github/contributors/delineateio/ngrok-example.svg?style=for-the-badge&logo=github
[contributors-url]: https://github.com/delineateio/ngrok-example/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/delineateio/ngrok-example.svg?style=for-the-badge&logo=github
[forks-url]: https://github.com/delineateio/ngrok-example/network/members
[stars-shield]: https://img.shields.io/github/stars/delineateio/ngrok-example.svg?style=for-the-badge&logo=github
[stars-url]: https://github.com/delineateio/ngrok-example/stargazers
[issues-shield]: https://img.shields.io/github/issues/delineateio/ngrok-example.svg?style=for-the-badge&logo=github
[issues-url]: https://github.com/delineateio/ngrok-example/issues
[license-shield]: https://img.shields.io/github/license/delineateio/ngrok-example.svg?style=for-the-badge&logo=github
[license-url]: https://github.com/delineateio/ngrok-example/blob/master/LICENSE
