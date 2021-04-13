

#  API interfaces use methods 

##  The preparatory work 

 All interface calls are made through the rayvision_api module, and an API object must be instantiated before use :

```python
user_info = {
    "domain_name": "jop.foxrenderfarm.com",
    "platform": "2",
    "access_id": "xxxxxxxxxxxxxxxxxxxxxx",
    "access_key": "xxxxxxxxxxxxxxxxxxxxx",
}

api = RayvisionAPI(access_id=user_info['access_id'],
                   access_key=user_info['access_key'],
                   domain=user_info['domain_name'],
                   platform=user_info['platform'])
```

**Warning：**

>   1.  the following interface calls will be made directly using the API of the above instance;
>   2.  In the rayvision_api, the interface actually returns the user only the value of the "data" parameter ;

## Obtain the platform list

**Interface path**： */api/render/common/queryPlatforms*

**Request parameters**： No

**Return parameters**：

| **Parameters** | **Type**  | **Description**             | **Memo**  |
|----------------|-----------|-----------------------------|-----------|
| platform       | Integer   | Platform number             |           |
| name           | String    | Platform number description |           |

**Example of request**：

```python
# automatically distinguish domestic and foreign according to the "domain" parameter 
platform = api.query.platforms()
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": [
        {
            "platform": 2,
            "name": "query_platform_w2"
        }
    ],
    "serverTime": 1535949047370
}
```

## Obtain the user information

**Interface path**：/api/render/setUp/queryUserProfile

**Request parameter**：No

**Example of request**：

```python
user_profile = api.user.query_user_profile()
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": {
        "userId": 10001136,
        "userName": "rayvision",
        "platform": 2,
        "phone": "173333333333",
        "email": "",
        "company": "",
        "name": "",
        "job": "",
        "communicationNumber": "",
        "softType": 2000,
        "softStatus": 1,
        "businessType": 1,
        "status": 1,
        "infoStatus": 0,
        "accountType": 1,
        "userType": 1,
        "mainUserId": 0,
        "level": 49,
        "pictureLever": null,
        "zone": 1,
        "rmbbalance": 0,
        "usdbalance": 0,
        "rmbCumulative": 0,
        "usdCumulative": 0,
        "credit": 0,
        "coupon": 49.93,
        "description": "",
        "country": "中国",
        "city": "广东 中山",
        "address": "",
        "cpuPrice": 0.67,
        "gpuPrice": 20,
        "shareMainCapital": 0,
        "subDeleteTask": 0,
        "useMainBalance": 0,
        "hideBalance": 0,
        "hideJobCharge": 0,
        "useLevelDirectory": 1,
        "downloadDisable": 0,
        "displaySubaccount": 1,
        "subaccountLimits": 5,
        "houdiniFlag": 0,
        "c4dFlag": 0,
        "blenderFlag": 0,
        "keyshotFlag": 0,
        "studentEndTime": null
    },
    "serverTime": 1535953580730
}
```

## Obtain user settings

**Interface path**： /api/render/setUp/queryUserSetting

**Request parameter**：No

**Return parameter**：

| **Parameter**             | **Type** | **Description**                                         | **Memo**                    |
| ------------------------- | -------- | ------------------------------------------------------- | --------------------------- |
| infoStatus                | Integer  |                                                         |                             |
| accountType               | Integer  |                                                         |                             |
| shareMainCapital          |          |                                                         |                             |
| subDeleteTask             |          |                                                         |                             |
| useMainBalance            |          |                                                         |                             |
| singleNodeRenderFrames    | String   | Multiple frames rendered on one machine                 |                             |
| maxIgnoreMapFlag          | String   | Can choose to ignore the max map error or not           | 0：Do not ignore，1：Ignore |
| autoCommit                | String   | Can choose start scene parameter rendering              | 1：Do not start，2 ：Start  |
| separateAccountFlag       | Integer  | Separate the primary and secondary account settings     |                             |
| mifileSwitchFlag          | Integer  | Indicate the switch option of mi Document analysis risk |                             |
| assfileSwitchFlag         | Integer  | Do not analyze the ass file switch identifier           |                             |
| manuallyStartAnalysisFlag | Integer  | Manually turn on the analysis switch                    |                             |
| downloadDisable           | Integer  | Choose to disable downloading or not                    | 1 Disable，0 Do not disable |
| taskOverTime              | Integer  | Timeout - hour                                          |                             |

**Example of request**：

```python
user_setting = api.user.query_user_setting()
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": {
        "infoStatus": null,
        "accountType": null,
        "shareMainCapital": 0,
        "subDeleteTask": 0,
        "useMainBalance": 0,
        "singleNodeRenderFrames": "1",
        "maxIgnoreMapFlag": "1",
        "autoCommit": "2",
        "separateAccountFlag": 0,
        "mifileSwitchFlag": 0,
        "assfileSwitchFlag": 0,
        "manuallyStartAnalysisFlag": 0,
        "downloadDisable": 0,
		"taskOverTime": 12,
		"taskOverTimeSec": 3600
    },
    "serverTime": 1535954828406
}
```

## Update user settings

**Interface path**： /api/render/setUp/updateUserSetting

**Request parameter**：

| **Parameter**  | **Type** | Necessary | **Description**                                | **Memo** |
| -------------- | -------- | --------- | ---------------------------------------------- | -------- |
| task_over_time | Integer  | Y         | Set up of Task timeout situation, unit: second |          |

**Return parameter: default**

**Example of return**：

```python
update_user_setting = api.user.update_user_settings(task_over_time=43200)
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": null,
    "serverTime": 1535957894211
}
```

## Obtain user transfer BID

**Interface path**：/api/render/transfer/getBid

**Request parameter**：default

**Return parameter**：

| **Parameter**        | **Type** | **Description**                                              | **Memo** |
| -------------------- | -------- | ------------------------------------------------------------ | -------- |
| config_bid           | String   | Configuration file transfer ID                               |          |
| output_bid           | String   | Download the transfer file ID                                |          |
| input_bid            | String   | Asset upload transfer ID                                     |          |
| parent_input_bid     | String   | Input transfer bid for corresponding main account            |          |
| sub_user_output_bids | Object   | Subaccount Outputbids: If the accessed user is the main account, there is a subaccount value; otherwise, it is empty |          |
| userId               | String   | ID of subaccount                                             |          |
| output_bid           | String   | output_bid for subaccount                                    |          |

**Example of request**：default

```python
user_transfer_bid = api.user.get_transfer_bid()
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": {
        "config_bid": "30201",
        "input_bid": "10201",
        "output_bid": "20201",
        "parent_input_bid": "10202",
        "sub_user_output_bids": [{
            userId:"119776",
            outputBid:"10401"
        }]
	},
    "serverTime": 1535957964631
}
```

## Create task ID

**Interface path**：/api/render/submit/createTask

**Request parameter**：

| **parameter**     | **Type**     | Necessary | **Description**                   | **Memo**                                                   |
| ----------------- | ------------ | --------- | --------------------------------- | ---------------------------------------------------------- |
| count             | Integer      | N         | create the number of task Numbers | Not required, Default  1                                   |
| out_user_id       | Long         | N         | external user ID                  | Not required，used to distinguish third party access users |
| task_user_level   | Integer      | N         | task user level                   | Not required，optional 50 and 60, default is 50            |
| labels            | List<String> | N         | custom tag                        | Not required                                               |
| clone_original_id | integer      | N         | Clone the original task ID        |                                                            |
| artist            | String       | N         | Productor                         |                                                            |

**Return parameter**：

| **Parameter**   | **Type**        | **Description** | **Memo** |
| --------------- | --------------- | --------------- | -------- |
| aliasTaskIdList | List\<String\>  | Task ID alias   |          |
| taskIdList      | List\<Integer\> | Task ID         |          |

**Example of request**：

```python
create_task_id = api.task.create_task(count=1, 
                                      task_user_level=50,
                                      labels=["label_test1", "label_test2"])
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": {
        "aliasTaskIdList": [
            "2W19097"
        ],
        "taskIdList": [
            19097
        ],
        "userId": 10007893
    },
    "serverTime": 1535959487092
}
```

## Submit task

**Interface path**：/api/render/submit/task

**Request parameter**：

| **Parameter** | **Type** | Necessary | **Description** | **Memo** |
| ------------- | -------- | --------- | --------------- | -------- |
| task_id       | Integer  | Y         | task id         |          |
| producer      | String   | N         | producer        |          |

**Return parameter**：default

**Example of request**：

```python
submit_task = api.task.submit_task(task_id=create_task_id[0])
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": null,
    "serverTime": 1535957894211
}
```

Warning: *Before committing, you need to call the transport interface to upload the relevant analysis configuration file .*

## Obtain analysis error code

**Interface path**： /api/render/submit/queryAnalyseErrorDetail

**Request parameter**：

| **Parameter** | **Type** | Necessary | **Description** | **Memo**                             |
| ------------- | -------- | --------- | --------------- | ------------------------------------ |
| code          | String   | N         | error code      | Codes and codes are either mandatory |
| codes         | String   | N         | Error code list | Codes and codes are either mandatory |
| language      | String   | N         | language        | 0：Chinese（default） 1：English     |

**Return parameter**：List\<CodeInfo\>

