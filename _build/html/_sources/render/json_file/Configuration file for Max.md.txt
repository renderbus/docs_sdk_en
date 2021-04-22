Max Profile document
======

> Analysis: We analyze and save the information needed in the scene to task.json, asset.json, upload.json, tips.json for further analysis and processing


### 1.task.json


> Description: Store scene analysis results, rendering settings and other information

**task.json**


```json
{
    "scene_info": {
        "common": {
            "CurrentProjectFolder": "C:/Users/dingyutao/Documents/3dsMax",
            "Faces": "3784",
            "Peak_Memory": "702.758",
            "Vertices": "1914",
            "all_camera": [
                "Camera001",
                "Camera002",
                "Camera003",
                "Camera004",
                "Camera005"
            ],
            "all_element_type": [
                ".tga",
                ".tif",
                ".jpg",
                ".png",
                ".exr",
                ".rla",
                ".rpf"
            ],
            "all_output_file_type": [
                ".tga",
                ".tif",
                ".jpg",
                ".png",
                ".exr",
                ".rla",
                ".rpf"
            ],
            "animation_range": "0-100",
            "cgv": "2018",
            "element_active": "1",
            "element_list": [
				"MultiMatteElement",
				"VRayAlpha",
				"VRayAtmosphere",
				"VRayBackground",
				"MultiMatteElement",
				"VRayAlpha",
				"VRayAtmosphere"
			],
			"element_path_list": [
				"jh_out_MultiMatteElement.rla",
				"jh_out_VRayAlpha.rla",
				"jh_out_VRayAtmosphere.rla",
				"jh_out_VRayBackground.rla",
				"jh_out_MultiMatteElement1.rla",
				"jh_out_VRayAlpha2.rla",
				"jh_out_VRayAtmosphere.rla"
			],
            "element_type": ".rla",
            "frames": "0",
            "gamma": "1",
            "gamma_val": "2.2",
            "global_proxy": "false",
            "height": "480",
            "in_gamma": "2.2",
            "is_picture": "0",
            "net_render": "0",
            "out_gamma": "2.2",
            "output_file": "E:/3D_Scene/Max/jh/output/1/jh_out.rla",
            "output_file_basename": "jh_out",
            "output_file_type": ".rla",
            "rend_save_file": "true",
            "rend_timeType": "1",
            "renderable_camera": [],
            "taskdurationlimit": "86400",
            "width": "640"
        },
        "renderer": {
            "name": "scanline",
            "renderer": "scanline",
            "renderer_orign": "Default_Scanline_Renderer"
        }
    },
    "scene_info_render": {
        "common": {
            "CurrentProjectFolder": "C:/Users/dingyutao/Documents/3dsMax",
            "Faces": "3784",
            "Peak_Memory": "702.758",
            "Vertices": "1914",
            "all_camera": [
                "Camera001",
                "Camera002",
                "Camera003",
                "Camera004",
                "Camera005"
            ],
            "all_element_type": [
                ".tga",
                ".tif",
                ".jpg",
                ".png",
                ".exr",
                ".rla",
                ".rpf"
            ],
            "all_output_file_type": [
                ".tga",
                ".tif",
                ".jpg",
                ".png",
                ".exr",
                ".rla",
                ".rpf"
            ],
            "animation_range": "0-100",
            "cgv": "2018",
            "element_active": "1",
            "element_list": [
                "Missing_Render_Element_Plug_in",
                "Missing_Render_Element_Plug_in",
                "Missing_Render_Element_Plug_in",
                "Missing_Render_Element_Plug_in",
                "Missing_Render_Element_Plug_in",
                "Missing_Render_Element_Plug_in",
                "Missing_Render_Element_Plug_in"
            ],
            "element_path_list": [],
            "element_type": ".rla",
            "frames": "0",
            "gamma": "1",
            "gamma_val": "2.2",
            "global_proxy": "false",
            "height": "480",
            "in_gamma": "2.2",
            "is_picture": "0",
            "net_render": "0",
            "out_gamma": "2.2",
            "output_file": "E:/3D_Scene/Max/jh/output/1/jh_out.rla",
            "output_file_basename": "jh_out",
            "output_file_type": ".rla",
            "rend_save_file": "true",
            "rend_timeType": "1",
            "renderable_camera": [
                "Camera001"
            ],
            "width": "640"
        },
        "renderer": {
            "name": "scanline",
            "renderer": "scanline",
            "renderer_orign": "Default_Scanline_Renderer"
        }
    },
    "software_config": {
        "cg_name": "3ds Max",
        "cg_version": "2018",
        "plugins": {}
    },
    "task_info": {
        "cg_id": "2001",
        "channel": "4",
        "distribute_render_node": "3",
        "enable_layered": "0",
        "frames_per_task": "1",
        "input_cg_file": "D:/houdini/CG file/jh/jh.max",
        "input_project_path": "",
        "is_distribute_render": "0",
        "is_layer_rendering": "1",
        "is_picture": "0",
        "job_stop_time": "259200",
        "os_name": "1",
        "platform": "2",
        "pre_frames": "100",
        "project_id": "200953",
        "project_name": "Project1",
        "ram": "64",
        "render_layer_type": "0",
        "stop_after_test": "1",
        "task_id": 28474141,
        "task_stop_time": "0",
        "tiles": "1",
        "tiles_type": "block",
        "time_out": "43200",
        "user_id": 100150764
    },
    "additional_info": {}
}
```

