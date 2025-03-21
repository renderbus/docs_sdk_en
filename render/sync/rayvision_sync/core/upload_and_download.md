### Upload

#### 1. Upload file cutting

> Some upload.json files may have up to hundreds of thousands of resources, at this time you may need to cut the upload file。

```
def cutting_upload(upload_path, max_resources_number=None, after_cutting_position=None):
    """Cut upload.json according to the number of custom files.

    Args:
        upload_path (str): upload.json absolute path.
        max_resources_number (int): Maximum number of resources in each upload file.
        after_cutting_position (str): save location of upload file generated after cutting.

    Returns:
        list: Absolute path of all upload files generated after cutting, excluding original upload files.
            e.g.:
                ['D:\\test\\test_upload\\1586250829\\upload_1.json',
                'D:\\test\\test_upload\\1586250829\\upload_2.json']

    """
```

> Use example:

```
from rayvision_sync.utils import cutting_upload
upload_pool = cutting_upload(r"D:\test\test_upload\1586250829\upload.json", max_resources_number=800)
```

#### 2. Use thread pool to control upload

> Thread pool can also be used for concurrent uploads

```
def thread_pool_upload(self, upload_pool, pool_size=10, **kwargs)::
    """Thread pool upload.

    Args:
        upload_pool (list or tuple): store a list or ancestor of uploaded files.
        pool_size (int): thread pool size, default is 10 threads.

    """
  
```

> Use example：

```
from rayvision_api import RayvisionAPI
from rayvision_sync.upload import RayvisionUpload

api = RayvisionAPI(access_id="xxxxx",
                   access_key="xxxxx",
                   domain="task.renderbus.com",
                   platform="2")

UPLOAD = RayvisionUpload(api)
UPLOAD.thread_pool_upload(upload_pool, pool_size=20)
```

#### 3. Only upload resources in upload

> Users who upload upload resources only need to log in

```
def upload_asset(self, upload_json_path, max_speed=None, is_db=True):
    """Run the cmd command to upload asset files.

    Args:
        upload_json_path (str): Path to the upload.json file.
        max_speed (str): Maximum transmission speed, default value
            is 1048576 KB/S.
        is_db (bool): Whether to produce local database record upload file.

    Returns:
        bool: True is success, False is failure.

    """
```

> Use example：

```
from rayvision_api import RayvisionAPI
from rayvision_sync.upload import RayvisionUpload

api = RayvisionAPI(access_id="xxxxx",
                   access_key="xxxxx",
                   domain="task.renderbus.com",
                   platform="2")
             
UPLOAD = RayvisionUpload(api)
UPLOAD.upload_asset(r"D:\test\test_upload\1586250829\upload.json")
```

#### 4. Only upload the json configuration file generated by analysis

```
def upload_config(self, task_id, config_file_list, max_speed=None):
    """Run the cmd command to upload configuration profiles.

    Args:
        task_id (str): Task id.
        config_file_list (list): Configuration file path list.
        max_speed (str): Maximum transmission speed, default value
            is 1048576 KB/S.

    Returns:
        bool: True is success, False is failure.

    """
```

> Use example:

```
from rayvision_api import RayvisionAPI
from rayvision_sync.upload import RayvisionUpload

api = RayvisionAPI(access_id="xxxxx",
                   access_key="xxxxx",
                   domain="task.renderbus.com",
                   platform="2")

CONFIG_PATH = [
    r"C:\workspace\work\tips.json",
    r"C:\workspace\work\task.json",
    r"C:\workspace\work\asset.json",
    r"C:\workspace\work\upload.json",
]

UPLOAD = RayvisionUpload(api)
UPLOAD.upload_config("5165465", CONFIG_PATH)
```

#### 5. Upload the configuration file first and then automatically upload the resource according to the upload file (task id must be)

```
def upload(self, task_id, task_json_path, tips_json_path, asset_json_path,
           upload_json_path, max_speed=None):
    """Run the cmd command to upload the configuration file.

    Args:
        task_id (str, optional): Task id.
        task_json_path (str, optional): task.json file absolute path.
        tips_json_path (str, optional): tips.json file absolute path.
        asset_json_path (str, optional): asset.json file absolute path.
        upload_json_path (str, optional): upload.json file absolute path.
        max_speed (str): Maximum transmission speed, default value
            is 1048576 KB/S.

    Returns:
        bool: True is success, False is failure.

    """
```

