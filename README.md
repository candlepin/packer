candlepin packer files
======================

This repo contains packer configs for building vagrant images for candlepin, subscription-manager, and related projects.

The centos kickstarts are based on those used for official CentOS vagrant images: https://github.com/CentOS/sig-cloud-instance-build

Building the Images
-------------------

Prerequisites:

 - Install packer from packer.io
 - Install ansible
 - Have a [vagrantcloud](https://app.vagrantup.com/) account that is linked to the [candlepin org](https://app.vagrantup.com/candlepin)
 - Set the environment variable `VAGRANT_CLOUD_TOKEN` to a token for your vagrantcloud account

```bash
ansible-galaxy install -r requirements.yml
packer build -force subman-centos7.json  # or other json files in this repo.
```

Notes:

 - Since `packer` is a common binary name (binary with the same name provided by the cracklib-dist package), you may need to use the full path to `packer` or adjust your `PATH`.
 - You can comment out the post-processor that uploads to vagrant-cloud if you just want to build the images locally.

See also:

 * https://github.com/candlepin/candlepin-jobs/blob/a2613632b9888404bde8b2ae701e55d8446752b7/jobs/submanVagrantUpstreamImagesJob.groovy
 * https://github.com/candlepin/candlepin-jobs/blob/a2613632b9888404bde8b2ae701e55d8446752b7/resources/subman-vagrant-images.sh

Build Details
-------------

Packer will download an installer ISO, provision it first with a kickstart to configure as a base vagrant image, and then apply appropriate ansible roles.

Future
------

We'll add more packer configs over time.
