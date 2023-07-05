1. insert CT_MANAGE 
   - 根据当前合同pk（例如a）复制当前行并插入新记录
     - 其中：
       - PK_CT_MANAGE为新值例如b
       - ACTIVEFLAG = 1
       - **PK_ORIGN** = 当前合同pk（例如a）
       - 其他字段于原纪录相同；

2. update CT_MANAGE 
   - 更新当前合同pk（例如a）对应的记录，where PK_CT_MANAGE = a
   	 - 其中：
   	   - VERSION 加**1.0**
   	   - TS 当前时间
   	   - CLASTOPERATORID 最后修改人 取当前操作人
   	   - TLASTMAKETIME 最后修改时间 取当前时间

3. insert CT_MANAGE_B

   - 根据当前合同CT_MANAGE_B表中的记录复制并插入新记录，基于PK_CT_MANAGE = a

     - 其中：

       - PK_CT_MANAGE 为步骤1中的新值b

       - PK_CT_MANAGE_B 创建新主键

       - 其他字段与原纪录相同

       - 且原合同中存在X行记录，便插入X行新记录

4. insert CT_MANAGE_B

   - 根据收货商品明细，新增记录
     - 其中：
       - PK_CT_MANAGE 为原合同主键a
       - PK_CT_MANAGE_B 创建新主键
       - CROWNO 为原记录CROWNO字段值加10，多行记录时依次加10
       - 其他为商品相关字段：商品、数量、单价、金额等

5. insert CT_CHANGE_BB1

   - 新增变更记录
     - 其中：
       - CHANGECODE 原记录最大值加**1.0**
       - CHGDATE 当前日期
       - CHGPSN 用户名
       - PK_CT_CHANGE 新主键
       - TS 取当前时间
       - 其他字段于原最新记录相同