> Use example:

```
from rayvision_api import RayvisionAPI
from rayvision_sync.upload import RayvisionUpload

api = RayvisionAPI(access_id="xxxxx",
                   access_key="xxxxx",
                   domain="task.renderbus.com",
                   platform="2")

CONFIG_PATH = [
    r"C:\workspace\work\tips.json",
    r"C:\workspace\work\task.json",
    r"C:\workspace\work\asset.json",
    r"C:\workspace\work\upload.json",
]

upload_obj = RayvisionUpload(api)
upload_obj.upload("5165465", **CONFIG_PATH)
```

#### 6. append_to_upload: Custom upload.json file

```python
from rayvision_api import RayvisionAPI
from rayvision_sync.upload import RayvisionUpload
from rayvision_api.utils import append_to_upload

api = RayvisionAPI(access_id="xxxxx",
                   access_key="xxxxx",
                   domain="task.renderbus.com",
                   platform="2")
UPLOAD = RayvisionUpload(api)

# 1. Can accept the list, the list can be passed in the folder path or file path
custom_info_to_upload = [
    r"E:\fang\ass_test\static_ass.ass",
    r"E:\fang",
    r"D:\houdini\CG file\F"
]
# 2.You can also receive a single string
# custom_info_to_upload = r"D:\houdini\CG file\houdini_file"

# Need to specify an existing upload.json path
append_to_upload(custom_info_to_upload, r"D:\test\upload.json")
UPLOAD.upload_asset(r"D:\test\upload.json")
```

#### 7. Upload file type (transmit_type)

> The upload file is controlled by the parameter "transmit_type", and the supported transmission file formats are: "upload_list" and "upload_json".

