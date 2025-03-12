# SDK tutorial

### I. Login authentication

```
render_para = {
    "domain": "task.renderbus.com",  # If it doesn't work, you can use "task.foxrenderfarm.com"
    "platform": "62",
    "access_id": "xxxx",
    "access_key": "xxxx",
}

api = RayvisionAPI(
        access_id=render_para['access_id'],
        access_key=render_para['access_key'],
        domain=render_para['domain'],
        platform=render_para['platform']
    )
```

RayvisionAPI Parameters:

| Parameters | Type   | Required | Default            | Description                                      |
| ---------- | ------ | -------- | ------------------ | ------------------------------------------------ |
| domain     | string | Y        | task.renderbus.com | China user：task.renderbus.com                   |
| platform   | string | Y        | 62                 | platform ID，example: W3:"62", GPU Region 1:"21" |
| access_id  | string | Y        |                    | user authorization id                            |
| access_key | string | Y        |                    | user authorization key                           |

### II. Analysis of the scene

> Analysis is independent(Maya / Houdini / Clarisse)

Example for Houdini:

```
from rayvision_houdini.analyze_houdini import AnalyzeHoudini

analyze_info = {
    "cg_file": r"D:\files\CG FILE\flip_test_slice4.hip",
    "workspace": "c:/workspace",
    "software_version": "17.5.293",
    "project_name": "Project1",
    "plugin_config": {
        'renderman': '22.6'
    }
}
analyze_obj = AnalyzeHoudini(**analyze_info)
analyze_obj.analyse()
```

Instructions：

- "workspace" is used to control the location of the generated json file. If workspace is not set, the default location is generated:

  ```
  windows : os.environ["USERPROFILE"] + "renderfarm_sdk"  
  Linux：os.environ["HOME"] + “renderfarm_sdk”
  ```
- Analytically generated task.json is no “task_id”、“user_id”、"project_id" parameters，Users can choose to write the three parameters themselves, or to write the three parameters automatically when check.

AnalyzeHoudini Parameters:

| Parameters       | Type   | Required | Default | Description                                                                                                  |
| ---------------- | ------ | -------- | ------- | ------------------------------------------------------------------------------------------------------------ |
| cg_file          | string | Y        |         | Scenario files to analyze                                                                                    |
| software_version | string | Y        |         | The version of the software                                                                                  |
| project_name     | string | N        |         | The project name                                                                                             |
| plugin_config    | dict   | N        |         | The plug-in configuration，example {'renderman': '22.6'}                                                     |
| workspace        | string | N        | None    | Analyze the location of the generated json file (avoiding duplication automatically adds a timestamp folder) |

### III. Add special fields and update the json file interface

> Only updates and modifications to the parameters of task.json and upload.json files are supported.

##### 1. Modify the task.json

`update_task_info(update_info, task_path)`

