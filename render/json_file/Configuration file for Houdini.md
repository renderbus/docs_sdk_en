Houdini Configuration
======================

> Analyze houdini scene and save the output as task.json, asset.json,upload.json and tips.json.

### 1.task.json


> File to save the analysis result of the scene, including scene name, cg software version, render settings, etc.

**task.json**


```json
{
    "scene_info_render": {
        "rop_node": [
            {
                "node": "/out/mantra1", 
                "frames": "1-10[1]", 
                "option": "-1", 
                "render": "1",
                "height": "720",
				"width": "1280",
            }
        ], 
        "geo_node": [],
        "distributedsim_node": [
			{
				"node": "/out/distributedsim",
				"output_driver": "/obj/distribute_flattank/save_slices",
				"render": "0",
				"simControlName": "/obj/flattank_sim/DISTRIBUTE_flattank_CONTROLS",
				"output_file": "/geo/flip_test_slice4.flattank.0.1.bgeo.sc",
				"num_slices": "4",
				"option": "1",
				"frames": "1-240[1]",
				"sliceType": "particle"
			},
    }, 
    "task_info": {
        "is_layer_rendering": "1", 
        "cg_id": "2004", 
        "ram": "64", 
        "os_name": "1", 
        "render_layer_type": "0", 
        "is_distribute_render": "1", 
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
```

**task.json Parametric Interpretation**


