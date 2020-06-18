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
        "enable_layered":"1",
        "is_distribute_render":"0",
        "time_out":"43200",
        "tiles_type":"block",
        "user_id":"100150764",
        "cg_id":"2013",
        "input_cg_file":"E:/copy/DHGB_sc05_zhuta_610-1570_v0102.project",
        "os_name":"1",
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

| parameter              | type   | Is it necessary | description                                                  | default  | example                                                      |
| ---------------------- | ------ | --------------- | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ |
| graphics_cards_num     | string | Y               | 1: open single card rendering 2: open dual card rendering   | "2"      | "2"                                                          |
| enable_layered         | string | Y               | render layer mode,"0":off, "1":on                            | "0"      | "1"                                                          |
| cg_id                  | string | Y               | software id."2013": Clarisse                                 |          | "2013"                                                       |
| ram                    | string | Y               | ram: 64 / 128                                                | "64"     | "64"                                                         |
| os_name                | string | Y               | Rendering machine operating system:  "0":Linux; "1": Windows | "1"      | "1"                                                          |
| render_layer_type      | string | N               | render layer mode:  "0"：renderlayer方式 "1"：rendersetup方式 | "0"      | "0"                                                          |
| is_distribute_render   | string | N               | distributed render mode,"0":off, "1":on                      | "0"      | "0"                                                          |
| input_cg_file          | string | Y               | input file path                                              |          | "E:/copy/DHGB_sc05_zhuta_610-1570_v0102.project"             |
| input_project_path     | string | Y               | project path, could be empty                                 | " "      |                                                              |
| job_stop_time          | string | Y               | Set the frame timeout time, will only affect the current frame, unit seconds | "259200" | "28800"                                                      |
| user_id                | string | Y               | user id                                                      |          |                                                              |
| pre_frames             | string | Y               | Priority rendering (priority frames are not recommended to customize multiple individual frames) | "000"    | "000: 1,3-4 [1]" means:  Priority rendering first frame: No  Priority rendering middle frame: No  Priority rendering last frame: No  Priority rendering custom frame: 1,3-4 [1] |
| platform               | string | Y               | submit platform : "2": "www2", "3": "www3", "6": "www4", "21": "gpu", |          | "2"                                                          |
| is_picture             | string | Y               | "0: Effect Chart "1": Animation Chart                        | "0"      | "0"                                                          |
| project_id             | string | Y               | project id                                                   | " "      | "200953"                                                     |
| project_name           | string | Y               | project name                                                 | " 0"     | "Project1"                                                   |
| channel                | string | Y               | 1:Web local analysis (animation deduction); 2:web cloud analysis; 3:Rendering plugin submission； 4：API/SDK submission; 8：Animation plugin submission | "4"      | "4"                                                          |
| tiles_type             | string | Y               | "block, strip"                                               | "block"  | "block"                                                      |
| tiles                  | string | Y               | tile number, 1 for single node, greater than 1 for tiles rendering(multi-nodes) | "1"      | "1"                                                          |
| distribute_render_node | string | N               | nodes number for distributed rendering                       | "3"      | "3"                                                          |
| frames_per_task        | string | Y               | frames per task                                              | "1"      | "1"                                                          |
| stop_after_test        | string | Y               | "1":pause after priority render, "2":continue after priority render (default "2") | "2"      | "2"                                                          |
| task_id                | string | Y               | task id                                                      |          |                                                              |
| task_stop_time         | string | Y               | Large task timeout stops in unit seconds, "0" means unlimited | "0"      | "86400"                                                      |
| time_out               | string | Y               | Overtime reminder time, unit: sec                            | "43200"  | "43200"                                                      |

> **Note:** Clarisse temporarily does not support distributed rendering (is_distribute_render) and tiled rendering (tiles)

**<span id="scene_info_render">scene_info_render</span>**


 parameter  | type   | description  | example                                                      
---|---|---|---
image_node | object | Clarisse IFX includes all images in the scene and 3dlayer under the image, and clarisse BUiLDER includes all VariableRange in the scene and ImageNodeWrite under VariableRange. | refer to [scene_info_render.image_node](#scene_info_render.image_node) 

**<span id="scene_info_render.common">scene_info_render.image_node</span>**


 parameter    | type   | description                                                  | example                                                      
---|---|---|---
renderable | string | "0": do not open rendering,<br>“1”: open rendering (this is not the value in the scene,the platform is not open by default, the platform is notrecommended to directly render image and VariableRange) | "0" 
output | string | The output path of the current image in clarisse IFX, no output in clarisse BUiLDER The output path of the current image in clarisse IFX, no in clarisse BUiLDER | "D:\temp\cam02" 
format | string | The output format of the current image in clarisse IFX, optional value, none under clarisse BUiLDER | "exr16" 
LUT | string | The stringIFX manages the output color of the current image. Non-essential values, none under clarisse BUiLDER | "linear" 
save_to_disk | string | Whether to save the output of the current image in clarisse IFX, no under clarisse BUiLDER | "1" 
name | string | The name of the current image in clarisse IFX, the name of the current VariableRange in clarisse BUiLDER, and the path of the two in the scene | "project://scene/cam02" 
layers | string | IFX is the 3dlayer in the current image, the value is list, the value of list is dict, there are several layers of dict in the current image, there are several layers of dict, clarisse BUiLDER is the ImageNodeWrite in the current VariableRange, the value is list, The value of list is dict. How many ImageNodeWrites are in the current VariableRange, there are several dicts of ImageNodeWrites. See scene_info_render.image_node.layers object analysis | [scene_info_render.image_node.layers](#scene_info_render.image_node.layers) 
 frames       | string | clarisse IFX is the frame range of the current image, clarisse BUiLDER is the value of the F or Frame variable of the current VariableRange | "0-50[1]"                                                    

**<span id="scene_info_render.image_node.layers">scene_info_render.image_node.layers</span>**


 parameter               | type   | description                                                  | example                               
---|---|---|---
frames | string | clarisse IFX is the current 3dlayer start frame and end frame, and clarisse BUiLDER is the coverage value of the ImageNodeWrite under the current VariableRange | "0-50[1]" 
renderable | string | "0": do not open rendering<br>“1”: open rendering | "1" 
output | string | The output path of the current layer in clarisse IFX, not under clarisse BUiLDER | "D:\\temp\\cam02_layer02" 
format | string | The output format of the current layer or ImageNodeWrite | "exr16" 
enable_deep_output | string | Whether to enable deep save output for the current layer in clarisse IFX, no under clarisse BUiLDER | "1" 
save_to_disk | string | Whether to save the output of the current layer in clarisse IFX, no under clarisse BUiLDER | "1"
enable_deep_output_path | string | clarisse IFX is the deep output path of the current layer, there is no under clarisse BUiLDER | "D:\\temp\\cam02_layer02_deep" 
name | string | 1: The current layer name in clarisse IFX is also the path in the scene; <br/>2: The name of the current ImageNodeWrite in clarisse BUiLDER, the value is the path in the scene of the current VariableRange and the current imageNodeWrite in the scene Path to === link | 1："project://scene/cam02.cam02_layer02"<br/>2：“build://yt_0080===build://cloudShadow” 

> 

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

