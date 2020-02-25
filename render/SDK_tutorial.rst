SDK Getting Started Tutorial
===============================

.. _header-n4:

1.Configuration parameters that the user needs to pass
-------------------------------------------------------

.. code:: python

   render_para = {
           "domain": "task.renderbus.com",  # Foreign users please use: task.foxrenderbus.com
           "platform": "2",  # platform id
           "access_id": "xxxxxxx",  # user's access_id(required)
           "access_key": "xxxxxxxxx",  # user's access_key(required)
           "local_os": 'windows',
           "workspace": "c:/workspace",  # local root directory of SDK, must be in english
           "render_software": "Houdini",  # CG software（Maya, Houdini, Katana, Clarisse）
           "software_version": "17.5.293",  # CG software version
           "project_name": "Project1",
           "plugin_config": {}  # CG plugins. If none, leave it as {}
      }
   cg_file = r"E:\copy\test02.hip"

**Parameters:**

================ ==== ======== =================================================== ========================
parameter        type required description                                         example
================ ==== ======== =================================================== ========================
domain           str  Y        China user:task.renderbus.com,                        task.renderbus.com
                               Foreign user:task.foxrenderbus.com
platform         str  Y        platform ID, like "2"                               2
access_id        str  Y        user authorization id
access_key       str  Y        user authorization key
workspace        str  Y        SDK working directory(to save configration)         c:\\workspace
local_os         str  Y        os, now support "window" and "linux"                windows
render_software  str  Y        CG software(“Maya", "Clarisse", "Houdini")          Houdini
software_version str  Y        CG software version                                 17.5.293
project_name     str  N        project name                                        Project1
plugin_config    dict N        plugin name                                         {"fumefx":"4.0.5"}
cg_file          str  Y        scene file for rendering                            scene file for rendering
================ ==== ======== =================================================== ========================

--------------

.. _header-n83:

2.Login
--------

.. code:: python

   api = RayvisionAPI(access_id=render_para['access_id'],
                      access_key=render_para['access_key'],
                      domain=render_para['domain'],
                      platform=render_para['platform'])

**return:**

An object of RayvisionAPI that can be used to call other methods

--------------

.. _header-n87:

3.Rendering Environment Setup(plug-in configuration, belonged project, software information verification)
----------------------------------------------------------------------------------------------------------

.. code:: python

   task = RayvisionTask(cg_file=cg_file, **render_para)

**return:**

An object of RayvisionAPI that can be used to call other methods

----------------

.. _header-n92:

4.Analysis and verification
----------------------------

-  Automatically analyze and verify data using SDK

.. code:: python

  RayvisionAnalyse.execute(task)
  RayvisionCheck(task).execute(task.task_info, task.upload_info)

-  Users can use their own files to analyze and verify data

   Refer to `the analysis file detailed configuration <para_configration.html>`__

.. code:: python

  task_info = {}
  upload_info = {}
  RayvisionCheck(task).execute(task_info, upload_info)

--------------

.. _header-n102:

5.Upload
----------

-  Instantiated transfer class

.. code:: python

   transfer_info = {
       'config_bid': api.user_info['config_bid'],
       'input_bid': api.user_info['input_bid'],
       "output_bid": api.user_info["output_bid"],
       "domain": render_para['domain'],
       "platform": render_para['platform'],
       "local_os": render_para['local_os'],
       "user_id": api.user_info['user_id'],
       "local_path": r"C:\workspace",  #  folder to save downloaded files
   }

   # start transfer
   trans = RayvisionTransfer(**transfer_info)

**Parameters:**

========== ==== ===================== ======================================================================== ==================
parameter  type required              description                                                              example
========== ==== ===================== ======================================================================== ==================
config_bid str  Y                     Transfer Configuration ID                                                30201
input_bid  str  Y                     storage ID                                                               10206
output_bid str  Y                     downloading ID                                                           20201
domain     str  Y                     domain name                                                              task.renderbus.com
platform   str  Y                     platform ID                                                              2
local_os   str  Y                     os, now support "window" and "linux"                                     windows
user_id    str  Y                     user account ID                                                          100150764
local_path str  N(upload),Y(download) local path to save downloaded files, could be empty if only upload files C:\\workspace
========== ==== ===================== ======================================================================== ==================

- Start uploading

.. code:: python

   resource_config_file = {
       "task_json_path": task.task_json_path,
       "tips_json_path": task.tips_json_path,
       "asset_json_path": task.asset_json_path,
       "upload_json_path": task.upload_json_path,
   }

   upload = RayvisionUpload(trans)
   upload.upload(task_id=task.task_id, **resource_config_file)

**Parameters:**

==================== ==== ======== ============================ ==========================================
parameter            type required description                  example
==================== ==== ======== ============================ ==========================================
    task_id          str  Y        task ID                      10837135
    task_json_path   str  Y        absolute path of task.json   C:\\workspace\\work\\9458292\\task.json
    tips_json_path   str  Y        absolute path of tips.json   C:\\workspace\\work\\9458292\\tips.json
    asset_json_path  str  Y        absolute path of asset.json  C:\\workspace\\work\\9458292\\asset.json
    upload_json_path str  Y        absolute path of upload.json C:\\workspace\\work\\9458292\\upload.json
==================== ==== ======== ============================ ==========================================

--------------

.. _header-n206:

6.Submit task
---------------

.. code:: python

   task_id = int(task.task_id)
   result = api.submit(task_id)

--------------

.. _header-n209:

7.Download
------------

.. code:: python

   manage_task = RayvisionManageTask(api.query)

   trans.manage_task = manage_task

   download = RayvisionDownload(trans)

   # SDK provide 2 downloading methods:

   # 1).Download after current frame finishes rendering

   download.auto_download([task_id])

   # 2).Download after all frames finish rendering

   download.auto_download_after_task_completed([task_id])
