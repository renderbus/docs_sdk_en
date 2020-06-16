Clarisse Configuration
========================

> Analyze clarisse scene and save the output as task.json, asset.json,
upload.json and tips.json.

### 1.task.json


> File to save the analysis result of the scene, including scene name, cg software version, render settings, etc.

**task.json example**


```json
{
    "scene_info_render": {
        "image_node": [
            {
                "frames": "0-50[1]",
                "renderable": "0",
                "output": "D:\\temp\\cam02",
                "format": "exr16",
                "LUT": "linear",
                "save_to_disk": "1",
                "name": "project://scene/cam02",
                "layers": [
                    {
                        "frames": "0-50[1]",
                        "renderable": "1",
                        "output": "D:\\temp\\cam02_layer02",
                        "format": "exr16",
                        "enable_deep_output": "1",
                        "save_to_disk": "1",
                        "enable_deep_output_path": "D:\\temp\\cam02_layer02_deep",
                        "name": "project://scene/cam02.cam02_layer02"
                    }
                ]
            }
        ]
    },
    "software_config":{
        "plugins":{},
        "cg_version":"clarisse_ifx_4.0_sp3",
        "cg_name":"Clarisse"
    },
    "task_info":{
        "task_stop_time":"259200",
        "frames_per_task":"1",
        "channel":"4",
        "task_id":"11022523",
        "project_name":"Project1",
        "platform":"2",
        "tiles":"1",
        "is_picture":"0",
        "project_id":"200953",
        "job_stop_time":"86400",
        "distribute_render_node":"3",
        "stop_after_test":"2",
        "clone_original_id":"",
        "ram":"64",
        "render_layer_type":"0",
        "test_frames":"000",
        "graphics_cards_num":"2",
        "edit_name":"",
        "pre_frames":"000",
        "input_project_path":"",
        "is_layer_rendering":"1",
        "is_distribute_render":"0",
        "time_out":"43200",
        "tiles_type":"block",
        "user_id":"100150764",
        "cg_id":"2013",
        "input_cg_file":"E:/copy/DHGB_sc05_zhuta_610-1570_v0102.project",
        "os_name":"1"
    },
    "scene_info":{
        "image_node": [
            {
                "frames": "0-50[1]",
                "renderable": "0",
                "output": "D:\\temp\\cam02",
                "format": "exr16",
                "LUT": "linear",
                "save_to_disk": "1",
                "name": "project://scene/cam02",
                "layers": [
                    {
                        "frames": "0-50[1]",
                        "renderable": "1",
                        "output": "D:\\temp\\cam02_layer02",
                        "format": "exr16",
                        "enable_deep_output": "1",
                        "save_to_disk": "1",
                        "enable_deep_output_path": "D:\\temp\\cam02_layer02_deep",
                        "name": "project://scene/cam02.cam02_layer02"
                    }
                ]
            }
        ]
    }
}
```


**task.json Parametric Interpretation**


