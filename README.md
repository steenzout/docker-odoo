# docker-odoo

[![License](https://img.shields.io/badge/license-LGPL%20v3-blue.svg?style=flat)](https://raw.githubusercontent.com/steenzout/docker-odoo/master/LICENSE)

This repo is a fork from [odoo/docker][odoo/docker].

I had made a PR to enhance this repo and
be able to generate new tags for any release for any point-in-time.

Since it wasn't merged and
I need to be able to build images for snapshots that Odoo doesn't support,
this repo got a life of its own.

In this repo you'll find several bash scripts to help you generate your own [Odoo][odoo] containers.

If you wish to simply use the images I publish,
they can be found [here][hub/steenzout/odoo].

Beware, one difference from [Odoo][odoo]'s docker images is that
each tag is based on a `<odoo version>:base` tag.



[hub/steenzout/odoo]:	https://hub.docker.com/r/steenzout/odoo/	"Odoo docker images by Pedro Salgado"
[odoo]:	https://www.odoo.com	"Odoo"
[odoo/docker]:	https://github.com/odoo/docker	"Odoo docker images by Odoo"
