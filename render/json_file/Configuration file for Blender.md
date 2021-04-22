Blender Profile documentation
================================

> We analyze the information needed in the scene and save it into multiple files such as task.json, asset.json, tips.json to further resolve and process.


### 1.task.json


> Storage scenario analysis results, rendering settings, etc.

**task.json**


```json
{
    "software_config": {
        "cg_name": "Blender",
        "cg_version": "2.81",
        "plugins": {}
    },
    "scene_info_render": {
        "common": {
            "width": "1024",
            "scene_name": [
                "Scene"
            ],
            "Output_path": "/tmp\\",
            "camera_name": "<bpy_struct, Object(\"Camera\")>",
            "height": "1024",
            "Render_Format": "OPEN_EXR",
            "frames": "1-1[1]"
        }
    },
    "task_info": {
        "os_name": "1",
        "pre_frames": "100",
        "distribute_render_node": "3",
        "time_out": "43200",
        "stop_after_test": "1",
        "frames_per_task": "1",
        "project_id": "14323",
        "tiles": "1",
        "user_id": "10013141",
        "enable_layered": "0",
        "is_layer_rendering": "1",
        "task_stop_time": "0",
        "task_id": "8368517",
        "job_stop_time": "259200",
        "input_project_path": "",
        "platform": "2",
        "input_cg_file": "D:/houdini/cg_file/PRAM RENDER 1.blend",
        "channel": "4",
        "cg_id": "2007",
        "ram": "64",
        "is_picture": "0",
        "render_layer_type": "0",
        "is_distribute_render": "0",
        "hardwareConfigId": "5",
        "project_name": "Project1",
        "tiles_type": "block"
    },
    "scene_info": {
        "common": {
            "width": "1024",
            "scene_name": [
                "Scene"
            ],
            "Output_path": "/tmp\\",
            "camera_name": "<bpy_struct, Object(\"Camera\")>",
            "height": "1024",
            "Render_Format": "OPEN_EXR",
            "frames": "1-1[1]"
        }
    },
    "additional_info": {}
}
```

**task.json**


