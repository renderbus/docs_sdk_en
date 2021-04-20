.. _header-n0:

RenderBus at a glance
======================

.. _header-n2:

Overview
------------

   We provide a simple Python rendering SDK to make use of our cloud rendering service easily;
   This official rendering SDK is developed and maintained by RD and TD groups of RENDERBUS;
   This rendering SDK has been tested on python2.7 and python3.6;

.. _header-n5:

Why to use the rendering SDK?
------------------------------

   1. Automation. The SDK automates the process of using the cloud rendering service (analysing scens, uploading assets, rendering, downloading, etc). Users can integrate the modules to there own workflow(such as DeadLine, Qube, etc).

   2. Open source. Users can customize the codes or submit development suggestions.

   3. Cross-version. Python2 and python3 are both supported.

   4. Cross-platform. Windows and Linux are both supported(rayvision_sync only supports Windows and Centos7 and above).

   5. Security. Dynamic signature algorithm authentication (HmacSHA256 + Base64 + UTC timestamp time-limited authentication + random number to prevent replay attacks) adopted, more secure.

   6. Provide a variety of invoking ways. Support local and remote analysis.

   7. Independence. Isolate the API functions, easily expanding.

   8. Complete Documentation.


.. _header-n8:

Supported software
---------------------

- Maya

- Houdini

- Clarisse

- 3ds Max

- Katana

- Arnorld Standalone

- VR Standalone

.. note::
   If the user analyzes the scene by himself, the theory can also support rendering software such as Blender, c4d, Arnold Standalone, and KeyShot.

.. _header-n19:

Preparation
-----------------

1. An account of `FOXRENDERFARM <https://task.foxrenderfarm.com/>`__

2. Apply to use the render SDK from `FOXRENDERFARM Developer Center <https://task.foxrenderfarm.com/user/developer>`__ and get the AccessID and AccessKey

.. _header-n26:

Installation
--------------

Refer to `Installation Guide <installation_guide.html>`_

.. _header-n29:

Get started
-----------------

Refer to `SDK Getting Started Tutorial <SDK_tutorial.html>`_

.. _header-n33:

Parameter setting
-------------------

Refer to `Detailed parameters configuration <para_configration.html>`_

.. _header-n37:

More
----------

`process example <demo/index.html>`_
