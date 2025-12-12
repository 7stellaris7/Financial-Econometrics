# Main Notebook 使用说明

## 概述

`main.ipynb` 是一个用于金融计量经济学数据分析的综合Jupyter笔记本。该笔记本设计用于分析CSV格式的数据文件 `final_data.csv`。

## 功能特点

### 1. 数据加载与检查
- 自动加载 `final_data.csv` 文件
- 显示数据的基本信息（形状、列名、数据类型）
- 检查缺失值

### 2. 描述性统计
- 计算均值、标准差、中位数、最小值、最大值
- 计算偏度和峰度
- 导出统计结果到 `descriptive_statistics.csv`

### 3. 数据可视化
笔记本会自动生成以下图表：

- **直方图** (`histograms.png`): 显示各变量的分布
- **核密度图** (`density_plots.png`): 显示变量的密度估计
- **箱线图** (`box_plots.png`): 显示数据分布和异常值
- **小提琴图** (`violin_plots.png`): 结合箱线图和密度图的优点
- **相关性热力图** (`correlation_heatmap.png`): 显示变量间的相关关系
- **散点图矩阵** (`scatter_matrix.png`): 显示变量两两之间的关系
- **单变量散点图** (`scatter_plot_example.png`): 详细展示两个变量的关系

### 4. 相关性分析
- 计算相关系数矩阵
- 生成热力图可视化
- 导出相关系数矩阵到 `correlation_matrix.csv`

### 5. 综合报告
- 自动生成数据分析摘要报告
- 列出所有生成的文件

## 使用方法

### 前提条件

确保已安装以下Python库：
```bash
pip install pandas numpy matplotlib seaborn scipy jupyter
```

### 步骤

1. **准备数据文件**
   - 将您的CSV数据文件命名为 `final_data.csv`
   - 将文件放在与 `main.ipynb` 相同的目录下

2. **启动Jupyter Notebook**
   ```bash
   jupyter notebook main.ipynb
   ```

3. **运行笔记本**
   - 方式1: 点击菜单栏 `Cell` -> `Run All` 运行所有单元格
   - 方式2: 按 `Shift + Enter` 逐个运行单元格

4. **查看结果**
   - 在笔记本中查看实时输出
   - 检查生成的图片文件（PNG格式）
   - 查看导出的CSV统计文件

## 数据要求

`final_data.csv` 文件应该：
- 使用逗号作为分隔符
- 第一行包含列名（变量名）
- 包含至少一个数值型变量用于分析
- 可以包含分类变量，但笔记本主要关注数值变量的分析

### 示例数据格式

```csv
variable1,variable2,variable3,category
1.5,2.3,3.1,A
2.1,3.4,2.8,B
1.8,2.9,3.5,A
...
```

## 输出文件

运行笔记本后，将生成以下文件：

### CSV文件
- `descriptive_statistics.csv`: 描述性统计结果
- `correlation_matrix.csv`: 相关系数矩阵

### 图像文件 (PNG格式，300 DPI)
- `histograms.png`: 直方图
- `density_plots.png`: 密度图
- `box_plots.png`: 箱线图
- `violin_plots.png`: 小提琴图
- `correlation_heatmap.png`: 相关性热力图
- `scatter_matrix.png`: 散点图矩阵
- `scatter_plot_example.png`: 示例散点图

## 自定义分析

如果需要对特定变量进行分析，可以修改笔记本中的代码：

```python
# 选择特定的列进行分析
selected_cols = ['variable1', 'variable2', 'variable3']
df_selected = df[selected_cols]
```

## 注意事项

1. **中文显示**: 笔记本配置了中文字体支持，如果您的系统没有 SimHei 字体，图表中的中文可能无法正常显示。可以修改 `plt.rcParams['font.sans-serif']` 设置。

2. **内存使用**: 对于大型数据集，某些可视化操作（如散点图矩阵）可能消耗较多内存。如果遇到问题，可以调整 `cols_to_plot` 的数量。

3. **图形质量**: 所有图形默认以300 DPI保存，适合在报告和论文中使用。

## 故障排除

### 问题: 找不到 final_data.csv
**解决方案**: 确保CSV文件与笔记本在同一目录，或修改文件路径：
```python
df = pd.read_csv('path/to/your/final_data.csv')
```

### 问题: 中文显示为方块
**解决方案**: 安装中文字体或修改字体设置：
```python
plt.rcParams['font.sans-serif'] = ['Arial Unicode MS']  # macOS
# 或
plt.rcParams['font.sans-serif'] = ['Microsoft YaHei']  # Windows
```

### 问题: 图形不显示
**解决方案**: 确保在Jupyter中启用了matplotlib内联显示：
```python
%matplotlib inline
```

## 扩展建议

1. 添加统计检验（t检验、ANOVA等）
2. 添加时间序列分析（如果数据包含时间序列）
3. 添加回归分析
4. 添加更多的可视化类型（如热力图、3D图等）

## 联系方式

如有问题或建议，请通过GitHub Issues反馈。
