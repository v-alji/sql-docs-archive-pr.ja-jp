---
title: Excel の行制限を回避する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a4c8700b-bef5-4440-a99c-bba5dcc46bfd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 128f65cf09833d23234da10bf7744c6ce30065ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633770"
---
# <a name="work-around-the-excel-row-limitation"></a><span data-ttu-id="59649-102">Excel の行制限を回避する</span><span class="sxs-lookup"><span data-stu-id="59649-102">Work Around the Excel Row Limitation</span></span>
  <span data-ttu-id="59649-103">このトピックでは、Excel にレポートをエクスポートときに Excel 2003 の行制限を回避する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="59649-103">This topic explains how to work around the Excel 2003 row limitation when you export reports to Excel.</span></span> <span data-ttu-id="59649-104">回避策は、テーブルのみを含むレポート向けのものです。</span><span class="sxs-lookup"><span data-stu-id="59649-104">The workaround is for a report that contains only a table.</span></span>  
  
 <span data-ttu-id="59649-105">Excel 2003 でサポートされる行数は、ワークシートあたり最大 65,536 行です。</span><span class="sxs-lookup"><span data-stu-id="59649-105">Excel 2003 supports a maximum of 65,536 rows per worksheet.</span></span> <span data-ttu-id="59649-106">この制限を回避するには、特定の行数の後に明示的な改ページを適用します。</span><span class="sxs-lookup"><span data-stu-id="59649-106">You can work around this limitation by forcing an explicit page break after a certain number of rows.</span></span> <span data-ttu-id="59649-107">Excel レンダラーでは、それぞれの明示的な改ページごとに、新しいワークシートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="59649-107">The Excel renderer creates a new worksheet for each explicit page break.</span></span>  
  
### <a name="to-create-an-explicit-page-break"></a><span data-ttu-id="59649-108">明示的な改ページを作成するには</span><span class="sxs-lookup"><span data-stu-id="59649-108">To create an explicit page break</span></span>  
  
1.  <span data-ttu-id="59649-109">[!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)] またはレポート マネージャーでレポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="59649-109">Open the report in [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)] or Report Manager.</span></span>  
  
2.  <span data-ttu-id="59649-110">テーブル内のデータ行を右クリックし、[**グループ**の親グループの追加] をクリックして、外側の  >  **Parent Group**テーブルグループを追加します。</span><span class="sxs-lookup"><span data-stu-id="59649-110">Right click the Data row in the table, and then click **Add Group** > **Parent Group** to add an outer table group.</span></span>  
  
     <span data-ttu-id="59649-111">![親グループの選択](../media/datarow-selectparentgroup.png "親グループの選択")</span><span class="sxs-lookup"><span data-stu-id="59649-111">![Select the Parent Group](../media/datarow-selectparentgroup.png "Select the Parent Group")</span></span>  
  
3.  <span data-ttu-id="59649-112">次の式を **[グループ化]** の式ボックスに入力し、 **[OK]** をクリックして、親グループを追加します。</span><span class="sxs-lookup"><span data-stu-id="59649-112">Enter the following formula in the **Group by** expression box, and then click **OK** to add the parent group.</span></span>  
  
     <span data-ttu-id="59649-113">=Int((RowNumber(Nothing)-1)/65000)</span><span class="sxs-lookup"><span data-stu-id="59649-113">=Int((RowNumber(Nothing)-1)/65000)</span></span>  
  
     <span data-ttu-id="59649-114">この式によって、データセット内の 65,000 行ごとに数値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="59649-114">The formula assigns a number to each set of 65000 rows in the dataset.</span></span> <span data-ttu-id="59649-115">グループに改ページが定義されている場合は、この式の結果として、65,000 行ごとに改ページが行われます。</span><span class="sxs-lookup"><span data-stu-id="59649-115">When a page break is defined for the group, the expression results in a page break every 65000 rows.</span></span>  
  
     <span data-ttu-id="59649-116">外部テーブルのグループを追加すると、レポートにグループ列が追加されます。</span><span class="sxs-lookup"><span data-stu-id="59649-116">Adding the outer table group adds a group column to the report.</span></span>  
  
4.  <span data-ttu-id="59649-117">グループ列を削除するには、列ヘッダーを右クリックし、 **[列の削除]** をクリックして、 **[列のみの削除]** を選択します。その後で、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59649-117">Delete the group column by right-clicking on the column header, clicking **Delete Columns**, selecting **Delete columns only**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="59649-118">![グループ列の削除](../media/groupcolumn-delete-updated.png "グループ列の削除")</span><span class="sxs-lookup"><span data-stu-id="59649-118">![Delete a group column](../media/groupcolumn-delete-updated.png "Delete a group column")</span></span>  
  
5.  <span data-ttu-id="59649-119">**[行グループ]** の **[グループ 1]** を右クリックし、 **[グループ プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59649-119">Right click **Group 1** in the **Row Groups** section, and then click **Group Properties**.</span></span>  
  
     <span data-ttu-id="59649-120">![グループのプロパティの表示](../media/groupproperties-updated.png "グループのプロパティの表示")</span><span class="sxs-lookup"><span data-stu-id="59649-120">![View group properties](../media/groupproperties-updated.png "View group properties")</span></span>  
  
6.  <span data-ttu-id="59649-121">**[グループ プロパティ]** ダイアログ ボックスの **[並べ替え]** ページで、既定の並べ替えオプションを選択し、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59649-121">On the **Sorting** page of the **Group Properties** dialog box, select the default sorting option and click **Delete**.</span></span>  
  
     <span data-ttu-id="59649-122">![既定の並べ替えの削除](../media/groupproperties-sorting-updated.png "既定の並べ替えの削除")</span><span class="sxs-lookup"><span data-stu-id="59649-122">![Delete default sorting](../media/groupproperties-sorting-updated.png "Delete default sorting")</span></span>  
  
7.  <span data-ttu-id="59649-123">**[改ページ]** ページで、 **[グループの各インスタンスの間]** をクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59649-123">On the **Page Breaks** page, click **Between each instance of a group** and then click **OK**.</span></span>  
  
     <span data-ttu-id="59649-124">![改ページの設定](../media/groupproperties-pagebreaks-updated.png "改ページの設定")</span><span class="sxs-lookup"><span data-stu-id="59649-124">![Set page breaks](../media/groupproperties-pagebreaks-updated.png "Set page breaks")</span></span>  
  
8.  <span data-ttu-id="59649-125">レポートを保存します。</span><span class="sxs-lookup"><span data-stu-id="59649-125">Save the report.</span></span> <span data-ttu-id="59649-126">Excel にレポートをエクスポートするとき、複数のワークシートへのエクスポートが行われ、各ワークシートには最大で 65,000 行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="59649-126">When you export it to Excel, it exports to multiple worksheets and each worksheet contains a maximum of 65000 rows.</span></span>  
  
  