| **Parameter**    | **Type** | **Description**                                    | **Memo**                                               |
| ---------------- | -------- | -------------------------------------------------- | ------------------------------------------------------ |
| id               |          |                                                    |                                                        |
| code             | Integer  | error code                                         |                                                        |
| type             | Integer  | Type                                               | 0 Warning-can be ignored，1 Error-can not be ignored   |
| languageFlag     | Integer  | languageType                                       | 0：Chinese，1：English                                 |
| desDescriptionCn | String   | Chinese description                                |                                                        |
| desSolutionCn    | String   | Solution                                           |                                                        |
| solutionPath     | String   | Connect to solution                                |                                                        |
| isRepair         | Integer  | Check if repairable or not                         | 1：Repairable ，0：Non-repairable                      |
| isOpen           | Integer  | Check if turn on the intercept of the error or not | 0：Not turn on the intercept，1：Turn on the intercept |
| updateTime       | Date     | The final update time                              |                                                        |

**Example of request**：

```python
error_detail = api.query.error_detail(code="50001")
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": [
        {
            "id": 5,
            "code": "15000",
            "type": 1,
            "languageFlag": 0,
            "desDescriptionCn": "启动3ds max卡住或者失败",
            "desSolutionCn": "1.检查启用对应版本的3ds max是否有特殊弹窗，有的话手动关闭；\n2.检查操作系统是否设置了高级别的权限",
            "solutionPath": "http://note.youdao.com/noteshare?id=d8f1ea0c46dfb524af798f6b1d31cf6f",
            "isRepair": 0,
            "isDelete": 1,
            "isOpen": 1,
            "lastModifyAdmin": "",
            "updateTime": 1534387709000
        }
    ],
    "serverTime": 1535962451356
}
```

## Obtain the task list

**Interface path**：/api/render/handle/getTaskList

**Request parameter**：

| **Parameter**  | **Type**        | Necessary | **Description**                                            | **Memo**                                  |
| -------------- | --------------- | --------- | ---------------------------------------------------------- | ----------------------------------------- |
| page_num       | Integer         | N         | Mandatary，number of current page                          | Default: 1                                |
| page_size      | Integer         | N         | Mandatary，quantities of displaying per page               | Default: 1                                |
| status_list    | List\<Integer\> | N         | status code list，query the status of the task in the list | Check task status description for details |
| search_keyword | String          | N         | Optional, scenario name or job ID                          | Fuzzy search                              |
| start_time     | String          | N         | Optional, search limit for start time                      | Example:yyyy-MM-dd HH:mm:ss               |
| end_time       | String          | N         | Optional, search limit for end time                        | Example:yyyy-MM-dd HH:mm:ss               |

**Task status description**：

| **Status**          | **Status code** | **Description**                       |
|---------------------|-----------------|---------------------------------------|
| WAITING             | 0               | Waiting                               |
| RENDERING           | 5               | Rendering                             |
| PRE_RENDERING       | 8               | Prepared to be handled                |
| STOP                | 10              | Stop                                  |
| ARREARAGE_STOP      | 20              | Stop due to arrearage                 |
| TIME_OUT_STOP       | 23              | Stop due to timing out                |
| FINISHED            | 25              | Finished                              |
| FINISHED_HAS_FAILED | 30              | Finished with failed frames contained |
| ABANDON             | 35              | Give up                               |
| FINISHED_TEST       | 40              | Test completed                        |
| FAILED              | 45              | Failed                                |
| ANALYSE             | 50              | Analyzing                             |

**Return parameter**：list\<Task Info\>

| **Parameter**         | **Type**             | **Description**                                           | **Memo**                                                     |
| --------------------- | -------------------- | --------------------------------------------------------- | ------------------------------------------------------------ |
| sceneName             | String               | Scene Name                                                |                                                              |
| id                    | Integer              | Task id                                                   |                                                              |
| taskAlias             | String               | Task Name                                                 |                                                              |
| taskStatus            | Byte                 | Task status                                               | 1/Waiting, 5/Rendering, 10/Stop, 15/User Stop, 20/Stop due to arrearage, 25/Finished, 30/Finished with failed frames contained, 35/Give up, 40/Test completed, 45/Failed |
| statusText            | String               | Status Text                                               |                                                              |
| preTaskStatus         | Byte                 | Preprocessi-ng Task Status                                |                                                              |
| preStatusText         | String               | Preprocessi-ng Task Status Text                           |                                                              |
| totalFrames           | Integer              | Total frames                                              |                                                              |
| abortFrames           | Integer              | Abort frames                                              |                                                              |
| executingFrames       | Integer              | Executing frames                                          |                                                              |
| doneFrames            | Integer              | Done frames                                               |                                                              |
| failedFrames          | Integer              | Failed frames                                             |                                                              |
| framesRange           | String               | Frames range                                              |                                                              |
| projectName           | String               | Project name                                              |                                                              |
| renderConsume         | BigDecimal           | Task render consume                                       |                                                              |
| taskArrears           | BigDecimal           | Task arrears                                              |                                                              |
| submitDate            | Date                 | Submit Date                                               |                                                              |
| startTime             | Date                 | Start Date                                                |                                                              |
| completedDate         | Date                 | Completed Date                                            |                                                              |
| renderDuration        | Long                 | Task render duration                                      |                                                              |
| userName              | String               | User name                                                 |                                                              |
| producer              | String               | producer                                                  |                                                              |
| taskLevel             | Byte                 | Task level                                                |                                                              |
| taskUserLevel         | Integer              | Task level of user                                        |                                                              |
| taskLimit             | Integer              | Task node limit                                           |                                                              |
| taskOverTime          | Long                 | Task timeout reminder time                                |                                                              |
| outputFileName        | String               | Output file name                                          |                                                              |
| munuTaskId            | String               | Dispatch id                                               |                                                              |
| layerParentId         | String               | About maya task，parent id                                |                                                              |
| cgId                  | Integer              | Task type                                                 | 2001/maya，2000/max                                          |
| taskKeyValueVo        | Object               | Task keyword                                              |                                                              |
| userAccountConsume    | Bigdecimal           | User account consume                                      |                                                              |
| couponConsume         | Bigdecimal           | Coupon consume                                            |                                                              |
| isOpen                | Byte                 | Whether the front-end expansion button is expanded or not |                                                              |
| taskType              | String               | Task type                                                 | Preprocessing, RenderPhoton, Render                          |
| renderCamera          | String               | Render camera                                             |                                                              |
| cloneParentId         | Integer              | Clone parent id                                           |                                                              |
| cloneOriginalId       | Integer              | Clone original id                                         |                                                              |
| shareMainCapital      | Byte                 | Whether to Share Main Account Assets                      | 0：no ,  1：yes                                              |
| taskRam               | Integer              | Task render memory                                        |                                                              |
| respRenderingTaskList | **List\<TaskInfo\>** | Child tasks of the open task                              | Structure the same of this object                            |
| layerName             | String               | Layer name                                                |                                                              |
| taskTypeText          | String               | Task type text                                            | photon/picture                                               |
| isDelete              | Byte                 | Whether or not to delete                                  | 0: deleted, 1: not deleted                                   |

**taskKeyValueVo**：

| **parameter**    | **Type** | **Description** | **Memo** |
|------------------|----------|-----------------|----------|
| tiles            | String   | Tile number     |          |
| allCamera        | String   | All Cameras     |          |
| RenderableCarema | String   | Render Cameras  |          |

**Example of request**：

