 **Arnold Standalone**  Configuration
===================


### 1.task.json


> File to save the analysis result of the scene, including scene name, cg software version, render settings, etc.

**task.json**


```json
{
    "software_config": {
        "plugins": {},
        "cg_version": "6.0.3.0",
        "cg_name": "Arnold Standalone"
    },
    "task_info": {
        "test_frames": "111",
        "tiles": "1",
        "graphics_cards_num": "2",
        "edit_name": "arnord1111",
        "job_stop_time": "86400",
        "stop_after_test": "1",
        "frames_per_task": "1",
        "ram": "64",
        "time_out": "43600",
        "pre_frames": "100",
        "task_id": "38226011",
        "user_id": "100150764",
        "project_name": "ff",
        "project_id": "426731",
        "input_cg_file": "E:/fang/ass_test/static_ass.ass",
        "task_stop_time": "86400",
        "cg_id": 2003
    },
    "additional_info": {},
    "scene_info_render": {
        "common": {
            "frames": "1-10[1]"
        }
    }
}
```

**task.json**


 parameter         | type   | Is it necessary | description                                          | example                                          
---|---|---|---|---
software_config | dict | Y | environment(cg software, version and plugins, etc.) | refer to [software_config](#software_config) 
task_info | dict | Y | render settings(priority frames, render range, etc.) | refer to [task_info](#task_info) 
scene_info_render | dict | Y | analysis result(render node, output, etc.) | refer to [scene_info_render](#scene_info_render) 

**<span id="software_config">software_config</span>**


 parameter  | type   | Is it necessary | description | example 
---|---|---|---|---
cg_name | string | Y | software | "Arnold Standalone" 
cg_version | string | Y | software version | "6.0.3.0" 
plugins | dict | N | The SDK or kernel version of Arnold | {}

**<span id="task_info">task_info</span>**

| parameter          | type   | Is it necessary | description                                                  | default  | example                                                      |
| ------------------ | ------ | --------------- | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ |
| graphics_cards_num | string | Y               | 1： open single card rendering 2: open dual card rendering   | "2"      | "2"                                                          |
| ram                | string | Y               | ram: 64 / 128                                                | "64"     | "64"                                                         |
| input_cg_file      | string | Y               | Input file path,you have to use backslashes                  |          | "E:/fang/ass_test/static_ass.ass"，or Serialized rendering: "E:/fang/ass_test/animation_ass.####.ass" |
| job_stop_time      | string | Y               | Set the frame timeout time, will only affect the current frame, unit seconds | "259200" | "28800"                                                      |
| user_id            | string | N               | user id,not necessary, can be automatically obtained from the server |          | "100150764"                                                  |
| pre_frames         | string | Y               | Priority rendering (priority frames are not recommended to customize multiple individual frames) | "000"    | "000: 1,3-4 [1]" means:  Priority rendering first frame: No  Priority rendering middle frame: No  Priority rendering last frame: No  Priority rendering custom frame: 1,3-4 [1] |
| project_id         | string | N               | project id                                                   | "0"      | "426731"                                                     |
| project_name       | string | N               | project name                                                 |          | "ff"                                                         |
| tiles              | string | N               | tile number, 1 for single node, greater than 1 for tiles rendering(multi-nodes) | "1"      | "1"                                                          |
| stop_after_test    | string | Y               | "1":pause after priority render, "2":continue after priority render (default "2") | "2"      | "2"                                                          |
| task_id            | string | N               | task id,Not necessary, can be automatically obtained from the server |          | "38226011"                                                   |
| task_stop_time     | string | N               | Large task timeout stops in unit seconds, "0" means unlimited | "0"      | "86400"                                                      |
| time_out           | string | Y               | Overtime reminder time, unit: sec                            | "43200"  | "43200"                                                      |
| cg_id              | int    | Y               | Arnold rendering cgid can only be 2003                       |          | 2003                                                         |

**<span id="scene_info_render">scene_info_render</span>**


 parameter         | type          | Is it necessary | description                                        | example                                    
---|---|---|---|---
common | string | Y | Public parameters for rendering |  
 frames    | string | Y               | Frame range for rendering       | "1-10[1]" 


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

**<span id="asset">asset Parametric Interpretation</span>**


 parameter | type   | description                                                  | example                                            
---|---|---|---
local | string | local path of asset | "D:/chensr/scene/maya2016_multi_layers_cameras.ma"
server | string | Relative path on the server side, generally consistent with local | "/D/chensr/scene/maya2016_multi_layers_cameras.ma"

