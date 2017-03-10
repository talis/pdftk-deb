# pdftk-deb

## Requirements

* Docker
* Docker Compose (v 1.9 or greater)

## Usage

pick your distro (currently only trusty) and then ```docker-compose run pdftk```, this will place a debian package in the out directory

## Newer pdftk?

New pdftk release? Simply edit the Dockerfile to point to the newer version ```docker-compose build && docker-compose run pdftk```
