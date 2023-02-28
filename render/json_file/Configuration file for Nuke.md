Nuke Profile document
======

> analyze ：We analyze the information needed in the scene and save it in task.json for further analysis and processing


### 1. task.json


> Store scene analysis results, rendering settings and other information

**task.json Example**


```json
{
	"concurrent_tasks": "1",
	"software_config": {
		"cg_version": "12.1",
		"cg_name": "Nuke",
		"plugins": {}
	},
	"task_info": {
		"graphics_cards_num": "2",
		"tiles": "1",
		"project_name": "",
		"edit_name": "test02",
		"frames_per_task": "1",
		"ram": "64",
		"job_stop_time": "259200",
		"stop_after_test": "1",
		"project_id": "0",
		"time_out": "86400",
		"cg_id": "2015",
		"input_cg_file": "D:/Myx/nuke_project/test_new_pipeline.nk",
		"pre_frames": "100",
        "hardwareConfigId": ""
	},
	"scene_info": {
		"write_nodes": [
			{
				"node": "Write3",
				"inputs": "1",
				"out_file": "D:/Myx/nuke_project/output/test_bb.mov",
				"renderable": "1",
				"file_type": "mov",
				"height": "1200",
				"width": "1920",
				"proxy": "",
				"render_mode": "0",
				"option": "0",
				"frames": "1-1[1]",
				"use_proxy": "False"
			}
		]
	}
}
```

**task.json Parameter **


Parameter | Type | **Is it necessary** | **Description** | **Example** 
---|---|---|---|---
software_config | object | Y | environment(cg software, version and plugins, etc.) | [refer to software_config](#software_config) 
task_info | object | Y | render settings(priority frames, render range, etc.) | [refer to task_info](#task_info) 
scene_info_render | object | Y | analysis result(render node, output, etc.) | [refer to scene_info_render](#scene_info_render) 
concurrent_tasks | string | N | The number of tasks in the same period | "1" 

**<span id="software_config">Software_Config Parameter</span>**


Parameter | Type | Is it necessary | Description | Example 
---|---|---|---|---
cg_name | string | Y | software | "Nuke" 
cg_version | string | Y | software version | "12.1" 
plugins | object | Y | plugin{name, version} | {}

**<span id="task_info">task_info Parameter </span>**

| Parameter          | Type   | Is it necessary | Description                                                  | Default  | Example                                                      |
| ------------------ | ------ | --------------- | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ |
| graphics_cards_num | string | Y               | "1": open single card rendering;<br /> "2": open dual card rendering | "2"      | “2”                                                          |
| cg_id              | string | Y               | software id: <br />"Nuke": "2015"                            |          | "2015"                                                       |
| ram                | string | Y               | Render machine memory selection: 64 / 128                    | “64”     | "64"                                                         |
| input_cg_file      | string | Y               | Render the scene local path                                  |          | "D:/Myx/nuke_project/test_new_pipeline.nk"                   |
| job_stop_time      | string | Y               | Set the frame timeout time, will only affect the current frame, unit seconds | “259200” | "28800"                                                      |
| user_id            | string | N               | user id                                                      |          |                                                              |
| pre_frames         | string | Y               | Priority rendering (Priority frame is not recommended to customize multiple individual frames) | “000”    | "000: 1,3-4 [1]" means: Priority rendering first frame: No Priority rendering middle frame: No Priority rendering last frame: No Priority rendering custom frame: 1,3-4 [1] |
| tiles              | string | Y               | tile number, 1 for single node, greater than 1 for tiles rendering(multi-nodes) | "1"      | "1"                                                          |
| project_id         | string | Y               | project id                                                   |          | "0"                                                          |
| project_name       | string | Y               | project name                                                 | " "      | ""                                                           |
| frames_per_task    | string | Y               | The number of frames that can be rendered by one machine     | "1"      | "1"                                                          |
| stop_after_test    | string | Y               | Whether to pause the task after the priority rendering is completed "1": Pause the task after the priority rendering is completed "2". Do not pause the task after the priority rendering is completed | "2"      | “2”                                                          |
| task_id            | string | Y               | task id                                                      |          |                                                              |
| task_stop_time     | string | Y               | Large task timeout stops in unit seconds, "0" means unlimited | "0"      | "86400"                                                      |
| time_out           | string | Y               | Overtime reminder time, unit: sec                            | “43200”  | "43200"                                                      |
| concurrent_tasks   | string | N               | The number of tasks in the same period                       | "1"      | "1"                                                          |

**<span id="scene_info_render">scene_info_render Parameter</span>**


**Parameter** | **Type** | **Is it necessary** | **Description** | **Example** 
---|---|---|---|---
**write_nodes** | **List** | **Y** | **node** | **[refer to scene_info_render.write_nodes](#scene_info_render.write_nodes)** 

**<span id="scene_info_render.write_nodes">scene_info_render.write_nodes Parameter</span>**


Parameter | Type |  | **Is it necessary** | Example 
---|---|---|---|---
node | string | Y | node name | "Write3" 
proxy | string | N | proxy output path | "P:/UW/Update_17/Shot_2/Shot_02_####.png" 
frames | string | Y | Whether to use the default camera, the default value is ‘1’ (use the default camera) | "1-1[1]" 
out_file | string | N | output path | "P:/UW/Update_17/Shot_2/Shot_02_####.png" 
inputs | string | N | Whether the current output node has an input source | "0": No， “1”：Yes 
file_type | string | N | Output file format | "mov" 
render_mode | string | Y | Render output mode, the default is "0";<br />0 use scene settings；<br />1  render full resolution；<br />2 render using proxies | “0” 
width | string | Y | Wide output resolution | "9348" 
height | string | Y | High output resolution | "2242" 
use_proxy | string | N | Whether the scene has proxy mode turned on:<br /> "False"：not open；<br />"True"：open; | "False" 
renderable | string | Y | Whether to render:<br />“0”: yes<br />“1”：no | "1" 
option | string | Y | render type:<br />"-1":Normal rendering, stand-alone single frame rendering;<br />"0":Output video type, all frames will be rendered stand-alone; | "0" 

