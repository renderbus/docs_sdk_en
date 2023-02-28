C4D Profile documentation
======

> We analyze the information needed in the scene and save it into multiple files such as task.json, asset.json, upload.json, tips.json to further resolve and process.


### 1.task.json


> Storage scenario analysis results, rendering settings, etc.

**task.json**


```json
{
  "scene_info_render": {
    "renderer": {
      "octane_renderer_info": {},
      "name": "Physical",
      "Octane_renderer_resave_info": {},
      "physical_sampler_mode": "",
      "physical_sampler": ""
    },
    "common": {
      "all_take_info": [],
      "frames": "0-333[1]",
      "multipass_saveonefile": "0",
      "fps": "25",
      "multipass_save_enabled": "0",
      "frame_rate": "25",
      "multi_pass": {
        "Post Effects": [],
      },
      "all_take_name": [],
      "saved_version": "MAXON CINEMA 4D Studio (RC - R18) 18.011",
      "regular_image_format": "TIFF",
      "multi_pass_format": "TIFF",
      "regular_image_saveimage_path": "ybt",
      "all_format": [
        "RLA",
        "HDR",
        "PSB",
        "TIFF",
        "TGA",
        "BMP",
        "IFF",
        "JPEG",
        "PICT",
        "PSD",
        "DDS",
        "RPF",
        "B3D",
        "PNG",
        "DPX",
        "EXR"
      ],
      "regular_image_save_enabled": "1",
      "created_version": "MAXON CINEMA 4D Studio 15.057",
      "all_camera": [
        "1"
      ],
      "width": "1920",
      "multipass_save_saveimage": "1",
      "multipass_saveimage_path": "",
      "height": "1080",
      "c4d_software_version": 22123
    }
  },
  "additional_info": {},
  "task_info": {
    "enable_layered": "0",
    "task_stop_time": "0",
    "concurrent_tasks": "1",
    "channel": "4",
    "frames_per_task": "1",
    "task_id": "54508419",
    "project_name": "Project1",
    "platform": "2",
    "tiles": "1",
    "is_picture": "0",
    "project_id": "469457",
    "job_stop_time": "259200",
    "distribute_render_node": "3",
    "stop_after_test": "1",
    "clone_original_id": "",
    "ram": "64",
    "render_layer_type": "0",
    "test_frames": "100",
    "edit_name": "",
    "pre_frames": "100",
    "input_project_path": "",
    "is_layer_rendering": "1",
    "is_distribute_render": "0",
    "tiles_type": "block",
    "time_out": "43200",
    "multi_node": "0",
    "cg_id": "2005",
    "user_id": "100150764",
    "input_cg_file": "D:/houdini/cg_file/ybt.c4d",
    "os_name": "1",
    "hardwareConfigId": ""
  },
  "software_config": {
    "plugins": {},
    "cg_version": "R22",
    "cg_name": "CINEMA 4D"
  },
  "scene_info": {
    "renderer": {
      "octane_renderer_info": {},
      "name": "Physical",
      "Octane_renderer_resave_info": {},
      "physical_sampler_mode": "",
      "physical_sampler": ""
    },
    "common": {
      "all_take_info": [],
      "frames": "0-333[1]",
      "multipass_saveonefile": "0",
      "fps": "25",
      "multipass_save_enabled": "0",
      "frame_rate": "25",
      "multi_pass": {
        "Post Effects": [],
      },
      "all_take_name": [],
      "saved_version": "MAXON CINEMA 4D Studio (RC - R18) 18.011",
      "regular_image_format": "TIFF",
      "multi_pass_format": "TIFF",
      "regular_image_saveimage_path": "ybt",
      "all_format": [
        "RLA",
        "HDR",
        "PSB",
        "TIFF",
        "TGA",
        "BMP",
        "IFF",
        "JPEG",
        "PICT",
        "PSD",
        "DDS",
        "RPF",
        "B3D",
        "PNG",
        "DPX",
        "EXR"
      ],
      "regular_image_save_enabled": "1",
      "created_version": "MAXON CINEMA 4D Studio 15.057",
      "all_camera": [
        "1"
      ],
      "width": "1920",
      "multipass_save_saveimage": "1",
      "multipass_saveimage_path": "",
      "height": "1080",
      "c4d_software_version": 22123
    }
  }
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
cg_version | string | Y | software version，E.g: R13/R14/R15/R16/R17/R18/R19 | "R22" 
plugins | object | Y | plugin{name:  version} | {"c4dtoa": "2.2.0", "vray":"1.9"} 

**<span id="task_info">task_info</span>**

| **parameter**          | **type** | **Is it necessary** | **description**                                              | **example**                                                  |
| ---------------------- | -------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| graphics_cards_num     | string   | Y                   | 1: open single card rendering 2: open dual card rendering    | “2”                                                          |
| enable_layered         | string   | Y                   | render layer mode,"0":off, "1":on                            | "0"                                                          |
| cg_id                  | string   | Y                   | software id."2005": C4d                                      | "2005"                                                       |
| ram                    | string   | Y                   | ram: 64 / 128                                                | "64"                                                         |
| os_name                | string   | Y                   | Rendering machine operating system: "0":Linux; "1": Windows, C4D only support windows。 | "1"                                                          |
| render_layer_type      | string   | Y                   | render layer mode(only support maya): <br>"0"：renderlayer；<br> "1"：rendersetup | "0"                                                          |
| is_distribute_render   | string   | N                   | distributed render mode,"0":off, "1":on                      | "0"                                                          |
| input_cg_file          | string   | Y                   | input file path                                              | "D:/houdini/cg_file/ybt.c4d"                                 |
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
renderer | dict | Y | Renderer detailed parameters |  

**<span id="scene_info.common">scene_info.common</span>**


**parameter** | **type** | Is it necessary | **description** | **example** 
---|---|---|---|---
all_take_info | list | Y | Sequence | [] 
frames | string | Y | Starting needle, isolated needle | "0-333[1]" 
multipass_saveonefile | string | Y | Whether the channel in the C4D software scenario is turned on | "1" 
fps | string | Y | Frame rate | "25" 
multipass_save_enabled | string | Y | Channel output switch (opened to 1, close 0) | "1" 
frame_rate | string | Y | Sequester | "25" 
multi_pass | dict | Y | Channel in the scene | 
all_take_name | list | Y | Field name | [] 
saved_version | string | Y | Save version | "MAXON CINEMA 4D Studio (RC - R18) 18.011" 
regular_image_format | string | Y | Main map output format | "TIFF" 
multi_pass_format | string | Y | Channel output format | "TIFF" 
regular_image_saveimage_path | string | Y | Main map output name (default display output file name) | "ybt" 
all_format | list | Y | All output formats | [<br/>				"RLA",<br/>				"HDR",<br/>				"PSB",<br/>				"TIFF",<br/>				"TGA",<br/>				"BMP",<br/>				"IFF",<br/>				"JPEG",<br/>				"PICT",<br/>				"PSD",<br/>				"DDS",<br/>				"RPF",<br/>				"B3D",<br/>				"PNG",<br/>				"DPX",<br/>				"EXR"<br/>			] 
regular_image_save_enabled | string | Y | Main map output switch (opened to 1, close to 0) | "1" 
created_version | string | Y | Create version | "MAXON CINEMA 4D Studio 15.057" 
all_camera | list | Y | All cameras in the scene | ["1"] 
width | string | Y | width | "1920" 
height | string | Y | high | "1080" 
multipass_save_saveimage | string | Y | Channel Save Path in C4D Software Scene | "1" 
multipass_saveimage_path | string | Y | Channel output name | "" 
c4d_software_version | int | Y | Software version | 22123 


### 2.upload.json


> File to save assets info

**upload.json**

```json
{
    "asset": [
        {
            "local": "D:/houdini/cg_file/ybt.c4d", 
            "server": "/D/houdini/cg_file/ybt.c4d"
        }
    ], 
    "scene": {
        "local": "D:\\houdini\\cg_file\\ybt.c4d", 
        "server": "/D/houdini/cg_file/ybt.c4d"
    }
}
```

**upload.json**


**parameter** | **type** | **description** | **example** 
---|---|---|---
asset | list | Asset path information to be uploaded | [refer to asset](#asset) 
scene | dict | Scene file | 

**<span id="asset">asset</span>**


**parameter** | **type** | **description** | **example** 
---|---|---|---
local | string | local path of asset | "D:/houdini/cg_file/ybt.c4d" 
server | string | Relative path on the server side, generally consistent with local | "/D/houdini/cg_file/ybt.c4d" 


### 3.tips.json


> File to save errors, warnings


```json
{"35001":"d:\\abc\\jdf.jpg"}
```