parameter | type | description | example 
---|---|---|---
software_config | object | environment(cg software, version and plugins, etc.) | refer to [software_config](#software_config) 
task_info | object | render settings(priority frames, render range, etc.) | refer to [task_info](#task_info) 
scene_info_render | object | analysis result(render node, output, etc.) | refer to [scene_info_render](#scene_info_render) 

**<span id="software_config">software_config</span>**


parameter | type | description | example 
---|---|---|---
cg_name | string | software | "Clarisse" 
cg_version | string | software version | "clarisse_ifx_4.0_sp3" 
plugins | object | plugin{name, version} | {} 

**<span id="task_info">task_info</span>**


 parameter              | type   | description                                                  | example                                                      
---|---|---|---
is_layer_rendering | string | render layer mode,"0":off, "1":on | "1"
cg_id | string | software id."2013": Clarisse | "2013" 
ram | string | ram: 64 / 128 | "64"
os_name | string | Rendering machine operating system: <br>"0":Linux; "1": Windows | "1" 
render_layer_type | string | render layer mode: <br/>"0"：renderlayer方式<br/>"1"：rendersetup方式 | "0"
is_distribute_render | string | distributed render mode,"0":off, "1":on | "0"
input_cg_file | string | input file path | "E:/copy/DHGB_sc05_zhuta_610-1570_v0102.project" 
job_stop_time | string | Set the frame timeout time, will only affect the current frame, unit seconds | "28800"
user_id | string | user id | 
pre_frames | string | Priority rendering (priority frames are not recommended to customize multiple individual frames) | "000: 1,3-4 [1]" means: <br/> Priority rendering first frame: No <br/> Priority rendering middle frame: No <br/> Priority rendering last frame: No <br/> Priority rendering custom frame: 1,3-4 [1] 
platform | string | submit platform :<br>"2": "www2",<br/>"3": "www3",<br/>"6": "www4",<br/>"21": "gpu", | "2"
is_picture | string | if it's architectural rendering | "0"
project_id | string | project id | "200953" 
channel | string | 1:Web local analysis (animation deduction);<br/>2:web cloud analysis;<br/>3:Rendering plugin submission；<br/>4：API/SDK submission;<br/>8：Animation plugin submission | "4"
tiles_type | string | "block, strip" | "block"
tiles | string | tile number, 1 for single node, greater than 1 for tiles rendering(multi-nodes) | "1"
project_name | string | project name | "Project1" 
distribute_render_node | string | nodes number for distributed rendering | "3"
frames_per_task | string | frames per task | "1"
stop_after_test | string | "1":pause after priority render,<br> "2":continue after priority render<br>(default "2") |"2"
input_project_path | string | project path, could be empty |
task_id | string | task id | 
task_stop_time | string | Set the task timeout time. The task timeout stops all frames in unit seconds,unit: sec | "86400"
time_out | string | Overtime reminder time, unit: sec | "43200" 

**<span id="scene_info_render">scene_info_render</span>**


 parameter  | type   | description  | example                                                      
---|---|---|---
image_node | object | general info | refer to [scene_info_render.image_node](#scene_info_render.image_node) 

**<span id="scene_info_render.common">scene_info_render.image_node</span>**


 parameter    | type   | description                                                  | example                                                      
---|---|---|---
renderable | string | "0": do not open rendering,<br>“1”: open rendering (this is not the value in the scene,the platform is not open by default, the platform is notrecommended to directly render image) | "0" 
output | string | output path of current image | "D:\temp\cam02" 
format | string | the output format for the current image | "exr16" 
LUT | string | the output color management of the current image | "linear" 
save_to_disk | string | Whether to open save output for the current image | "1" 
name | string | the name of the current image is also the path in the scene | "project://scene/cam02" 
layers | string | The value of 3dlayer in the current image is list, and the value of list is dict | [scene_info_render.image_node.layers](#scene_info_render.image_node.layers) 
 frames       | string | frame range                                            | "0-50[1]"                                                    

**<span id="scene_info_render.image_node.layers">scene_info_render.image_node.layers</span>**


 parameter               | type   | description                                                  | example                               
---|---|---|---
frames | string | frame range | "0-50[1]" 
renderable | string | "0": do not open rendering<br>“1”: open rendering | "1" 
output | string | output path | "D:\\temp\\cam02_layer02" 
format | string | image format | "exr16" 
enable_deep_output | string | Whether the current layer should enable deep to save the output | "1" 
save_to_disk | string |  | "3"
enable_deep_output_path | string | The deep output path of the current layer | "D:\\temp\\cam02_layer02_deep" 
name | string | The name of the current layer is also the path in the scene | "project://scene/cam02.cam02_layer02" 

### 2.upload.json

> File to save assets info

**upload.json example**

```json
{
    "scene": [
        {
            "local": "E:\\work\\Trex\\ep\\ani_fly\\clarisse\\trex_fly_env_songshu.project",
            "server": "/E/work/Trex/ep/ani_fly/clarisse/trex_fly_env_songshu.project"
        }
    ],
    "asset": [
        {
            "local": "E:\\work\\Trex\\ep\\ani_fly\\clarisse\\assets\\speedtree\\guanmu01\\LeafHD2.png",
            "server": "/E/work/Trex/ep/ani_fly/clarisse/assets/speedtree/guanmu01/LeafHD2.png"
        },
        {
            "local": "E:\\work\\Trex\\ep\\ani_fly\\clarisse\\assets\\speedtree\\tree_far\\tree_far08\\HuangshanPineBark_Normal.png",
            "server": "/E/work/Trex/ep/ani_fly/clarisse/assets/speedtree/tree_far/tree_far08/HuangshanPineBark_Normal.png"
        }
    ]
}
```

**upload.json**


 parameter | type   | description                           | example                  
---|---|---|---
asset | object | Asset path information to be uploaded | refer to [asset](#asset) 
scene | object | Scene file information | refer to [scene](#scene) 

**<span id="asset">asset</span>**


 parameter | type   | description                                                  | example                                                      
---|---|---|---
local | string | local path of asset | "E:\\work\\Trex\\ep\\ani_fly\\clarisse\\assets\\speedtree\\guanmu01\\LeafHD2.png" 
server | string | Relative path on the server side, generally consistent with local | "/E/work/Trex/ep/ani_fly/clarisse/assets/speedtree/guanmu01/LeafHD2.png" 

**<span id="scene">scene</span>**

| parameter | type   | description                                                  | example                                                      |
| --------- | ------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| local     | string | local path of project                                        | "E:\\work\\Trex\\ep\\ani_fly\\clarisse\\trex_fly_env_songshu.project" |
| server    | string | Relative path on the server side, generally consistent with local | "/E/work/Trex/ep/ani_fly/clarisse/trex_fly_env_songshu.project" |



### 3.tips.json


> File to save errors, warnings


```json
{
    "50001":[
        "Nodes: /obj/flattank_fluid/compressed_cache/file_mode  File name: $HIP/geo/$HIPNAME.$OS.$F.bgeo.sc  miss file: /geo/flip_test_slice4.compressed_cache.1.bgeo.sc ",
    ]
}
```

