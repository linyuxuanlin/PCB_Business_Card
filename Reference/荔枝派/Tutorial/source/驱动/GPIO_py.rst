Python 操作GPIO
=============================

.. contents:: 本文目录

为了大家使用方便，这里同时提供了pyhton的gpio库：lpi_gpio.so

接口名与C的函数库相同，这里是一个简单的使用示例：

.. code-block:: Python
   :caption: test_gpio.py

    import lpi_gpio
    import signal
    import time

    def exit(signum, frame):
            lpi_gpio.deinitlib()
            print('exit test_gpio')    
            exit()

    signal.signal(signal.SIGINT, exit)
    signal.signal(signal.SIGTERM, exit)

    lpi_gpio.initlib()
    lpi_gpio.init(6,0,1,0)
    while True:		#闪烁PG0 绿灯
            lpi_gpio.w(6,0,0)
            time.sleep(0.5)
            lpi_gpio.w(6,0,1)
            time.sleep(0.5)

.. admonition:: 交流与答疑

    对于本节内容，如有疑问，欢迎到 `外设驱动交流帖 <http://bbs.lichee.pro/d/18-->`_ 提问或分享经验