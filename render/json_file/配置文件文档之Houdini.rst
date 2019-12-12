.. _header-n0:

Houdini
====================

Analyze houdini scene and save the output as task.json, asset.json,
upload.json and tips.json.

.. _header-n6:

1.task.json
---------------

File to save the analysis result of the scene, including scene name, cg software version, render settings, etc.

**task.json example**

.. code:: json

   {
       "scene_info_render": {
           "rop_node": [
               {
                   "node": "/out/mantra1",
                   "frames": "1-10[1]",
                   "option": "-1",
                   "render": "1"
               }
           ],
           "geo_node": []
       },
       "task_info": {
           "is_layer_rendering": "1",
           "cg_id": "2004",
           "ram": "64",
           "os_name": "1",
           "render_layer_type": "0",
           "is_distribute_render": "0",
           "input_cg_file": "D:/gitlab/renderSDK/scenes/houdini_test/sphere.hip",
           "job_stop_time": "28800",
           "user_id": "10000031",
           "pre_frames": "000",
           "platform": "2",
           "is_picture": "0",
           "project_id": "3316",
           "channel": "4",
           "tiles_type": "block",
           "tiles": "1",
           "project_name": "dasdd",
           "distribute_render_node": "3",
           "frames_per_task": "1",
           "stop_after_test": "2",
           "input_project_path": "",
           "task_id": "440149",
           "task_stop_time": "86400",
           "time_out": "12"
       },
       "software_config": {
           "cg_version": "16.5.268",
           "cg_name": "Houdini",
           "plugins": {}
       }
   }

**task.json parameters**

===================== ====== ==================================================== ====================================================
parameter             type   description                                           example
===================== ====== ==================================================== ====================================================
software_config       object environment(cg software, version and plugins, etc.)  refer to `software_config <配置文件文档之Houdini.html#header-n341>`_
task_info             object render settings(priority frames, render range, etc.) refer to `task_info <配置文件文档之Houdini.html#header-n340>`_
scene_info_render     object analysis result(render node, output, etc.)           refer to `scene_info_render <配置文件文档之Houdini.html#header-n339>`_
===================== ====== ==================================================== ====================================================

.. _header-n341:

**software_config**

========== ====== ============================================ ==========
parameter  type   description                                  example
========== ====== ============================================ ==========
cg_name    string software                                     "Houdini"
cg_version string software version                             "16.5.268"
plugins    dict   plugin{name, version}                          {}
========== ====== ============================================ ==========

.. _header-n340:

**task_info**

========================== ====== ======================================================================================== =================================================================================================================
parameter                  type   description                                                                              example
========================== ====== ======================================================================================== =================================================================================================================
is_layer_rendering         string render layer mode,"0":off, "1":on                                                        "1"
cg_id                      string software id."2004": Houdini                                                              "2004"
ram                        string ram,64/128                                                                               "64"
os_name                    string os, "0":Linux; "1": Windows                                                              "0"
render_layer_type          string render layer mode,"0"：renderlayer,"1"：rendersetup                                      "0"
is_distribute_render       string distributed render mode,"0":off, "1":on                                                  "0"
input_cg_file              string input file path
job_stop_time              string stop when job exceeds time-out, unit:sec                                                 "28800"
user_id                    string user id
pre_frames                 string priority frames                                                                          "000:1,3-4[1]"
platform                   string platform id                                                                              "2"
is_picture                 string if it's architectural rendering                                                          "0"
project_id                 string project id
channel                    string submit manner。"4":API/SDK                                                                "4"
tiles_type                 string "block,strip"                                                                             "block"
tiles                      string tile number, 1 for single node, greater than 1 for tiles rendering(multi-nodes)           "1"
project_name               string project name                                                                              "test"
distribute_render_node     string nodes number for distributed rendering                                                    "3"
frames_per_task            string frames per task                                                                           "1"
stop_after_test            string "1":pause after priority render, "2":continue after priority render
input_project_path         string project path, could be empty
task_id                    string task id
task_stop_time             string stop when task exceeds time-out, unit:sec                                                 "86400"
time_out                   string time out setting, unit: sec                                                               "43200"
========================== ====== ======================================================================================== =================================================================================================================

.. _header-n339:

**scene_info_render**

========= ====== ===============
parameter type   description
========= ====== ===============
rop_node  object render node
geo_node  object simulation node
========= ====== ===============


**scene_info_render.rop_node and geo_node**

========== ====== ============================================================================ ================
parameter  type   description                                                                   example
========== ====== ============================================================================ ================
node       string rop / geo full path                                                           "/out/mantra1"
frames     string rop / frame range                                                             "1-10[1]"
option     string rop / render/simulation id, -1:render, other:number of nodes for simulation   "-1"
render     string rop / whether to activate rendering, 1:active(render/simulation),0:inactive   "1"
========== ====== ============================================================================ ================

.. _header-n234:

2.upload.json
-----------------

File to save assets info

**upload.json**

.. code:: json

   {
     "asset": [
       {
         "local": "D:/gitlab/renderSDK/scenes/houdini_test/sphere.hip",
         "server": "/D/gitlab/renderSDK/scenes/houdini_test/sphere.hip"
       }
     ]
   }

**upload.json**

========== ====== ========================== ============================================================
parameter  type    description                example
========== ====== ========================== ============================================================
asset      object Asset path information
                  that needs to be uploaded   refer to asset `<配置文件文档之Houdini.html#header-n338>`__
========== ====== ========================== ============================================================

.. _header-n338:

**asset**

========= ====== ===================================== =====================================================
parameter type   description                           example
========= ====== ===================================== =====================================================
local     string local path of asset                   "D:/gitlab/renderSDK/scenes/houdini_test/sphere.hip"
server    string relative path of server               "/D/gitlab/renderSDK/scenes/houdini_test/sphere.hip"
========= ====== ===================================== =====================================================

.. _header-n272:

3.tips.json
---------------

File to save errors, warnings

.. code:: json

   {}
