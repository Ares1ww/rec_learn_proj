# 营销算法项目_文档

### 数据集说明

数据集来源：https://tianchi.aliyun.com/dataset/140281 

本项目使用了两个数据集：

1. User_item_beh_log  (用户历史行为表) 
   字段为：
   user_id, item_id, action,  vtime
2. Item_dim (商品维表) 
   字段为：
   user_id,   item_id,  cate_1,    cate_2,   seller_id,   brand_id



### 特征工程

- feature_eng/data_process/data_warehouse/user_beh_log_dw.sql  
  构造中间表，对原始的两个数据表进行join、按时间分区等操作，目的是按照用户的四种历史行为分开存储，方便后续的特征处理



- feature_eng/data_process/feature_process
  这个文件夹中，包含，从用户、品牌、用户与品牌的一级类目，二级类目等交叉特征，三个方面的特征构造



### 样本，以及样本与特征的 join

- feature_eng/sample
  包括，baseline LGBM与深度模型的样本特征拼接
- feature_eng/seq_feature_process
  用户行为序列特征的构造，用户最近50个点击、加购、购买，三种行为的行为序列，进行了按时间排序以及对于多次交互只保留最近一次交互记录等操作



### 模型构建与训练

- DIN 模型
  model_code/model_main/model/din_model.py

- DIN结合MoE模型
  model_code/model_main/model/moe_model.py

- 模型训练代码
  model_code/train_main
