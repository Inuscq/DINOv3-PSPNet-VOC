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
- `sample_segmentation.png`：训练后预测效果（无真值）
- `segmentation_untrained.png`：训练前随机预测（对比训练前后差异）
- `qualitative_grid.png`：输入/真值/预测三联对比
- `overlay_comparison.png`：真值叠加 vs 预测叠加
- `per_class_iou.png`：21个类别IoU柱状图
- `confusion_matrix.png`：21×21混淆矩阵
- `failure_cases.png`：IoU最低的失败案例
