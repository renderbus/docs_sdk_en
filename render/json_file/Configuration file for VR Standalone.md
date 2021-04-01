**VR Standalone** Profile document
======

> analyze ：We analyze the information needed in the scene and save it in task.json for further analysis and processing


### 1.task.json


> Store scene analysis results, rendering settings and other information

**task.json**


```json
{
	"software_config": {
		"plugins": {},
		"cg_version": "standalone_vray5.00.05",
		"cg_name": "VR Standalone"
	},
	"scene_info": {},
	"task_info": {
		"multi_node": "0",
		"tiles": "1",
		"edit_name": "",
		"project_id": "0",
		"job_stop_time": "86400",
		"stop_after_test": "1",
		"concurrent_tasks": "1",
		"frames_per_task": "1",
		"project_name": "",
		"time_out": "43200",
		"cg_id": "2008",
		"input_cg_file": "D:/houdini/cg_file/test2014vr_vraystandaloneaCopy.vrscene",
        "is_distribute_render": "1",
		"distribute_render_node": "3"
	}
}
```

**task.json**


 Parameter       | Type   | **Is it necessary** | **Description**                                      | **Example**                                  
---|---|---|---|---
software_config | object | Y | environment(cg software, version and plugins, etc.) | [refer to software_config](#software_config) 
task_info | object | Y | render settings(priority frames, render range, etc.) | [refer to task_info](#task_info) 
scene_info | object | Y | analysis result(render node, output, etc.) |  

**<span id="software_config">software_config</span>**


 Parameter  | Type   | Is it necessary | Description           | Example                  
---|---|---|---|---
cg_name | string | Y | software | "VR Standalone" 
cg_version | string | Y | software version | "standalone_vray5.00.05" 
plugins | object | N | plugin{name, version} | {}

**<span id="task_info">task_info</span>**

| Parameter              | Type   | Is it necessary | Description                                                  | Default  | Example                                                     |
| ---------------------- | ------ | --------------- | ------------------------------------------------------------ | -------- | ----------------------------------------------------------- |
| tiles                  | string | N               | tile number, 1 for single node, greater than 1 for tiles rendering(multi-nodes) | "1"      | "1"                                                         |
| project_id             | string | N               | project id                                                   |          | "0"                                                         |
| job_stop_time          | string | N               | Set the frame timeout time, will only affect the current frame, unit seconds | “259200” | "28800"                                                     |
| stop_after_test        | string | N               | Whether to pause the task after the priority rendering is completed "1": Pause the task after the priority rendering is completed "2". Do not pause the task after the priority rendering is completed | "2"      | “2”                                                         |
| project_name           | string | N               | project name                                                 | " "      | ""                                                          |
| time_out               | string | N               | Time-out, task yellowing Time-out reminder, in seconds       | “43200”  | "43200"                                                     |
| cg_id                  | string | N               | software id, <br>"VR Standalone": "2008"                     |          | "2008"                                                      |
| input_cg_file          | string | Y               | Render the scene path                                        |          | "D:/houdini/cg_file/test2014vr_vraystandaloneaCopy.vrscene" |
| is_distribute_render   | string | N               | Whether to turn on distribution is rendering<br>"1": open ;<br>"0": Not open;<br>Default is not open | "0"      | "1"                                                         |
| distribute_render_node | string | N               | The number of distributed rendering nodes is controlled as far as possible to "3", "6", "9". | “0”      | "3"                                                         |
| user_id                | string | N               | user id                                                      |          |                                                             |
| task_id                | string | N               | task id                                                      |          |                                                             |
| ram                    | string | N               | Render machine memory selection: 64 / 128                    | “64”     | "64"                                                        |

