---
title: データマイニングクエリのタイムアウト値を変更する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- time-out
ms.assetid: f1add4bc-e882-440a-a98b-333cfa274c3e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9dcdcdcbb6e2aef48dd8725f10f38180c73f5f6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642424"
---
# <a name="change-the-time-out-value-for-data-mining-queries"></a><span data-ttu-id="2cece-102">データ マイニング クエリのタイムアウト値の変更</span><span class="sxs-lookup"><span data-stu-id="2cece-102">Change the Time-out Value for Data Mining Queries</span></span>
  <span data-ttu-id="2cece-103">リフト チャートの作成時や、予測クエリの実行時には、予測に必要なすべてのデータの生成に時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2cece-103">When you build a lift chart or execute a prediction query, sometimes it can take a long time to generate all the data required for the prediction.</span></span> <span data-ttu-id="2cece-104">クエリがタイムアウトするのを防ぐため、クエリの完了を [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーで待機する時間を制御する値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="2cece-104">To prevent the query from timing out, you can change the value that controls how long the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server waits to complete a query.</span></span>  
  
 <span data-ttu-id="2cece-105">既定値は 15 ですが、モデルが複雑な場合やデータ ソースが大規模な場合、これでは十分でない場合があります。</span><span class="sxs-lookup"><span data-stu-id="2cece-105">The default value is 15; however, if your models are complex or the data source is large, this might not be enough.</span></span> <span data-ttu-id="2cece-106">必要に応じて値を大幅に増やし、処理に十分な時間を確保します。</span><span class="sxs-lookup"><span data-stu-id="2cece-106">If necessary, you can increase the value significantly, to enable enough time for processing.</span></span> <span data-ttu-id="2cece-107">たとえば、 **[クエリ タイムアウト]** を 600 に設定すると、クエリを 10 分間実行し続けることができます。</span><span class="sxs-lookup"><span data-stu-id="2cece-107">For example, if you set **Query Timeout** to 600, the query could continue to run for up to 10 minutes.</span></span>  
  
 <span data-ttu-id="2cece-108">予測クエリの詳細については、「 [データ マイニングのクエリ タスクと操作方法](data-mining-query-tasks-and-how-tos.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cece-108">For more information about prediction queries, see [Data Mining Query Tasks and How-tos](data-mining-query-tasks-and-how-tos.md).</span></span>  
  
### <a name="configure-the-time-out-value-for-data-mining-queries"></a><span data-ttu-id="2cece-109">データ マイニング クエリのタイムアウト値の構成</span><span class="sxs-lookup"><span data-stu-id="2cece-109">Configure the time-out value for data mining queries</span></span>  
  
1.  <span data-ttu-id="2cece-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、 **[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2cece-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], from the **Tools** menu, selection **Options**.</span></span>  
  
2.  <span data-ttu-id="2cece-111">**[オプション]** ペインで **[ビジネス インテリジェンス デザイナー]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="2cece-111">In the **Options** pane, expand **Business Intelligence Designers**.</span></span>  
  
3.  <span data-ttu-id="2cece-112">**[クエリ タイムアウト]** ボックスをクリックし、秒数の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="2cece-112">Click the **Query Timeout** text box, and type a value for the number of seconds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cece-113">参照</span><span class="sxs-lookup"><span data-stu-id="2cece-113">See Also</span></span>  
 <span data-ttu-id="2cece-114">[データマイニングのクエリタスクと操作方法](data-mining-query-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="2cece-114">[Data Mining Query Tasks and How-tos](data-mining-query-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="2cece-115">データマイニングクエリ</span><span class="sxs-lookup"><span data-stu-id="2cece-115">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
