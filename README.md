# TechDing_SmallMol
智源抗疫 - 药物研发小分子性质预测赛 比赛代码

初赛排名：51名，排名不高，只是凑个数而已，复赛没有提交，错过时间了，但根据分数推测，应该在20名以内。

竞赛官网：https://biendata.com/competition/molecule/leaderboard/

主要思路参考baseline（https://biendata.com/models/category/4058/L_notebook/），并在其基础上修改而来：

1. 准备训练数据集，排除全都是缺失值的列。

2. 用LGBMRegressor回归器对数据集进行建模，分p1-p6六个不同模型来建模。

3. 每个模型的建模采用随机5折建模法，得到5个不同模型后对测试集预测取平均值进行模型集成。

4. p1和p3这两种类别的建模比较难，得到的loss比较大，所以说如果能够有效降低这两个类别的loss，那么结果将会非常好。

5. 模型融合的方法比较有效，能够降低一些loss值。

6. CatBoost方法几乎无法得到比较好的结果，所以说，LGBM is all you need.

7. 此处我将某些特征转变为类别特征再进行建模，效果几乎没有提升，所以以后建模要多试试几种方法。