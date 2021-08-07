# TensorFlow

官方文档地址：https://tensorflow.google.cn/

## 安装

首先检查你的电脑是否有英伟达显卡，更新你的显卡驱动

- GPU版

  在你的终端或者cmd或者powershell中执行：

  ```bash
  conda update conda
  conda install tensorflow-gpu
  ```

  正常情况下执行命令后会同时下载cudnn和cudatoolkit。如果没有，则

  ```bash
  conda install tensorflow-gpu cudnn cudatoolkit
  ```

  测试是否能进行GPU加速
  
  - 方法一
  
    运行
  
    ```python	
    import tensorflow as tf
    print(tf.test.is_gpu_available())
    ```
  
    若输出`True`则安装成功
  
  - 方法二
  
    运行
  
    ```python
    import tensorflow as tf
    print(tf.config.list_physical_devices())
    ```
  
    若输出
  
    ```bash
    [PhysicalDevice(name='/physical_device:CPU:0', device_type='CPU'),
     PhysicalDevice(name='/physical_device:GPU:0', device_type='GPU')]
    ```
  
    则安装成功

## 自定义训练过程

- 训练两个具有级联结构的模型

    ```python
    x = model_1(inputs)
    x = model_2(x)
    ```

	训练过程如下

    ```python
    @tf.function
    def train_step(images):
        with tf.GradientTape() as tape_1, tf.GradientTape() as tape_2: #创建两个梯度带
          x = model_1(inputs)
          x = model_2(x)
          loss = loss_function(x)
	
        grads_1 = tape_1.gradient(loss, model_1.trainable_variables)
        grads_2 = tape_2.gradient(loss, model_2.trainable_variables)
	
        optimizer_1.apply_gradients(zip(grads_1, model_1.trainable_variables))
        optimizer_2.apply_gradients(zip(grads_2, model_2.trainable_variables))
	```

## Debug

- 训练loss出现nan

  请先检查你的数据集是否存在空缺

  ```python
  np.any(np.isnan(dataset))
  ```