```python
task_list = api.query.get_task_list(page_num=1, page_size=1)
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": {
        "pageCount": 32,
        "pageNum": 1,
        "total": 32,
        "size": 1,
        "items": [
            {
                "sceneName": "衣帽间.max",
                "id": 18278,
                "taskAlias": "P18278",
                "taskStatus": 0,
                "statusText": "render_task_status_0",
                "preTaskStatus": 25,
                "preStatusText": "render_task_status_25",
                "totalFrames": 0,
                "abortFrames": null,
                "executingFrames": null,
                "doneFrames": null,
                "failedFrames": 0,
                "framesRange": "0",
                "projectName": "",
                "renderConsume": null,
                "taskArrears": 0,
                "submitDate": 1535602289000,
                "startTime": null,
                "completedDate": null,
                "renderDuration": null,
                "userName": "xiaoguotu_ljian",
                "producer": null,
                "taskLevel": 79,
                "taskUserLevel": 0,
                "taskLimit": 200,
                "taskOverTime": null,
                "userId": 10001520,
                "outputFileName": null,
                "munuTaskId": "",
                "layerParentId": 0,
                "cgId": 2001,
                "taskKeyValueVo": {
                            "tiles": null,
                            "allCamera": null,
                            "renderableCamera": null
                        },
                "userAccountConsume": null,
                "couponConsume": null,
                "isOpen": 1,
                "taskType": "",
                "renderCamera": "VRayCam003",
                "cloneParentId": null,
                "cloneOriginalId": null,
                "shareMainCapital": 0,
                "taskRam": null,
                "respRenderingTaskList": [
                    {
                        "sceneName": "衣帽间.max",
                        "id": 18280,
                        "taskAlias": "P18280",
                        "taskStatus": 25,
                        "statusText": "render_task_status_25",
                        "preTaskStatus": null,
                        "preStatusText": null,
                        "totalFrames": 1,
                        "abortFrames": 0,
                        "executingFrames": 0,
                        "doneFrames": 1,
                        "failedFrames": 0,
                        "framesRange": "0",
                        "projectName": "",
                        "renderConsume": 1.57,
                        "taskArrears": 0,
                        "submitDate": 1535602289000,
                        "startTime": 1535602601000,
                        "completedDate": 1535603874000,
                        "renderDuration": 1176,
                        "userName": "xiaoguotu_ljian",
                        "producer": null,
                        "taskLevel": 79,
                        "taskUserLevel": 0,
                        "taskLimit": 200,
                        "taskOverTime": 86400000,
                        "userId": 10001520,
                        "outputFileName": "18280_衣帽间",
                        "munuTaskId": "2018083000075",
                        "layerParentId": 18278,
                        "cgId": 2001,
                        "taskKeyValueVo": {
                            "tiles": null,
                            "allCamera": null,
                            "renderableCamera": null
                        },
                        "userAccountConsume": 0,
                        "couponConsume": 1.57,
                        "isOpen": 0,
                        "taskType": "RenderPhoton",
                        "renderCamera": "VRayCam003",
                        "cloneParentId": 0,
                        "cloneOriginalId": 0,
                        "shareMainCapital": 0,
                        "taskRam": null,
                        "respRenderingTaskList": null,
                        "layerName": null,
                        "taskTypeText": "render_photons_task",
                        "isDelete": 1
                    },
                    {
                        "sceneName": "衣帽间.max",
                        "id": 18281,
                        "taskAlias": "P18281",
                        "taskStatus": 25,
                        "statusText": "render_task_status_25",
                        "preTaskStatus": null,
                        "preStatusText": null,
                        "totalFrames": 17,
                        "abortFrames": 0,
                        "executingFrames": 0,
                        "doneFrames": 17,
                        "failedFrames": 0,
                        "framesRange": "0",
                        "projectName": "",
                        "renderConsume": 6.7,
                        "taskArrears": 0,
                        "submitDate": 1535602289000,
                        "startTime": 1535603885000,
                        "completedDate": 1535604765000,
                        "renderDuration": 5028,
                        "userName": "xiaoguotu_ljian",
                        "producer": null,
                        "taskLevel": 79,
                        "taskUserLevel": 0,
                        "taskLimit": 200,
                        "taskOverTime": 86400000,
                        "userId": 10001520,
                        "outputFileName": "18281_衣帽间",
                        "munuTaskId": "2018083000079",
                        "layerParentId": 18278,
                        "cgId": 2001,
                        "taskKeyValueVo": {
                            "tiles": null,
                            "allCamera": null,
                            "renderableCamera": null
                        },
                        "userAccountConsume": 0,
                        "couponConsume": 6.7,
                        "isOpen": 0,
                        "taskType": "Render",
                        "renderCamera": "VRayCam003",
                        "cloneParentId": 0,
                        "cloneOriginalId": 0,
                        "shareMainCapital": 0,
                        "taskRam": null,
                        "respRenderingTaskList": null,
                        "layerName": null,
                        "taskTypeText": "render_major_picture_task",
                        "isDelete": 1
                    }
                ],
                "layerName": null,
                "taskTypeText": null,
                "isDelete": 1
            }
        ]
    },
    "serverTime": 1535964116655
}
```

## Stop task

**Interface path**： /api/render/handle/stopTask

**Request parameter**：

| **parameter**   | **Type**        | Necessary | **Description**            | **Memo** |
| --------------- | --------------- | --------- | -------------------------- | -------- |
| task_param_list | List\<Integer\> | Y         | Combination of the task ID |          |

**Return parameter**：default

**Example of request**：

```python
stop_task = api.task.stop_task(task_param_list=[13798105])
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": null,
    "serverTime": 1535957894211
}
```

## Start task

**Interface path**：/api/render/handle/startTask

**Request parameter**：

| **parameter**   | **Type**        | Necessary | **Description**            | **Memo** |
| --------------- | --------------- | --------- | -------------------------- | -------- |
| task_param_list | List\<Integer\> | Y         | Combination of the task ID |          |

**Return parameter**：default

**Example of request**：

```python
start_task = api.task.start_task(task_param_list=[13798105])
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": null,
    "serverTime": 1535957894211
}
```

## Abandon task

**Interface path**：/api/render/handle/abandonTask

**Request parameter**：

| **Parameter**   | **Type**        | Necessary | **Description**            | **Memo** |
| --------------- | --------------- | --------- | -------------------------- | -------- |
| task_param_list | List\<Integer\> | Y         | Combination of the task ID |          |

**Return parameter**：default

**Example of request**：

```python
abort_task = api.task.abort_task(task_param_list=[13798105])
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": null,
    "serverTime": 1535957894211
}
```

## Delete task

**Interface path**：/api/render/handle/deleteTask

**Request parameter**：

| **Parameter**   | **Type**        | Necessary | **Description** | **Memo** |
| --------------- | --------------- | --------- | --------------- | -------- |
| task_param_list | List\<Integer\> | Y         | Task ID list    |          |

**Return parameter**：default

**Example of request**：

```python
delete_task = api.task.delete_task(task_param_list=[13798105])
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": null,
    "serverTime": 1535957894211
}
```

## Obtain the task rendering frame details

**Interface path:**  /api/render/handle/queryTaskFrames 

**Request parameter**：

| **Parameter**  | **Type** | Necessary | **Description**                                              | **Memo**                                                     |
| -------------- | -------- | --------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| task_id        | Integer  | Y         | Task ID                                                      | Task ID，Is the unique identifier of the task, mandatary field |
| search_keyword | String   | N         | Query based on the name of the multiple frames that rendered on one machine | Is a string that be queried based on name of the multiple frames that rendered on one machine, optional field |
| page_num       | Integer  | N         | Current page number                                          |                                                              |
| page_size      | Integer  | N         | Size of the data that displayed per page                     |                                                              |

**Return parameter**：List\<FrameInfo\>

| **Parameter**    | **Type** | **Description**                    | **Memo**                                                     |
| ---------------- | -------- | ---------------------------------- | ------------------------------------------------------------ |
| id               | Integer  | frame id                           |                                                              |
| userId           | Long     | userID                             |                                                              |
| framePrice       | Double   | Render pricing                     |                                                              |
| feeType          | Integer  | Fee charge type                    | 0 Quantity-based，1 Machine-bashed，2 Project-based          |
| platform         | Integer  | Platform                           |                                                              |
| frameIndex       | String   | Frame sequence name                |                                                              |
| frameBlock       | String   | Current frame number               |                                                              |
| frameStatus      | Integer  | Current frame status               | 1/Waiting,2/Processing,3/Stopped,4/Complete,5/Failed,6/Waiting for the pre-handeling,7/Waiting for photonic frame rendering completed,8/Waiting for the priority rendering completed,9/ Wait for the photon job to finish rendering,10/Waiting for the settlement job rendering completed,11/Task timing out |
| feeAmount        | Double   | Balance deduction                  |                                                              |
| couponFee        | Double   | Vouchers deduction                 |                                                              |
| startTime        | Long     | Start time (ms)                    |                                                              |
| endTime          | Long     | End time (ms)                      |                                                              |
| frameExecuteTime | Long     | Rendering frame time               |                                                              |
| frameStatusText  | String   | Frame status description           |                                                              |
| arrearsFee       | Double   | Render frame arrears amount        |                                                              |
| taskId           | Long     | Task ID                            |                                                              |
| frameType        | Integer  | Frame Type                         | 1/Pre-rendering (only one frame, even for multi-camera case), 2/photon frame, 3/combine photon frame, 4/priority frame, 5/main render frame, 6 priority /maya/max composite rendering frame, 7/maya/max rendering main picture composite frame, 8/houdini settlement frame, 9/max channel frame |
| recommitFlag     | Integer  | Recount times                      | Indicate the recount time default is 0,increased as the recount time increase |
| taskOverTime     | Integer  | overtime                           | Overtime details                                             |
| gopName          | String   | Houdini Settlement node name       |                                                              |
| frameRam         | Integer  | Memory of the task rendering frame | No memory requirement if description does not specified      |

**Example of request:**

```python
task_frame = api.query.task_frames(task_id=13790691, page_num=1, page_size=1)
```

