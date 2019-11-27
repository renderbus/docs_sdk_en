.. _header-n0:

Maya
=================

Analysis：analyze maya scene and save the output as task.json, asset.json,
upload.json and tips.json.

.. _header-n6:

1.task.json
---------------

File to save the analysis result of the scene, including scene name, cg software version, render settings, etc.

**task.json example**

.. code:: json

   {
       "scene_info_render": {
           "defaultRenderLayer": {
               "renderable": "1",
               "env": {},
               "is_default_camera": "1",
               "option": "",
               "common": {
                   "image_format": "exr",
                   "end": "10",
                   "width": "960",
                   "image_file_prefix": "",
                   "all_camera": [
                       "stereoCameraRightShape",
                       "stereoCameraLeftShape",
                       "stereoCameraCenterCamShape",
                       "perspShape",
                       "cameraShape2",
                       "cameraShape1"
                   ],
                   "render_camera": [
                       "cameraShape1"
                   ],
                   "start": "1",
                   "animation": "False",
                   "renderer": "mentalRay",
                   "frames": "1-10[1]",
                   "height": "540",
                   "renumber_frames": "False",
                   "by_frame": "1"
               }
           },
           "mut": {
               "renderable": "1",
               "is_default_camera": "1",
               "option": "",
               "common": {
                   "image_format": "exr",
                   "end": "10",
                   "width": "960",
                   "image_file_prefix": "",
                   "all_camera": [
                       "stereoCameraRightShape",
                       "stereoCameraLeftShape",
                       "stereoCameraCenterCamShape",
                       "perspShape",
                       "cameraShape2",
                       "cameraShape1"
                   ],
                   "render_camera": [
                       "cameraShape1",
                       "stereoCameraLeftShape"
                   ],
                   "start": "1",
                   "animation": "False",
                   "renderer": "mentalRay",
                   "frames": "1-10[1]",
                   "height": "540",
                   "renumber_frames": "False",
                   "by_frame": "1"
               }
           }
       },
       "task_info": {
           "is_layer_rendering": "1",
           "cg_id": "2000",
           "ram": "64",
           "os_name": "1",
           "render_layer_type": "0",
           "is_distribute_render": "0",
           "input_cg_file": "D:/chensr/scene/maya2016_multi_layers_cameras.ma",
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
           "task_id": "439800",
           "task_stop_time": "86400",
           "time_out": "12"
       },
       "software_config": {
           "cg_version": "2016",
           "cg_name": "Maya",
           "plugins": {}
       }
   }

**task.json parameters**

===================== ====== ==================================================== ====================================================================
parameter             type   description                                          example
===================== ====== ==================================================== ====================================================================
software_config       object environment(cg software, version and plugins, etc.)  refer to `software_config  <配置文件文档之Maya.html#header-n339>`_
task_info             object render settings(priority frames, render range, etc.) refer to `task_info  <配置文件文档之Maya.html#header-n338>`_
scene_info_render     object analysis result(render node, output, etc.)           refer to `scene_info_render <配置文件文档之Maya.html#header-n337>`_
===================== ====== ==================================================== ====================================================================

.. _header-n339:

**software_config**

========== ====== ============================================ ======
parameter  type   description                                  example
========== ====== ============================================ ======
cg_name    string software                                     "Maya"
cg_version string software version                             "2016"
plugins    dict   plugin{name, version}                        {}
========== ====== ============================================ ======

.. _header-n338:

**task_info**

========================== ====== ======================================================================================== =================================================================================================================
parameter                  type   description                                                                              example
========================== ====== ======================================================================================== =================================================================================================================
is_layer_rendering         string render layer mode,"0":off, "1":on                                                        "1"
cg_id                      string software id."2000": Maya                                                                 "2000"
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

.. _header-n337:

**scene_info_render**

===== ====== =========== =========================================================================
para  type   description example
===== ====== =========== =========================================================================
layer object layer info  refer to scene_info_render.layer `<配置文件文档之Maya.html#header-n336>`_
===== ====== =========== =========================================================================

.. _header-n336:

**scene_info_render.layer**

===================== ====== =============================== ================================================================================
parameter             type   description                     example
===================== ====== =============================== ================================================================================
renderable            string Render layer switch             "1"
env                   object                                 {}
is_default_camera     string use default camera?,default "1" "1"
option                string info of renderer                ""
common                object scene general info              refer to `scene_info_render.layer.common <配置文件文档之Maya.html#header-n335>`_
===================== ====== =============================== ================================================================================

.. _header-n335:

**scene_info_render.layer.common**

===================== ====== =============================== ==========================================
parameter             type   description                      example
===================== ====== =============================== ==========================================
image_format          string output format                    "jpg"
end                   string end frame                        "100"
width                 string image resolution of the wide     "1920"
image_file_prefix     string output image prefix setting      ""
all_camera            list   all camera                       ["stereoCameraRightShape", "cameraShape1"]
render_camera         list   list of cameras to render        ["stereoCameraRightShape"]
start                 string start frame                      "1"
animation             string on/off                           "1"
renderer              string Renderer name                    "arnold"
frames                string render frame                     "1-10[1]"
height                string image resolution of the height   "1080"
renumber_frames       string                                  "1"
by_frame              string frame interval                   "1"
===================== ====== =============================== ==========================================

.. _header-n307:

2.upload.json
-----------------

File to save assets info.

**upload.json example**

.. code:: json

   {
     "asset": [
       {
         "local": "D:/chensr/scene/maya2016_multi_layers_cameras.ma",
         "server": "/D/chensr/scene/maya2016_multi_layers_cameras.ma"
       }
     ]
   }

**upload.json**

===== ====== ====================== =======================================================
param type   description            example
===== ====== ====================== =======================================================
asset object assets info            refer to `asset <配置文件文档之Maya.html#header-n334>`_
===== ====== ====================== =======================================================

.. _header-n334:

**asset**

====== ====== ===================================== ====================================================
param  type   description                           example
====== ====== ===================================== ====================================================
local  string local path of asset                   "D:/chensr/scene/maya2016*multi*_layers_cameras.ma"
server string relative path of server               "/D/chensr/scene/maya2016*multi*_layers_cameras.ma"
====== ====== ===================================== ====================================================

.. _header-n345:

3.tips.json
---------------

File to save errors, warnings.

.. code:: json

   {}
