###	range
	
	range(m,n)	#产生等差数列，序列开始于m，重复加1，直到n之前的n-1。
	range(n)	#等价于range(0,n)
	range(m,n,s)	#步长s：step value，变步长的整数序列。




##	NUMPY
###	ndarray(numpy的对象)

	ndarray.ndim	#数据轴的个数。二维数据两个轴。
	ndarray.shape	#数组的矩阵形状
	ndarray.size	#数组元素总个数
	ndarray.dtype	#数组元素的对象

###	创建数组
    
	np.array	#(列表)
    reshape(m,n)	#m行n列数组
    np.zeros((m,n))	#0矩阵
    np.ones((m,n))	#1矩阵


###	数组统计运算
   
	sum(arr)	#全部行和列的和
    sum(arr,axis=1)	#每行求和
    sum(arr,axis=0)	#每列求和