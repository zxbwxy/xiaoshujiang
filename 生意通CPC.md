---
title: 生意通CPC
tags: 新建,模板,小书匠
grammar_cjkRuby: true
---

[toc]


![推广计划][2]

![计划详情--单元][3]

# 流程
## 1.新建推广计划

| Index  |  Desc    |
| ---    | ---   |
|   URL  |  aps/new/cpc_new_promotion_by_name.htm <br>{	name，dept，startDate}| 
|   VIEW |  new\cpc\cpc_standard_promotion_list.ftl  |
|   CODE |   [新建计划](#newPromotion)   |
## 2.计划关联推广单元
| Index  |  Desc    |
| ---    | ---   |
|   URL  |  /aps-sale-web/aps/new/cpc_promotion_detail.htm?</br>startDate=2018-03-23&endDate=2018-03-23&promotionId=16078106| 
|   VIEW |  new/cpc/cpc_promotion_detail.ftl --productType=2(生意通)</br>new/cpc_shop/cpc_promotion_shop_detail.ftl--productType=4(CPC店铺推广)|
|   CODE |   [关联推广单元](#promotionDetail)   |

## 3.开始推广计划



## 4.暂停推广计划
| Index  |  Desc    |
| ---    | ---  |
|   URL  |  /aps/new/cpc_pause_promotion.htm <br>{promotionId }| 
|   VIEW |  new\cpc\cpc_standard_promotion_list.ftl  |
|   CODE |   [暂停推广计划](#pausePromotion)   |

----------

# 备忘
## <span id="newPromotion">新建推广计划</span>

最低价：系统参数KEYWORD_DAY_LOWER_PRICE
USER_TYPE==1 设置事业部编码 默认0
开始时间不能小于今天
该名称推广计划是否存在

``` sql
   SELECT COUNT(1) 
    		FROM T_APS_PROMOTION 	WHERE NAME = :creatPromotionName AND USER_ID = :userId AND PAY_TYPE = 2 AND ISACTIVE=1 AND PROMOTION_ID != :promotionId
```


根据开始时间判断推广计划的状态
\>today  1:等待推广
=today  3:正在推广

序列：SEQ_T_APS_PROMOTION
sqlId: standardPromotion.createPromotion   **T_APS_PROMOTION**

记录用户操作日志



---------
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













## <span id="productPromotion">商品推广&& 店铺推广列表</span>

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



  [2]: https://i.loli.net/2018/03/23/5ab4bcdb77a48.jpg
  [3]: https://i.loli.net/2018/03/23/5ab4bc4f56c1a.jpg