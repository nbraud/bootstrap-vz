Docker
======

The `Docker <https://www.docker.com/>`__ provider creates a docker image
from scratch, creates a Dockerfile for it and imports the image to a repo
specified in the manifest.

In order to reduce the size of the image, it is highly recommend
to make use of the `minimize_size <../../plugins/minimize_size>`__ plugin.
With optimal settings a 64-bit jessie image can be whittled down to 81.95 MB
(built on Dec 13th 2015 with ``manifests/examples/docker/jessie-minimized.yml``).


Manifest settings
-----------------

Name
~~~~

-  ``name``: The image name is the repository and tag to where an
   image should be imported.
   ``required``
   ``manifest vars``


Provider
~~~~~~~~

-  ``dockerfile``: Inline dockerfile that should be appended to
   the one created by the bootstrapper.
   ``optional``

-  ``labels``: Labels that should be added to the dockerfile.
   The image name specified at the top of the manifest
   will be added as the label ``name``.
   Check out the `docker docs <https://docs.docker.com/engine/userguide/labels-custom-metadata/>`__
   for more information about custom labels.
   `Project atomic <http://www.projectatomic.io/>`__
   also has some `useful recommendations <https://github.com/projectatomic/ContainerApplicationGenericLabels>`__
   for generic container labels.
   ``optional``
   ``manifest vars``

Example:

.. code:: yaml

    ---
    name: bootstrap-vz:latest
    provider:
      name: docker
      dockerfile: >
        CMD /bin/bash
      labels:
        name: debian-{system.release}-{system.architecture}-{%y}{%m}{%d}
        description: Debian {system.release} {system.architecture}
