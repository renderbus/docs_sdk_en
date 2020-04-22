FAQ
===========


.. _header-n3:

1. What versions of Python does the RenderBus SDK support?
-----------------------------------------------------------

RenderBus SDK currently supports Python 2.7 and Python 3.6

.. _header-n5:

2. How to download the SDK package with pycharm?
--------------------------------------------------

Please refer to `Installation Guide <installation_guide.html>`__

.. _header-n13:

3. To download only the first frame, how to set?
--------------------------------------------------

 ::

   from rayvision_api.utils import update_task_info
   update_task = {
        "pre_frames": "100",
    }
    update_task_info(update_task, task_path=r"C:\workspace\1586932339\task.json")


.. _header-n14:

4. After the priority frame rendered, how to set to automatically render at full speed?
-------------------------------------------------------------------------------------------

 ::

   from rayvision_api.utils import update_task_info
   update_task = {
        "stop_after_test": "1"
    }
   update_task_info(update_task, task_path=r"C:\workspace\1586932339\task.json")


For details, please refer to `Detailed Parameter Configuration <json_file>`__


.. _header-n34:

5. How to set to download the rendering result immediately after current rendered frame rendered?
----------------------------------------------------------------------------------------------------

We provide 2 downloading methods:

- Download after all frames finish rendering

- Download after current frame finishes rendering

For details, please refer to `SDK Usage <SDK_tutorial.html#header-n209>`__

.. _header-n9:

6. What is the easiest way to use?
------------------------------------

If you want to use it directly without customization, you can download the corresponding rendering package directly,
then select the corresponding [common full process sample] to experience the full process rendering. For details, please refer to the `SDK Getting Started Tutorial <SDK_tutorial.html>`__
