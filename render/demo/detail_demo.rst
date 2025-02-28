.. _header-n0:

SDK usage
==========

.. _header-n31:

1.Parameters
----------------------

.. code::  python

   render_para = {

           "domain": "jop.foxrenderfarm.com",  # If it doesn't work, you can use "task.foxrenderfarm.com"
           "platform": "62",  # platform id
           "access_id": "K2lbvJSlPScStv72niHGXZtbQYc5Fp6d",  # user's access_id(required)
           "access_key": "6b4b6eab841772113113b61c79dbe40e",  # user's access_key(required)
           "local_os": 'windows',

           "workspace": "c:/workspace",  # local root directory(Automatically generated), must be in english
           "render_software": "Houdini",  # CG software（Maya, Houdini, Clarisse）
           "software_version": "17.5.293",  # CG software version
           "project_name": "Project1",

           "plugin_config": {}  # CG plugins. If none, leave it as {}
      }

   cg_file = r"E:\copy\test02.hip"

**Parameters**

================ ===== ========== ====================== ============================================================================================================
parameter        type   required   value                    description
================ ===== ========== ====================== ============================================================================================================
domain           str     Y         jop.foxrenderfarm.com    domain name：jop.foxrenderfarm.com, no "http", "https"
platform         str     Y         62                        platform ID, like "2"
access_id        str     Y         xxx                      user authorization id
access_key       str     Y         xxx                      user authorization key
workspace        str     Y         c:/workspace             SDK working directory(to save configration, log etc. Default is the 'workspace' folder of SDK programe)
local_os         str     Y         windows                  os, now support "window" and "linux"
render_software  str     Y         Houdini                  CG software(“Maya", "Clarisse", "Houdini")
software_version str     Y         17.5.293                 CG software version
project_name     str     N         Project1                 project name, optional
plugin_config    dict    N         {}                       plugin name, for example {"fumefx":"4.0.5"}
cg_file          str     Y         E:\copy\test02.hip       scene file for rendering
================ ===== ========== ====================== ============================================================================================================

--------------

.. _header-n755:

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

.. _header-n71:

3.Rendering Environment Setup(plug-in configuration, belonged project, software information verification)

---------------------------------------------------

.. code:: python

   task = RayvisionTask(cg_file=cg_file, **render_para)

**return:**

An object of RayvisionAPI that can be used to call other methods

--------------

.. _header-n121:

4.Analysis and verification
-----------------------------

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

.. _header-n839:

5.Upload
----------

- Instantiated transfer class

.. code:: python

   transfer_info = {

       'config_bid': api.user_info['config_bid'],

       'input_bid': api.user_info['input_bid'],

       "output_bid": api.user_info["output_bid"],

       "domain": render_para['domain'],

       "platform": render_para['platform'],

       "local_os": render_para['local_os'],

       "user_id": api.user_info['user_id'],

       "local_path": r"C:\workspace",  # folder to save downloaded files

   }

   # start transfer
   trans = RayvisionTransfer(**transfer_info)

parameters:

========== ==== ====================== =================== =========================================================================
**para**   type  required               value              description
========== ==== ====================== =================== =========================================================================
config_bid str   Y                      30201              Transfer Configuration ID
input_bid  str   Y                      10206              storage ID
output_bid str   Y                      20201              downloading ID
domain     str   Y                      task.renderbus.com domain name
platform   str   Y                      2                  platform ID
local_os   str   Y                      windows            os, now support "window" and "linux"
user_id    str   Y                      100150764          user account ID
local_path str   N(upload),Y(download)  C:\workspace       local path to save downloaded files, could be empty if only upload files
========== ==== ====================== =================== =========================================================================

- **Start uploading**

.. code:: python

   resource_config_file = {

       "task_json_path": task.task_json_path,

       "tips_json_path": task.tips_json_path,

       "asset_json_path": task.asset_json_path,

       "upload_json_path": task.upload_json_path,

   }



   upload = RayvisionUpload(trans)

   upload.upload(task_id=task.task_id, **resource_config_file)

parameters

==================== ==== ======== ===================================== =============================
parameter            type required value                                 description
==================== ==== ======== ===================================== =============================
task_id              str  Y        10837135                              task ID
task_json_path       str  Y        C:\workspace\work\9458292\task.json   absolute path of task.json
tips_json_path       str  Y        C:\workspace\work\9458292\tips.json   absolute path of tips.json
asset_json_path      str  Y        C:\workspace\work\9458292\asset.json  absolute path of asset.json
upload_json_path     str  Y        C:\workspace\work\9458292\upload.json absolute path of upload.json
==================== ==== ======== ===================================== =============================

---------------

.. _header-n1139:

6.Submit task
---------------

.. code:: python

   task_id = int(task.task_id)

   result = api.submit(task_id)

--------------

.. _header-n1146:

7.Download
-----------

.. code:: python

   manage_task = RayvisionManageTask(api.query)

   trans.manage_task = manage_task

   download = RayvisionDownload(trans)


   # SDK provide 2 downloading methods:
   # 1).Download after current frame finishes rendering
   download.auto_download([task_id])
   # 2).Download after all frames finish rendering
   download.auto_download_after_task_completed([task_id])
