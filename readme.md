# Resume and Portfolio
[![build-and-publish](https://github.com/conceptualshark/conceptualshark.github.io/actions/workflows/publish.yml/badge.svg)](https://github.com/conceptualshark/conceptualshark.github.io/actions/workflows/publish.yml) [![pages-build-deployment](https://github.com/conceptualshark/conceptualshark.github.io/actions/workflows/pages/pages-build-deployment/badge.svg)](https://github.com/conceptualshark/conceptualshark.github.io/actions/workflows/pages/pages-build-deployment) ![Built with Markdown](https://img.shields.io/badge/Markdown-blue) ![Built with Mkdocs](https://img.shields.io/badge/Mkdocs-red)

## :zap: About
I am a technical and UX writer with a background in software engineering and project management. This repository serves as a home for my portfolio and resume, and can be viewed live at [https://conceptualshark.github.io/](https://conceptualshark.github.io/). 

This project is built using [Material for Mkdocs](https://squidfunk.github.io/mkdocs-material/), a static site generator. Pages are written in Markdown, customized using the Mkdocs configuration file and CSS overrides, and published using [Github Pages](https://pages.github.com/).

## :rocket: Deployment

### Requirements
- [Docker](https://www.docker.com/) (20.10.11+)

### Clone and deploy
To deploy this project on your own, first clone the repository:
```
git clone https://github.com/conceptualshark/conceptualshark.github.io.git
```
Ensure Docker is running. From the root directory of the cloned project, run the following command:

```
docker run --rm -it -p 8000:8000 -v ${PWD}:/docs squidfunk/mkdocs-material
```

Docker will serve the site at [localhost:8000](localhost:8000). 

## :books: Learn more
Find out more about my work on [LinkedIn](https://www.linkedin.com/in/cole-isaac/).

To build a similar site of your own, check out the [Mkdocs guides](https://squidfunk.github.io/mkdocs-material/getting-started/), or learn how to get started with [Github Pages](https://pages.github.com/).