**task.json**


parameter | type | Is it necessary | description | example 
---|---|---|---|---
software_config | dict | Y | environment(cg software, version and plugins, etc.) | [refer to software_config](#software_config) 
task_info | dict | Y | render settings(priority frames, render range, etc.) | [refer to task_info](#task_info) 
scene_info_render | dict | Y | analysis result(render node, output, etc.) | [refer to scene_info_render](#scene_info_render) 
scene_info | dict | N | same as scene_info_render | 
additional_info | dict | N | Location of user-defined parameters (need to use custom parameters, need to confirm with the company business personnel) |  

**<span id="software_config">software_config</span>**


parameter | type | Is it necessary | description | example 
---|---|---|---|---
cg_name | string | Y | software name | "3ds Max" 
cg_version | string | Y | software version | "2001" 
plugins | object | Y | rendering plugin | {} 

**<span id="task_info">task_info</span>**

| parameter              | type   | Is it necessary | description                                                  | default  | example                                                      |
| ---------------------- | ------ | --------------- | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ |
| graphics_cards_num     | string | Y               | 1： open single card rendering 2: open dual card rendering   | "2"      |                                                              |
| enable_layered         | string | Y               | render layer mode,"0":off, "1":on                            | "0"      | "1"                                                          |
| cg_id                  | string | Y               | software id."2001": Max                                      |          | "2001"                                                       |
| ram                    | string | Y               | ram: 64 / 128                                                | "64"     | "64"                                                         |
| os_name                | string | Y               | Rendering machine operating system:  "0":Linux; "1": Windows | "1"      | "1"                                                          |
| render_layer_type      | string | N               | render layer mode:  "0"：renderlayer "1"：rendersetup        | "0"      | "0"                                                          |
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

> **Note**:
>
> - Only when the GI setting is enabled can you use block rendering. The tile rendering mode (tiles_type) and the multi-frame rendering mode (frames_per_task) are mutually exclusive. Only one mode can be used at the same time.
> - Max temporarily does not support distributed rendering (is_distribute_render).
> - Max no layered rendering (enable_layered).

**<span id="scene_info_render">scene_info_render</span>**


parameter | type | Is it necessary | description | example 
---|---|---|---|---
renderer | dict | Y | Renderer | [refer to scene_info_render.renderer](#scene_info_render.renderer) 
common | dict | Y | Scene general information | [refer to scene_info_render.common](#scene_info_render.common) 

**<span id="scene_info_render.common">scene_info_render.common</span>**


parameter | type | Is it necessary | description | example 
---|---|---|---|---
CurrentProjectFolder | string | Y | The project path of the scene | "C:/Users/dingyutao/Documents/3dsMax" 
Faces | string | N | Number of faces in the scene | "3784" 
Peak_Memory | string | Y | Peak memory | "702.758" 
Vertices | string | Y | vertex | "1914" 
all_camera | list | Y | List of all cameras | ["Camera001", "Camera002"，“Camera003”] 
all_element_type | list | Y | All supported rendering element types | [<br/>                ".tga",<br/>                ".tif",<br/>                ".jpg",<br/>                ".png",<br/>                ".exr",<br/>                ".rla",<br/>                ".rpf"<br/>            ] 
all_output_file_type | list | Y | All supported output file types | [<br/>                ".tga",<br/>                ".tif",<br/>                ".jpg",<br/>                ".png",<br/>                ".exr",<br/>                ".rla",<br/>                ".rpf"<br/>            ] 
animation_range | string | N | Animation frame range                  | "0-100" 
cgv | string | Y | Max software version | “2018“ 
element_active | string | Y | Whether to output rendering elements<br/>"1": output; "0": no output | "1" 
element_list | list | Y | Render element list | [<br/>				"MultiMatteElement",<br/>				"VRayAlpha",<br/>				"VRayAtmosphere",<br/>				"VRayBackground",<br/>				"MultiMatteElement",<br/>				"VRayAlpha",<br/>				"VRayAtmosphere"<br/>			] 
element_path_list | list | N | List of element paths | [<br/>				"jh_out_MultiMatteElement.rla",				"jh_out_VRayAlpha.rla",<br/>				"jh_out_VRayAtmosphere.rla",<br/>				"jh_out_VRayBackground.rla",<br/>				"jh_out_MultiMatteElement1.rla",<br/>				"jh_out_VRayAlpha2.rla",<br/>				"jh_out_VRayAtmosphere.rla"<br/>			] 
element_type | string | Y | Output element type | ".rla" 
frames | string | Y | Current rendered frame | “0” 
gamma | string | Y | Whether gamma is enabled in the scene<br/>"1": enabled; <br/>"0": not enabled | “1” 
gamma_val | string | Y | Gamma | “2.2” 
global_proxy | string | Y | Whether to open the global agent | “false” 
height | string | Y | Resolution, high | "480" 
width | string | Y | Resolution, width | "640" 
in_gamma | string | Y | fileingamma | "2.2" 
is_picture | string | Y | "0: Effect Chart "1": Animation Chart | "0" 
net_render | string | N | Whether network rendering<br/>"1": on; <br/>"0": not on | "0" 
out_gamma | string | Y | fileoutgamma | "2.2" 
output_file | string | Y | The main image output path in the scene | "E:/3D_Scene/Max/jh/output/1/jh_out.rla" 
rend_save_file | string | N | Whether to save the output file | “true” 
rend_timeType | string | N | rendTimeType | “1” 
renderable_camera | list | N | Need to submit the rendered camera | ["Camera001"] 

**<span id="scene_info_render.renderer">scene_info_render.renderer</span>**

| parameter      | type   | Is it necessary | description                  | example                     |
| -------------- | ------ | --------------- | ---------------------------- | --------------------------- |
| name           | string | Y               | renderers.production         | "scanline"                  |
| renderer       | string | Y               | classof renderers.production | "scanline"                  |
| renderer_orign | string | Y               | renderer orign               | "Default_Scanline_Renderer" |

### 2.upload.json


> Description: Store asset path information to be uploaded

**upload.json**

```json
{
    "asset": [
        {
            "server": "/C/3D_Scene/Max/jh/3d66Model-545019-files-1.JPG",
            "local": "D:/houdini/CG file/jh/3d66Model-545019-files-1.JPG"
        },
        {
            "server": "/C/3D_Scene/Max/jh/3d66Model-545019-files-3.jpg",
            "local": "D:/houdini/CG file/jh/3d66Model-545019-files-3.jpg"
        },
        {
            "server": "/C/3D_Scene/Max/jh/3d66Model-545019-files-4.jpg",
            "local": "D:/houdini/CG file/jh/3d66Model-545019-files-4.jpg"
        },
        {
            "server": "/C/3D_Scene/Max/jh/3d66Model-545019-files-6.JPG",
            "local": "D:/houdini/CG file/jh/3d66Model-545019-files-6.JPG"
        },
        {
            "server": "/C/3D_Scene/Max/jh/3d66Model-545019-files-8.jpg",
            "local": "D:/houdini/CG file/jh/3d66Model-545019-files-8.jpg"
        },
        {
            "server": "/C/Program Files/Autodesk/3ds Max 2018/maps/uvwunwrap/UV_Checker.png",
            "local": "C:/Program Files/Autodesk/3ds Max 2018/maps/uvwunwrap/UV_Checker.png"
        },
        {
            "server": "/D/houdini/CG file/jh/jh.max.7z",
            "local": "C:/workspace/max/1593418445/jh.max.7z"
        }
    ],
    "scene": {
        "hash": "8a0d163994a2361808b6f5390967a614",
        "server": "/D/houdini/CG file/jh/jh.max.7z",
        "local": "C:/workspace/max/1593418445/jh.max.7z"
    },
    "vrlmap": [],
    "vrmap": []
}
```

**upload.json**


parameter | type | description | description | example 
---|---|---|---|---
asset | list | Y | Asset path information to be uploaded | [refer to asset](#asset) 
scene | dict | Y | Information of scene compressed files to be uploaded | 
vrlmap | list | N | Light cache information to be uploaded | 
vrmap | list | N | The cache information of the luminous texture to be uploaded | 

**<span id="asset">asset</span>**


parameter | type | description | example 
---|---|---|---
local | string | Asset local path | "D:/chensr/scene/maya2016_multi_layers_cameras.ma"
server | string | Server-side relative paths are generally consistent with local. | "/D/chensr/scene/maya2016_multi_layers_cameras.ma"


### 3.tips.json


>  Description: Storage of analytical errors, warnings


```json
{
    "10035": [
        "not activation camera"
    ],
    "15031": [
        "Missing_Render_Element_Plug_in",
        "Missing_Render_Element_Plug_in",
        "Missing_Render_Element_Plug_in",
        "Missing_Render_Element_Plug_in",
        "Missing_Render_Element_Plug_in",
        "Missing_Render_Element_Plug_in",
        "Missing_Render_Element_Plug_in"
    ]
}
```