![task_info](https://blog-tao625.oss-cn-shenzhen.aliyuncs.com/izone/blog/20200402094336.png)

```
from rayvision_api.utils import update_task_info, append_to_task, append_to_upload
update_task = {
    "pre_frames": "100",  # Sets the priority to render the first frame
    "stop_after_test": "1"  # Stop rendering after rendering the priority frame
}
update_task_info(update_task, analyze_obj.task_json)
```

##### 2. task.json add custom parameters

> The added custom parameters will be integrated into dictionary for key is "additional_info".
> 【Warning】：Custom parameters will not take effect immediately. If you have this requirement, please contact our customer service。

![additional_info](https://blog-tao625.oss-cn-shenzhen.aliyuncs.com/izone/blog/20200402094058.png)

```
custom_info_to_task = {
    "env": "houdini_env"
}
append_to_task(custom_info_to_task, analyze_obj.task_json)
```

##### 3. user custom upload.json

> Support custom add file path to upload.json, will automatically deduplicate
> `append_to_upload(files_paths, upload_path)`

![upload](https://blog-tao625.oss-cn-shenzhen.aliyuncs.com/izone/blog/20200402094235.png)

```
custom_info_to_upload = [
    r"D:\houdini\CG file\Cam003\cam.abc",
]
append_to_upload(custom_info_to_upload, analyze_obj.upload_json)
```

### IV. Setting hardware Configuration and Validate json file

The hardware configuration is controlled by the parameter "hardwareconfigid", which can be obtained through the API interface.("API interfaces use methods" --> "Get platform hardware configuration information")

Specify the hardware configuration by setting `model`, `ram`, `gpuNum` of hardware_config

```
hardware_config = {
    "model": "Default",  # Platform CPU: Default or Platform GPU: 1080Ti or 2080Ti
    "ram": "64GB",  # memory: 64GB or 128GB
    "gpuNum": None  # GPU platform requires input like 2*GPU, if CPU platform it is None
}
```

When validating,we set the hardware configuration based on the hardware_config and check whether there is `user_id`, `project_id`, `task_id` in task.json,
If not, the interface is called to fetch the relevant parameters from the server and write task.json

```
check_obj = RayvisionCheck(api, analyze_obj)
task_id = check_obj.execute(hardware_config, analyze_obj.task_json, analyze_obj.upload_json)
```

### V. Upload

> Now there are two ways:

##### 1.Upload the json file first and then upload the resource file according to "upload.json":

Four json files are uploaded, and the transfer engine automatically starts uploading the scene, resource, and other files based on the upload.json file.

`upload(self,task_id,task_json_path,tips_json_path,asset_json_path,upload_json_path, max_speed=None)`

```
CONFIG_PATH = [
    r"C:\workspace\work\tips.json",
    r"C:\workspace\work\task.json",
    r"C:\workspace\work\asset.json",
    r"C:\workspace\work\upload.json",
]
upload_obj = RayvisionUpload(api)
upload_obj.upload(str(task_id), *CONFIG_PATH)
```

##### 2.Uploading json files is completely independent of the user resources:

Uploading resources：`upload_asset(self, upload_json_path, max_speed=None, is_db=True)`

Upload json file: `upload_config(self, task_id, config_file_list, max_speed=None)`

```
CONFIG_PATH = [
    r"C:\workspace\work\tips.json",
    r"C:\workspace\work\task.json",
    r"C:\workspace\work\asset.json",
]
UPLOAD = RayvisionUpload(api)
UPLOAD.upload_asset(r"C:\workspace\work\upload.json", is_db=False)
UPLOAD.upload_config("5165465", CONFIG_PATH)
```

【Warning】:You need a task ID to upload a json file, but you don't need a task ID to upload a resource file;
The 'is_db' parameter in upload_asset is used to control whether or not a local database is needed. By default, a local database is used;

### VI. Submit Task

```
api.submit(int(task_id))
```

### VIII. Download

> Download now provides 3 ways:

##### 1. Supports custom downloads of hierarchical directory structures under each rendering task.

`download(self, task_id_list=None, max_speed=None, print_log=True, download_filename_format="true",local_path=None, server_path=None)`

```
download = RayvisionDownload(api)
download.download(download_filename_format="true", server_path="18164087_muti_layer_test/l_ayer2")
```

Warning：This method needs to provide the task ID if the "server_path" is not empty, and the task ID does not take effect if there is a custom "server_path".

##### 2. Realtime download, that is, the task rendering completed a frame began to download

`auto_download(self, task_id_list=None, max_speed=None,                       print_log=False, sleep_time=10,                       download_filename_format="true",                       local_path=None)`

```
download = RayvisionDownload(api)
download.auto_download([18164087], download_filename_format="false")
```

Warning：The method task ID cannot be empty

##### 3. The task is not downloaded until all frames are rendered

`auto_download_after_task_completed(self, task_id_list=None,                                            max_speed=None, print_log=True,                                            sleep_time=10,                                            download_filename_format="true",                                            local_path=None):`

```
download = RayvisionDownload(api)
download.auto_download_after_task_completed([18164087], download_filename_format="false")
```

Warning: The method task ID cannot be empty

### IX. Attachment: transfer configuration file

**1. Transport configuration Settings include:**

Select database type, database file path Settings, transfer log path Settings

**2. The transport configuration file used by default: db_config.ini， The following figure**

   ![db_config.ini](https://blog-tao625.oss-cn-shenzhen.aliyuncs.com/izone/blog/20200415114705.png)

   db_config.ini:

```ini
[TRANSFER_LOG_PATH]
transfer_log_path =

[DATABASE_CONFIG]
on = true
type = sqlite
db_path =D:\test\upload

[REDIS]
host = 127.0.0.1
port = 6379
password =
table_index = 0
timeout = 5000

[SQLITE]
temporary = false
```

   The user can also modify the configuration for the template based on the default configuration and specify the database configuration file location,
   specifying a custom configuration file as follows.

```
from rayvision_sync.upload import RayvisionUpload

UPLOAD = RayvisionUpload(api, db_config_path=r"D:\test\upload\db_config.ini")
```

**3. db_config.ini Parameters:**

| Parameters        | instructions                                                                                                                                   | Default   |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- | --------- |
| transfer_log_path | Transfer engine log file path                                                                                                                  |           |
| on                | Whether to use a local database, true / false: Yes / No                                                                                        | true      |
| type              | Select database,currently only supports "redis" and "sqlite"                                                                                   | sqlite    |
| db_path           | The database file saves the path                                                                                                               |           |
| host              | redis database host                                                                                                                            | 127.0.0.1 |
| port              | redis database port                                                                                                                            | 6379      |
| password          | redis database password                                                                                                                        |           |
| table_index       | Redis Repositories，cannot be empty                                                                                                            |           |
| timeout           | Redis client connection timeout,unit ms                                                                                                        | 5000      |
| temporary         | When using sqlite database, if the uploaded record data is deleted after the completion of the upload, the default "false" will not be deleted | false     |

**4. transfer_log_path and db_path The priority rule for values is as follows:**

- db_config.ini custom paths are preferred if they are set；
- No custom path is as follows:

  transfer_log_path

  > - Use environment variables first 'RAYVISION_LOG'
  > - Second use:
  >
  >   window: The environment variable "USERPROFILE"/<renderfarm_sdk>
  >   Linux: The environment variable "HOME" /<renderfarm_sdk>
  >

  db_path

  > - Use environment variables first 'RAYVISION_LOG'
  > - Second use:
  >
  >   window: The environment variable "USERPROFILE"/<renderfarm_sdk>
  >   Linux：The environment variable "HOME" /<renderfarm_sdk>
  >