**Example of return:**

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": {
        "pageCount": 9,
        "pageNum": 1,
        "total": 17,
        "size": 2,
        "items": [
            {
                "id": 1546598,
                "userId": null,
                "framePrice": null,
                "feeType": null,
                "platform": null,
                "frameIndex": "0-1",
                "frameStatus": 4,
                "feeAmount": 0.44,
                "startTime": 1535960273000,
                "endTime": 1535960762000,
                "frameExecuteTime": 489,
                "frameStatusText": "task_frame_status_4",
                "arrearsFee": null,
                "munuJobId": "0",
                "taskId": 19088,
                "munuTaskId": "2018090300040",
                "frameType": 5,
                "couponFee": 0,
                "recommitFlag": 0,
                "isCopy": null,
                "frameBlock": "1",
                "taskOverTime": 86400000,
                "gopName": null,
                "frameRam": null
            },
            {
                "id": 1546599,
                "userId": null,
                "framePrice": null,
                "feeType": null,
                "platform": null,
                "frameIndex": "0-2",
                "frameStatus": 4,
                "feeAmount": 0.43,
                "startTime": 1535960856000,
                "endTime": 1535961338000,
                "frameExecuteTime": 482,
                "frameStatusText": "task_frame_status_4",
                "arrearsFee": null,
                "munuJobId": "1",
                "taskId": 19088,
                "munuTaskId": "2018090300040",
                "frameType": 5,
                "couponFee": 0,
                "recommitFlag": 0,
                "isCopy": null,
                "frameBlock": "2",
                "taskOverTime": 86400000,
                "gopName": null,
                "frameRam": null
            }
        ]
    },
    "serverTime": 1535966967143
}
```

## Gets the page frame details for the specified task

[^api]: Add in v2.4.0

**Request parameter**：

| **Parameter** | **Type** | **Is necessary** | **Description**                                              | **Memo**                                           |
| ------------- | -------- | ---------------- | ------------------------------------------------------------ | -------------------------------------------------- |
| task_id       | Integer  | Y                | small task id                                                | If the job ID is "2W35736251", task_ID is 35736251 |
| start_page    | Integer  | N                | Query Start Page, default is 1                               |                                                    |
| end_page      | Integer  | N                | Query end page, default is 2000                              |                                                    |
| page_size     | Integer  | N                | Specifies the number of frames to display per page, which defaults to a maximum of 100 |                                                    |

**Example of request**：

```python
all_frames = api.query.get_all_frames(task_id=35736251)
```

**Example of return**：

```json
{
    "1": {
        "id": 665078505,
        "userId": null,
        "framePrice": null,
        "feeType": null,
        "platform": null,
        "frameIndex": "1",
        "frameStatus": 1,
        "feeAmount": 0.0,
        "startTime": 0,
        "endTime": 0,
        "frameExecuteTime": 33,
        "currentRenderTime": 0,
        "frameStatusText": "task_frame_status_1",
        "arrearsFee": null,
        "munuJobId": "0",
        "taskId": 37439351,
        "munuTaskId": "2020092801043",
        "frameType": 4,
        "couponFee": 0.037,
        "recommitFlag": 0,
        "isCopy": null,
        "frameBlock": "",
        "taskOverTime": 259200,
        "gopName": null,
        "frameRam": 64,
        "averageCpu": 9,
        "averageMemory": 2240647168,
        "isOverTime": 0,
        "overOneMonth": null,
        "renderRam": null,
        "nodeId": "10.60.3.224",
        "openRenderRam": null
    },
    "2-4[1]": {
        "id": 665078511,
        "userId": null,
        "framePrice": null,
        "feeType": null,
        "platform": null,
        "frameIndex": "2-4[1]",
        "frameStatus": 1,
        "feeAmount": null,
        "startTime": 0,
        "endTime": 0,
        "frameExecuteTime": 0,
        "currentRenderTime": 0,
        "frameStatusText": "task_frame_status_1",
        "arrearsFee": null,
        "munuJobId": "0",
        "taskId": 37439351,
        "munuTaskId": "2020092801165",
        "frameType": 5,
        "couponFee": null,
        "recommitFlag": 0,
        "isCopy": null,
        "frameBlock": "",
        "taskOverTime": 259200,
        "gopName": null,
        "frameRam": 64,
        "averageCpu": 0,
        "averageMemory": 0,
        "isOverTime": 0,
        "overOneMonth": null,
        "renderRam": null,
        "nodeId": "",
        "openRenderRam": null
    }
}
```

## Obtain the overview of task rendering frames

**Interface path**： /api/render/handle/queryAllFrameStats

**Request parameter**：No

**Return parameter**：

| **parameter**        | **Type** | **Description**                   | **Memo** |
|----------------------|----------|-----------------------------------|----------|
| executingFramesTotal | Integer  | Number of frames in rendering     |          |
| doneFramesTotal      | Integer  | Number of frames completed        |          |
| failedFramesTotal    | Integer  | Number of rendered frames failed  |          |
| waitingFramesTotal   | Integer  | Number of frames in waiting       |          |
| totalFrames          | Integer  | Number of overall rendered frames |          |

**Example of request**：

```python
all_frame_status = api.query.all_frame_status()
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": {
        "executingFramesTotal": 1,
        "doneFramesTotal": 308,
        "failedFramesTotal": 2,
        "waitingFramesTotal": 153,
        "abandonFramesTotal": 113,
        "totalFrames": 577
    },
    "serverTime": 1535968038725
}
```

## Re-submit the failed frames

**Interface path**：  /api/render/handle/recommitTasks

**Request parameter**：

| **Parameter**   | **Type**        | Necessary | **Description**                                              | **Memo** |
| --------------- | --------------- | --------- | ------------------------------------------------------------ | -------- |
| task_param_list | List\<Integer\> | Y         | Task ID list                                                 |          |
| status          | List\<Integer>  | N         | A set of frame task states that are not filled to represent failed frames |          |

**Return parameter**：default

**Example of request**：

```python
restart_failed_frames = api.query.restart_failed_frames(task_param_list=[13788981])
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": null,
    "serverTime": 1535957894211
}
```

## Re-submit the specified frames based on the frame number

[^api]: Add in v2.4.0 

**Request parameter**：

| **Parameter** | **Type**  | Necessary | **Description**                                | **Memo**                                           |
| ------------- | --------- | --------- | ---------------------------------------------- | -------------------------------------------------- |
| task_id       | Integer   | Y         | small task id                                  | If the job ID is "2W35736251", task_ID is 35736251 |
| restartframes | List[str] | Y         | List of frame Numbers that need to be replayed | example：["6", "7-9[1]"]                           |

**Example of request**：

```python
restart_frame = api.query.get_custome_frames(task_id=37439351, restartframes=["6", "7-9[1]"])
```

**Example of return**：None

## Re-submit the specified frames

**Interface path**： /api/render/handle/recommitTaskFrames

**Request parameter**：

| **Parameter** | **Type**        | Necessary | **Description**         | **Memo**                                 |
| ------------- | --------------- | --------- | ----------------------- | ---------------------------------------- |
| task_id       | Integer         | N         | Task ID                 |                                          |
| ids_list      | List\<Integer\> | N         | Combine the frame ID    | Effective if 0 displayed when select_all |
| select_all    | Integer         | N         | Choose if re-submit all | 1：All，0：Only the specified frame      |
| status        | List\<Integer>  | N         | frame status            | Only pass taskId will take effect        |

**Return parameter**：default

**Example of request**：

```python
restart_frame = api.query.restart_frame(task_id=14362099, select_all=1)
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": null,
    "serverTime": 1535957894211
}
```

## Obtain the task details

**Interface path**： /api/render/handle/queryTaskInfo

**Request parameter**：

| **Parameter** | **Type**        | Necessary | **Description**           | **Memo** |
| ------------- | --------------- | --------- | ------------------------- | -------- |
| task_ids_list | List\<Integer\> | N         | Combine the shell task ID |          |

**Return parameter**：List\<TaskInfo\>

| **Parameter**         | **Type**             | **Description**                                           | **Memo**                                                     |
| --------------------- | -------------------- | --------------------------------------------------------- | ------------------------------------------------------------ |
| sceneName             | String               | Scene Name                                                |                                                              |
| id                    | Integer              | Task id                                                   |                                                              |
| taskAlias             | String               | Task Name                                                 |                                                              |
| taskStatus            | Byte                 | Task status                                               | 1/Waiting, 5/Rendering, 10/Stop, 15/User Stop, 20/Stop due to arrearage, 25/Finished, 30/Finished with failed frames contained, 35/Give up, 40/Test completed, 45/Failed |
| statusText            | String               | Status Text                                               |                                                              |
| preTaskStatus         | Byte                 | Preprocessi-ng Task Status                                |                                                              |
| preStatusText         | String               | Preprocessi-ng Task Status Text                           |                                                              |
| totalFrames           | Integer              | Total frames                                              |                                                              |
| abortFrames           | Integer              | Abort frames                                              |                                                              |
| executingFrames       | Integer              | Executing frames                                          |                                                              |
| doneFrames            | Integer              | Done frames                                               |                                                              |
| failedFrames          | Integer              | Failed frames                                             |                                                              |
| framesRange           | String               | Frames range                                              |                                                              |
| projectName           | String               | Project name                                              |                                                              |
| renderConsume         | BigDecimal           | Task render consume                                       |                                                              |
| taskArrears           | BigDecimal           | Task arrears                                              |                                                              |
| submitDate            | Date                 | Submit Date                                               |                                                              |
| startTime             | Date                 | Start Date                                                |                                                              |
| completedDate         | Date                 | Completed Date                                            |                                                              |
| renderDuration        | Long                 | Task render duration                                      |                                                              |
| userName              | String               | User name                                                 |                                                              |
| producer              | String               | producer                                                  |                                                              |
| taskLevel             | Byte                 | Task level                                                |                                                              |
| taskUserLevel         | Integer              | Task level of user                                        |                                                              |
| taskLimit             | Integer              | Task node limit                                           |                                                              |
| taskOverTime          | Long                 | Task timeout reminder time                                |                                                              |
| outputFileName        | String               | Output file name                                          |                                                              |
| munuTaskId            | String               | Dispatch id                                               |                                                              |
| layerParentId         | String               | About maya task，parent id                                |                                                              |
| cgId                  | Integer              | Task type                                                 | 2001/maya，2000/max                                          |
| taskKeyValueVo        | Object               | Task keyword                                              |                                                              |
| userAccountConsume    | Bigdecimal           | User account consume                                      |                                                              |
| couponConsume         | Bigdecimal           | Coupon consume                                            |                                                              |
| isOpen                | Byte                 | Whether the front-end expansion button is expanded or not |                                                              |
| taskType              | String               | Task type                                                 | Preprocessing, Render photon, Render picture                 |
| renderCamera          | String               | Render camera                                             |                                                              |
| cloneParentId         | Integer              | Clone parent id                                           |                                                              |
| cloneOriginalId       | Integer              | Clone original id                                         |                                                              |
| shareMainCapital      | Byte                 | Whether to Share Main Account Assets                      | (0：no 1：yes)                                               |
| taskRam               | Integer              | Task render memory                                        |                                                              |
| respRenderingTaskList | **List\<TaskInfo\>** | Child tasks of the open task                              | Structure the same of this object                            |
| layerName             | String               | Layer name                                                |                                                              |
| taskTypeText          | String               | Task type text                                            | photon/picture                                               |

**Example of request**：

```python
task_info = api.query.task_info(task_ids_list=[14400249])
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": {
        "pageCount": 1,
        "pageNum": 1,
        "total": 1,
        "size": 100,
        "items": [
            {
                "sceneName": "test_no_randerman_175.hip",
                "id": 14400249,
                "taskAlias": "2W14400249",
                "taskStatus": 25,
                "statusText": "render_task_status_25",
                "preTaskStatus": null,
                "preStatusText": null,
                "totalFrames": 1,
                "abortFrames": 0,
                "executingFrames": 0,
                "doneFrames": 1,
                "failedFrames": 0,
                "framesRange": "/out/geometry110-200[1]",
                "projectName": "analysis_multi_project_empty_placeholder",
                "renderConsume": 0.0,
                "taskArrears": 0.0,
                "submitDate": 1577765849000,
                "startTime": 1577765851000,
                "completedDate": 1577766104000,
                "renderDuration": 13,
                "userName": "ding625yutao",
                "producer": "丁玉涛",
                "taskLevel": 81,
                "taskUserLevel": 0,
                "taskLimit": 1,
                "taskOverTime": 43200,
                "overTimeStop": 86400,
                "userId": 100150764,
                "outputFileName": "14400249_test_no_randerman_175",
                "munuTaskId": "2019123100841",
                "munuTaskIds": "2019123100841",
                "layerParentId": 0,
                "cgId": 2004,
                "userAccountConsume": 0.0,
                "couponConsume": 0.039,
                "qyCouponConsume": null,
                "isOpen": 0,
                "taskType": "GopRender",
                "renderCamera": "",
                "cloneParentId": 0,
                "cloneOriginalId": 0,
                "shareMainCapital": 0,
                "taskRam": 64,
                "respRenderingTaskList": null,
                "layerName": "",
                "taskTypeText": null,
                "locationOutput": "C:/RenderFarm/Download",
                "isDelete": 1,
                "channel": 1,
                "remark": "",
                "labels": "{}",
                "isOverTime": 0,
                "taskKeyValueVo": {
                    "tiles": null,
                    "allCamera": null,
                    "renderableCamera": null
                },
                "waitingCount": null,
                "stopType": 0
            }
        ]
    },
    "serverTime": 1578046630345,
    "requestId": "py6RCN-VGFzay1TZXJ2aWNlMDc-1578046630330"
}
```

## Add a custom label

**Interface path**： /api/render/project/add

**Request parameter**：

| **Parameter** | **Type** | Necessary | **Description** | **Memo**                    |
| ------------- | -------- | --------- | --------------- | --------------------------- |
| new_name      | String   | N         | Label name      |                             |
| status        | Integer  | N         | Lable status    | 0: on, 1: off, default is 1 |

**Return parameter**：default

**Example of request**：

```python
task_info = api.tag.add_label(new_name="test_tag4", status=0)
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": null,
    "serverTime": 1535957894211
}
```

## Delete custom label

**Interface path**： /api/render/project/delete

**Request parameter**：

| **Parameter** | **Type** | **Description** | **Memo** |
| ------------- | -------- | --------------- | -------- |
| del_name      | String   | Label name      |          |

**Return parameter**：default

**Example of request**：

```python
delete_label_name = api.tag.delete_label(del_name="test_tag2")
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": null,
    "serverTime": 1535957894211
}
```

## Get the project name

**Interface path**： /api/render/project/getList

**Request parameter**：No

**Return parameter**：

| **Parameter**      | **Type** | **Description**   | **Memo** |
| ------------------ | -------- | ----------------- | -------- |
| projectNameList    | List     | Project name list |          |
| Object.projectName | String   | Project name      |          |
| Object.projectId   | Integer  | Project id        |          |

**Example of request**：

```python
label_list = api.tag.get_label_list()
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": {
        "projectNameList": [
            {
                "projectId": 3671,
                "projectName": "myLabel"
            }
        ]
    },
    "serverTime": 1546998557770
}
```

## Get the project name(Control by flag)

**Interface path:**   /api/render/project/list

**Request parameter**：

| Parameter | Type | Necessary | Description                                                  | Memo       |
| --------- | ---- | --------- | ------------------------------------------------------------ | ---------- |
| flag      | int  | N         | 0:Check the items under this account;<br>1:Check the items under this account and the main account;<br>2:Query associated with all items (all items under the same main account); | default: 0 |

**Return parameter**：

| **Parameter**      | **Type**       | **Description** | **Memo** |
| ------------------ | -------------- | --------------- | -------- |
| projectNameList    | List\<Object\> | project list    |          |
| Object.projectName | String         | project name    |          |
| Object.projectId   | Integer        | project id      |          |

**Example of request**：

```python
new_projects = api.tag.get_list(flag=0)
```

**Example of return**：

```python
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": {
        "projectNameList": [
            {
                "projectId": 3671,
                "projectName": "myLabel"
            }
        ]
    },
    "serverTime": 1546998557770
}
```

## Add a task label

**Interface path:** /api/render/handle/addTaskLabel

**Request parameter**：

| **Parameter** | **Type**  | Necessary | **Description**     | **Memo** |
| -------- | --------- | ------------ | -------- | -------- |
| tag      | string    | Y  | task tag    |          |
| task_ids | list[int] | Y | task id list |          |

**Return parameter**：No

**Example of request**：No

```python
tag = api.tag.add_task_tag(tag="test_tag", task_ids=[29445045, 29435295])
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": null,
    "serverTime": 15942751740441
}
```

## Delete task label

**Interface path:** /api/render/task/deleteTaskLabel

**Request parameter**：

| **Parameter** | **Type**  | **Description**        | **Memo** |
| ------------- | --------- | ---------------------- | -------- |
| tag_ids       | list[int] | Delete the task tag ID |          |

**Return parameter**：No

**Example of request**：No

```python
del_tag = api.tag.delete_task_tag(tag_ids=[21205])
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": null,
    "serverTime": 15942760110461
}
```

## Obtain the supported rendering software

**Interface path**：/api/render/plugin/querySoftwareList

**Request parameter**：No

**Return parameter**：

| **Parameter**  | **Type**                     | **Description**                       | **Memo** |
| -------------- | ---------------------------- | ------------------------------------- | -------- |
| isAutoCommit   | Integer                      | Choose if submit automatically or not |          |
| renderInfoList | List\<[Software](#software)> | Renderer version list                 |          |
| defaultCgId    | Integer                      | Default renderer ID                   |          |

**<span id='software'>Software</span>**

| **Parameter**     | **Type** | **Description**                        | **Memo** |
| ----------------- | -------- | -------------------------------------- | -------- |
| cgId              | Integer  | Render software ID                     |          |
| cgName            | String   | Render software name                   |          |
| cgType            | String   | Render file suffix support             |          |
| iconPath          | String   | Rendering software icon address        |          |
| isNeedProjectPath | Integer  |                                        |          |
| isNeedAnalyse     | Integer  | Need to analyze                        |          |
| isSupportLinux    | Integer  | Indicates if linux is supported or not |          |

**Example of request**：

```python
support_software = api.query.supported_software()
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": {
        "isAutoCommit": 2,
        "renderInfoList": [
            {
                "cgId": 2000,
                "cgName": "Maya",
                "cgType": "ma;mb",
                "iconPath": "/img/softimage/maya.png",
                "isNeedProjectPath": 1,
                "isNeedAnalyse": 1,
                "isSupportLinux": 1
            },
            {
                "cgId": 2001,
                "cgName": "3ds Max",
                "cgType": "max",
                "iconPath": "/img/softimage/max.png",
                "isNeedProjectPath": 1,
                "isNeedAnalyse": 1,
                "isSupportLinux": 0
            },
            {
                "cgId": 2004,
                "cgName": "Houdini",
                "cgType": "hip;hipnc;hiplc",
                "iconPath": "/img/softimage/houdini.png",
                "isNeedProjectPath": 2,
                "isNeedAnalyse": 1,
                "isSupportLinux": 1
            },
            {
                "cgId": 2005,
                "cgName": "Cinema 4D",
                "cgType": "c4d",
                "iconPath": "/img/softimage/cinema-4D.png",
                "isNeedProjectPath": 1,
                "isNeedAnalyse": 1,
                "isSupportLinux": 0
            },
            {
                "cgId": 2007,
                "cgName": "Blender",
                "cgType": "blend",
                "iconPath": "/img/softimage/blender.png",
                "isNeedProjectPath": 1,
                "isNeedAnalyse": 1,
                "isSupportLinux": 0
            },
            {
                "cgId": 2008,
                "cgName": "VR Standalone",
                "cgType": "vrscene",
                "iconPath": "/img/softimage/VR-standalone.png",
                "isNeedProjectPath": 3,
                "isNeedAnalyse": 2,
                "isSupportLinux": 0
            },
            {
                "cgId": 2012,
                "cgName": "KeyShot",
                "cgType": "bip",
                "iconPath": "/img/softimage/keyshot.png",
                "isNeedProjectPath": 2,
                "isNeedAnalyse": 1,
                "isSupportLinux": 0
            },
            {
                "cgId": 2013,
                "cgName": "Clarisse",
                "cgType": "project;render",
                "iconPath": "/img/softimage/clarisse.png",
                "isNeedProjectPath": 3,
                "isNeedAnalyse": 1,
                "isSupportLinux": 1
            }
        ],
        "defaultCgId": 2001
    },
    "serverTime": 1578048938715,
    "requestId": "W12mkM-VGFzay1TZXJ2aWNlMDc-1578048938685"
}
```

## Obtain supported rendering software plugins

**Interface path**：/api/render/plugin/querySoftwareDetail

**Request parameter**：

| **Parameter** | **Type** | Necessary | **Description**    | **Memo** |
| ------------- | -------- | --------- | ------------------ | -------- |
| name          | String   | Y         | Render software ID |          |

**Return parameter**：

| **Parameter** | **Type**             | **Description**         | **Memo** |
| ------------- | -------------------- | ----------------------- | -------- |
| cgPlugin      | List\<Plugin\>       | Supported plugin list   |          |
| cgVersion     | List\<Soft Version\> | Supported software list |          |

**Plugin**：

| **Parameter**  | **Type**                   | **Description**                                     | **Memo** |
| -------------- | -------------------------- | --------------------------------------------------- | -------- |
| cvId           | Integer                    | Rendering software version ID (**Soft Version.id**) |          |
| pluginName     | String                     | Plugin name                                         |          |
| pluginVersions | List\<**Plugin Version**\> | Plugin version list                                 |          |

**PluginVersion**

| **Parameter** | **Type** | **Description**   | **Memo** |
| ------------- | -------- | ----------------- | -------- |
| pluginId      | Integer  | Plugin version ID |          |
| pluginName    | String   | Plugin name       |          |
| pluginVersion | String   | Plugin version    |          |

**SoftVersion**：

| **Parameter** | **Type** | **Description**            | **Memo** |
| ------------- | -------- | -------------------------- | -------- |
| id            | Integer  | Render software version ID |          |
| cgId          | Integer  | Render software ID         |          |
| cgName        | String   | Render software name       |          |
| cgVersion     | String   | Render software version    |          |

**Example of request**：

```python
support_software_plugin = api.query.supported_plugin(name='maya')
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": {
        "isAutoCommit": 2,
        "renderInfoList": [
            {
                "cgId": 2000,
                "cgName": "Maya",
                "cgType": "ma;mb",
                "iconPath": "/img/softimage/maya.png",
                "isNeedProjectPath": 3,
                "isNeedAnalyse": 1,
                "isSupportLinux": 1
            }
        ],
        "defaultCgId": 2001
    },
    "serverTime": 1535973558961
}
```

## New user rendering environment configuration

**Interface path**：/api/render/plugin/addUserPluginConfig

**Request parameter**：

| **Parameter**             | **Type** | Necessary | **Description**                  | **Memo**                     |
| ------------------------- | -------- | --------- | -------------------------------- | ---------------------------- |
| [render_env](#render_env) | Dict     | Y         | Render environment configuration | Detailed parameters refer to |

**<span id="render_env">render_env</span>**：

| **Parameter**   | **Type**        | Necessary | **Description**                | **Memo**                     |
| --------------- | --------------- | --------- | ------------------------------ | ---------------------------- |
| cgId            | Integer         | Y         | Render software ID             | **Soft Version.cgId**        |
| cgName          | String          | Y         | Render software name           | **Soft Version.cgName**      |
| cgVersion       | String          | Y         | Render software version        | **Soft Version.cgVersion**   |
| renderLayerType | Integer         | N         | Maya render Type               |                              |
| editName        | String          | Y         | render environment custom name |                              |
| renderSystem    | Integer         | Y         | Render system                  | 0 linux, 1 windows           |
| pluginIds       | List\<Integer\> | Y         | render plugin list             | **Plugin Version.plugin Id** |
| projectPath     | String          | N         | Engineering path               |                              |

**Return parameter**：

| **Parameter** | **Type** | **Description**                | **Memo** |
| ------------- | -------- | ------------------------------ | -------- |
| editName      | String   | render environment custom name |          |

**Example of request**：

```python
env = {
    "cgId": 2000,
    "cgName": "Maya",
    "cgVersion": "2020",
    "renderLayerType": 0,
    "editName": "testRenderEnv",
    "renderSystem": "0",
    "pluginIds": [1166]
}
add_user_env = api.env.add_render_env(render_env=env)
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": {
		"editName": "testRenderEnv"
	},
    "serverTime": 1535957894211
}
```

## Adjust user render environment configuration

**Interface path**：/api/render/plugin/editUserPluginConfig

**Request parameter**：

| **Parameter**             | **Type** |      | **Description**                  | **Memo**                     |
| ------------------------- | -------- | ---- | -------------------------------- | ---------------------------- |
| [render_env](#render_env) | Dict     | Y    | Render environment configuration | Detailed parameters refer to |

**<span id="render_env">render_env</span>**：

| **Parameter**   | **Type**      | Necessary | **Description**                | **Memo**                     |
| --------------- | ------------- | --------- | ------------------------------ | ---------------------------- |
| cgId            | Integer       | Y         | Render software ID             | **Soft Version.cgId**        |
| cgName          | String        | Y         | Render software name           | **Soft Version.cgName**      |
| cgVersion       | String        | Y         | Render software version        | **Soft Version.cgVersion**   |
| renderLayerType | Integer       | N         | Maya render Type               |                              |
| editName        | String        | Y         | render environment custom name |                              |
| renderSystem    | Integer       | Y         | Render system                  | 0 linux, 1 windows           |
| pluginIds       | List<Integer> | Y         | render plugin list             | **Plugin Version.plugin Id** |
| projectPath     | String        | N         | Engineering path               |                              |

**Return parameter**：default

**Example of request**：

```python
update_env = {
    "cgId": 2000,
    "cgName": "Maya",
    "cgVersion": "2020",
    "renderLayerType": 0,
    "editName": "testRenderEnv",
    "renderSystem": "0",
    "pluginIds": []
}
update_user_env = api.env.update_render_env(render_env=update_env)
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": null,
    "serverTime": 1536027063801
}
```


Delete user render environment configuration 
---------------------------------------------

**Interface path:**  /api/render/plugin/deleteUserPluginConfig

**Request parameter**：

| **parameter** | **Type** | Necessary | **Description**                | **Memo** |
| ------------- | -------- | --------- | ------------------------------ | -------- |
| edit_name     | String   | Y         | render environment custom name |          |

**Return parameter**：default

**Example of request**：

```python
delete_user_env = api.env.delete_render_env(edit_name="testRenderEnv")
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": null,
    "serverTime": 1536027063801
} 
```


Set up default render environment configuration
-----------------------------------------------

**Interface path**：/api/render/plugin/setDefaultUserPluginConfig

**Request parameter**：

| **parameter** | **Type** | Necessary | **Description**                | **Memo** |
| ------------- | -------- | --------- | ------------------------------ | -------- |
| edit_name     | String   | Y         | render environment custom name |          |

**Return parameter**：default

**Example of request**：

```python
set_default_user_env = api.env.set_default_render_env(edit_name="testRenderEnv")
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": null,
    "serverTime": 1536027063801
}
```

## Obtain user render environment configuration

**Interface path**：/api/render/plugin/getUserPluginConfig

**Request parameter**：

| **Parameter** | **Type**      |      | **Description**         | **Memo**                           |
| ------------- | ------------- | ---- | ----------------------- | ---------------------------------- |
| name          | String        | N    | Rendering software name | cg_names and name must fill in one |
| cg_names      | List\<string> | N    | 渲染软件名列表          | cg_names and name must fill in one |
| os_name       | Integer       | N    | 选择操作系统            | 0:Linux，1:windows,默认1           |

**Return parameter**: List\<RenderEnv\>

| **Parameter**         | **Type**                   | **Description**                          | **Memo**                                               |
| --------------------- | -------------------------- | ---------------------------------------- | ------------------------------------------------------ |
| cgId                  | Integer                    | Render software ID                       |                                                        |
| editName              | String                     | render environment custom name           |                                                        |
| cgName                | String                     | Render software name                     |                                                        |
| cgVersion             | String                     | Render software version                  |                                                        |
| osName                | Integer                    | render environment system                | 0：Linux，1：windows                                   |
| renderLayerType       | Integer                    |                                          |                                                        |
| isDefault             | Integer                    | Check if it is the default configuration | 0 Not default configuration 1 Is default configuration |
| respUserPluginInfoVos | List\<**Plugin Version**\> | render environment plugin list           |                                                        |

**Example of request**：

```python
user_render_config = api.env.get_render_env(name='houdini')
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": [
        {
            "cgId": 2004,
            "editName": "175",
            "cgName": "Houdini",
            "cgVersion": "17.5",
            "osName": 1,
            "renderLayerType": 0,
            "isDefault": 0,
            "projectPath": "",
            "isMainUserId": 1,
            "respUserPluginInfoVos": [
                {
                    "pluginId": 5304,
                    "pluginName": "renderman",
                    "pluginVersion": "renderman 22.6"
                }
            ]
        },
        {
            "cgId": 2004,
            "editName": "pianwan",
            "cgName": "Houdini",
            "cgVersion": "17.5",
            "osName": 1,
            "renderLayerType": 0,
            "isDefault": 0,
            "projectPath": "",
            "isMainUserId": 1,
            "respUserPluginInfoVos": []
        },
        {
            "cgId": 2004,
            "editName": "houdini_test",
            "cgName": "Houdini",
            "cgVersion": "17.5",
            "osName": 0,
            "renderLayerType": 0,
            "isDefault": 0,
            "projectPath": "",
            "isMainUserId": 1,
            "respUserPluginInfoVos": []
        },
        {
            "cgId": 2004,
            "editName": "16.5",
            "cgName": "Houdini",
            "cgVersion": "16.5",
            "osName": 1,
            "renderLayerType": 0,
            "isDefault": 0,
            "projectPath": "",
            "isMainUserId": 1,
            "respUserPluginInfoVos": []
        }
    ],
    "serverTime": 1578282315348,
    "requestId": "23IhQf-VGFzay1TZXJ2aWNlMDQ-1578282315343"
}
```


Task Progress (Only support Max )
-------------

**Interface path**：/api/render/handle/loadTaskProcessImg

**Request parameter**：

| **Parameter** | **Type** | Necessary | **Description** | **Memo**                                                     |
| ------------- | -------- | --------- | --------------- | ------------------------------------------------------------ |
| task_id       | Integer  | Y         | Task ID         | required                                                     |
| frame_type    | Integer  | N         | Frame type      | 2：photon，5：picture Without transmission, the background will dynamically return the results according to the stage of the rendering task |

**Return parameter**：

| **Parameter**         | **Type**             | **Description**         | **Memo**                                           |
| --------------------- | -------------------- | ----------------------- | -------------------------------------------------- |
| width                 | Integer              | Image resolution width  |                                                    |
| height                | Integer              | Image resolution height |                                                    |
| block                 | Integer              | Block number            |                                                    |
| isRenderPhoton        | Boolean              | Is render photon        | True:task is render photon                         |
| currentTaskType       | String               | Task render stage       | Render: render picture RenderPhoton: render photon |
| sceneName             | String               | Scene name+camera name  |                                                    |
| startTime             | String               | Task start time         |                                                    |
| endTime               | String               | Task end time           |                                                    |
| [grabInfo](#grabinfo) | List\<List\<dict\>\> | Block frame info        |                                                    |

Block frame info：<span id="grabinfo">grabInfo</span>

| **Parameter** | **Type** | **Description**                              | **Memo** |
| ------------- | -------- | -------------------------------------------- | -------- |
| startTime     | String   | Start time                                   |          |
| endTime       | String   | End time                                     |          |
| frameStatus   | String   | Frame status                                 |          |
| isMaxPrice    | String   | Is max picture                               |          |
| feeAmount     | String   | Fee amount                                   |          |
| couponFee     | String   | Coupon fee                                   |          |
| frameIndex    | String   | Frame number                                 |          |
| frameBlock    | String   | Block number                                 |          |
| framePercent  | String   | Frame render percent                         |          |
| frameUsed     | String   | Frame render time consumed                   |          |
| frameEst      | String   | Predicted Remaining Time for Frame Rendering |          |
| renderInfo    | String   | Frame Rendering Progress Information         |          |
| grabUrl       | String   | Frame Rendering Schedule Connection Address  |          |

**Example of request**：

```python
task_processing_img = api.query.get_task_processing_img(task_id=14470635, frame_type=2)
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": {
        "isRenderPhoton": true,
        "completedTime": "2020-01-03 10:02:55",
        "currentTaskType": "RenderPhoton",
        "sceneName": "翻新就沙发.max-Camera001",
        "grabInfo": [
            [
                {
                    "couponFee": "1.04",
                    "frameIndex": "0",
                    "renderInfo": "",
                    "frameBlock": null,
                    "frameEst": "0",
                    "grabUrl": "/mnt/output/d2_1/small_pic/100033000/100033433/14470635/RenderPhoton_2020010200306_0_rayvision0000[-]tga.jpg",
                    "feeAmount": "0.00",
                    "frameUsed": "174",
                    "frameStatus": "4",
                    "framePercent": "100",
                    "isMaxPrice": "0",
                    "startTime": "2020-01-03 09:57:18",
                    "endTime": "2020-01-03 10:00:12"
                }
            ]
        ],
        "width": 700,
        "block": 1,
        "startTime": "2020-01-02 09:35:51",
        "height": 518
    },
    "serverTime": 1578299393862,
    "requestId": "qELLr0-VGFzay1TZXJ2aWNlMDc-1578299393837"
}
```

## Task Setting Of  Over Time Stop

**Interface path**： /api/render/handle/setTaskOverTimeStop

**Request parameter**：

| **Parameter** | **Type**        | Necessary | **Description**   | **Memo**             |
| ------------- | --------------- | --------- | ----------------- | -------------------- |
| task_id_list  | List\<Integer\> | Y         | Task ID           | required             |
| overtime      | Long            | Y         | Time of Task stop | Required,unit:second |

**Example of request**：

```python
set_task_overtime = api.task.set_task_overtime_top(task_id_list=[14684405], overtime=60)
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": "SUCCESS",
    "serverTime": 1578308287155,
    "requestId": "8VNTma-VGFzay1TZXJ2aWNlMDc-1578308286842"
}
```

## Task thumbnail

**Interface path**：/api/render/handle/loadingFrameThumbnail

**Request parameter**：

| **Parameter** | **Type** | Necessary | **Description** | **Memo**                                                     |
| ------------- | -------- | --------- | --------------- | ------------------------------------------------------------ |
| frame_id      | Integer  | Y         | Frame ID        | This can be obtained through the "Obtain the task rendering frame details" interface |
| frame_status  | Integer  | N         | Frame status    | A value of 4 means complete, only thumbnails are available when completed |

**Example of request**：

```python
frame_thumbnall = api.query.get_frame_thumbnall(frame_id=230772361)
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": "SUCCESS",
    "serverTime": 1578308287155,
    "requestId": "8VNTma-VGFzay1TZXJ2aWNlMDc-1578308286842"
}
```

## Get Raysync transmission message

**Interface path**： /api/render/transfer/getServerInfo

**Request parameter**：No

**Example of request**：

```python
transfer_server_msg = api.query.get_transfer_server_msg()
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": {
        "clientVersion": "3.2.8.2",
        "protocolVersion": "3.2.8.2",
        "raysyncTransfer": {
            "serverIp": "127.0.0.1",
            "serverPort": 2121,
            "proxyIp": "42.123.110.38",
            "proxyPort": 32001,
            "sslPort": 2443,
            "port": 2442
        }
    },
    "serverTime": 1565678980735,
    "requestId": "YenJW9-1565678980088"
}
```

## Get Raysync authentication key

**Interface path**：/api/render/user/getRaySyncUserKey

**Request parameter**：No

**Example of request**：

```python
raysync_user_key = api.query.get_raysync_user_key()
```

**Example of return**：

```json
{
	"version": "1.0.0",
	"result": true,
	"message": "success",
	"code": 200,
	"data": {
		"channel": 2,
		"platform": 2,
		"signature": "rayvision2017",
		"version": "1.0.0",
		"userKey": "5394a44e890557d8d937b92086482dab",
		"id": 1868599,
		"userName": "wsh_12345",
		"zone": 1,
		"phone": "183160224171",
		"email": "testwangshunhui@rayvision",
		"loginTime": 1565682011157,
		"infoStatus": 0,
		"accountType": 2,
		"shareMainCapital": 0,
		"subDeleteTask": 0,
		"subDeleteCapital": 1,
		"useMainBalance": 0,
		"downloadDisable": 0,
		"raySyncUserKey": "40d59041f72809ffaa16146a36780595666c681e"
	},
	"serverTime": 1565682019430,
	"requestId": "4lkn0I-1565682010026"
}
```

## Full  Speed Render

**Interface path**： /api/render/handle/fullSpeedRendering

**Request parameter**：

| **Parameter** | **Type**        | Necessary | **Description** | **Memo** |
| ------------- | --------------- | --------- | --------------- | -------- |
| task_id_list  | List\<Integer\> | Y         | Yes             | Task id  |

**Example of request**：

```python
full_speed_render = api.task.full_speed(task_id_list=[13652193])
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": "成功",
    "serverTime": 1578311448826,
    "requestId": "X81MN5-VGFzay1TZXJ2aWNlMDQ-1578311448620"
}
```

##  Get transport configuration 

**Interface path**：  /api/render/transfer/getConfig

**Request parameter**：No

**Return parameter**：

| Parameter           | **Type** | **Description**                                      | **Memo** |
| ------------------- | -------- | ---------------------------------------------------- | -------- |
| inputBid            | String   | Input bid                                            |          |
| outputBid           | String   | output bid                                           |          |
| configBid           | String   | config bid                                           |          |
| parentInputBid      | String   | Input Bid corresponds to the main account            |          |
| resqEngines         | Object[] | Engine configuration                                 |          |
| engineName          | String   | Engine name                                          |          |
| checkServer         | String   | Check server                                         |          |
| checkPort           | String   | Check port                                           |          |
| checkEnable         | String   | Check for availability                               |          |
| checkExcludType     | String   | Detect exception file type, separate                 |          |
| automaticCheck      | number   | Automatic detection and switching of line 1 is 0: No |          |
| isDefault           | number   | 1: Yes; 0: No, default 1                             |          |
| resqEngineAccounts  | Object[] | aspera account                                       |          |
| bid                 | String   | aspera input bid                                     |          |
| name                | String   | aspera username                                      |          |
| password            | String   | aspera password                                      |          |
| respTaskEngineLines | Object[] | Engine list                                          |          |
| name                | String   | Line name                                            |          |
| server              | String   | Line server IP                                       |          |
| port                | String   | Line server port                                     |          |
| isDefault           | Number   | 1: Yes; 0: No, default 1                             |          |
| lineId              | Number   | ID of line tables                                    |          |
| type                | Number   | Line type 1. Special line 0. General line            |          |
| subUserOutputBids   | Object[] | Collection outputbid subaccount                      |          |
| userId              | String   | ID of subaccount                                     |          |
| outputBid           | String   | outputBid                                            |          |

**Example of request**：

```python
transfer_config = api.transmit.get_transfer_config()
```

**Example of return**：

```json
{
    "version": "1.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": {
        "inputBid": "10202",
        "outputBid": "20202",
        "configBid": "30201",
        "parentInputBid": null,
        "resqEngines": [
            {
                "resqEngineAccounts": [
                    {
                        "bid": "20202",
                        "name": "20202",
                        "password": "xB9CWAML1qd+k1X9prYHheQUAtZ0hcpmJHxe7mfVw9Q="
                    }
                ],
                "respTaskEngineLines": [
                    {
                        "name": "Aspera_main",
                        "server": "10.60.197.79",
                        "port": "10221",
                        "isDefault": 1,
                        "lineId": 123,
                        "type":1
                    }
                ],
                "engineName": "trtt",
                "automaticCheck": 1,
                "checkServer": "677",
                "checkPort": "8888",
                "checkEnable": "1",
                "checkExcludType": "88",
                "isDefault": 0
            },
            {
                "resqEngineAccounts": null,
                "respTaskEngineLines": [
                    {
                        "name": "raysync_main",
                        "server": "10.60.197.79",
                        "port": "10200",
                        "isDefault": 1,
                        "lineId": 121
                    }
                ],
                "engineName": "RaySync",
                "automaticCheck": 0,
                "checkServer": "10.60.196.151",
                "checkPort": "10100",
                "checkEnable": "0",
                "checkExcludType": "tx",
                "isDefault": 1
            },
            {
                "resqEngineAccounts": [
                    {
                        "bid": "30201",
                        "name": "30201",
                        "password": "ACz/0lNMCgyq/7WjR0QGpaXmR0/Xb0//6UaMn/s8QN4="
                    }
                ],
                "respTaskEngineLines": [
                    {
                        "name": "Aspera_main",
                        "server": "10.60.197.79",
                        "port": "10221",
                        "isDefault": 1,
                        "lineId": 123
                    }
                ],
                "engineName": "Aspera",
                "automaticCheck": 0,
                "checkServer": "test2.raysync.cn",
                "checkPort": "8888",
                "checkEnable": "0",
                "checkExcludType": "tx",
                "isDefault": 0
            }
        ],
        "subUserOutputBids": [
            {
                "userId": "119784",
                "outputBid": "10202"
            }
        ]
    },
    "serverTime": 1587380763325,
    "requestId": "K7wW6L-QmV5b25kTGVlZGVNYWNCb29rLVByby5sb2NhbA-1587380762156"
}
```

##  Upload the task profile 

**Interface path**：  /api/render/submit/taskJsonFile 

**Request parameter**：

| Parameter | **Type** | Necessary | **Description**           | **Memo**           |
| --------- | -------- | --------- | ------------------------- | ------------------ |
| task_id   | Integer  | Y         | task id                   |                    |
| content   | String   | Y         | File values in jsonformat |                    |
| file_name | String   | N         | file name                 | default“task.json” |

**Return parameter**：No

**Example of request**：

```Python
start_task = api.task.start_task(task_param_list=[13798105])
```

**Example of return**：

```json
{
    "version": "2.0.0",
    "result": true,
    "message": "success",
    "code": 200,
    "data": null,
    "serverTime": 1589532607599,
    "requestId": null
}
```

##  Gets the user storage file structure 

[^2021/1/18]: Add New Interface

**Interface path**：  /api/render/file/operate/getOutputUserDirFile 

**Request parameter**：

| **Parameter** | **Type** | Necessary | **Description**                                              | **Memo**                  |
| ------------- | -------- | --------- | ------------------------------------------------------------ | ------------------------- |
| task_id       | Integer  | N         | Task number, if it is a hierarchical task, refers to the sub-task number, that is, the task number of each layer. |                           |
| tree_path     | String   | N         | The path relative to the user storage (output) root.         | The default value is: "/" |

**Return parameter[data]**：

| Parameter  | **Type** | **Description**                                              |
| ---------- | -------- | ------------------------------------------------------------ |
| fileName   | string   | Current file name or folder name                             |
| fileSize   | int      | File size, or "null" if it is a folder                       |
| iconPath   | string   | Chart path (this parameter can be ignored)                   |
| lastModify | string   | File or folder update date                                   |
| fileType   | string   | File suffix, or "null" if it is a folder                     |
| filePath   | string   | The relative path of the file or folder to the user storage output root |
| directory  | bool     | Whether it is a folder, "true": is a folder, "false": not a folder |
| isArrears  | int      | Whether you are in arrears, 0: Not in arrears, 1: In arrears |

**Example of request**：

```
paths = api.transmit.get_output_files(task_id=1484861)
```

**Example of return**：

```json
[
    {
        "fileName": "1484861_muti_layer_test",
        "fileSize": null,
        "iconPath": null,
        "lastModify": "2021-01-15 12:11:59",
        "fileType": null,
        "filePath": "/1484861_muti_layer_test",
        "directory": true,
        "isArrears": 0
    }
]
```

##  Get all subtask numbers of the task 

[^2021/1/18]: Add New Interface

**Interface path**：

**Request parameter**：

| Parameter | **Type**          | Necessary | **Description**                                              |
| --------- | ----------------- | --------- | ------------------------------------------------------------ |
| task_id   | Integer or string | Y         | Get all sub-accounts under the main account, if there is no sub-account, return the current account ID. |

**Return parameter[data]**：

**Example of request**：

```python
ids = api.query.get_small_task_id(task_id=1521323)
```

**Example of return**：

```
[1521325, 1521327, 1521329]
```

##  Get platform hardware configuration information 

[^2021/4/12]: add new interface in rayvision_api 2.8.0 

**Interface path**：/api/render/hardwareConfig/list

**Request parameter**：

| **Parameter** | **Type**  | Necessary | **Description**                                              |
| ------------- | --------- | --------- | ------------------------------------------------------------ |
| task_ids      | List[str] | N         | A collection of task numbers that queries the configuration parameters of the specified task |

**Return parameter[data]**：

| **Parameter**  | **Type**  | **Description**                                              |
| -------------- | --------- | ------------------------------------------------------------ |
| id             | int       | Hardware Configuration ID (HardwareConfigID)                 |
| type           | int       | 1: CPU ;<br>2: GPU                                           |
| model          | string    | Hardware model, default "default"                            |
| ram            | String    | memory                                                       |
| gpuNum         | String    | Number of GPU cards, CPU platform is "null"                  |
| platform       | int       | Platform number                                              |
| current        | bool      | When task_ids is not null， the query is the task's current hardware configuration<br>false: is the current task hardware configuration<br>true: Is not the current task hardware configuration. |
| notSupportCgId | list[int] | Unsupported cgId, (cgid corresponding software can query "General Parameter" -- > "ID mapping of DCC software") |
| status         | int       | Status,<br>1: Enabled;<br>0: Disabled                        |

**Example of request**：

```json
hardware_config = api.user.get_hardware_config(task_ids=["6306543"])
```

**Example of return**：

```json
[
    {
        "id": 301,
        "type": 1,
        "model": "Default",
        "gpuNum": null,
        "ram": "64GB",
        "platform": 2,
        "current": false,
        "notSupportCgId": [],
        "status": 1
    },
    {
        "id": 303,
        "type": 1,
        "model": "Default",
        "gpuNum": null,
        "ram": "128GB",
        "platform": 2,
        "current": false,
        "notSupportCgId": [],
        "status": 1
    },
    {
        "id": 337,
        "type": 1,
        "model": "1080Ti",
        "gpuNum": null,
        "ram": "64GB",
        "platform": 2,
        "current": true,
        "notSupportCgId": [
            2005,
            2000
        ],
        "status": 1
    },
    {
        "id": 339,
        "type": 1,
        "model": "2080Ti",
        "gpuNum": null,
        "ram": "64GB",
        "platform": 2,
        "current": false,
        "notSupportCgId": [],
        "status": 1
    },
    {
        "id": 341,
        "type": 1,
        "model": "1080Ti",
        "gpuNum": null,
        "ram": "128GB",
        "platform": 2,
        "current": false,
        "notSupportCgId": [
            2005
        ],
        "status": 1
    }
]
```

