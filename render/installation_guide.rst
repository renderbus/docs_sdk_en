.. important::
    Make sure local Python environment and PIP are available before use.
   

Installation Guide
====================

**Method One (recommended):**

.. note::
   Users who have limited access to the Python official address network
   can download and install from our custom server。

- Download from Python official pypi (recommended)

   ``pip install rayvision_maya``

   ``pip install rayvision_clarisse``

   ``pip install rayvision_houdini``

- Install from a custom PIP server

   Before using specific rendering modules, such as Houdini rendering,
   please refer to the following installation method to install the modules in turn
   `rayvision_log`, `rayvision_api` , `rayvision_utils` , `rayvision_sync`,

**Method Two:**

Download source code directly from GitHub:

``git clone https://github.com/renderbus/rayvision_log.git``

``git clone https://github.com/renderbus/rayvision_api.git``

``git clone https://github.com/renderbus/rayvision_utils.git``

``git clone https://github.com/renderbus/rayvision_sync.git``

*other modules are installed similarly to the secondary installation method*

**Method Three:**

* Setup IDE for PIP with address: ``https://pip.renderbus.com/simple/``

* Take pycharm as an example:

.. image:: ../_static/image/pycharm配置PIP地址.png

.. image:: ../_static/image/pycharm安装自定义包.png
