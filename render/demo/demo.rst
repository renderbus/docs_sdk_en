###  *Demo for maya, houdini and clarisse*

Maya demo
-----------

 ::

    from __future__ import print_function
    from rayvision_api.core import RayvisionAPI
    from rayvision_utils.analyse_handle import RayvisionAnalyse
    from rayvision_api.task.handle import RayvisionTask
    from rayvision_api.task.check import RayvisionCheck
    from rayvision_sync.transfer import RayvisionTransfer
    from rayvision_sync.upload import RayvisionUpload
    from rayvision_sync.manage import RayvisionManageTask
    from rayvision_sync.download import RayvisionDownload

    # Set necessary parameters.

    render_para = {
        "domain": "task.renderbus.com",  # no need to modify
        "platform": "2",
        "access_id": "xxxx",  # user's access_id(required)
        "access_key": "xxxx",  # user's access_key(required)
        "local_os": 'windows',
        "workspace": "c:/workspace",  # local root directory(Automatically generated), must be in english
        "render_software": "Maya",  # CG software（Maya, Houdini, Katana, Clarisse）
        "software_version": "2018",  # CG software version
        "project_name": "Project1",
        "plugin_config": {  # CG plugins. If none, leave it as {}
            "mtoa": "3.1.2.1"
        }
    }

    # absolute path of CG assets(required)
    cg_file = r"E:\copy\muti_layer_test.ma"

    api = RayvisionAPI(access_id=render_para['access_id'],
                       access_key=render_para['access_key'],
                       domain=render_para['domain'],
                       platform=render_para['platform'])

    # print user's info
    print(api.user.query_user_profile())

    # Rayvision analysis
    task = RayvisionTask(cg_file=cg_file, **render_para)
    RayvisionAnalyse.execute(task)
    RayvisionCheck(task).execute(task.task_info, task.upload_info)

    # Upload json file
    transfer_info = {
        'config_bid': api.user_info['config_bid'],
        'input_bid': api.user_info['input_bid'],
        "output_bid": api.user_info["output_bid"],
        "domain": render_para['domain'],
        "platform": render_para['platform'],
        "local_os": render_para['local_os'],
        "user_id": api.user_info['user_id'],
        "local_path": r"C:\workspace",  # folder to save downloaded files
    }

    resource_config_file = {
        "task_json_path": task.task_json_path,
        "tips_json_path": task.tips_json_path,
        "asset_json_path": task.asset_json_path,
        "upload_json_path": task.upload_json_path,
    }

    # start transfer
    trans = RayvisionTransfer(**transfer_info)
    upload = RayvisionUpload(trans)
    upload.upload(task_id=task.task_id, **resource_config_file)

    task_id = int(task.task_id)
    result = api.submit(task_id)

    # download
    manage_task = RayvisionManageTask(api.query)
    trans.manage_task = manage_task
    download = RayvisionDownload(trans)

    # provide 2 methods of downloading
    # download.auto_download_after_task_completed([task_id])  # Download after all frames finish rendering
    download.auto_download([task_id])  # Download after current frame finishes rendering


