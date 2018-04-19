---
title: 生意通CPC
tags: 新建,模板,小书匠
grammar_cjkRuby: true
---

[toc]


# 流程
## 推广计划
### 1.新建
| Index  |  Desc    |
| ---    | ---   |
|   URL  |  aps/new/cpc_new_promotion_by_name.htm <br>{	name，dept，startDate}| 
|   VIEW |  new\cpc\cpc_standard_promotion_list.ftl  |
|  TABLE | t_aps_promotion  |
|   CODE |   [计划：新建](#promotionNew) |

### 2.查询
| Index  |  Desc    |
| ---    | ---   |
|   URL  |  aps/new/cpc_standard_promotion_list.htm| 
|   VIEW |  new\cpc\cpc_standard_promotion_list.ftl  |
|  TABLE | t_aps_promotion  |
|   CODE |   [计划：查询](#promotionList) |

### 3.编辑
| Index  |  Desc    |
| ---    | ---   |
|   URL  |  aps-sale-web/aps/new/cpc_promotion_detail.htm?</br>startDate=2018-03-23&endDate=2018-03-23&promotionId=16078106| 
|   VIEW |  new/cpc/cpc_promotion_detail.ftl --productType=2(生意通)</br>new/cpc_shop/cpc_promotion_shop_detail.ftl--productType=4(CPC店铺推广)|
|   CODE |   [计划：编辑/详情](#promotionDetail)   |

### 4.暂停
| Index  |  Desc    |
| ---    | ---  |
|   URL  |  /aps/new/cpc_pause_promotion.htm <br>{promotionId }| 
|   VIEW |  new\cpc\cpc_standard_promotion_list.ftl  |
|   CODE |   [计划：暂停](#promotionPause)   |


### 5.恢复
| Index  |  Desc    |
| ---    | ---  |
|   URL  |  aps/new/cpc_resume_promotion.htm?promotionId=<br>{promotionId }| 
|   VIEW |  new\cpc\cpc_standard_promotion_list.ftl  |
|   CODE |   [计划：恢复](#promotionResume)   |

### 6.修改计划名称
| Index  |  Desc    |
| ---    | ---   |
|   URL  |  aps/new/cpc_modify_promotion_name.htm</br>{</br>promotionId : promotionId,</br>	name : name</br>	}| 
|   VIEW |  new\cpc\cpc_standard_promotion_list.ftl  |
|  TABLE | t_aps_promotion |
|   CODE |   [计划：修改名称](#promotionModifyName) |

### 7.修改时间定向
| Index  |  Desc    |
| ---    | ---   |
|   URL  |  aps-sale-web/aps/new/cpc/promotion/saveHours.htm?promotionId=promotionId&throwHours=0+2+3| 
|   VIEW |  new\cpc\cpc_standard_promotion_list.ftl  |
|  TABLE | t_aps_promotion、t_aps_promotion_item(1001)  |
|   CODE |   [计划：修改时间定向](#promotionModifyHours) |

### 8.设置投放平台
| Index  |  Desc    |
| ---    | ---   |
|   URL  |aps/save/updateCpcThrowControlByPromotion.htm </br>{</br>promotionId : promotionId,</br>throwDiscount :putDiscount,</br>positionType : app\|hot</br>}| 
|  TABLE | t_aps_promotion、t_aps_promotion_item(1001)[promotionId]  |
|   CODE |   [计划：设置投放平台](#promotionSetThrowPlat) |

### 设置投放时间
| Index  |  Desc    |
| ---    | ---   |
|   URL  |aps/new/cpc_set_throwtime.htm </br>{</br>promotionId : 16078106,</br>startDate : 2018-03-24,</br>endDate : 2018-04-20,</br>slotArr :0 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23</br>}| 
|  TABLE | t_aps_promotion、t_aps_promotion_item(1001)  |
|   CODE |   [设置投放时间](#promotionSetThrowTime) |

### 修改（定向）投放地域
| Index  |  Desc    |
| ---    | ---   |
|   URL  | 列表页： aps/new/cpc/promotion/saveArea.htm?promotionId=16078106&throwArea=10+20</br></br>编辑页：aps/new/cpc_set_throwarea.htm?promotionId=16078106&areaStr=10 20 30| 
|   VIEW |  new\cpc\cpc_standard_promotion_list.ftl  |
|  TABLE | t_aps_promotion、t_aps_promotion_item(1002)   |
|   CODE |   [修改定向地域](#promotionModifyArea) |



### 修改日限额
| Index  |  Desc    |
| ---    | ---   |
|   URL  |  查询：aps/customBudget/cpc_daycost_init_data.htm?promotionId=promotionId</br></br>设置：aps-sale-web/aps/customBudget/cpc_set_daycost.htm?</br>{	promotionId : promotionId,</br>cpcDayAmount: {"defaultUserLimitAmount":1000,"customData"::[{"date":"2018-04-02","userLimitAmount":1200},{"date":"2018-04-03","userLimitAmount":1300},{"date":"2018-04-04","userLimitAmount":1400}]}| 
|  TABLE | t_aps_promotion  |
|   CODE |   [修改日限额](#promotionModifyDayCost) |

## 推广单元
### 新建
| 选择商品  |  Desc    |
| ---    | ---   |
|   URL  |  aps-sale-web/new/unit/selectProduct.htm?promotionId=16078106| 
|   VIEW |  /new/cpc/cpc_unit_select_product.ftl|
|   CODE |   [新建推广单元](#unitNew) |
|    *  |
| **选择商品图片**    |  **Desc**    |
|   URL  |  aps-sale-web/new/unit/selectProduct.htm?promotionId=16078106| 
|   VIEW |  /new/cpc/cpc_unit_select_picture.ftl|
|   CODE |   [新建推广单元](#unitNew) |
|    *  |
| **设置投放位置**    |  **Desc**    |
|   URL  | aps-sale-web/new/unit/selectKeywordAndCatalog.htm?imgIndex=2&promotionId=16078106&productNum=000000011051101634&src=| 
|   VIEW |  /new/cpc/cpc_unit_select_keyword.ftl|
|  TABLE | t_aps_promotion  |
|   CODE |   [新建推广单元](#unitNew) |



### 删除
| 删除推广单元  |  Desc    |
| ---    | ---   |
|   URL  |  /aps-sale-web/aps/new/cpc_delete_promotion_unit.htm</br>$.param({</br>	promotionId : '16078106',</br>	unitId : unitId</br>	}| 
|   VIEW |  /new/cpc/cpc_unit_select_product.ftl|
|   CODE |   [新建推广单元](#unitDel) |


### 暂停
| 暂停推广单元  |  Desc    |
| ---    | ---   |
|   URL  |aps/new/cpc_pause_promotion_unit.htm?promotionId=16078106&unitId=16105314| 
|   VIEW |  /new/cpc/cpc_unit_select_product.ftl|
|   CODE |   [暂停推广单元](#unitPause) |

### 开始
| 开始推广单元  |  Desc    |
| ---    | ---   |
|   URL  |  aps/new/cpc_resume_promotion_unit.htm?promotionId=16078106&unitId=16105314&productType=2| 
|   CODE |   [开始推广单元](#unitStart) |


### 编辑
| 编辑推广单元  |  Desc    |
| ---    | ---   |
|   URL  |加载： new/unit/modifyUnit.htm?cpcPromotionId=16105318&promotionId=16078106 </br></br>提交：ajax/unit/updateUnit.htm| 
|   VIEW |/new/cpc/cpc_unit_modify.ftl|
|   CODE |   [编辑推广单元](#unitEdit) |



# 投放报表
## 4.推广计划报表
| Index  |  Desc    |
| ---    | ---  |
|   URL  |  aps/new/report_promotion_plan.htm| 
|   VIEW |  new\cpc\cpc_standard_promotion_list.ftl  |
|   CODE |   [推广计划_查询](#promotion_report)   |


----------

# 备忘
## <span id="promotionNew">计划：新建</span>

1.处理页面入参
最低价：系统参数KEYWORD_DAY_LOWER_PRICE
USER_TYPE==1 设置事业部编码 默认0

2.校验 开始时间不能小于今天、该名称推广计划是否存在(T_APS_PROMOTION.NAME)
``` sql
   SELECT COUNT(1) 
    		FROM  	WHERE NAME = :creatPromotionName AND USER_ID = :userId AND PAY_TYPE = 2 AND ISACTIVE=1 AND PROMOTION_ID != :promotionId
```

3.组装计划信息 入库
   根据开始时间判断推广计划的状态： ==\>today  1:等待推广    =today  3:正在推广==
   推广计划id：：==SEQ_T_APS_PROMOTION==
sqlId: standardPromotion.createPromotion   **T_APS_PROMOTION**

4.记录用户操作日志



---------
## <span id="unitNew">单元：新建</span>
一.选择商品
{promotionId=16078106,  userType=1, supplierType=C, shopId=0070057240, searchUrl=http://csearchpre.cnsuning.com/emall/cshop/queryByKeyword.do, 
productPicUrl=http://uimgpre.cnsuning.com,
productPicLinkUrl=http://productpre.cnsuning.com, 
proInfo={PROMOTION_ID=16078106, NAME=zxbTest, START_DATE=2018-03-24 00:00:00.0, END_DATE=null, USER_LIMIT_AMOUNT=1000, CREATE_DATE=2018-03-23 16:11:05.741}}
**商品查询**
商户编码 18（左补0
/ajax/unit/queryProduct.htm
data : "date=1521804144793&productNum=000000011051101634&productType=2"
该商品是否已被计划占用
``` sql
	    	SELECT 
	    		A.NAME
	    	FROM 
	    		T_APS_PROMOTION A,T_APS_PROMOTION_CPC B 
			WHERE 
				A.PROMOTION_ID=B.PROMOTION_ID 
				AND A.USER_ID=:userId
				<#if productType?exists>AND A.PRODUCT_TYPE = :productType</#if>
				AND A.PROMOTION_STATUS !=8
				AND B.GOODS_CODE=:productNum
				AND A.ISACTIVE=1 
				AND B.ISACTIVE=1
```
businessType: "priceText"
dataExchangeInfo {
  goodsCode: "000000011051101634"
  cityCode: "025"
  shopCode: "0070057240"
  terminalType: "1"
}
http://admdspre.cnsuning.com/admdso/goods/textprice
1.自营旗舰店账户：(USER_TYPE=4)&& 系统参数AD_QUERY_STATUS=1

2.sop外部商户需要查询商品状态信息：(USER_TYPE=2)&& 系统参数AD_QUERY_STATUS=1
appliCode:供应商编码
productQueryService.getProductStatus(GoodsCodeUtil.getValidGoodsCode(productNum),appliCode.substring(2))
 需要查询商品状态信息 supplierType=C  [!=LT联营特卖商户]
    {
    type=00,   00：子码   01：通码 的商品编码不符合要求
    status=Y 商品编码与商户匹配&&在售
    }
3.非自营旗舰店USER_TYPE!=4 
调用rsf或esb接口查询商品相关信息

productQueryService.getProduct(productNum, appliCode)
scm上的scm.goodsinfo.intftype配置如果不存在或者配的是rsf，就使用商品中心的rsf接口查询商品信息
接口返回：
{returnCode=0, brandName=海尔(Haier), brandId=000070743, catentryId=null, partNumber=000000011051101634, catentryName=11位商品编码测试003, categoryCode=R2403004, published=null, goodsName=11位商品编码测试003, lastCatagoryId=258004, desc=3333333333333测试}

result：
{flag=true, datas={brandName=海尔(Haier), THIRD_PAGE_CODE=258004, catentryId=null, catentryName=11位商品编码测试003, categoryCode=R2403004, published=null, lastCatagoryId=258004, returnCode=0, FIRST_PAGE_CODE=157122, brandId=000070743, partNumber=000000011051101634, isInStock=false, goodsName=11位商品编码测试003, SECOND_PAGE_CODE=258003, desc=3333333333333测试, priceUrl=http://price1.suning.cn/webapp/wcs/stores/prdprice/11051101634_9173_0070057240_9-1.png}}

二、选择商品图片
 cpcPromotionInfoProcessService.getProductPicUrl(productNum, user.get("shopId")))
 RSF查询商品图片版本信息，未查询到则按默认规则拼凑
 ![enter description here][1]
 
 三、设置投放位置
 aps-sale-web/new/unit/selectKeywordAndCatalog.htm?imgIndex=2&promotionId=16078106&productNum=000000011051101634&src=
1.获取session中保存的商品信息
```java
   Map<String, Object> proInfo = (Map<String, Object>) user.get(Aps.PRO_INFO);
        if (null == proInfo || proInfo.isEmpty()) {
            proInfo = unitService.queryPromotionInfoById(promotionId);
        }
```
```sql
 SELECT A.PROMOTION_ID,A.NAME,A.CREATE_DATE,B.START_DATE,B.END_DATE,B.USER_LIMIT_AMOUNT 
 FROM T_APS_PROMOTION A,T_APS_PROMOTION_CPC B 
 WHERE A.PROMOTION_ID = :promotionId AND A.PROMOTION_ID= B.PROMOTION_ID
```
2.查询系统推荐词：系统参数 KEYWORD_TOOLS_METHOD--1：数据平台
三级目录关键词不够+二级目录关键词
``` java
     if ("1".equals(isNew)) {
                //按照类目相关度、search_num降序排列(取20条)
                recWordList = unitService.querySysRecWordsFromDataPlat(thirdCataId);
            } else {
                recWordList = unitService.querySysRecWords(thirdCataId);
            }
```
``` sql
WITH BASE (KEYWORD,SCORE,SEARCH_NUM,POSITION_ID,PERCENT,AVGPRICE) AS (
			        SELECT 
			                DISTINCT A.KEYWORD,
			                ${score} SCORE,
			                C.SEARCH_NUM,
			                '100000001' AS POSITION_ID,
			                decimal(ROUND(NVL(C.CLICK_PERCENT*100.0,0.0),2),10,2) AS percent,
			                decimal(round(NVL(C.AVG_PRICE,0)/100.0,2),10,2) AS avgPrice
			        FROM T_APS_KEYWORD_PAGE_REL A,T_APS_KEYWORD_TOOL_DATA_FRONT C 
			        WHERE A.KEYWORD=C.KEYWORD 
			                AND A.STATUS=1
			                <#if thirdCode?exists && thirdCode != ''>
								AND A.THIRD_PAGE_CODE = :thirdCode
							</#if> 
							<#if secondCode?exists && secondCode != ''>
								AND A.SECOND_PAGE_CODE = :secondCode
							</#if> 
							<#if keywrods?exists && keywrods != ''>
								AND A.KEYWORD NOT IN(:keywrods)
							</#if> 
			                AND EXISTS(SELECT 'X' FROM T_APS_SEARCH_KEYWORD B WHERE B.KEYWORD_NAME=A.KEYWORD)
			        ORDER BY C.SEARCH_NUM DESC
			        FETCH FIRST ${rowNum} ROWS ONLY
			)
			
			SELECT E.*,NVL(P.COMPET_NUM,0) AS COMPET_NUM
			FROM BASE E LEFT JOIN
			(SELECT 
			        D.NAME,COUNT(1) COMPET_NUM 
			        FROM T_APS_CPC_PROMOTION_DATA D
			        WHERE D.PROMOTION_TYPE=0  
			        AND D.PROMOTION_DATE= CURRENT DATE 
			        GROUP BY D.NAME
			) P
			ON E.KEYWORD = P.NAME WITH UR
```

3.查询系统推荐类目：系统参数  CATALOG_TOOLS_METHOD
 

``` sql
     --	{thirdCode=258004, saleObj=1, secondCode='%!_258003!_%', status=1}
     		SELECT A.LIST_SEQ,
			        A.SCORE,
			        A.LIST_SEQ as KEYWORD,
			        A.NAME_SEQ,
			        A.CODE_SEQ AS CODE,
			        A.POSITION_ID,
			        NVL(B.SEARCH_NUM,0) SEARCH_NUM,
			        decimal(ROUND(NVL(B.CLICK_PERCENT*100.0,0.0),2),10,2) AS percent,
			        decimal(round(NVL(B.AVG_PRICE,0)/100.0,2),10,2) AS avgPrice
			FROM 
			        (SELECT T1.LIST_SEQ,(CASE WHEN T1.CODE_SEQ=${thirdCode} THEN '100' ELSE '80' END ) SCORE,
			        		T1.NAME_SEQ,T1.CODE_SEQ,T2.POSITION_ID 
			         FROM T_APS_CPC_POSITION_REL T1,T_APS_ADS_POSITION T2 
			         WHERE T1.LIST_SEQ LIKE ${secondCode} ESCAPE '!' AND T1.POSITION_ID=T2.POSITION_ID AND T1.STATUS = 1 
			        AND T1.EFFECT_DATE <= current timestamp AND (T2.SALE_OBJ=2 OR T2.SALE_OBJ=:saleObj)) A 
			LEFT JOIN
			        (SELECT KEYWORD,SEARCH_NUM,CLICK_PERCENT,AVG_PRICE FROM T_APS_KEYWORD_TOOL_DATA_FRONT WHERE PROMOTION_TYPE=1) B
			ON A.CODE_SEQ=B.KEYWORD
			WITH UR
```


4.查询系统限制的三级类目,若该商品为限制类目下面的商品，
则其投放的关键词不能夸三级类目，投放类目只能是该三级类目
数据字典配置：THIRD_PAGE_LIMIT

关键词系统最低出价KEYWORD_LOWER_PRICE
类目系统最低出价LOCATION_LOWER_PRICE
 
     @ApsScmConf("scm.cpc.isShowYJQ")
    private String isShowYJQ;

    @ApsScmConf("scm.cpc.isShowYJQ")
    private String isShowYJQ;
  一键抢排名功能展示开关SCM配置
    @ApsScmConf("scm.cpc.isShowMorePositionRank")
    private String isShowMorePostionRank;
  是否开启多广告位的预估排名
  
"cpcPositionControlGroup",cpcCommonService.queryAllPositionControlInfoByRelId(Long.parseLong(promotionId),1)

**提交**
 selectWord.goSubmit('/ajax/unit/savePromotionUnit.htm');
请求：
{
  "datas": "[{w:258004//类目,pId:100001033//广告位id,p:0.38//用户出价},{w:笔记本,p:0.10},{w:联想笔记本,p:0.10}]",
  "productNum": "000000011051101634",
  "promotionId": "16078106",
  "needTodayRec": true,
  "cpcUnitItemListJson": [
    {
      "itemCode": "1002",
      "itemValue": "top3"
      //前三名
    },
    {
      "itemCode": "1003",
      "itemValue": "10"
      //溢价系数
    },
    {
      "itemCode": "1004",
      "itemValue": "1"
      //一键抢 1：checked
    },
    {
      "itemCode": "1001",
      "itemValue": "2"
      // 1：精准匹配 2：广泛匹配
    }
  ]
}
1.类目
质量得分计算结果：
{relateScore=10, qualityScore=10, detailList=[{score=10, qualityType=1, percent=1.0}], standardScore=1}



分类编码层级

``` sql
 	SELECT LIST_SEQ  FROM T_APS_CPC_POSITION_REL WHERE STATUS=1 
                                                     AND CODE_SEQ=258004 AND POSITION_ID = 100001033
01_157122_258003_258004
```


根节点_一级目录_二级目录_三级目录
**cataMap:**{FIRST_PAGE_CODE=157122, THIRD_PAGE_CODE=258004, SECOND_PAGE_CODE=258003}

字典表AD_QUALITY_MATCH_SCORE 配置 质量得分分段及分数
**scoreMap:**{1=10, 2=8, 3=4, 4=1}
**goodsMap:**{brandName=海尔(Haier), THIRD_PAGE_CODE=258004, catentryId=null, catentryName=11位商品编码测试003, categoryCode=R2403004, published=null, lastCatagoryId=258004, returnCode=0, FIRST_PAGE_CODE=157122, brandId=000070743, partNumber=000000011051101634, isInStock=false, goodsName=11位商品编码测试003, SECOND_PAGE_CODE=258003, desc=3333333333333测试, priceUrl=http://price1.suning.cn/webapp/wcs/stores/prdprice/11051101634_9173_0070057240_9-1.png}

> 得分 三级目录》二级目录》一级目录

**weight：** 字典表 AD_QUALITY_PERCENT 配置权重 key==1对应的value/100


相关度得分
质量得分==cataMap跟goodsMap中目录匹配后(关联scoreMap)得分*权重



2.关键词


temp:{258004={positionId=100001033, price=38, relateScore=10, qualityScore=10, detailList=[{score=10, qualityType=1, percent=1.0}], standardScore=1}, 
笔记本={positionId=100000001, price=10, relateScore=10, qualityScore=10, detailList=[{score=10, qualityType=1, percent=1.0}], standardScore=1, keyword=笔记本}}

调用评价系统接口

                maxSize = this.getReviewSizeConfig("MAX_CMMDTY_REVIEW_SIZE", 22);
                minSize = this.getReviewSizeConfig("MIN_CMMDTY_REVIEW_SIZE", 8);
                // 通过调用评价系统接口，推广商品的评价标签拼接信息，保存至pInfo中，准备下一步入库到推广单元表中 end
                pInfo.put("jsonArr", jsonArr);
                // 调用搜索商品中心ESB接口，查询子码对应的通码数据 start
                String generalCmmdtyCode = generalCmmdtyCodeQueryService.getGeneralCmmdtyCodeByGoodsCode(productNum);

保存推广单元数据
seqId:SEQ_T_APS_PROMOTION_CPC
sqlId:proUnit.persistCpcPromotion   INSERT INTO T_APS_PROMOTION_CPC
	UPDATE T_APS_PROMOTION SET UPDATE_DATE = CURRENT TIMESTAMP,STATUS_UPDATE_TIME = CURRENT TIMESTAMP WHERE PROMOTION_ID = :promotionId
 更新推广单元属性 proUnit.insertUnitItemList


``` sql
			INSERT
			INTO
			    T_APS_PROMOTION_CPC_ITEM
			    (
			        ID,
			        CPC_PROMOTION_ID,
			        ITEM_CODE,
			        ITEM_VALUE,
			        CREATE_DT
			    )
			    VALUES
			    (
			        nextval FOR SEQ_T_APS_CPC_UNIT_ITEM_ID,
			        :cpcPromotionId,
			        :itemCode,
			        :itemValue,
			        SYSDATE
			    )
```
存储所有关键词/类目的信息，用于后续生成所有detail
proUnit.persistCpcDetailNew INSERT	INTO T_APS_PROMOTION_CPC_DETAIL
调用kafka发送逻辑

暂停一键推广中的商品
 cpcOneThrow.queryPromotion
 			SELECT P.PROMOTION_ID, P.USER_ID, P.PROMOTION_STATUS, P.STATUS,P.USER_LIMIT_AMOUNT AS DAY_AMOUNT, P.NAME,
			(
			        SELECT
			            COUNT(1)
			        FROM
			            T_APS_CPC_PROMOTION_COST_OVER c
			        WHERE
			            c.PROMOTION_ID = P.PROMOTION_ID
			        AND c.PROMOTION_DATE = :promotionDate) AS "COST_OVER",
			        U.COMPANY_CODE, U.TYPE AS USER_TYPE
			FROM T_APS_PROMOTION P INNER JOIN T_APS_USER U ON P.USER_ID=U.USER_ID
			WHERE P.USER_ID=:userId AND P.PRODUCT_TYPE=:productType AND ISACTIVE=:isActive
			

---------

## <span id="promotionModifyName">计划：修改推广名称</span>
更新推广计划表 计划名称和更新时间 ==T_APS_PROMOTION（NAME、UPDATE_DATE）==

## <span id="promotionModifyHours">计划：修改时间定向</span>

 1. 修改计划时间属性 T_APS_PROMOTION_ITEM ( PROMOTION_ID,ITEM_CODE, ITEM_VALUE,CREATE_DT)
 2. 获取推广计划信息&&计划下正常推广单元数
 3. 满足==推广状态：正在推广，推广计划状态：正常==的计划，修改了投放时段后

    执行冻结操作（计划下有正常推广单元）
    : 冻结成功，kafka 发送计划变更信息
    冻结失败，更新推广计划STATUS为 0余额不足暂停

## <span id="promotionSetThrowPlat">计划：设置投放平台</span>
备注：投放时会将单元投放到不同的广告位，有标准广告位和溢价广告位
设置投放平台和投放折扣后，更新常量配置中的positionId为溢价广告位的单元出价。
1.更新溢价广告位控制数据（修改溢价折扣）

![enter description here](https://i.loli.net/2018/04/04/5ac49f339cb5e.jpg)

``` java
        Map<Long, String> appPositionIdMap = new HashMap();
        appPositionIdMap.put(100000007L, "keyword");
        appPositionIdMap.put(100000008L, "category");
        appPositionIdMap.put(100000009L, "guess");
        appPositionIdMap.put(100000016L, "guess");
        appPositionIdMap.put(100000017L, "guess");
        appPositionIdMap.put(100000018L, "guess");
        Map<Long, String> hotPositionIdMap = new HashMap();
        hotPositionIdMap.put(100000002L, "keyword");
        hotPositionIdMap.put(100000003L, "category");
```
广告位控制Map
**cpcPositionControlGroup**
this.groupMap.put(positionId, cpcPositionControlDto);

2.更新具体detail数据
获取该推广计划的所有详情数据

``` sql
-- standardPromotion.geiAllCpcPromotionDetailInAllPosition
            SELECT
                d.CPC_PROMOTION_DETAIL_ID,
                d.CPC_PROMOTION_ID,
                d.TYPE,
                d.KEYWORD,
                d.SORT,
                d.START_DATE,
                d.END_DATE,
                d.USER_PRICE,
                d.MIN_PRICE,
                d.POSITION_ID,
                d.PUSH_DATE,
                d.QUALITY,
                d.STANDARD_QUALITY,
                d.KEYWORD_CATEGORY,
                d.KEYWORD_BRAND
            FROM
                APSADMIN.T_APS_PROMOTION pro,
                APSADMIN.T_APS_PROMOTION_CPC cpc,
                APSADMIN.T_APS_PROMOTION_CPC_DETAIL d
            WHERE
                pro.PROMOTION_ID = cpc.PROMOTION_ID
            AND cpc.CPC_PROMOTION_ID = d.CPC_PROMOTION_ID
            AND cpc.ISACTIVE = 1
            AND pro.PROMOTION_ID = :promotionid
```


分组
detailGroup // key:单元id-关键词（CPC_PROMOTION_ID-KEYWORD），value:List<detail数据>

 2.更新具体detail数据
 逐个单元下的每一个词，单独重新计算出价，如果出价有变化[通过positioId区分出标准和溢价广告位，两者相比较]，存入需要更新出价的清单中，用于之后批量更新

``` javascript
 detailGroup.each(
 function(index,element){
 
 typeMap.put(element.positionId,element)
  Map<String, Object> keywordDetail=typeMap.get('100000001')//关键词基础数据
  Map<String, Object> categoryDetail =typeMap.get('100001033')//类目基础数据
 
 关键词出价和溢价后的关键词出价不相同，需要更新
 需要做溢价的广告位出价!=标准类目出价 x 该溢价广告位的折扣
 });
```
3.更新需要变更出价的 溢价广告位数据
==standardPromotion.batchThrowAppDetail T_APS_PROMOTION_CPC_DETAIL.USER_PRICE==

 4.存在需要更新的出价数据，就需要发送整个计划的kafka消息
            kafkaPromotionService.sendSaveThorwDetailKafka(userId, companyCode, userType, String.valueOf(promotionId));
            
## <span id="promotionSetThrowTime">计划：设置投放时间</span>	
	1.更新推广计划属性	
	2. 设置投放时间
	 开始时间不能修改为小于今天
     结束时间不能早于当前系统时间
     晚上8点后再修改的推广计划，结束时间至少是第二天
   3. 推广计划由等待推广改为正在推广	
实时投放，判断是否需要冻结以及发送kafka消息
存在未删除且正常推广的推广单元
原本计划就是正在推广状态，直接发送单纯的计划信息修改
cpcFreezeRealTimeKafkaService.freezeAndSendUpdatePromotion(promotionId, null);
如果原计划为等待推广，由于改变开始时间，导致变更成了正在推广状态，发送计划下的全部单元数据的实时投放消息
cpcFreezeRealTimeKafkaService.freezeAndSendUpdatePromotionWithAllUnit(promotionId, null);
 更新推广计划STATUS为 1正常
editPromotionStatus(Integer.valueOf(ApsConstants.STATUS_1), promotionId);


## <span id="promotionModifyArea">计划：修改定向地域</span>

``` java
        CpcPromotionItem cpi = new CpcPromotionItem();
        cpi.setPromotionId(promotionId);
        cpi.setItemCode(CpcPromotionItem.AREA_ITEM_CODE：1002);
        cpi.setItemValue(areaStr);
        cpcCommonService.updatePromotionItem(cpi);
        
        apscommom_cpcBase.deletePromotionItemList 、t_aps_promotion_item(1002) 
        apscommom_cpcBase.insertPromotionItemList
        // 发送消息到kafka
        sendPromotionData(promotionId, userId);
```


## <span id="promotionModifyDayCost">计划：修改日限额</span>
查询：aps/customBudget/cpc_daycost_init_data.htm?promotionId=promotionId

``` sql
--cpcDayAmount.getDayAmountByPromotionID
		SELECT
				SUBSTR(PROMOTION_DATE,1,10) AS date ,
				USER_LIMIT_AMOUNT AS userLimitAmount
			FROM
					APSADMIN.T_APS_PROMOTION_CUSTOM_BUDGET b--特殊日预算集合

			WHERE
				b.PROMOTION_ID=:promotionId
-----------------------------------------------	
--standardPromotion.queryPromotion
	    	    SELECT
			    USER_LIMIT_AMOUNT--默认日预算
			FROM
			    T_APS_PROMOTION
			WHERE
			    PROMOTION_ID = :PROMOTION_ID
```
1、校验是否大于系统默认最低日限额:KEYWORD_DAY_LOWER_PRICE
2、校验每日预算表：批量验证每日日预算、并且在批量验证的时候， 获取今天的日预算
3.如果推广计划在正常推广，则需要设置将今天的日预算与今日实时消耗金额做比较
 非完成推广状态的推广计划的日预算不能调低至比当前实际消耗的金额还低
``` sql
--sqlId:account.getNowCpcRealCostByPromotionId  |params:{promotionDate=2018-04-02, promotionId=16078106}
	SELECT
			    p.DAY_COST
			FROM
			    T_APS_RELEASE_CPC_PROMOTION p
			WHERE
			    p.PROMOTION_ID = :promotionId
			AND p.PROMOTION_DATE = :promotionDate
```
cpcNowRealCost + maxDayCostIntervalPrice[CPC推广计划实时消耗金额上浮区间（单位分）]:系统配置 MAX_CPC_DAYCOST_INTERVAL_PRICE
4.校验通过：
更新推广计划日预算 -1：失败；0：成功

``` sql
			UPDATE T_APS_PROMOTION SET
				NAME = :NAME, 
				PAY_TYPE = :PAY_TYPE, 
				PROMOTION_STATUS = :PROMOTION_STATUS, 
				STATUS = :STATUS, 
				TOTAL_DAYS = :TOTAL_DAYS, 
				TOTAL_AMOUNT = :TOTAL_AMOUNT, 
				DEPARTMENT_ID = :DEPARTMENT_ID, 
				CREATE_DATE = :CREATE_DATE, 
				UPDATE_DATE = CURRENT TIMESTAMP, 
				STATUS_UPDATE_TIME = CURRENT TIMESTAMP, 
				PRODUCT_TYPE = :PRODUCT_TYPE, 
				USER_LIMIT_AMOUNT = <#if USER_LIMIT_AMOUNT??>:USER_LIMIT_AMOUNT<#else>NULL</#if>, 
				START_DATE = <#if START_DATE?? && START_DATE != ''>:START_DATE<#else>NULL</#if>,
				END_DATE = <#if END_DATE?? && END_DATE != ''>:END_DATE<#else>NULL</#if>
			WHERE PROMOTION_ID = :PROMOTION_ID
```
更新每日日预算表
sqlId:cpcDayAmount.delDayAmoutByPromotionIDs (PROMOTION_DATE >= CURRENT DATE)
sqlId:cpcDayAmount.batchInsertDayAmout

推广计划为正在推广，推广计划有正常推广的推广单元，并且不是余额不足状态，执行冻结操作
推广计划是否点爆

``` java
 if (costOver > 0) {
    // 如果日预算耗尽，修改日预算则发送推广单元数据
    cpcFreezeRealTimeKafkaService.freezeAndSendUpdatePromotionWithAllUnit(promotionId, null);
    apscommom_cpcBase.queryPromotionByPromotionId
    apscommom_cpcDayAmount.getDefaultUserLimitAmount --默认日预算-T_APS_PROMOTION.USER_LIMIT_AMOUNT
    apscommom_cpcKafka.getAllUnitIdInPromotion
} else {
   // 如果日预算未耗尽，则只发送推广计划数据
   cpcFreezeRealTimeKafkaService.freezeAndSendUpdatePromotion(promotionId, null);
}
```
根据推广计划ID删除点爆表中的记录

注：冻结流程??
   日限额=个性化日限额？个性化日预算：默认日预算、
   
sqlId:apscommom_cpcFreeze.getPromotionUserAccount
   	<!-- 查询广告主资金账户信息 -->
	<sql id="getPromotionUserAccount">
    	<![CDATA[
    	    SELECT * FROM T_APS_ACCOUNT WHERE  USER_TYPE = '0' AND USER_ID = :userId
    	]]>
	</sql>
     paramMap.put("promotionId", promotionId);
     paramMap.put("accountId", account.getAccountId());
     paramMap.put("freezeDay", freezeDay);
sqlId: apscommom_cpcFreeze.getPromotionFreezeInfo
   	<!-- 查询指定日期的推广计划冻结数据 -->
	<sql id="getPromotionFreezeInfo">
		<![CDATA[	
			SELECT
				fu.FREEZE_UNBIND_ID "freezeUnbindId",
			    fu.LEFT_FE_AMOUNT "leftFeAmount"
			FROM
			    APSADMIN.T_APS_FREEZE_UNBIND fu
			WHERE
			    fu.TYPE = 3
			AND fu.PROMOTION_DATE = :freezeDay
			AND fu.ACCOUNT_ID = :accountId
			AND fu.PROMOTION_ID = :promotionId
		]]>
	</sql>

        
## <span id="promotionPause">计划：暂停</span>
aps/new/cpc_pause_promotion.htm?promotionId=16078106

1.根据推广计划ID查询推广计划信息
  T_APS_PROMOTION 关联 T_APS_PROMOTION_CPC 查询计划基本信息+推广计划下正常推广单元个数
  
2.满足 ==**推广状态：正在推广&& 推广计划状态:正常&& 计划下正常推广的单元数>0**== ；封装kafka消息并发送==单元==下线操作

3.更新状态 ==standardPromotion.pausePromotionNew==

``` sql
UPDATE
  T_APS_PROMOTION
SET
  PROMOTION_STATUS   = 2,--暂停
  UPDATE_DATE        = CURRENT TIMESTAMP,
  STATUS_UPDATE_TIME = CURRENT TIMESTAMP
WHERE
  PROMOTION_ID = :PROMOTION_ID
  AND
  USER_ID = :USER_ID
```
## <span id="promotionResume">计划：恢复</span>

aps/new/cpc_resume_promotion.htm?promotionId=16078106

1.根据推广计划ID查询推广计划信息
  T_APS_PROMOTION 关联 T_APS_PROMOTION_CPC 查询计划基本信息+推广计划下正常推广单元个数
  
2.满足暂停状态[==推广状态：2 暂停推广&& 推广计划状态：0余额不足暂停==]，可以执行恢复操作

3.根据计划开始、结束时间 ，判断恢复后的计划状态 [==正在推广1、等待推广3、完成推广4==]

4.批量更新计划状态
==standardPromotion.updatePromotionStatusNew==
5.处理推广计划推广状态是暂停推广或余额不足暂停的计划数据
推广计划下有正常推广的推广单元
  
 - 今天在推广计划时间段内--冻结日预算
       ==cpcFreezeRealTimeKafkaService.freezeAndSendUpdatePromotionWithAllUnit(promotionId,null);==
 - 冻结成功，修改推广计划STATUS为正常
 - 冻结失败,余额不足   // 当前计划的status状态翻成0

6.开始推广成功后，判断计划中的商品是否存在一键优选中，如果存在，则暂停一键优选中的正在推广的商品(PRODUCT_TYPE==5)

 - 6.1 查询该商户的一键优选计划 ==T_APS_PROMOTION.PRODUCT_TYPE=5==
 - 6.2 满足==推广状态：3正在推广&&推荐计划状态：1正常== 继续暂停操作
 - 6.3 根据一键优选计划的promotionId查询商品信息 ==cpcOneThrow.queryGoodsFromUnit==
``` sql
			SELECT CPC_PROMOTION_ID, GOODS_NAME , GOODS_CODE  FROM T_APS_PROMOTION_CPC 
			WHERE PROMOTION_ID=:promotionId AND ISACTIVE =1 AND STATUS=1:正在推广
```
 - 6.4 根据页面需要恢复的计划promotionIds 查询商品信息
``` sql
	SELECT C.GOODS_CODE
		FROM T_APS_PROMOTION P INNER JOIN T_APS_PROMOTION_CPC C ON P.PROMOTION_ID=C.PROMOTION_ID
		WHERE P.USER_ID=:userId 
		AND P.PRODUCT_TYPE=2--生意通
		AND P.PROMOTION_STATUS in(1,2,3)
		AND P.ISACTIVE=1
		AND P.STATUS=1
		AND P.PROMOTION_ID IN(${promotionIds})
		AND C.ISACTIVE=1 AND C.STATUS=1
```
 - 6.5 对比 6.3、6.4查询结果得到unitIds（一键优选中使用到的商品的单元CPC_PROMOTION_ID）,暂停、更新推广单元状态
        - 更新一键优选计划的更新时间，状态变更时间 ==standardPromotion.updateStatusUpdateTime==
        - 更新该计划下的推广单元状态[暂停] ==standardPromotion.pauseUnit== T_APS_PROMOTION_CPC.STATUS=0
        - Kafka 发送单元下线消息[只要一键优选计划不是余额不足暂停]
``` sql
<!-- 暂停/开始推广单元 -->
	<sql id="pauseUnit">
    	<![CDATA[
    	    UPDATE 
    	    	T_APS_PROMOTION_CPC C
    	    SET 
    	    	STATUS = :status, UPDATE_TIME = CURRENT TIMESTAMP
    	    WHERE
    	    	STATUS <> :status
    	    AND 
    	    	CPC_PROMOTION_ID IN(${unitId})
    	    AND
    	    	PROMOTION_ID = :promotionId
    	    AND (SELECT USER_ID FROM T_APS_PROMOTION P WHERE C.PROMOTION_ID = P.PROMOTION_ID) = :userId
    	]]>
	</sql>
```


cpcOneThrow.queryGoodsFromUnit
<sql id="queryGoodsFromUnit">
		<![CDATA[	
			SELECT CPC_PROMOTION_ID, GOODS_NAME , 
			GOODS_CODE
			  FROM T_APS_PROMOTION_CPC 
			WHERE PROMOTION_ID=:promotionId AND ISACTIVE =:isActive AND STATUS=:status
		]]>
	</sql>
	
//[3] query goodscode info by promotionIds
        Map<String, Object> condition = new HashMap();
        condition.put("productType", "2");
        condition.put("isActive", "1");
        condition.put("status", "1");
        condition.put("userId", userId);
        condition.put("promotionStatus", "1,2,3");
        if (StringUtils.isNotBlank(promotionIds)) {
            condition.put("promotionIds", promotionIds);
        }
apscommom_cpcBatch.queryPromotingGoods

//compare 2 and 3, if goods both in 2 and3, then, pause unit in 2

standardPromotionService.updateUnitStatus
	standardPromotion.updateStatusUpdateTime

	<sql id="updateStatusUpdateTime">
		<![CDATA[
			 UPDATE 
    	    	T_APS_PROMOTION
    	    SET 
    	    	STATUS_UPDATE_TIME= CURRENT TIMESTAMP,
    	    	UPDATE_DATE = CURRENT TIMESTAMP
    	    WHERE
    	    	PROMOTION_ID = :promotionId
    	    AND 
    	    	USER_ID = :userId
    	]]>
	</sql>
	更新单元状态
	standardPromotion.pauseUnit
    UPDATE 
    	    	T_APS_PROMOTION_CPC C
    	    SET 
    	    	STATUS = :status, UPDATE_TIME = CURRENT TIMESTAMP
    	    WHERE
    	    	STATUS <> :status
    	    AND 
    	    	CPC_PROMOTION_ID IN(${unitId})
    	    AND
    	    	PROMOTION_ID = :promotionId
    	    AND (SELECT USER_ID FROM T_APS_PROMOTION P WHERE C.PROMOTION_ID = P.PROMOTION_ID) = :userId
   	发送kafka
                        // 如果当前为暂停操作
                        if ("0".equals(status)) {
                            kafkaPromotionService.sendPauseUnitKafka(userId, companyCode, userType, unitIdBak,
                                    promotionId);
                        } else { // 如果为开始操作
                            kafkaPromotionService.sendResumeUnitKafka(userId, companyCode, userType, unitIdBak,
                                    promotionId, productType);
                        }

## <span id="promotionDetail">关联推广单元</span>
1.获取推广计划信息
sqlId:standardPromotion.getPromotionByIdAndProductType
``` sql
SELECT * FROM
			T_APS_PROMOTION P
			WHERE
			P.PROMOTION_ID = :promotionId
			AND P.PRODUCT_TYPE = :productType
			AND P.ISACTIVE = 1
```
2.获取当前推广计划的各个广告位的溢价折扣策略 ???
sqlId:apscommom_cpcBase.queryAllPositionControlInfoByRelId

3.获取推广计划报表数据(从数据平台获取数据 推广计划层次)
{endDate=2018-03-23, userId=429004445, promotionId=16078106, startDate=2018-03-23, queryType=queryByPromotionId}
mergeData(promotionKeyIds,queryTodayData(promotionKeyIds,condition,isPromotionUnit),queryHistoryData(promotionKeyIds,condition,isPromotionUnit))

4.获取推广单元
sqlId: standardPromotion.getPromotionUnitCount、standardPromotion.getPromotionUnits
{endDate=2018-03-23, keyword=, userId=429004445, promotionId=16078106, startDate=2018-03-23}
根据推广单元ID查询推广单元投放数据
``` sql
--获取推广单元{endDate=2018-03-23, rowNum=1, pageSize=10, keyword=, userId=429004445, promotionId=16078106, startDate=2018-03-23}
			SELECT 
		       	COUNT(1)
			FROM 
		       	T_APS_PROMOTION_CPC U, T_APS_PROMOTION P
			WHERE 
		        U.PROMOTION_ID = :promotionId
		    AND 
		    	P.USER_ID = :userId
		    AND P.ISACTIVE=1
		    AND U.ISACTIVE=1
			AND 
		        P.PROMOTION_ID = U.PROMOTION_ID
			<#if keyword?? && keyword != ''>
	        AND 
	        	U.GOODS_NAME LIKE '%${keyword}%' escape '!'
			</#if>
		   	WITH UR
```

```sql
    SELECT
      ROW_NUMBER()
      OVER (
        ORDER BY U.UPDATE_TIME DESC ) AS ROW_NUM,
      P.PAY_TYPE,
      U.CPC_PROMOTION_ID,
      U.STATUS,
      U.GOODS_CODE,
      U.LINK_URL,
      U.GOODS_NAME,
      U.NAME                          AS UNIT_NAME,
      S.SHOP_NAME,
      S.SHOP_URL,
      0                               AS SHOW_NUM,
      0                                  CLICK_NUM,
      0                                  DAY_COST,
      0                               AS CLICK_PERCENT,
      it.ITEM_VALUE
    FROM
      T_APS_PROMOTION_CPC U
      LEFT JOIN
      T_APS_PROMOTION_CPC_SHOP S ON U.CPC_PROMOTION_ID = S.CPC_PROMOTION_ID
      LEFT JOIN APSADMIN.T_APS_PROMOTION_CPC_ITEM it  ON it.CPC_PROMOTION_ID = U.CPC_PROMOTION_ID AND it.ITEM_CODE = '1001',
      T_APS_PROMOTION P
    WHERE
      P.PROMOTION_ID = U.PROMOTION_ID
      AND U.PROMOTION_ID = 16078106
      AND P.USER_ID = 429004445
      AND P.ISACTIVE = 1
      AND U.ISACTIVE = 1
```

5.获取最低日限额
6.获取推广计划属性
 Map<String, String> itemMap = cpcCommonService.queryAllPromotionItemMapByPromotionId(pager.getPromotionId());
 sqlId:apscommom_cpcBase.queryAllPromotionItemByPromotionId
 7.图层控制 HOT_POSITION_CTRL_VERSION










## <span id="unitPause">单元：暂停</span>
1.更新推广单元状态
	T_APS_PROMOTION_CPC.STATUS --'0 是暂停，1 是正常

2.仅推广计划状态为正在推广时，kafka发送单元下架信息

3.更新计划表变更时间
	T_APS_PROMOTION.UPDATE_TIME,STATUS_UPDATE_TIME

4.记录用户操作日志


## <span id="unitStart">单元：开始</span>
1.更新推广单元状态
	T_APS_PROMOTION_CPC.STATUS --'0 是暂停，1 是正常

2.仅推广计划状态为正在推广时，kafka发送单元下架信息

3.更新计划表变更时间
	T_APS_PROMOTION.UPDATE_TIME,STATUS_UPDATE_TIME

4.暂停一键推广中的商品
T_APS_PROMOTION_CPC.PRODUCT_TYPE=5
T_APS_PROMOTION_CPC.GOODS_CODE

5.记录用户操作日志


## <span id="unitEdit">单元：编辑</span>
加载页面数据：
1.获取推广单元信息 ==proUnit.getPromotionInfoById==

设置广告主日限额
:   特殊日预算  T_APS_PROMOTION_CUSTOM_BUDGET.USER_LIMIT_AMOUNT
:   默认日预算  T_APS_PROMOTION_CPC.USER_LIMIT_AMOUNT

2.获取商品图片
查询CPC商品图片版本信息:GoodsPicUrlRsfQueryService.querySupplierCmmdtyMessage17

> http://uimgpre.cnsuning.com/uimg/b2c/newcatentries/0070057240-000000000750049472_[1-4]_200x200.jpg

3.获取商品编码对应的三级类目==proUnit.queryGoodRelByProductCode==

``` sql
	SELECT * FROM T_APS_GOODS_PAGE_REL WHERE GOODS_CODE=:productNum/000000000750049472  {T_APS_PROMOTION_CPC.GOODS_CODE}
```
|COLUMN|DATA
|---|---
|REL_ID|1432429	
|GOODS_CODE|000000000750049472
|FIRST_PAGE_CODE|157122
|SECOND_PAGE_CODE|258003
|THIRD_PAGE_CODE|258004
|CREATE_DATE|	2017-03-30 16:16:41.304802
|UPDATE_DATE|2018-04-08 11:57:56.975470
|PARTNUMBER|000000000750049472|
4.根据三级目录获取系统关键词 
*KEYWORD_TOOLS_METHOD：关键词分析工具查询方式(1.数据平台)*
==mysql:keywordTool.queryRecommendKeywords==
==db2:proUnit.getSysRecWords==

``` sql
mysql:keywordTool.queryRecommendKeyword {thirdCode=258004, score=100, rowNum=20}

	select 
			distinct a.KEYWORD,
            ${score} SCORE,
             b.search_num as SEARCH_NUM,
            '100000001' AS POSITION_ID,
            ROUND(IFNULL(b.click_percent*100.0,0.0),2) AS PERCENT,
            round(IFNULL(b.avg_price,0)/100.0,2) AS AVGPRICE,
            round(IFNULL(b.shop_avg_price,0)/100.0,2) AS SHOP_AVG_PRICE,
            IFNULL(b.compet_num,0) AS COMPET_NUM,
            IFNULL(b.shop_compet_num,0) AS SHOP_COMPET_NUM
			from  t_aps_keyword_page_rel a,t_aps_keyword_analysis  b where  
			a.KEYWORD = b.keyword 
			<#if thirdCode?exists && thirdCode != ''>
				AND a.THIRD_PAGE_CODE = :thirdCode
			</#if> 
			<#if secondCode?exists && secondCode != ''>
				AND a.SECOND_PAGE_CODE = :secondCode
			</#if> 
			<#if keywrods?exists && keywrods != ''>
				AND a.KEYWORD NOT IN(:keywrods)
			</#if> 
			  ORDER BY b.search_num DESC 
			limit :pageNumber,:pageSize
------------------------------------------------
	WITH BASE (KEYWORD,SCORE,SEARCH_NUM,POSITION_ID,PERCENT,AVGPRICE) AS (
			        SELECT 
			                DISTINCT A.KEYWORD,
			                ${score} SCORE,
			                C.SEARCH_NUM,
			                '100000001' AS POSITION_ID,
			                decimal(ROUND(NVL(C.CLICK_PERCENT*100.0,0.0),2),10,2) AS percent,
			                decimal(round(NVL(C.AVG_PRICE,0)/100.0,2),10,2) AS avgPrice
			        FROM T_APS_KEYWORD_PAGE_REL A,T_APS_KEYWORD_TOOL_DATA_FRONT C 
			        WHERE A.KEYWORD=C.KEYWORD 
			                AND A.STATUS=1
			                <#if thirdCode?exists && thirdCode != ''>
								AND A.THIRD_PAGE_CODE = :thirdCode
							</#if> 
							<#if secondCode?exists && secondCode != ''>
								AND A.SECOND_PAGE_CODE = :secondCode
							</#if> 
							<#if keywrods?exists && keywrods != ''>
								AND A.KEYWORD NOT IN(:keywrods)
							</#if> 
			                AND EXISTS(SELECT 'X' FROM T_APS_SEARCH_KEYWORD B WHERE B.KEYWORD_NAME=A.KEYWORD)
			        ORDER BY C.SEARCH_NUM DESC
			        FETCH FIRST ${rowNum} ROWS ONLY
			)
			
			SELECT E.*,NVL(P.COMPET_NUM,0) AS COMPET_NUM
			FROM BASE E LEFT JOIN
			(SELECT 
			        D.NAME,COUNT(1) COMPET_NUM 
			        FROM T_APS_CPC_PROMOTION_DATA D
			        WHERE D.PROMOTION_TYPE=0  
			        AND D.PROMOTION_DATE= CURRENT DATE 
			        GROUP BY D.NAME
			) P
			ON E.KEYWORD = P.NAME WITH UR


```



5.根据三级目录获取系统推荐类目
*CATALOG_TOOLS_METHOD：类目分析工具查询方式(1.数据平台)*
==mysql:pcKeyword.querySysCataAnalysis==
==db2:proUnit.getParentCode
``` sql
{thirdCode=258004, saleObj=1, status=1}
	SELECT
			page_list AS "LIST_SEQ"
		    <#if thirdCode?exists && thirdCode != "">
			,(CASE WHEN page_code= :thirdCode THEN 100 ELSE 80 END ) AS "SCORE",
			</#if>
			page_list as  "KEYWORD",
			page_name AS "NAME_SEQ",
			page_code as "CODE",
			position_id as "POSITION_ID",
			ROUND(search_num <#if searchInc?exists>* :searchInc</#if>) AS "SEARCH_NUM",
			compet_num AS "COMPET_NUM",
			click_percent AS "PERCENT",
			ROUND(avg_price <#if avgPriceInc?exists>* :avgPriceInc/100,2</#if>) AS "AVGPRICE"
		FROM
			t_aps_page_analysis
	    WHERE 1=1
	         <#if saleObj?exists && saleObj != "">
	             and (SALE_OBJ=2 OR SALE_OBJ=:saleObj)
	         </#if>   
	         <#if pageCode?exists && pageCode != "">
	             and page_list LIKE ${pageCode} ESCAPE '!' 
	         </#if>
	         order by 
	         <#if thirdCode?exists && thirdCode != "">
	             SCORE desc,
	         </#if>
	         search_num desc
	         
	         
	         <sql id="getSysRecCatas">
    	<![CDATA[  	
    		SELECT A.LIST_SEQ,
			        A.SCORE,
			        A.LIST_SEQ as KEYWORD,
			        A.NAME_SEQ,
			        A.CODE_SEQ AS CODE,
			        A.POSITION_ID,
			        NVL(B.SEARCH_NUM,0) SEARCH_NUM,
			        decimal(ROUND(NVL(B.CLICK_PERCENT*100.0,0.0),2),10,2) AS percent,
			        decimal(round(NVL(B.AVG_PRICE,0)/100.0,2),10,2) AS avgPrice
			FROM 
			        (SELECT T1.LIST_SEQ,(CASE WHEN T1.CODE_SEQ=${thirdCode} THEN '100' ELSE '80' END ) SCORE,
			        		T1.NAME_SEQ,T1.CODE_SEQ,T2.POSITION_ID 
			         FROM T_APS_CPC_POSITION_REL T1,T_APS_ADS_POSITION T2 
			         WHERE T1.LIST_SEQ LIKE ${secondCode} ESCAPE '!' AND T1.POSITION_ID=T2.POSITION_ID AND T1.STATUS = 1 
			        AND T1.EFFECT_DATE <= current timestamp AND (T2.SALE_OBJ=2 OR T2.SALE_OBJ=:saleObj)) A 
			LEFT JOIN
			        (SELECT KEYWORD,SEARCH_NUM,CLICK_PERCENT,AVG_PRICE FROM T_APS_KEYWORD_TOOL_DATA_FRONT WHERE PROMOTION_TYPE=1) B
			ON A.CODE_SEQ=B.KEYWORD
			WITH UR
		]]>
	</sql>
```

6.查询今日推荐信息
IS_OPEN_FOR_ALL|| thirdCataId in THIRD_PAGE_CODE_FOR_TODAY
7. 用户日预算\创建时间 unitInfo.get()
8. 查询关键词和类目[详情数据]
``` sql
	    	SELECT
	    		 A.CPC_PROMOTION_DETAIL_ID,
	    		 A.KEYWORD,
	    		 A.USER_PRICE,
	    		 A.POSITION_ID,
	    		 A.START_DATE,
	    		 A.QUALITY,
	    		 A.STANDARD_QUALITY,
	    		 B.NAME_SEQ,
	    		 A.TYPE,
	    		 A.QUALITY*A.USER_PRICE AS TOTAL
			FROM
				T_APS_PROMOTION_CPC_DETAIL A LEFT JOIN T_APS_CPC_POSITION_REL B
			ON A.KEYWORD = B.CODE_SEQ AND A.POSITION_ID=B.POSITION_ID AND B.STATUS = 1
			WHERE
				A.TYPE IN ('0','1') AND A.CPC_PROMOTION_ID=:cpcPromotionId WITH UR
```
9.查询系统限制的三级类目==THIRD_PAGE_LIMIT==,若该商品为限制类目下面的商品，则其投放的关键词不能夸三级类目，投放类目只能是该三级类目
10.获取推广单元属性map(cpcPromotionId)==T_APS_PROMOTION_CPC_ITEM==
11.  一键抢，预估排名
@ApsScmConf("scm.cpc.isShowYJQ")
@ApsScmConf("scm.cpc.isShowMorePositionRank")

12.修改并提交
'/ajax/unit/savePromotionUnit.htm

## <span id="promotionList">商品推广&& 店铺推广列表</span>

首页：
推广基本信息+商品点击等数据(调接口)
aps-sale-web/aps/new/cpc_standard_promotion_list.htm
？productType=2 商品推广  
？productType=4 店铺推广


view：
new/cpc/cpc_standard_promotion_list.ftl

code:
``` sql
SELECT
  USER_ID,
  COMPANY_CODE,
  TYPE --'0：系统管理员 1：内部事业部账号 2：SOP合作商家主账号 3:SCS供应商账号,4:自营旗舰店账号,5虚拟币账户';
FROM T_APS_USER
WHERE USER_NAME = 'soppre0803@126.com'
```
控制是否开放店铺推广
系统参数AD_CPC_SHOP_SWITCH==1 && (TYPE==2||TYPE==23)

{endDate=2018-03-22, userId=429004445, startDate=2018-03-22, productType=2, statusCode=-2}

 // 根据计划ID查询报表历史数据
当日数据 
    提交订单不包括 成交订单    所以 ： 总订单=直接提交订单+间接提交订单+直接成交订单+间接成交订单
http://admdspre.cnsuning.com/admdso/general-intf?key=h_saleCpcRT_plan_20180322_16075927,h_saleCpcRT_plan_20180322_16078059
历史数据(startDate>CurrentDate)    
   提交订单 包括 成交订单  所以 ：总订单=直接提交订单+间接提交订单
报表平台 apsReportService    
QUERY_REALTIME_PROMOTION("cpcRealtimeReport.queryRealtimePromotionPlanData"),
QUERY_REALTIME_PROMOTION_UNIT("cpcRealtimeReport.queryRealtimePromotionUnitData");
    
public static final String  KEY_ALL_ORDER_NUM="all_order_num";//总订单数
public static final String  KEY_ALL_ORDER_AMOUNT="all_order_amount";//总订单金额

合并项： KEY_ALL_ORDER_AMOUNT,KEY_ALL_ORDER_NUM,KEY_CLICK,KEY_COST,KEY_PV

//可删除标识
 PROMOTION_STATUS==8|| CPCAMOUNT==0
 // 如果是商品推广则添加地域和时段的
 apscommom_cpcBase.queryAllPromotionItemByPromotionId
 


```sql
--'推广状态1：等待  2:暂停 3：正在 4：等待关联素材 8：完成 9：关闭     51：等待业务审核   52：等待设计创意审核 61：业务审核驳回62:设计创意审核驳回';
    select count(promotion_id) 
    	    	from t_aps_promotion p 
    	    	where pay_type = 2 
    	    	and p.isactive=1 and user_id = :userId
    	    	and p.PRODUCT_TYPE = :productType
    	    	<#if statusCode?? && statusCode != -1>
					<#if statusCode == -2>
						and p.PROMOTION_STATUS != 8
					<#elseif statusCode==1||statusCode==3 >
	                 AND p.PROMOTION_STATUS =:statusCode AND p.STATUS = 1
	                <#elseif statusCode==2> 
	                 AND (p.PROMOTION_STATUS =:statusCode OR p.STATUS = 0)
					<#else>
						and p.PROMOTION_STATUS = :statusCode
					</#if>
				</#if>
```


```sql
SELECT
  T.*,
  (
    SELECT COUNT(1)
    FROM
      T_APS_PROMOTION_CPC
    WHERE
      PROMOTION_ID = T.PROMOTION_ID
      AND ISACTIVE = 1
  )  AS CPCAMOUNT,

  (
    SELECT COUNT(1)
    FROM
      T_APS_PROMOTION_CPC
    WHERE
      PROMOTION_ID = T.PROMOTION_ID
      AND ISACTIVE = 1 AND STATUS = 1--'0 是暂停，1 是正常';
  ) AS CPC_PROMOTION_AMOUNT
FROM
  (
    SELECT
      ROW_NUMBER()
      OVER (
        ORDER BY P.UPDATE_DATE DESC ) AS ROW_NUM,
      P.PROMOTION_ID,
      P.PROMOTION_STATUS,
      P.USER_LIMIT_AMOUNT,
      P.UPDATE_DATE,
      P.STATUS,
      P.PAY_TYPE,
      P.NAME,
      O.ID                            AS "dayCost_over",
      0                               AS SHOW_NUM,
      0                               AS CLICK_NUM,
      0                               AS CLICK_PERCENT,
      0                               AS TODAY_COST,
      0                               AS DAY_COST
    FROM
      T_APS_PROMOTION P
      LEFT JOIN
      T_APS_CPC_PROMOTION_COST_OVER O
        ON P.PROMOTION_ID = O.PROMOTION_ID
           AND O.PROMOTION_DATE = CHAR(CURRENT_DATE)
    WHERE
      P.PAY_TYPE = 2  --'广告计费模式：0：CPT；1：CPM 2：CPC分类列表页 3: CPC搜索结果页';
      AND P.ISACTIVE = 1
      AND P.USER_ID = 429004445
      AND p.PRODUCT_TYPE = 2   --'产品线类型:1.聚客宝 2.生意通 3.大聚惠';
      --AND P.PROMOTION_STATUS ？
  ) T

```


----------


## <span id="promotionDetail">推广计划报表</span>
Table:
t_cpc_yxb_promotion_7day、_15day
t_cpc_promotion_hour_7day、_15day
 
1.	数据总览
    点击量 CLICK_NUM
    点击率 CLICK_NUM/SHOW_NUM
    花费 COST
    平均点击花费 COST/CLICK_NUM
    投入产出比 TOTAL_SUBMIT_AMOUNT/COST --总提交金额（单位：分）/花费
2.	时间趋势图
3.	表格:各计划数据概览+下载（底部添加合计行）
4.	详情[promotionId]
    4.1分时
    4.2分日

## <span id="promotionDetail">推广单元报表</span>


T_APS_PROMOTION_CUSTOM_BUDGET
CPC个性化日预算表（指定计划某一天的日预算）

t_aps_promotion_item
推广计划属性表[投放时段（1001）、定向地域（1002）]

T_APS_CPC_POSITION_CONTROL
CPC广告位溢价表（广告位溢价与开关）
| COLUMN  |COMMENT|
|---|---|
|ID            |      主键
|REL_ID        |      关联id（推广计划ID、推广单元ID、推广详情ID）
|REL_TYPE      |      关联id类型（1.推广计划ID，2.推广单元ID，3.推广详情ID）
|POSITION_ID   |      广告位id
|CONTROL_FLAG  |      是否投放此广告位（0.关闭、1.开启）
|DISCOUNT      |      该广告位折扣（百分数，例:90==90%）
|CREATE_DT     |     创建时间
[T_APS_CPC_POSITION_CONTROL-- cpc广告位控制表（广告位溢价与开关）]


![推广计划][2]

![计划详情--单元][3]

![新建推广单元--选择商品][4]

![新建推广单元--选择商品图片][5]

![设置投放平台](https://i.loli.net/2018/04/04/5ac49f6baf3da.jpg)

  [1]: https://i.loli.net/2018/03/26/5ab85fb16c743.jpg
  [2]: https://i.loli.net/2018/03/23/5ab4bcdb77a48.jpg
  [3]: https://i.loli.net/2018/03/23/5ab4bc4f56c1a.jpg
  [4]: https://i.loli.net/2018/03/23/5ab4e33269d89.jpg
  [5]: https://i.loli.net/2018/03/26/5ab861ce6b9dc.jpg