- 1. upload_list

  > The content of the "upload_json_path" file specified by this upload mode (support txt and json files) can be a file absolute path or folder absolute path for each line. If it is a folder, all files in the folder will be uploaded.
  >

  For Example:

  ![](https://blog-tao625.oss-cn-shenzhen.aliyuncs.com/izone/blog/20201116160335.png)
- 2. upload_json

  > The content of the "upload_json_path" file (json file) specified by this upload mode must follow a fixed format, and only files can be uploaded.
  >

  For Example:

  ```json
  {
    "asset": [
      {
        "local": "D:/houdini/CG file/local/clarisse_test1.project", 
        "server": "/D/houdini/CG file/local/clarisse_test1.project"
      }
    ]
  }
  ```

### Download

#### 1. The automatic download is completed with a single frame as the granularity rendering (task id must be)

```python
    def auto_download(self, task_id_list=None, max_speed=None,
                      print_log=False, sleep_time=10,
                      download_filename_format="true",
                      local_path=None,
                      engine_type="aspera", server_ip=None, server_port=None,
                      network_mode=0, is_test_stop=False):
        """Automatic download (complete one frame download).

        Wait for all downloads to update undownloaded records.

        Args:
            task_id_list (list of int): List of tasks ids that need to be
                downloaded.
            max_speed (str, optional): Download speed limit,
                The unit of 'max_speed' is KB/S,default value is 1048576 KB/S,
                means 1 GB/S.
            print_log (bool, optional): Print log, True: print, False: not
                print.
            sleep_time (int, optional): Sleep time between download,
                unit is second.
            download_filename_format: File download local save style,
                "true": tape task ID and scene name,
                "false" : download directly without doing processing.
            local_path (str): Download file locally save path,
                default Window system is "USERPROFILE" environment variable address splicing "renderfarm_sdk",
                Linux system is "HOME" environment variable address splicing "renderfarm_sdk".
            engine_type (str, optional): set engine type, support "aspera" and "raysyncweb", Default "aspera".
            server_ip (str, optional): transmit server host,
                if not set, it is obtained from the default transport profile.
            server_port (str, optional): transmit server port,
                if not set, it is obtained from the default transport profile.
            network_mode (int): network mode： 0: auto selected, default,
                                               1:tcp
                                               2:udp
            is_test_stop(bool): default False, Control test completion status whether to continue downloading

        Returns:
            bool: True is success.

        """
```

> Use example

```python
from rayvision_api import RayvisionAPI
from rayvision_sync.download import RayvisionDownload

api = RayvisionAPI(access_id="xxx",
                   access_key="xxx",
                   domain="task.renderbus.com",
                   platform="2")

download = RayvisionDownload(api)
download.auto_download([18164087], download_filename_format="false")
```

#### 2. Taking task as the granularity, downloading starts when all frames in the task are rendered (task id must be)

```python
    def auto_download_after_task_completed(self, task_id_list=None,
                                           max_speed=None, print_log=True,
                                           sleep_time=10,
                                           download_filename_format="true",
                                           local_path=None,
                                           engine_type="aspera", server_ip=None, server_port=None):
        """Auto download after the tasks render completed.

        Args:
            task_id_list(list of int): List of tasks ids that need to be
                downloaded.
            max_speed(str, optional): Download speed limit,
                The unit of 'max_speed' is KB/S,default value is 1048576 KB/S,
                means 1 GB/S.
            print_log(bool, optional): Print log, True: print, False: not
                print.
            sleep_time(int, optional): Sleep time between download,
                unit is second.
            download_filename_format: File download local save style,
                "true": tape task ID and scene name,
                "false" : download directly without doing processing.
            local_path (str): Download file locally save path,
                default Window system is "USERPROFILE" environment variable address splicing "renderfarm_sdk",
                Linux system is "HOME" environment variable address splicing "renderfarm_sdk".
            engine_type (str, optional): set engine type, support "aspera" and "raysyncweb", Default "aspera".
            server_ip (str, optional): transmit server host,
                if not set, it is obtained from the default transport profile.
            server_port (str, optional): transmit server port,
                if not set, it is obtained from the default transport profile.

        Returns:
            bool: True is success.

        """
```

> Use example

```python
from rayvision_api import RayvisionAPI
from rayvision_sync.download import RayvisionDownload

api = RayvisionAPI(access_id="xxx",
                   access_key="xxx",
                   domain="task.renderbus.com",
                   platform="2")

download = RayvisionDownload(api)
download.auto_download_after_task_completed([18164087], download_filename_format="false")
```

#### 3. User-defined download server directory structure download (task id is not required)

```python
    def download(self, task_id_list=None,
                 max_speed=None, print_log=True,
                 download_filename_format="true",
                 local_path=None, server_path=None,
                 engine_type="aspera", server_ip=None, server_port=None):
        """Download and update the undownloaded record.

        Args:
            task_id_list (list of int): List of tasks ids that need to be
                downloaded.
            max_speed (str, optional): Download speed limit,
                The unit of ``max_speed`` is KB/S,default value is 1048576
                KB/S, means 1 GB/S.
            print_log (bool, optional): Print log, True: print, False: not
                print.
            download_filename_format: File download local save style,
                "true": tape task ID and scene name,
                "false" : download directly without doing processing.
            local_path (str): Download file locally save path,
                default Window system is "USERPROFILE" environment variable address splicing "renderfarm_sdk",
                Linux system is "HOME" environment variable address splicing "renderfarm_sdk",
            server_path (str or list): The user customizes the file structure to be downloaded from
                the output server, and all file structures are downloaded by default,
                example: "18164087_test/l_layer".
            engine_type (str, optional): set engine type, support "aspera" and "raysyncweb", Default "aspera".
            server_ip (str, optional): transmit server host,
                if not set, it is obtained from the default transport profile.
            server_port (str, optional): transmit server port,
                if not set, it is obtained from the default transport profile.

        Returns:
            bool: True is success.

        """
```

> Use example:

```python
from rayvision_api import RayvisionAPI
from rayvision_sync.download import RayvisionDownload

api = RayvisionAPI(access_id="xxx",
                   access_key="xxx",
                   domain="task.renderbus.com",
                   platform="2")

download = RayvisionDownload(api)
download.download(download_filename_format="true", server_path="18164087_muti_layer_test/l_ayer2")
```

### Automatically obtain transmission lines

#### 1. to enable automatic acquisition of transmission lines (default is off), set automatic_line = True, for example:

- Automatically obtain the transmission line when uploading:

  `RayvisionUpload(api, automatic_line=True)`
- Download the transmission line automatically:

  `RayvisionDownload(api, automatic_line=True)`

#### 2. Enable automatic acquisition of transmission lines and select a network provider

The network business name can be obtained through the interface `get_transfer_config`

- Upload automatically obtain the transmission line and customize the network provider.

  `RayvisionUpload(api, automatic_line=True, internet_provider="移动")`
- Automatically obtain the transmission line and customize the network provider when downloading.

  `RayvisionDownload(api, automatic_line=True, internet_provider="移动")`

### Select transmission mode: tcp or udp

network_mode:  Control network transmission mode parameters
     0: Automatic selection (default)
     1:  tcp mode to transmit
     2:  udp mode to transmit

```
# Take download as an example:
download.auto_download([49240085], network_mode=2)
```

### Customize upload service address and transport engine selection

> Upload service address generally does not need to be modified, if the line is not good also support custom modification.

##### 1. The following upload interface supports custom server addresses and transport engine Settings

> Transport engine support: "aspera" and "raysync"

- upload_asset

  > ```python
  > UPLOAD.upload_asset(r"D:\test\upload.json", engine_type='aspera', server_ip="45.251.92.16", server_port="12121")
  > ```
  >
- upload_config

  ```python
  CONFIG_PATH = [
      r"C:\workspace\work\tips.json",
      r"C:\workspace\work\task.json",
      r"C:\workspace\work\asset.json",
      r"C:\workspace\work\upload.json",
  ]
  UPLOAD.upload_config(task_id="5165465",
                       config_file_list=config_list,
                       server_ip="45.251.92.16",
                       server_port="12121")
  ```
- upload

  ```python
  UPLOAD.upload(task_id="41235091",
                    engine_type='aspera',
                    server_ip="45.251.92.16",
                    server_port="12121",
                    task_json_path=r"C:\workspace\work\task.json",
                    tips_json_path=r"C:\workspace\work\tips.json",
                    asset_json_path=r"C:\workspace\work\asset.json",
                    upload_json_path=r"C:\workspace\work\upload.json")
  ```

##### 2. Download custom transmission address and custom transmission engine settings

- download

  ```
  download.download([49240085], server_ip="45.251.92.16", server_port="12121")
  ```
- auto_download

  ```
  download.auto_download([49240085], server_ip="45.251.92.16", server_port="12121")
  ```
- auto_download_after_task_completed

  ```
  download.auto_download_after_task_completed([49228557], server_ip="45.251.92.16", server_port="12121")
  ```

##### 3. select raysyncweb engine create a transfer task

```python
    def start_transfer(self, server_ip, server_port, local_path, server_path, storage_id, 
                       task_type=None, task_id=None, file_type="normal", 
                       downstorage="output", max_speed=None, max_timeout=18000, network_mode=1):
        """Download and update on the start.

        Args:
            server_ip (str): IP address of the raysyncweb transmission server.
            server_port (str or int): The transfer service port of the raysyncweb.
            local_path (str): if task_type is 'upload', the type of local_path is the local file path;
                              if task_type is 'download', the type of local_path is the local dir path;
                              if task_type is 'upload-list', the type of local_path is 'upload.json' file path.
            task_type (str): task_type is "download" or "upload" or "upload-list"
            server_path (str): if task_type is 'upload', the type of local_path is the local dir path;
                               if task_type is 'download', the type of local_path is the local file path;
                               if task_type is 'upload-list', the type of local_path is ''.
            task_id (str or int): if file_type="json" task_id is not None; else task_id is None.
                                  if file_type="normal" task_id is default None
            downstorage (str): Select the storage to download; default "output", optional "input" or "output".
            max_speed (int): default is 1GB/S.
            max_timeout(int): Maximum time for querying task status, default is 18000s
            network_mode(int): Transport Protocol Type, default is 1
                                0 is "default";
                                1 is "tcp-only";
                                2 is "udp-only"

        Returns (int): 0 or 100,101,102,500.....
              0: sucess
              100,101,102,500.....: failed
        """
```

fro example:

```python
from rayvision_sync.rayvision_raysync.transfer_raysync import RayvisionTransferRaysync

#Instantiating an object
trans = RayvisionTransferRaysync(task_domain, user_id, user_name, raysync_key, platform, logger)
#Creating a Transport Task
response_code = trans.start_transfer(server_ip, server_port, local_path,
                     server_path, storage_id, task_type="download",
                     )
# 0 is success, else failed

#Querying all Task Status
response = trans.get_task_list_status()

#Querying one Task Status
response = trans.get_task_status(task_id)
```
