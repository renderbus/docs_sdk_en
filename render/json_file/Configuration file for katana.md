Katana Configuration
===================

> Analyze katana scene and save the output as task.json, asset.json,
> tips.json.


### 1.task.json


> File to save the analysis result of the scene, including scene name, cg software version, render settings, etc.

**task.json**


```json
{
  "scene_info_render": {
    "rendernodes": {
      "Render": {
        "renderable": "1",
        "denoise": "0",
        "frames": "1-1[1]",
        "aov": {
          "aaa": "F:/cache/test.exr"
        }
      }
    }
  },
  "additional_info": {},
  "task_info": {
    "enable_layered": "0",
    "task_stop_time": "0",
    "concurrent_tasks": "1",
    "channel": "4",
    "frames_per_task": "1",
    "task_id": 34399251,
    "project_name": "Project1",
    "platform": "2",
    "tiles": "1",
    "is_picture": "0",
    "project_id": "200953",
    "job_stop_time": "259200",
    "distribute_render_node": "3",
    "stop_after_test": "1",
    "clone_original_id": "",
    "ram": "64",
    "render_layer_type": "0",
    "test_frames": "100",
    "graphics_cards_num": "2",
    "edit_name": "",
    "pre_frames": "100",
    "input_project_path": "",
    "is_layer_rendering": "1",
    "is_distribute_render": "0",
    "tiles_type": "block",
    "time_out": "43200",
    "cg_id": "2016",
    "user_id": 100150764,
    "input_cg_file": "F:/cache/arnold_test.katana",
    "os_name": "1",
    "hardwareConfigId": ""
  },
  "software_config": {
    "plugins": {
      "KtoA": "2.4.0.3"
    },
    "cg_version": "3.2v1",
    "cg_name": "Katana"
  },
  "scene_info": {
    "rendernodes": {
      "Render": {
        "renderable": "1",
        "denoise": "0",
        "frames": "1-1[1]",
        "aov": {
          "aaa": "F:/cache/test.exr"
        }
      }
    }
  }
}
```

**task.json**


 parameter         | type   | description                                          | example                                          
