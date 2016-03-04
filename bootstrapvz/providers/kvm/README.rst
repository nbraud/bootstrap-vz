KVM
---

The `KVM <http://www.linux-kvm.org/page/Main_Page>`__ provider creates
virtual images for Linux Kernel-based Virtual Machines. It supports the
installation of `virtio kernel
modules <http://www.linux-kvm.org/page/Virtio>`__ (paravirtualized
drivers for IO operations).

Manifest settings
-----------------

Provider
~~~~~~~~

-  ``virtio``: Specifies which virtio kernel modules to install.
   ``optional``

Example:

.. code-block:: yaml

    ---
    provider:
      name: kvm
      virtio:
        - virtio_blk
        - virtio_net
