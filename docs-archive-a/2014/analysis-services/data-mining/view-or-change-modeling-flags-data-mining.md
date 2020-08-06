---
title: モデリングフラグの表示または変更 (データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d1169735-fb18-417b-b8d6-9a161e444020
author: minewiskan
ms.author: owend
ms.openlocfilehash: bf0edd827321685a2d6a9041759328a7ac6e7cbd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717024"
---
# <a name="view-or-change-modeling-flags-data-mining"></a><span data-ttu-id="dce86-102">モデリング フラグの表示または変更 (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="dce86-102">View or Change Modeling Flags (Data Mining)</span></span>
  <span data-ttu-id="dce86-103">モデリング フラグは、マイニング構造列またはマイニング モデル列に設定して、分析時にアルゴリズムがデータを処理する方法を制御するためのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="dce86-103">Modeling flags are properties that you set on a mining structure column or mining model columns to control how the algorithm processes the data during analysis.</span></span>  
  
 <span data-ttu-id="dce86-104">データ マイニング デザイナーでは、マイニング構造やマイニング列に関連付けられているモデリング フラグを、その構造またはモデルのプロパティを表示することによって表示および変更することができます。</span><span class="sxs-lookup"><span data-stu-id="dce86-104">In Data Mining Designer, you can view and modify the modeling flags associated with a mining structure or mining column by viewing the properties of the structure or model.</span></span> <span data-ttu-id="dce86-105">DMX、AMO、または XMLA を使用してモデリング フラグを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="dce86-105">You can also set modeling flags by using DMX, AMO, or XMLA.</span></span>  
  
 <span data-ttu-id="dce86-106">この手順では、デザイナーでモデリング フラグを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dce86-106">This procedure describes how to change the modeling flags in the designer.</span></span>  
  
### <a name="view-or-change-the-modeling-flag-for-a-structure-column-or-model-column"></a><span data-ttu-id="dce86-107">構造列またはモデル列のモデリング フラグの表示または変更</span><span class="sxs-lookup"><span data-stu-id="dce86-107">View or change the modeling flag for a structure column or model column</span></span>  
  
1.  <span data-ttu-id="dce86-108">SQL Server Design Studio で、ソリューション エクスプローラーを開き、マイニング構造をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="dce86-108">In SQL Server Design Studio, open Solution Explorer, and then double-click the mining structure.</span></span>  
  
2.  <span data-ttu-id="dce86-109">NOT NULL モデリングフラグを設定するには、[**マイニング構造**] タブをクリックします。リグレッサーフラグまたは MODEL_EXISTENCE_ONLY フラグを設定するには、[**マイニングモデル**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="dce86-109">To set the NOT NULL modeling flag, click the **Mining Structure** tab. To set the REGRESSOR or MODEL_EXISTENCE_ONLY flags, click the **Mining Model** tab.</span></span>  
  
3.  <span data-ttu-id="dce86-110">表示または変更する列を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dce86-110">Right-click the column you want to view or change, and select **Properties**.</span></span>  
  
4.  <span data-ttu-id="dce86-111">新しいモデリング フラグを追加するには、 **[ModelingFlags]** プロパティの横にあるテキスト ボックスをクリックし、使用するモデリング フラグのチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="dce86-111">To add a new modeling flag, click the text box next to the **ModelingFlags** property, and select the check box or check boxes for the modeling flags you want to use.</span></span>  
  
     <span data-ttu-id="dce86-112">その列のデータ型に合ったモデリング フラグのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dce86-112">Modeling flags are displayed only if they are appropriate for the column data type.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dce86-113">モデリング フラグを変更した後、モデルを再処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dce86-113">After you change a modeling flag, you must reprocess the model.</span></span>  
  
### <a name="get-the-modeling-flags-used-in-the-model"></a><span data-ttu-id="dce86-114">モデルで使用されているモデリング フラグの取得</span><span class="sxs-lookup"><span data-stu-id="dce86-114">Get the modeling flags used in the model</span></span>  
  
-   <span data-ttu-id="dce86-115">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、DMX クエリ ウィンドウを開き、次のようなクエリを入力します。</span><span class="sxs-lookup"><span data-stu-id="dce86-115">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open a DMX Query window, and type a query like the following:</span></span>  
  
    ```  
    SELECT COLUMN_NAME, CONTENT_TYPE, MODELING_FLAG  
    FROM $system.DMSCHEMA_MINING_COLUMNS  
    WHERE MODEL_NAME = 'Forecasting'  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="dce86-116">参照</span><span class="sxs-lookup"><span data-stu-id="dce86-116">See Also</span></span>  
 <span data-ttu-id="dce86-117">[マイニングモデルタスクと操作方法](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="dce86-117">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="dce86-118">モデリング フラグ (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="dce86-118">Modeling Flags &#40;Data Mining&#41;</span></span>](modeling-flags-data-mining.md)  
  
  