---|---|---|---
software_config | object | environment(cg software, version and plugins, etc.) | refer to [software_config](#software_config) 
task_info | object | render settings(priority frames, render range, etc.) | refer to [task_info](#task_info) 
scene_info_render | object | analysis result(render node, output, etc.) | refer to [scene_info_render](#scene_info_render) 

**<span id="software_config">software_config</span>**


 parameter  | type   | Is it necessary | description | example 
---|---|---|---|---
cg_name | string | Y | software | "Katana" 
cg_version | string | Y | software version | "3.2v1" 
plugins | object | Y | plugin{name, version} | {"KtoA": "2.4.0.3"} 

**<span id="task_info">task_info</span>**

| parameter              | type   | Is it necessary | description                                                  | default  | example                                                      |
| ---------------------- | ------ | --------------- | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ |
| graphics_cards_num     | string | Y               | 1： open single card rendering 2: open dual card rendering   | "2"      |                                                              |
| enable_layered         | string | Y               | render layer mode,"0":off, "1":on                            | "0"      | "1"                                                          |
| cg_id                  | string | Y               | software id."2016": Katana                                   |          | "2016"                                                       |
| ram                    | string | Y               | ram: 64 / 128                                                | "64"     | "64"                                                         |
| os_name                | string | Y               | Rendering machine operating system:  "0":Linux; "1": Windows | "1"      | "1"                                                          |
| render_layer_type      | string | N               | render layer mode:  "0"：renderlayer "1"：rendersetup        | "0"      | "0"                                                          |
| is_distribute_render   | string | N               | distributed render mode,"0":off, "1":on                      | "0"      | "0"                                                          |
| input_cg_file          | string | Y               | input file path                                              |          | "F:/cache/arnold_test.katana"                                |
| input_project_path     | string | Y               | project path, could be empty                                 | " "      |                                                              |
| job_stop_time          | string | Y               | Set the frame timeout time, will only affect the current frame, unit seconds | "259200" | "28800"                                                      |
| user_id                | string | Y               | user id                                                      |          |                                                              |
| pre_frames             | string | Y               | Priority rendering (priority frames are not recommended to customize multiple individual frames) | "000"    | "000: 1,3-4 [1]" means:  Priority rendering first frame: No  Priority rendering middle frame: No  Priority rendering last frame: No  Priority rendering custom frame: 1,3-4 [1] |
| platform               | string | Y               | submit platform : "2": "www2", "3": "www3", "6": "www4", "21": "gpu", |          | "2"                                                          |
| is_picture             | string | Y               | "0: Effect Chart "1": Animation Chart                        | "0"      | "0"                                                          |
| project_id             | string | Y               | project id                                                   | " "      | "200953"                                                     |
| project_name           | string | Y               | project name                                                 | "0"      | "Project1"                                                   |
| channel                | string | Y               | 1:Web local analysis (animation deduction); 2:web cloud analysis; 3:Rendering plugin submission； 4：API/SDK submission; 8：Animation plugin submission | "4"      | "4"                                                          |
| tiles_type             | string | Y               | "block, strip"                                               | "block"  | "block"                                                      |
| tiles                  | string | Y               | tile number, 1 for single node, greater than 1 for tiles rendering(multi-nodes) | "1"      | "1"                                                          |
| distribute_render_node | string | N               | nodes number for distributed rendering                       | "3"      | "3"                                                          |
| frames_per_task        | string | Y               | frames per task                                              | "1"      | "1"                                                          |
| stop_after_test        | string | Y               | "1":pause after priority render, "2":continue after priority render (default "2") | "2"      | "2"                                                          |
| task_id                | string | Y               | task id                                                      |          |                                                              |
| task_stop_time         | string | Y               | Large task timeout stops in unit seconds, "0" means unlimited | "0"      | "86400"                                                      |
| time_out               | string | Y               | Overtime reminder time, unit: sec                            | "43200"  | "43200"                                                      |

> **Note**: 
>
> -  Katana do not support distributed rendering (is_distribute_render) and block rendering (tiles)

**<span id="scene_info_render">scene_info_render</span>**


 parameter | type   | Is it necessary | description | example                                                      
---|---|---|---|---
rendernodes | dict | Y | Render output nodes | refer to [scene_info_render.rendernodes](#scene_info_render.rendernodes) 

**<span id="scene_info_render.rendernodes">scene_info_render.rendernodes</span>**


parameter | type | description | example 
---|---|---|---
 Render    | dict | Node names, which may have multiple different node names depending on the scenario | [scene_info_render.rendernodes.Render](#scene_info_render.rendernodes.Render) 

**<span id="scene_info_render.rendernodes.Render">scene_info_render.rendernodes.Render</span>**


 parameter         | type          | Is it necessary | description                                        | example                                    
---|---|---|---|---
 renderable | string | Y | Whether the node is active, "1" : active, "0" : inactive     |                    
 denoise    | string | N | Noise reduction (effective only on GPU platform), "0" : not on, "1" : on | "denoise": "0"     
 frames     | string | Y | Frame range of current node                                  | "frames": "1-1[1]" 
 aov        | dict   | Y | AOV must be the path in the scene, key: AOV name, value: output address |                    


### 2.upload.json


> Katana does not analyze asset files, but has an Upload.json file that contains only scenario files

**upload.json example**

```json
{
  "scene": [
    {
      "local": "F:/cache/arnold_test.katana",
      "server": "/F/cache/arnold_test.katana",
      "hash": "41985d615b8e6d44ce7e7881c46971de"
    }
  ],
  "asset": [
    {
      "local": "F:/cache/arnold_test.katana",
      "server": "/F/cache/arnold_test.katana"
    },
  ]
}
```

**upload.json**


 parameter | type   | description                           | example                  
---|---|---|---
asset | object | Asset path information to be uploaded | refer to [asset](#asset) 
scene | object | Scene file information | refer to [scene](#scene) 

**<span id="asset">asset Parametric Interpretation</span>**


 parameter | type   | description                                                  | example                                            
---|---|---|---
local | string | local path of asset | "F:/cache/arnold_test.katana 
server | string | Relative path on the server side, generally consistent with local | "/F/cache/arnold_test.katana" 
hash | string | hash value | "41985d615b8e6d44ce7e7881c46971de" 


### 3.tips.json


> File to save errors, warnings


```json
{
    "50001":[
        "Nodes: /obj/flattank_fluid/compressed_cache/file_mode  File name: $HIP/geo/$HIPNAME.$OS.$F.bgeo.sc  miss file: /geo/flip_test_slice4.compressed_cache.1.bgeo.sc ",
    ]
}
```

