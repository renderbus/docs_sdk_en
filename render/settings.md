## General Parameter

### PACKAGE_NAME

> Set the log name and package name to deploy automatically with gitlab， for example:
>
> ​      PACKAGE_NAME = "rayvision_clarisse"

### ID mapping of DCC software

```python
DCC_ID_MAPPINGS = {
        'maya': 2000,
        '3ds Max': 2001,
        'lightwave': 2002,
        'arnold': 2003,
        'houdini': 2004,
        'cinema4d': 2005,
        'softimage': 2006,
        'blender': 2007,
        'vr_standalone': 2008,
        'mr_standalone': 2009,
        'sketchup': 2010,
        'vue': 2011,
        'keyshot': 2012,
        'clarisse': 2013,
        'octane_render': 2014,
        'katana': 2016,
    }
```

### HEADERS

```python
HEADERS = {
        'accessId': '',
        'channel': '4',
        'platform': '',
        'UTCTimestamp': '',
        'nonce': '',
        'signature': '',
        'version': '1.0.0',
        'Content-Type': 'application/json'
    }
```

### task_info default parameters

```python
TASK_INFO = {
        'task_info': {
            'input_cg_file': '',
            'is_picture': '0',
            'task_id': '',
            'frames_per_task': '1',
            'pre_frames': '000',
            'job_stop_time': '86400',
            'task_stop_time': '259200',
            'time_out': '43200',
            'stop_after_test': '2',
            'project_name': '',
            'project_id': '',
            'channel': '4',
            'cg_id': '',
            'platform': '',
            'tiles_type': 'block',
            'tiles': '1',
            'is_layer_rendering': '1',
            'is_distribute_render': '0',
            'distribute_render_node': '3',
            'input_project_path': '',
            'render_layer_type': '0',
            'user_id': '',
            'os_name': '1',
            'ram': '64'
        },
        'software_config': {},
        'scene_info': {},
        'scene_info_render': {}
    }
```

### TASK END STATUS CODE LIST

```python
TASK_END_STATUS_CODE_LIST = ['10', '20', '23', '25', '30', '35', '45']
```

### TASK STATUS CODE

| **Code** | **Description**                                              | **Memo**            |
| -------- | ------------------------------------------------------------ | ------------------- |
| 0        | waiting                                                      | WAITING             |
| 5        | rendering                                                    | RENDERING           |
| 8        | for preprocessing tasks, start preprocessing, state in preprocessing | PRE_RENDERING       |
| 10       | stop                                                         | STOP                |
| 20       | stop (arrears)                                               | ARREARAGE_STOP      |
| 23       | timeout to stop                                              | TIME_OUT_STOP       |
| 25       | finished                                                     | FINISHED            |
| 30       | completed but failed frames                                  | FINISHED_HAS_FAILED |
| 35       | abandon                                                      | ABANDON             |
| 40       | test completion                                              | FINISHED_TEST       |
| 45       | ailed                                                        | FAILED              |
| 50       | analyzing                                                    | ANALYSE             |
| 100      | Status update                                                | UPDATING            |

###  Frame State Code

| **Code** | **Description**                                   | **Memo**          |
| -------- | ------------------------------------------------- | ----------------- |
| 1        | Waiting for execution                             | WAITING           |
| 2        | Being executed                                    | STARTED           |
| 3        | stop                                              | ABORTED           |
| 4        | carry out                                         | DONE              |
| 5        | Error (failure)                                   | ERROR             |
| 6        | Wait for preprocessing to complete                | PREDONEWAITING    |
| 7        | Wait for the photon frame rendering to complete   | PHOTONDONEWAITING |
| 9        | Wait for the photon job to finish rendering       | PREDONEJOBWAITING |
| 10       | Wait for the settlement job rendering to complete | GOPJOBWAITING     |
| 11       | Task timeout                                      | TIMEOUT           |

