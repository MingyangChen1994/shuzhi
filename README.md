## 背景

​	教育中大数据分析目的包括改善学生成绩，服务教务设计，优化学生服务。而学生成绩中有一系列重要的信息往往被我们常规研究所忽视。通过大数据分析和可视化展示，挖掘重要信息，改善学生服务，对于教学改进意义重大。

​	为了更好的优化教学大数据应用场景，比赛通过学校教育数据分析和可视化工作，探索面向学生、校园的数据分析体系，募集优秀数据分析及可视化方案，设计并形成数据分析门户，从而更好服务精细化教学管理工作。

​	本工作主要利用MySQL，python进行数据预处理及相应指标计算，利用QuickBI工具进行数据门户的可视化。

**由于QuickBI数据门户页面无法公开，只能单独浏览各个分区仪表板**  
主页：https://bi.aliyuncs.com/token3rd/dashboard/view/pc.htm?pageId=787147fa-7ae4-4ce0-988f-b570aab0ada1&accessToken=1a5dbd1a7142670b7e8c26486a64b67f  
班级页面：https://bi.aliyuncs.com/token3rd/dashboard/view/pc.htm?pageId=253992e8-19bd-414f-8a33-51112d3bb1a7&accessToken=987bca25712e708da1c9f654a3f84f38  
教师页面：https://bi.aliyuncs.com/token3rd/dashboard/view/pc.htm?pageId=368460cc-f4b5-42de-aeda-a0754b18fd97&accessToken=fe26eebcf41b8dd9b4d828d6cef7fd50  
学生页面：https://bi.aliyuncs.com/token3rd/dashboard/view/pc.htm?pageId=989e2aa1-591f-48e6-82a1-a3b8be09be9d&accessToken=df76b0c01b185d2e486be764cbbce6d4  
荣誉墙及科目：https://bi.aliyuncs.com/token3rd/dashboard/view/pc.htm?pageId=bb081b92-4615-4475-9d01-3e6872a784aa&accessToken=3c61a9b7c26ff7a0fecaa82a7a6c3913


## 数据集

数据集 1_teacher

- term：学期，以数字形式存储，前两个字段为年限，第三个字段为学期。如2014-2015-1
- cla_id：班级id，以数字形式存储，如708
- cla_Name：班级，以文本和字符形式存储，如高二(02)
- gra_name：年级，以文本形式存储，如高二
- sub_id：学科id，以数字形式存储，如1
- sub_Name：学科名，以文本形式存储，如语文
- bas_id：班级老师id，以数字形式存储，如224
- bas_Name：班级老师姓名，以文本形式存储，如徐老师

数据集 2_student_info

- bf_StudentID：学生ID，以数字形式存储，如14454
- bf_Name：学生姓名，以文本的形式存储，但是已经脱敏，如陈某某
- bf_sex：学生性别，以文本的形式存储，数据呈二异性，如男
- bf_nation：学生民族，以文本的形式存储，如汉族
- bf_BornDate：出生日期，以数字形式存储，存在缺失值，如2001
- cla_Name：班级名称，以文本的形式存储，如白-高二(01)
- bf_NativePlace：出生地，以文本的形式存储，如宁波
- Bf_ResidenceType：出生地类型，以文本形式存储，如城镇
- bf_policy：政治面貌，以文本形式存储，大致分为三类：一般、少先队员、共青团员
- cla_id：班级id，以数字的形式存储，如901
- cla_term：学期，以数字形式存储，前两个字段为年限，第三个字段为学期。如2018-2019-1
- bf_zhusu：是否住校，以数字形式存储，如住宿为1，空白为0
- bf_leaveSchool：是否离校，以数字形式存储，如离校为1，空白为0
- bf_qinshihao：寝室号，以数字形式存储，数字表示寝室号码，空白表示不住校

 数据集 3_kaoqin

- kaoqing_id：考勤机的id，以数字的形式存储，如134324
- qj_term：考勤的学期，以数字的形式存储，前面两个是年限，后面一个为学期
- DataDateTime：考勤打卡的时间，以数字时间的形式存储，精确到年月日时分，如2018/1/27 12:21
- ControllerID：考勤机记录的类型，以数字的形式进行存储，如99003表示早退
- controler_name：考勤机记录的类型，以文本的形式进行存储，如早退[移动考勤机]
- control_task：控制任务，以数字的形式进行存储，为分类型数据，如9900300
- bf_studentID：考勤打卡的学生id，以数字形式存储，如13893
- bf_Name：考勤打卡学生的姓名，以文本形式存储，如陈某某
- cla_Name：班级号，以文本的形式进行存储，如高三(11)
- bf_classid：班级的id，以数字的形式进行存储，如872

数据集 4_kaoqintype

- controler_id：考勤id，以数字形式存储（如：1001）
- controler_name：考勤类型名称，以文本形式存储（如：迟到_晚到）
- control_task_order_id：考勤事件id，以数字形式存储（如：100000）
- control_task_name：考勤事件名称，以文本形式存储（如：早上迟到）

