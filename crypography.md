##用对称密码实现保密性
	
1.	目的：
	*	加密什么
	*	在什么地方加密
2.	基本方法：
	*	链路加密（通信链路加密）
	*	端对端加密（终端加密）
3.	链路加密
	1.	优点
		*	抵御通信量分析
	2.	缺点
		*	消息在节点公开
		*	密钥量与节点个数有关，较大
4.	端对端加密
	1.	优点
		*	消息在节点不公开
	2.	缺点
		*	不能抵御通信量分析
5.	加密放置
	1.	混合使用两种加密方法
	2.	链路加密放在层1、层2
	3.	端对端加密放在层3、层4、层6、层7
	4.	越是上层，加密信息越小，安全性能越好
6.	密钥分配
	
		任何密码系统的强度都与密钥分配方法有关
	1.	

##随机数

	要求：随机性和不可预测性

1.	应用
	*	临时交互号，用于防止重复攻击
	*	会话密钥产生
	*	RSA算法中密钥产生
2.	随机数的源
	*	真随机数（物理噪声发生器，难以获得）
	*	伪随机数（算法生成）



##用户认证
###Kerberos认证

	基于对称密钥体制

1.	在分布式网络中提供有第三方参与的基于私钥的认证
	1.	允许用户通过访问分布在网络中的服务
	2.	没有必要相信所有的工作站
	3.	都信任中心服务器
2.	模型
	1.	认证服务器AS
	2.	认证证书TGT（ticket granting ticket）
	3.	票据授权服务器TGS
3.	Kerberos作用
	1.	Ticket的安全传递
	2.	Session Key的安全发布




###X.509认证
基于公开密钥体制和数字签名