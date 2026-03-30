# Unreal Engine Configuration File Documentation

> Analysis: We extract the required information from the scene and save it into `task.json`, `asset.json`, `upload.json`, and `tips.json` for further parsing and processing.

------

### 1. task.json Parsing

> Description: Stores scene analysis results, rendering settings, and other related information.

**Example of `task.json`**

```json
{
    "scene_info_render": {
      "all_game_map": [
        "/Game/Levels/MH_Ragdoll/MH_Ragdoll",
        "/Game/Levels/MH_Ragdoll/MH_Ragdoll_AI",
      ],
      "all_movie_pipline_queue": [
        {
          "renderable": "1",
          "render_job": [
            {
              "origin_height": "1080", 
              "frames": "0-1[1]",
              "origin_width": "1920",
              "is_enable": "1",
              "file_name_format": "{sequence_name}.{frame_number}",
              "job_sequence": "/Game/Sequencer/MetaHumanSample_Sequence",
              "start_frame": "0",
              "job_map": "/Game/Levels/MetaHumanSample",
              "custom_end_frame": "0",
              "format_type": [
                "JPG"
              ],
              "job_num": "0",
              "job_name": "MetaHumanSample_Sequence",
              "end_frame": "1562",
              "width": "1920",
              "custom_start_frame": "0",
              "job_valid": "1",
              "flush_disk_writes_per_shot": false,
              "height": "1080"
            },
            {
              "origin_height": "1080",
              "frames": "0-1[1]",
              "origin_width": "1920",
              "is_enable": "1",
              "file_name_format": "{sequence_name}.{frame_number}",
              "job_sequence": "/Game/Sequencer/MetaHumanSample_Sequence",
              "start_frame": "0",
              "job_map": "/Game/Levels/MetaHumanSample",
              "custom_end_frame": "0",
              "format_type": [
                "JPG"
              ],
              "job_num": "1",
              "job_name": "MetaHumanSample_Sequence",
              "end_frame": "1562",
              "width": "1920",
              "custom_start_frame": "0",
              "job_valid": "1",
              "flush_disk_writes_per_shot": false,
              "height": "1080"
            }
          ],
          "name": "/Game/JOB/EditorMoviePipelineQueue",
          "all_format_type": [
            "PNG",
            "EXR",
            "TIFF",
            "jpg"
          ]
        }
      ],
      "render_mod": "mrq",
      "all_level_sequence": [
        "/Game/Sequencer/MetaHumanSample_Sequence"
      ]
    }, 
    "task_info": {
        "is_layer_rendering": "1", 
        "cg_id": "2020", 
        "ram": "64", 
        "os_name": "1", 
        "render_layer_type": "0", 
        "is_distribute_render": "0", 
        "input_cg_file": "D:/files/CG file/test.uproject", 
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
        "cg_version": "5.4.4", 
        "cg_name": "Unreal Engine", 
        "plugins": {},
        "cg_inst_dir": "C:/Program Files/Epic Games/UE_5.4"
    }
}
```

**Parameter Descriptions for `task.json`**

