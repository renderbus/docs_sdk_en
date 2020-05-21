Maya 配置文件文档
======

> Analyze clarisse scene and save the output as task.json, asset.json,
> upload.json and tips.json.


### 1.task.json


> File to save the analysis result of the scene, including scene name, cg software version, render settings, etc.

**task.json**


```json
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
cg_name | string | Y | software | "Maya"
cg_version | string | Y | software version | "2016"
plugins | object | Y | plugin{name, version} | {}

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


 parameter | type   | Is it necessary | description | example                                                      
---|---|---|---|---
layer | object | Y | layer info | refer to [scene_info_render.layer](#scene_info_render.layer) 

**<span id="scene_info_render.layer">scene_info_render.layer</span>**


parameter | type |  | description | example 
---|---|---|---|---
renderable | string | Y | Render layer switch | "1"
env | object | N | Environmental information | {}
is_default_camera | string | N | Whether to use the default camera, the default value is ‘1’ (use the default camera) | "1" 
option | string | N | Renderer corresponding information | ""
common | object | Y | Scene general information | refer to [scene_info_render.layer.common](#scene_info_render.layer.common) 

**<span id="scene_info_render.layer.common">scene_info_render.layer.common</span>**


 parameter         | type          | Is it necessary | description                                        | example                                    
---|---|---|---|---
image_format | string | Y | Render element output file type | "jpg"
end | string | Y | end frame | "100"
width | string | Y | Width-resolution | "1920"
image_file_prefix | string | Y | Output file name setting，"<RenderLayer>/<Scence>" | ""
all_camera | array<string> | Y | List of all cameras | ["stereoCameraRightShape", "cameraShape1"]
render_camera | array<string> | Y | List of cameras to be rendered | ["stereoCameraRightShape"]
start | string | Y | Start frame | "1"
animation | string | N | Animation switch | "1"
renderer | string | Y | Renderer name | “arnold“
frames | string | Y | Render frame | "1-10[1]"
height | string | Y | High-resolution | "1080"
renumber_frames | string | N | Frame overlay | "1"
by_frame | string | Y | Frame interval | "1"


### 2.upload.json


> File to save assets info

**upload.json example**

```json
{
  "asset": [
    {
      "local": "D:/chensr/scene/maya2016_multi_layers_cameras.ma", 
      "server": "/D/chensr/scene/maya2016_multi_layers_cameras.ma"
    }
  ]
}
```

**upload.json**


 parameter | type   | description                           | example                  
---|---|---|---
asset | object | Asset path information to be uploaded | refer to [asset](#asset) 

**<span id="asset">asset对象解析</span>**


 parameter | type   | description                                                  | example                                            
---|---|---|---
local | string | local path of asset | "D:/chensr/scene/maya2016_multi_layers_cameras.ma"
server | string | Relative path on the server side, generally consistent with local | "/D/chensr/scene/maya2016_multi_layers_cameras.ma"


### 3.tips.json


> File to save errors, warnings


```json
{
    "50001":[
        "Nodes: /obj/flattank_fluid/compressed_cache/file_mode  File name: $HIP/geo/$HIPNAME.$OS.$F.bgeo.sc  miss file: /geo/flip_test_slice4.compressed_cache.1.bgeo.sc ",
    ]
}
```