Houdini demo
-------------
 ::

    from __future__ import print_function
    from rayvision_api.core import RayvisionAPI
    from rayvision_utils.analyse_handle import RayvisionAnalyse
    from rayvision_api.task.handle import RayvisionTask
    from rayvision_api.task.check import RayvisionCheck
    from rayvision_sync.transfer import RayvisionTransfer
    from rayvision_sync.upload import RayvisionUpload
    from rayvision_sync.manage import RayvisionManageTask
    from rayvision_sync.download import RayvisionDownload

    # Set necessary parameters

    render_para = {
        "domain": "task.renderbus.com",  # no need to modify
        "platform": "2",  # platform id
        "access_id": "xxxxxx",  # user's access_id(required)
        "access_key": "xxxxx",  # user's access_key(required)
        "local_os": 'windows',
        "workspace": "c:/workspace",  # local root directory(Automatically generated), must be in english
        "render_software": "Houdini",  # CG software（Maya, Houdini, Katana, Clarisse）
        "software_version": "17.5.293",  # CG software version
        "project_name": "Project1",
        "plugin_config": {}  # CG plugins. If none, leave it as {}
    }

    # absolute path of CG assets(required)
    cg_file = r"E:\copy\test02.hip"

    api = RayvisionAPI(access_id=render_para['access_id'],
                       access_key=render_para['access_key'],
                       domain=render_para['domain'],
                       platform=render_para['platform'])

    # print user's info
    print(api.user.query_user_profile())

    # Rayvision analysis
    task = RayvisionTask(cg_file=cg_file, **render_para)
    RayvisionAnalyse.execute(task)
    RayvisionCheck(task).execute(task.task_info, task.upload_info)

    # Upload json file
    transfer_info = {
        'config_bid': api.user_info['config_bid'],
        'input_bid': api.user_info['input_bid'],
        "output_bid": api.user_info["output_bid"],
        "domain": render_para['domain'],
        "platform": render_para['platform'],
        "local_os": render_para['local_os'],
        "user_id": api.user_info['user_id'],
        "local_path": r"C:\workspace",  #  folder to save downloaded files
    }

    resource_config_file = {
        "task_json_path": task.task_json_path,
        "tips_json_path": task.tips_json_path,
        "asset_json_path": task.asset_json_path,
        "upload_json_path": task.upload_json_path,
    }

    # start transfer
    trans = RayvisionTransfer(**transfer_info)
    upload = RayvisionUpload(trans)
    upload.upload(task_id=task.task_id, **resource_config_file)

    task_id = int(task.task_id)
    result = api.submit(task_id)

    # download
    manage_task = RayvisionManageTask(api.query)
    trans.manage_task = manage_task
    download = RayvisionDownload(trans)

    # provide 2 methods of downloading
    # download.auto_download_after_task_completed([task_id])  # Download after all frames finish rendering
    download.auto_download([task_id])  # Download after current frame finishes rendering

Clarisse demo
--------------

 ::

    from __future__ import print_function

    from rayvision_api.core import RayvisionAPI
    from rayvision_api.task.check import RayvisionCheck
    from rayvision_api.task.handle import RayvisionTask
    from rayvision_sync.download import RayvisionDownload
    from rayvision_sync.manage import RayvisionManageTask
    from rayvision_sync.transfer import RayvisionTransfer
    from rayvision_sync.upload import RayvisionUpload
    from rayvision_utils.analyse_handle import RayvisionAnalyse

    # Set necessary parameters.
    render_para = {
        "domain": "task.renderbus.com",
        "platform": "2",
        "access_id": "xxxxx",
        "access_key": "xxxxxx",
        "local_os": 'windows',
        "workspace": "c:/workspace",  # local root directory(Automatically generated), must be in english
        "render_software": "Clarisse",  # CG software（Maya, Houdini, Katana, Clarisse）
        "software_version": "clarisse_ifx_4.0_sp3",  # CG software version
        "project_name": "Project1",
        "plugin_config": {},  # CG plugins. If none, leave it as {}
    }

    # absolute path of CG assets(required)
    # cg_file = "E:/copy/DHGB_sc05_zhuta_610-1570_v0102.project"
    cg_file = r"D:\ziyuan\class01\feichuan.project"

    api = RayvisionAPI(access_id=render_para['access_id'],
                       access_key=render_para['access_key'],
                       domain=render_para['domain'],
                       platform=render_para['platform'])

    # print user's info
    print(api.user.query_user_profile())


    # Rayvision analysis
    task = RayvisionTask(cg_file=cg_file, **render_para)
    RayvisionAnalyse.execute(task)
    RayvisionCheck(task).execute(task.task_info, task.upload_info)

    # upload
    transfer_info = {
        'config_bid': api.user_info['config_bid'],
        'input_bid': api.user_info['input_bid'],
        "output_bid": api.user_info["output_bid"],
        "domain": render_para['domain'],
        "platform": render_para['platform'],
        "local_os": render_para['local_os'],
        "user_id": api.user_info['user_id'],
        "local_path": r"C:\workspace",  #  folder to save downloaded files
    }

    resource_config_file = {
        "task_json_path": task.task_json_path,
        "tips_json_path": task.tips_json_path,
        "asset_json_path": task.asset_json_path,
        "upload_json_path": task.upload_json_path,
    }

    # start transfer
    trans = RayvisionTransfer(**transfer_info)
    upload = RayvisionUpload(trans)
    upload.upload(task_id=task.task_id, **resource_config_file)

    task_id = int(task.task_id)
    result = api.submit(task_id)

    # download
    manage_task = RayvisionManageTask(api.query)
    trans.manage_task = manage_task
    download = RayvisionDownload(trans)

    # provide 2 methods of downloading
    # download.auto_download_after_task_completed([task_id])  # Download after all frames finish rendering
    download.auto_download([task_id])  # Download after current frame finishes rendering