| Parameter         | Type   | Description                              | Example                                  |
| ----------------- | ------ | ---------------------------------------- | ---------------------------------------- |
| software_config   | object | Rendering environment (software type, version, plugins used) | [See software_config](#software_config)  |
| task_info         | object | Rendering settings (priority frames, number of frames, timeout, etc.) | [See task_info](#task_info)              |
| scene_info_render | object | Scene analysis results (render nodes, output paths, etc.) | [See scene_info_render](#scene_info_render) |

------

**<span id="software_config">software_config Object</span>**

| Parameter            | Type   | Description                              | Example                              |
| -------------------- | ------ | ---------------------------------------- | ------------------------------------ |
| cg_name              | string | Software name                            | "Unreal Engine"                      |
| cg_version           | string | Software version                         | "5.4.4"                              |
| plugins              | object | Plugin object.Key: plugin name, Value: version | {}                                   |
| cg_inst_dir | string | Local UE installation path               | "C:/Program Files/Epic Games/UE_5.4" |

------

**<span id="task_info">task_info Object</span>**

| Parameter              | Type   | Description                              | Example |
| ---------------------- | ------ | ---------------------------------------- | ------- |
| is_layer_rendering     | string | Enable layer rendering."0": Disabled"1": Enabled | "1"     |
| cg_id                  | string | Rendering software ID. "2020": Unreal Engine | "2020"  |
| ram                    | string | Memory requirement. 64/128               | "64"    |
| os_name                | string | Render OS. "0": Linux; "1": Windows (Windows only) | "0"     |
| render_layer_type      | string | Layer selection method."0": renderlayer"1": rendersetup | "0"     |
| is_distribute_render   | string | Enable distributed rendering."0": Disabled"1": Enabled | "0"     |
| input_cg_file          | string | Local path to the rendering scene        |         |
| job_stop_time          | string | Timeout for subtask stop, in seconds     | "28800" |
| user_id                | string | User ID                                  |         |
| pre_frames             | string | Priority rendering."000:1,3-4[1]" means:Priority first frame: NoPriority middle frames: NoPriority last frame: NoPriority custom frames: 1,3-4[1] |         |
| platform               | string | Submission platform                      | "2"     |
| is_picture             | string | Whether it's a still image               | "0"     |
| project_id             | string | Project ID                               |         |
| channel                | string | Submission method. "4": API/SDK          | "4"     |
| tiles_type             | string | "block" or "strip"                       | "block" |
| tiles                  | string | Number of tiles. >1 for block/strip, =1 for single machine | "1"     |
| project_name           | string | Project name                             | "test"  |
| distribute_render_node | string | Number of distributed render nodes       | "3"     |
| frames_per_task        | string | Number of frames rendered per machine    | "1"     |
| stop_after_test        | string | Whether to pause after priority rendering."1": Pause"2": Do not pause |         |
| input_project_path     | string | Project path, empty if not set           |         |
| task_id                | string | Task ID                                  |         |
| task_stop_time         | string | Main task timeout, in seconds            | "86400" |
| time_out               | string | Timeout in hours                         | "12"    |

------

**<span id="scene_info_render">scene_info_render Object</span>**

| Parameter               | Type          | Description                      | Example                                  |
| ----------------------- | ------------- | -------------------------------- | ---------------------------------------- |
| all_game_map            | array<string> | All maps (levels) in the project | ["/Game/Levels/MH_Ragdoll/MH_Ragdoll"]   |
| all_movie_pipline_queue | object        | All MRQ render queues            | See all_movie_pipline_queue              |
| render_mod              | string        | Render mode (MRQ/MSC)            | "mrq"                                    |
| all_level_sequence      | array<string> | All sequences in the project     | ["/Game/Sequencer/MetaHumanSample_Sequence"] |

------

**<span id="mrq">all_movie_pipline_queue Object</span>**

| Parameter       | Type          | Description            | Example                              |
| --------------- | ------------- | ---------------------- | ------------------------------------ |
| renderable      | string        | Layer rendering switch | "1"                                  |
| render_job      | object        | Render job details     | See render_job                       |
| name            | string        | Render queue name      | "/Game/JOB/EditorMoviePipelineQueue" |
| all_format_type | array<string> | List of output formats | ["PNG", "EXR", "TIFF", "jpg"]        |

------

**<span id="render_job">render_job Object</span>**

| Parameter                  | Type          | Description                              | Example                             |
| -------------------------- | ------------- | ---------------------------------------- | ----------------------------------- |
| origin_width               | string        | Original scene width                     | "1920"                              |
| origin_height              | string        | Original scene height                    | "1080"                              |
| width                      | string        | Output width                             | "1920"                              |
| height                     | string        | Output height                            | "1080"                              |
| is_enable                  | string        | Whether the job is renderable (MRQ setting) | "1"                                 |
| custom_start_frame         | string        | Sequence start frame (from analysis)     | "0"                                 |
| custom_end_frame           | string        | Sequence end frame (from analysis)       | "150"                               |
| start_frame                | string        | Render start frame                       | "0"                                 |
| end_frame                  | string        | Render end frame                         | "1"                                 |
| frames                     | string        | Frame range description                  | "1-10[1]"                           |
| file_name_format           | string        | Output file naming template (MRQ setting) | "{sequence_name}.{frame_number}"    |
| job_sequence               | string        | Sequence associated with the job         | "/Game/Sequences/Sun/Seq_MasterSun" |
| job_map                    | string        | Map (level) associated with the job      | "/Game/Main"                        |
| format_type                | array<string> | Output image formats                     | ["JPG"]                             |
| job_num                    | string        | Job index in MRQ queue                   | "0"                                 |
| job_name                   | string        | Job name                                 | "Seq_MasterSun"                     |
| job_valid                  | string        | Whether the job is valid (1=valid, 0=invalid) | "1"                                 |
| flush_disk_writes_per_shot | bool          | Whether to flush disk writes after each shot | false                               |

------

### **2. upload.json Parsing**

> Description: Stores asset path information to be uploaded.

**Example of `upload.json**`

```json
{
  "asset": [
    {
      "local": "D:/files/CG file/test.uproject",
      "server": "/D/files/CG file/test.uproject"
    }
  ]
}
```

**Parameter Descriptions for `upload.json`**

| Parameter | Type   | Description                      | Example   |
| --------- | ------ | -------------------------------- | --------- |
| asset     | object | Asset path information to upload | See asset |

------

**<span id="asset">asset Object</span>**

| Parameter | Type   | Description                              | Example                          |
| --------- | ------ | ---------------------------------------- | -------------------------------- |
| local     | string | Local asset path                         | "D:/files/CG file/test.uproject" |
| server    | string | Relative server path, usually same as local | "/D/files/CG file/test.uproject" |

------

### 3. tips.json Parsing

> Description: Stores error and warning messages from the analysis.

```json
{}
```

