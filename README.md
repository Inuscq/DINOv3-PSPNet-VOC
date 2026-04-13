# DINOv3 + PSPNet 语义分割实验复现

本项目基于 DINOv3 作为 backbone，结合 PSPNet 分割头，在 Pascal VOC 2012 数据集上实现语义分割。

## 参考工作
- DINOv3: https://github.com/facebookresearch/dinov3
- PSPNet: https://arxiv.org/abs/1612.01105
- 主要代码参考: https://github.com/TimesloverJIE/voc-dinov3-pspnet

## 个人工作
- 在 Kaggle 环境中独立完成代码整合与调试
- 解决 DINOv3 权限问题，后改用 ModelScope 加载模型
- 完成完整训练流程（60 epochs），最佳 mIoU 达到 0.6599
- 生成完整的评估报告（定性对比、每类 IoU、混淆矩阵、失败案例）
  
## 实验结果
- **Backbone**: DINOv3 ViT-S/16
- **分割头**: PSPNet
- **数据集**: Pascal VOC 2012
- **最佳 mIoU**: 0.6599
- **模型权重**：‘best_pspnet.pth’
- **测试输出**
| 图片 | 内容 | 说明 |
|---|---|---|
| `segmentation_untrained.png` | 4组输入/真值/未训练预测对比 | 训练前随机初始化模型的输出，用于对比训练前后的差异 |
| `sample_segmentation.png` | 6组输入/预测对比 | 训练完成后的快速验证，展示模型分割效果（无真值对比） |
| `qualitative_grid.png` | 6组输入/真值/预测三联对比 | 随机选取的验证集样本，越接近真值说明效果越好 |
| `overlay_comparison.png` | 4组真值叠加 vs 预测叠加 | 分割结果半透明覆盖原图，对比边界贴合程度 |
| `per_class_iou.png` | 21个类别的IoU柱状图 | 横轴为类别，纵轴为IoU值，越高表示该类分割越准 |
| `confusion_matrix.png` | 混淆矩阵热力图 | 对角线为正确分类比例，非对角线为错误分类 |
| `failure_cases.png` | 6组IoU最低的失败案例 | 模型表现最差的样本，用于分析模型短板 |