**parameter** | **type** | **Is it necessary** | **description** | **example** 
---|---|---|---|---
software_config | object | Y | environment(cg software, version and plugins, etc.) | [refer to software_config](#software_config) 
task_info | object | Y | render settings(priority frames, render range, etc.) | [refer to task_info](#task_info) 
scene_info | object | Y | Scene analysis results (rendering nodes in the scene, output path, etc.) | [refer to scene_info](#scene_info) 
scene_info_render | object | N | General with "Scene_info" |  

**software_config**


**parameter** | **type** | Is it necessary | **description** | **example** 
---|---|---|---|---
cg_name | string | Y | software name | "CINEMA 4D" 
cg_version | string | Y | software version | "2.81" 
plugins | object | Y | plugin{name:  version} | {} 

**<span id="task_info">task_info</span>**

| **parameter**          | **type** | **Is it necessary** | **description**                                              | **example**                                                  |
| ---------------------- | -------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| graphics_cards_num     | string   | Y                   | 1: open single card rendering 2: open dual card rendering    | “2”                                                          |
| enable_layered         | string   | Y                   | render layer mode,"0":off, "1":on                            | "0"                                                          |
| cg_id                  | string   | Y                   | software id."2007": Blender                                  | "2007"                                                       |
| ram                    | string   | Y                   | ram: 64 / 128                                                | "64"                                                         |
| os_name                | string   | Y                   | Rendering machine operating system: "0":Linux; "1": Windows, C4D only support windows。 | "1"                                                          |
| render_layer_type      | string   | Y                   | render layer mode(only support maya): <br>"0"：renderlayer；<br> "1"：rendersetup | "0"                                                          |
| is_distribute_render   | string   | N                   | distributed render mode,"0":off, "1":on                      | "0"                                                          |
| input_cg_file          | string   | Y                   | input file path                                              | "D:/houdini/cg_file/PRAM RENDER 1.blend"                     |
| input_project_path     | string   | Y                   | project path, could be empty                                 |                                                              |
| job_stop_time          | string   | Y                   | Set the frame timeout time, will only affect the current frame, unit seconds | "28800"                                                      |
| user_id                | string   | N                   | user id                                                      |                                                              |
| pre_frames             | string   | Y                   | Priority rendering (priority frames are not recommended to customize multiple individual frames) | "000: 1,3-4 [1]" means: Priority rendering first frame: No Priority rendering middle frame: No Priority rendering last frame: No Priority rendering custom frame: 1,3-4 [1] |
| platform               | string   | Y                   | submit platform : "2": "www2", "3": "www3", "6": "www4", "21": "gpu", | "2"                                                          |
| is_picture             | string   | Y                   | "0: Effect Chart "1": Animation Chart                        | "0"                                                          |
| channel                | string   | Y                   | 1:Web local analysis (animation deduction); 2:web cloud analysis; 3:Rendering plugin submission； 4：API/SDK submission; 8：Animation plugin submission | "4"                                                          |
| tiles_type             | string   | Y                   | "block, strip"                                               | "block"                                                      |
| tiles                  | string   | Y                   | tile number, 1 for single node, greater than 1 for tiles rendering(multi-nodes) | "1"                                                          |
| project_id             | string   | N                   | project id                                                   | "200953"                                                     |
| project_name           | string   | Y                   | project name                                                 | "Project1"                                                   |
| distribute_render_node | string   | N                   | nodes number for distributed rendering                       | "3"                                                          |
| frames_per_task        | string   | Y                   | frames per task                                              | "1"                                                          |
| stop_after_test        | string   | Y                   | "1":pause after priority render, "2":continue after priority render (default "2") | “2”                                                          |
| task_id                | string   | N                   | task id                                                      | “54508419”                                                   |
| task_stop_time         | string   | Y                   | Large task timeout stops in unit seconds, "0" means unlimited | "86400"                                                      |
| time_out               | string   | Y                   | Overtime reminder time, unit: sec                            | "43200"                                                      |

**<span id="scene_info">scene_info</span>**


**parameter** | **type** | **description** | **description** | **example** 
---|---|---|---|---
common | dict | Y | Loading platform normal parameters | **[refer to scene_info.common](#scene_info.common)** 

**<span id="scene_info.common">scene_info.common</span>**

| **parameter** | **type** | **description** | **description**         | **example**                        |
| ------------- | -------- | --------------- | ----------------------- | ---------------------------------- |
| frames        | string   | Y               | render frames           | "1-1[1]"                           |
| Output_path   | string   | N               | output path             | "/tmp\\\\"                         |
| width         | string   | N               | width                   | "1024"                             |
| height        | string   | N               | height                  | "1024"                             |
| camera_name   | string   | N               | camera name             | "<bpy_struct, Object(\"Camera\")>" |
| Render_Format | string   | N               | Rendering output format | "OPEN_EXR"                         |
| scene_name    | list     | N               | scene name              | ["Scene"]                          |

### 2.upload.json


> Blender does not automatically generate Upload.json by analyzing, requiring users to build Upload.json upload resources themselves,
>
> Custom UPLOAD.json can refer to rayvision_api.utils.Append_to_upload。

**upload.json**

```json
{
	"asset": [
		{
			"local": "D:/houdini/cg_file/blender_test.blend",
			"server": "/D/houdini/cg_file/blender_test.blend"
		}
	]
}
```

**upload.json**


**parameter** | **type** | **description** | **example** 
---|---|---|---
asset | list | Asset path information to be uploaded | [refer to asset](#asset) 

**<span id="asset">asset</span>**


**parameter** | **type** | **description** | **example** 
---|---|---|---
local | string | local path of asset | "D:/houdini/cg_file/blender_test.blend" 
server | string | Relative path on the server side, generally consistent with local | "/D/houdini/cg_file/blender_test.blend" 


### 3.tips.json


> File to save errors, warnings


```json
{"35001":"d:\\abc\\jdf.jpg"}
```
