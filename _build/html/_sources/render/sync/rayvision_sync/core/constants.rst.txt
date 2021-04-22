Constants
==========

.. automodule:: rayvision_sync.constants
   :members:
   :undoc-members:
   :show-inheritance:

PACKAGE_NAME
...............

``PACKAGE_NAME`` Set the name of log files and package name for gitlab(CD)::

    PACKAGE_NAME = 'rayvision_sync

TASK_STATUS_DESCRIPTION
...........................

Status code when task is running::

   TASK_STATUS_DESCRIPTION = {
    "0": {
        "0": "等待中",
        "1": "Waiting"
    },
    "5": {
        "0": "渲染中",
        "1": "Rendering"
    },
    "8": {
        "0": "预处理中",
        "1": "Preprocessing"
    },
    "10": {
        "0": "停止",
        "1": "Stop"
    },
    "20": {
        "0": "欠费停止",
        "1": "Arrearage-stop"
    },
    "23": {
        "0": "超时停止",
        "1": "Timeout stop"
    },
    "25": {
        "0": "已完成",
        "1": "Done"
    },
    "30": {
        "0": "已完成(有失败帧)",
        "1": "Done(with failed frame)"
    },
    "35": {
        "0": "放弃",
        "1": "Abort"
    },
    "40": {
        "0": "等待全速渲染",
        "1": "Test done"
    },
    "45": {
        "0": "失败",
        "1": "Failed"
    }
   }

TASK_END_STATUS_CODE_LIST
........................................

Status code when task ends::

   TASK_END_STATUS_CODE_LIST = ['10', '20', '23', '25', '30', '35', '45']

HEADERS
.........

Initial parameters::

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
