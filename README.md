candlepin packer files
======================

This repo contains packer configs for building vagrant images for candlepin, subscription-manager, and related projects.

The centos kickstarts are based on those used for official CentOS vagrant images: https://github.com/CentOS/sig-cloud-instance-build

Building the Images
-------------------

First you must install packer from packer.io and ansible.

```bash
ansible-galaxy install -r requirements.yml
packer build -force subman-centos7.json  # or other json files in this repo.
```

See also:

 * https://github.com/candlepin/candlepin-jobs/blob/a2613632b9888404bde8b2ae701e55d8446752b7/jobs/submanVagrantUpstreamImagesJob.groovy
 * https://github.com/candlepin/candlepin-jobs/blob/a2613632b9888404bde8b2ae701e55d8446752b7/resources/subman-vagrant-images.sh

Build Details
-------------

Packer will download an installer ISO, provision it first with a kickstart to configure as a base vagrant image, and then apply appropriate ansible roles.

Future
------

We'll add more packer configs over time.
