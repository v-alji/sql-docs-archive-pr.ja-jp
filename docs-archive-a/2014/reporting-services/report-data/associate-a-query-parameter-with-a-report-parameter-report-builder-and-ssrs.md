---
title: クエリ パラメーターのレポート パラメーターへの関連付け (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- queries [Reporting Services], parameters
- parameters [Reporting Services], queries
ms.assetid: 6d297e1a-ff71-472a-addc-349e863092b5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f65aa36e8910378d68963c8c9990518b661025ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713894"
---
# <a name="associate-a-query-parameter-with-a-report-parameter-report-builder-and-ssrs"></a><span data-ttu-id="ca361-102">クエリ パラメーターのレポート パラメーターへの関連付け (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="ca361-102">Associate a Query Parameter with a Report Parameter (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ca361-103">クエリ変数を含んだデータセット クエリを定義すると、クエリ コマンドが解析されます。</span><span class="sxs-lookup"><span data-stu-id="ca361-103">When you define a dataset query that contains a query variable, the query command is parsed.</span></span> <span data-ttu-id="ca361-104">クエリ変数ごとに、対応するデータセット クエリ パラメーターおよびレポート パラメーターが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ca361-104">For each query variable, a corresponding dataset parameter and report parameter are created.</span></span> <span data-ttu-id="ca361-105">データセット パラメーターは、レポート パラメーターを参照します。</span><span class="sxs-lookup"><span data-stu-id="ca361-105">The dataset parameter points to the report parameter.</span></span> <span data-ttu-id="ca361-106">これにより、クエリに直接渡される値を入力できます。</span><span class="sxs-lookup"><span data-stu-id="ca361-106">This enables a user to enter a value that passes directly to the query.</span></span> <span data-ttu-id="ca361-107">クエリ コマンドを編集するたびに、同じ処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="ca361-107">Each time you edit the query command, the same process takes place.</span></span>  
  
 <span data-ttu-id="ca361-108">クエリ パラメーターにバインドされているレポート パラメーターの名前を変更した場合、このトピックの手順で、名前を変更したレポート パラメーターにクエリ パラメーターを手動でリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca361-108">If you rename a report parameter that is bound to a query parameter, you need to manually link the query parameters to the renamed report parameter by using the procedure in this topic.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-associate-a-query-parameter-with-a-report-parameter"></a><span data-ttu-id="ca361-109">クエリ パラメーターをレポート パラメーターに関連付けるには</span><span class="sxs-lookup"><span data-stu-id="ca361-109">To associate a query parameter with a report parameter</span></span>  
  
1.  <span data-ttu-id="ca361-110">レポート データ ペインでデータセットを右クリックし、 **[データセットのプロパティ]** をクリックして、 **[パラメーター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca361-110">In the Report Data pane, right-click the dataset, click **Dataset Properties**, and then click **Parameters**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ca361-111">レポート データ ペインが表示されていない場合は、 **[表示]** メニューの **[レポート データ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca361-111">If the Report Data pane is not visible, click **Report Data** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="ca361-112">**[パラメーター名]** 列で、クエリ パラメーターの名前を探します。</span><span class="sxs-lookup"><span data-stu-id="ca361-112">In the column **Parameter Name**, find the name of the query parameter.</span></span> <span data-ttu-id="ca361-113">パラメーター名は、クエリに基づいて自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ca361-113">Parameter names are automatically populated based on the query.</span></span> <span data-ttu-id="ca361-114">クエリを変更するたびに、新しいクエリ パラメーターがチェックされます。</span><span class="sxs-lookup"><span data-stu-id="ca361-114">Every time you change the query, the query is checked for new query parameters.</span></span> <span data-ttu-id="ca361-115">手動で作成したクエリ パラメーターは、クエリが変更されても変更されません。</span><span class="sxs-lookup"><span data-stu-id="ca361-115">Query parameters that you create manually are not changed when the query changes.</span></span>  
  
    -   <span data-ttu-id="ca361-116">**[パラメーター名]** で、クエリ内に表示された名前と同じクエリ パラメーターを探します。</span><span class="sxs-lookup"><span data-stu-id="ca361-116">In **Parameter Name**, find the query parameter name as it exists in the query.</span></span> <span data-ttu-id="ca361-117">新しいクエリ パラメーターを手動で追加して、名前を入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="ca361-117">You can also manually add a new query parameter and enter a name.</span></span>  
  
    -   <span data-ttu-id="ca361-118">**[パラメーター値]** では、クエリ パラメーターに渡す値に評価される式を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="ca361-118">In **Parameter Value**, type or select an expression that evaluates to the value to pass to the query parameter.</span></span> <span data-ttu-id="ca361-119">これは通常、レポート パラメーターの名前です。</span><span class="sxs-lookup"><span data-stu-id="ca361-119">This is typically the name of the report parameter.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="ca361-120">クエリ パラメーターの値には、レポート パラメーター以外も指定できます。</span><span class="sxs-lookup"><span data-stu-id="ca361-120">You are not limited to report parameters as values for a query parameter.</span></span> <span data-ttu-id="ca361-121">このパラメーター値に対応する値に評価される式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ca361-121">You can use any expression that evaluates to a value for the parameter value.</span></span>  
  
3.  <span data-ttu-id="ca361-122">クエリ パラメーターを追加する場合は、手順 2. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="ca361-122">Repeat step 2 for additional query parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca361-123">参照</span><span class="sxs-lookup"><span data-stu-id="ca361-123">See Also</span></span>  
 <span data-ttu-id="ca361-124">[レポート埋め込みデータセットと共有データセット &#40;レポートビルダーと SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ca361-124">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ca361-125">レポートパラメーターの概念 &#40;レポートビルダーと SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ca361-125">Report Parameters Concept &#40;Report Builder and SSRS&#41;</span></span>](../report-design/report-parameters-concepts-report-builder-and-ssrs.md)  
  
  
