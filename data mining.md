## 基本统计描述
+ **度量数据中心趋势**
	+ 均值、加权平均、中位数、众数、中列数(最大值和最小值的平均值)

+ **度量数据散布**
	+ 极差：最大值和最小值之差
	+ n-分位数：将数据划分成n个大小相等的连贯集。
		+ 二分位数：Q2，即中位数
		+ 四分位数：将数据划分成4个大小相等的连贯集。第一个四分位数称为Q1(数据的前25%)，第二个四分位数称为Q2(数据的前50%)，第三个四分位数称为Q3(数据的前75%)。
		+ 四分位数极差IQR：IQR=Q3-Q1
	+ 方差、标准差：指出数据分布的散布程度，低标准差表明数据靠近均值。

+ **图形**	
	+ 盒图：用来比较若干个可比较的数据集。
		+ 五数概括：最小值、Q1、Q2、Q3、最大值
			+ Q2：中位数由盒内的线标记；
			+ Q3和Q1：盒的端点一般在四分位数上，使得盒的长度是四分位数极差IQR；
			+ 最小值和最大值：盒外的两条线(称胡须)延伸到最小和最大观测值。当最小值和最大值超出四分位数的距离不到1.5 x IQR时，胡须扩展到它们，也就是说，胡须最大扩展到四分位数±1.5 x IQR的位置。
		+ 离群点：Q3之上或Q1之下至少1.5 x IQR处的值。
	+ 散点图：描述两个数值变量之间是否存在联系；
		+ 正相关：递增
		+ 负相关：递减
	+ 分位数图、分位数-分位数图、直方图

+ **相异性和相似性度量**
	+ 度量方法
		+ 非对称二元属性：对于仅有两个可能状态的标称属性，如果两个状态不同等重要，则称非对称二元属性；
			+ Jaccard系数
		+ 对称二元属性：对于仅有两个可能状态的标称属性，如果两个状态同等重要，则称对称二元属性；
		+ 曼哈顿距离：L1范数
		+ 欧几里得距离：L2范数
		+ 闵可夫斯基距离：Lp范数
		+ 上确界距离(切比雪夫距离)：L无穷范数；
		+ 对于稀疏数据，余弦度量和Tanimoto系数；
		+ pearson相关系数：衡量两个数据集是否在一条线上；用来描述两组线性的数据一同变化移动的趋势。
			+ pearson相关系数等于两个变量的协方差除于两个变量的标准差。
			+ 连续数据，正态分布，线性关系，用pearson相关系数；上述任一条件不满足，就用spearman相关系数，不能用pearson相关系数；两个定序测量数据之间也用spearman相关系数，不能用pearson相关系数。
	
	+ 应用
		+ 聚类、离群点分析、最近邻分类等

## 数据预处理		
+ **数据清理**
	+ 缺失值处理：
		+ 忽略元组：缺少类标号时
		+ 人工填写缺失值
		+ 使用一个全局常量填充，如：“Unknow”
		+ 使用属性的中心度量填充：中位数(倾斜数据而言)或均值
		+ 使用与给定元组属于同一类的所有样本的属性均值或中位数
		+ 使用最可能的值填充缺失值：决策树、贝叶斯推理

	+ 噪声数据
		+ 分箱：将有序的值分布到箱中，并用周围的值来光滑有序数据。
			+ 用箱均值光滑
			+ 用箱中位数光滑
			+ 用箱边界光滑
		+ 回归
		+ 离群点分析
			+ 利用聚类来检测离群点
		
+ **数据集成**
	+ 定义：合并来自多个数据存储的数据。
	+ 实体识别问题
	+ 冗余和相关分析
		+ 定义：一个属性可以由其他属性“导出”，称为冗余；利用相关分析来分析数据冗余，相关性越强，表明冗余度高。
		+ 卡方检验：标称数据
		+ 相关系数或协方差：数值属性
			+ 相关系数：Pearson系数
			+ 协方差：评估两个属性如何一起变化。
	+ 元组重复
	+ 数据值冲突的检测与处理

+ **数据归约**
	+ 维归约：把原数据变换或投影到较小的空间；
		+ 小波变换
		+ 主成分分析
		+ 属性子集选择(决策树中的做法)
	+ 数量归约：用较小的、替代的数据表示形式替换原数据；
		+ 参数方法：回归和对数-线性模型
		+ 非参数方法：直方图、聚类、抽样和数据立方体聚集
	+ 数据压缩：使用变换，以便得到原数据的归约或压缩表示；
		+ 有损压缩：只能近似重构原数据。
		+ 无损压缩：原数据能够从压缩后的数据重构，而不损失信息。
	
+ **数据变换和离散化**
	+ 光滑：去掉数据中的噪声；
		+ 分箱、回归和聚类
	+ 属性构造：可以由给定的属性构造新的属性并添加到属性集中；
	+ 聚集：对数据进行汇总或聚集；
	+ 规范化：把属性数据按比例缩放，使之落入一个特定的小区间；
		+ 最小-最大规范化
		+ z分数规范化
		+ 小数定标规范化：通过移动属性值的小数点位置进行规范化；
	+ 离散化：数值属性的原始值用区间标签或概念标签替换；
		+ 通过分箱离散化
		+ 通过直方图分析离散化
		+ 通过聚类、决策树和相关分析离散化
	+ 由标称数据产生概念分层



+ ****
+ ****