数据集 5_chengji

- mes_TestID：考试id，以数字形式存储（如：136424），考试编码相同并且考试学科相同，则考试id相同
- exam_number：考试编码，以数字形式存储（如：284），与考试编码名称一一对应
- exam_numname：考试编码名称，以文本形式存储（如：2017学年度第一学期期中考试），与考试编码一一对应
- mes_sub_id：考试学科id，以数字形式存储（如：17），与考试学科名一一对应
- mes_sub_name：考试学科名，以文本形式存储（如：政治），与考试学科id一一对应
- exam_term：考试学期，以数字形式存储（如：2017-2018-1，表示2017到2018年度第一学期）
- exam_type：考试类型，数字形式（如：2），对应考试类型表，与考试编码差不多，表示某个考试编码名称
- exam_sdate：考试开始时间，数字形式（如：2017/9/20 00:00:00）
- mes_StudentID：学生id，数字形式，对应某学生
- mes_Score：考试成绩，数字形式（注意：-1为作弊，-2为缺考，-3为免考，这三种情况均无下面三种成绩，为缺失值）
- mes_Z_Score：换算成Z-score，数字形式
- mes_T_Score：换算成T-score，数字形式
- mes_dengdi：换算成等第，数字形式

数据集 6_exam_type

- EXAM_KIND_ID：考试类型id，数字形式（如：2），对应数据集5中的考试类型
- EXAM_KIND_NAME：考试类型名称，文本形式（如：期中）

数据集 7_consumption

- DealTime：消费时间，形式与上面形式相同
- MonDeal：消费金额，数字形式，均为负数
- bf_studentID：对应学生信息表中的学生id，数字形式
- AccName：学生姓名，文本形式，已脱敏
- PerSex：学生性别，文本形式，男/女

## 目标

1. 学生成绩可视化帮助教师调整及学生指导；
2. 学科七选三推荐；
3. 通过消费数据挖掘潜在的贫困学生进行帮扶。

## 数据门户结构框架

​	学校网站面向不同用户，如校领导，班主任，学生，学生家长等，针对不同人群将数据门户分为了主页、班级页面、学生页面、教师页面及分析页面。详情如下：

|     层级     |     面向对象     |                      分析展示点                       |
| :----------: | :--------------: | :---------------------------------------------------: |
| 学校门户主页 | 校领导、学生家长 |           1. 学生总体概况；2. 教师整体概况            |
|   班级页面   |  校领导、班主任  | 1. 班级总成绩及各科目情况；2. 班级考勤；3. 班级贫困生 |
|   学生页面   | 教师、家长、学生 |        1. 学生成绩详情；2. 学生成绩趋势及预测         |
|   教师页面   |   校领导、教师   |      1. 师资力量概况；2. 教师授课科目及班级情况       |
|   分析页面   |    教师、学生    |               1. 荣誉墙；2. 科目七选三                |

1. 学校门户主页。  

![Alt text](https://github.com/MingyangChen1994/shuzhi/blob/master/%E6%80%9D%E7%BB%B4%E5%AF%BC%E5%9B%BE/%E4%B8%BB%E9%A1%B5.png)

2. 学生画像。  

![Alt text](https://github.com/MingyangChen1994/shuzhi/blob/master/%E6%80%9D%E7%BB%B4%E5%AF%BC%E5%9B%BE/%E5%AD%A6%E7%94%9F%E9%A1%B5%E9%9D%A2.png)

3. 班级画像。  

![Alt text](https://github.com/MingyangChen1994/shuzhi/blob/master/%E6%80%9D%E7%BB%B4%E5%AF%BC%E5%9B%BE/%E7%8F%AD%E7%BA%A7%E9%A1%B5%E9%9D%A2.png)

4. 教师画像。  

![Alt text](https://github.com/MingyangChen1994/shuzhi/blob/master/%E6%80%9D%E7%BB%B4%E5%AF%BC%E5%9B%BE/%E6%95%99%E5%B8%88%E9%A1%B5%E9%9D%A2.png)

5. 荣誉墙及科目推荐  

![Alt text](https://github.com/MingyangChen1994/shuzhi/blob/master/%E6%80%9D%E7%BB%B4%E5%AF%BC%E5%9B%BE/%E5%88%86%E6%9E%90%E9%A1%B5%E9%9D%A2.png)

**定义指标包括：**

**1. 优秀学生：排名年级前100；**

**2. 偏科学生：最高分与最低分年级排名相差200；**

**3. 进步之星：当前比上月考试排名进步超过200名；**

**4. 退步：当前比上月考试排名退步超过200名；**

**5. 优秀班级：班级总分平均分排名前10%；**

**6. 优秀教师：带的班级的科目平均分超过总的班级科目平均分/排名前5；**

**7. 贫困学生：消费低于全校平均月消费且消费额度班级排名倒数前5**



​	
