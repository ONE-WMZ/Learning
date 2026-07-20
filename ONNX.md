# ONNX(Open Neural Network Exchange)
~~~
概念: 
    1、开放神经网络交换格式: 把模型从“某个框架专属”，变成“跨框架、跨平台可运行”的标准格式;
    2、模型训练环境 ≠ 模型部署环境; 
    3、ONNX 的核心结构不是文件，是计算图;
    计算图: 输入 → 运算节点 → 运算节点 → 输出; 
    4、ONNX 不关心是怎么训练的，只关心怎么计算; 
    5、ONNX 针对对多端部署提供统一表达; 

总结: ONNX 本质是模型的中间执行协议，通过统一计算图表达，实现模型从训练框架到多端推理环境的解耦与高效部署。 
~~~

~~~
局限:
    1、不支持所有算子: 有些PyTorch自定义算子导不出来，需要手写转换;
    2、动态shape支持有限: 变长输入处理复杂,attention 结构转换困难;
    3、转换 ≠ 性能提升: ONNX只是中间层;
~~~


~~~
环境: 
    pip install --upgrade onnx onnxscript
    pip install onnxruntime

Pytorch导出ONNX:
    torch_model = model()
    input = (torch.randn(1, 1, 32, 32),)
    onnx_program = torch.onnx.export(
        torch_model,        # 模型
        input,              # 输入 
        dynamo=True,        # 
    )
    onnx_program.save("onnx_model.onnx")

加载ONNX:
    onnx_model = onnx.load("onnx_model.onnx")
    onnx.checker.check_model(onnx_model)

可视化: Netron (https://netron.app/) 

迁移(推理):
    import onnxruntime
    ort_session = onnxruntime.InferenceSession("./onnx_model.onnx", 
                                               providers=["CPUExecutionProvider"],)
    onnxruntime_input = ?
    onnxruntime_outputs = ort_session.run(None, onnxruntime_input,)[0]
~~~


## 参考文献：
~~~
[1] https://docs.pytorch.ac.cn/tutorials/beginner/onnx/export_simple_model_to_onnx_tutorial.html 
[2] https://www.bilibili.com/video/BV1cM4y187Xc/?spm_id_from=333.337.search-card.all.click
[3] https://blog.csdn.net/Anthony1453/article/details/159958366
[4] https://onnx.com.cn/onnx/index.html
~~~