parameter | type |  | description | example 
---|---|---|---|---
software_config | object | Y | environment(cg software, version and plugins, etc.) | refer to [software_config](#software_config) 
task_info | object | Y | render settings(priority frames, render range, etc.) | refer to [task_info](#task_info) 
scene_info_render | object | Y | analysis result(render node, output, etc.) | refer to [scene_info_render](#scene_info_render) 

**<span id="software_config">software_config</span>**


 parameter  | type   | description           | example    
---|---|---|---
cg_name | string | software | "Houdini"
cg_version | string | software version | "16.5.268"
plugins | object | plugin{name, version} | {}

**<span id="task_info">task_info</span>**

| parameter              | type   | description                                                  | example                                                      |
| ---------------------- | ------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| is_layer_rendering     | string | render layer mode,"0":off, "1":on                            | "1"                                                          |
| cg_id                  | string | software id."2013": Clarisse                                 | "2013"                                                       |
| ram                    | string | ram: 64 / 128                                                | "64"                                                         |
| os_name                | string | Rendering machine operating system:  "0":Linux; "1": Windows | "1"                                                          |
| render_layer_type      | string | render layer mode:  "0"：renderlayer方式 "1"：rendersetup方式 | "0"                                                          |
| is_distribute_render   | string | distributed render mode,"0":off, "1":on                      | "0"                                                          |
| input_cg_file          | string | input file path                                              | "E:/copy/DHGB_sc05_zhuta_610-1570_v0102.project"             |
| job_stop_time          | string | Set the frame timeout time, will only affect the current frame, unit seconds | "28800"                                                      |
| user_id                | string | user id                                                      |                                                              |
| pre_frames             | string | Priority rendering (priority frames are not recommended to customize multiple individual frames) | "000: 1,3-4 [1]" means:  Priority rendering first frame: No  Priority rendering middle frame: No  Priority rendering last frame: No  Priority rendering custom frame: 1,3-4 [1] |
| platform               | string | submit platform : "2": "www2", "3": "www3", "6": "www4", "21": "gpu", | "2"                                                          |
| is_picture             | string | if it's architectural rendering                              | "0"                                                          |
| project_id             | string | project id                                                   | "200953"                                                     |
| channel                | string | 1:Web local analysis (animation deduction); 2:web cloud analysis; 3:Rendering plugin submission； 4：API/SDK submission; 8：Animation plugin submission | "4"                                                          |
| tiles_type             | string | "block, strip"                                               | "block"                                                      |
| tiles                  | string | tile number, 1 for single node, greater than 1 for tiles rendering(multi-nodes) | "1"                                                          |
| project_name           | string | project name                                                 | "Project1"                                                   |
| distribute_render_node | string | nodes number for distributed rendering                       | "3"                                                          |
| frames_per_task        | string | frames per task                                              | "1"                                                          |
| stop_after_test        | string | "1":pause after priority render, "2":continue after priority render (default "2") | "2"                                                          |
| input_project_path     | string | project path, could be empty                                 |                                                              |
| task_id                | string | task id                                                      |                                                              |
| task_stop_time         | string | Set the task timeout time. The task timeout stops all frames in unit seconds,unit: sec | "86400"                                                      |
| time_out               | string | Overtime reminder time, unit: sec                            | "43200"                                                      |

**<span id="scene_info_render">scene_info_render</span>**


 parameter           | type   | description      | example 
---|---|---|---
rop_node | object | Render node | 
geo_node | object | Solve node | 
distributedsim_node | object | Distributed node | 

**<span id="scene_info_render.rop_node">scene_info_render.rop_node和geo_node</span>**


 parameter | type   | Is it necessary | description | example 
---|---|---|---|---
node | string | Y | Node full path name | "/out/mantra1"
frames | string | Y | Frame number range | "1-10[1]"
option | string | Y | Task type: <br/> -1: rendering; <br/> 0: general solution; <br/> 1: distributed solution; | "-1"
render | string | Y | Whether to activate rendering: <br/> 1: Render (solve) the node; <br/> 0: The node does not participate in rendering (solve) | "1"
height | string | N | Camera height | “720” 
width | string | N | Camera width | “1280” 

**<span id="scene_info_render.distributedsim_node">scene_info_render.distributedsim_node对象解析</span>**

| parameter      | type   | Is it necessary | description                                                  | example                                          |
| -------------- | ------ | --------------- | ------------------------------------------------------------ | ------------------------------------------------ |
| node           | string | Y               | Node full path name                                          | "/out/distributedsim"                            |
| output_driver  | string | N               | Output driver                                                | "/obj/distribute_flattank/save_slices"           |
| render         | string | Y               | Whether to activate rendering: <br/> 1: Render (solve) the node; <br/> 0: The node does not participate in rendering (solve) | "0"                                              |
| simControlName | string | N               | Solve node name                                              | "/obj/flattank_sim/DISTRIBUTE_flattank_CONTROLS" |
| output_file    | string | N               | Output file                                                  | "/geo/flip_test_slice4.flattank.0.1.bgeo.sc"     |
| num_slices     | string | N               | Block calculation of the total number of blocks (the total cannot exceed 16) | "4"                                              |
| option         | string | Y               | Task type: <br/> -1: rendering; <br/> 0: general solution; <br/> 1: distributed solution; | "1"                                              |
| frames         | string | Y               | Solve Frame Range                                            | "1-240[1]"                                       |
| sliceType      | string | N               | Slice type                                                   | "particle"                                       |

### 2.upload.json


> File to save asset info

**upload.json example**

```json
{
  "asset": [
    {
      "local": "D:/gitlab/renderSDK/scenes/houdini_test/sphere.hip", 
      "server": "/D/gitlab/renderSDK/scenes/houdini_test/sphere.hip"
    }
  ]
}
```

**upload.json**


 parameter | type   | description                           | example                  
---|---|---|---
asset | object | Asset path information to be uploaded | refer to [asset](#asset) 

**<span id="asset">asset</span>**


 parameter | type   | description                                                  | example                                              
---|---|---|---
local | string | local path of asset | "D:/gitlab/renderSDK/scenes/houdini_test/sphere.hip"
server | string | Relative path on the server side, generally consistent with local | "/D/gitlab/renderSDK/scenes/houdini_test/sphere.hip"

### 3.tips.json


> File to save errors, warnings


```json
{
    "50001":[
        "Nodes: /obj/flattank_fluid/compressed_cache/file_mode  File name: $HIP/geo/$HIPNAME.$OS.$F.bgeo.sc  miss file: /geo/flip_test_slice4.compressed_cache.1.bgeo.sc ",
    ]
}
```

