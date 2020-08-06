---
title: XML 形式での実行プランの保存 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- XML query plans [SQL Server]
- opening execution plans
- XML Showplans [SQL Server]
- execution plans [SQL Server], saving
- saving execution plans
ms.assetid: c439e53b-56f3-4442-97c6-dabd48a203d8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 84ed341d186993ed77260e8361156b324c597839
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642740"
---
# <a name="save-an-execution-plan-in-xml-format"></a><span data-ttu-id="f925a-102">XML 形式での実行プランの保存</span><span class="sxs-lookup"><span data-stu-id="f925a-102">Save an Execution Plan in XML Format</span></span>
  <span data-ttu-id="f925a-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用すると、実行プランを XML ファイルとして保存し、開いて参照することができます。</span><span class="sxs-lookup"><span data-stu-id="f925a-103">Use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to save execution plans as an XML file, and to open them for viewing.</span></span>  
  
 <span data-ttu-id="f925a-104">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]の実行プラン機能または XML プラン表示 SET オプションを使用するには、実行プランを生成する [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリを実行するための適切な権限と、クエリが参照するすべてのデータベースに対する SHOWPLAN 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="f925a-104">To use the execution plan feature in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], or to use the XML Showplan SET options, users must have the appropriate permissions to execute the [!INCLUDE[tsql](../../includes/tsql-md.md)] query for which an execution plan is being generated, and they must be granted the SHOWPLAN permission for all databases referenced by the query.</span></span>  
  
### <a name="to-save-a-query-plan-by-using-the-xml-showplan-set-options"></a><span data-ttu-id="f925a-105">XML 表示プラン SET オプションを使用してクエリ プランを表示するには</span><span class="sxs-lookup"><span data-stu-id="f925a-105">To save a query plan by using the XML Showplan SET options</span></span>  
  
1.  <span data-ttu-id="f925a-106">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でクエリ エディターを開き、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="f925a-106">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] open a query editor and connect to [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f925a-107">次のステートメントを使用して、SHOWPLAN_XML を有効にします。</span><span class="sxs-lookup"><span data-stu-id="f925a-107">Turn SHOWPLAN_XML on with the following statement:</span></span>  
  
    ```  
    SET SHOWPLAN_XML ON;  
    GO  
    ```  
  
     <span data-ttu-id="f925a-108">次のステートメントを使用して、STATISTICS XML を有効にします。</span><span class="sxs-lookup"><span data-stu-id="f925a-108">To turn STATISTICS XML on, use the following statement:</span></span>  
  
    ```  
    SET STATISTICS XML ON;  
    GO  
    ```  
  
     <span data-ttu-id="f925a-109">SHOWPLAN_XML は、クエリのコンパイル時クエリ実行プラン情報を生成しますが、クエリの実行は行いません。</span><span class="sxs-lookup"><span data-stu-id="f925a-109">SHOWPLAN_XML generates compile-time query execution plan information for a query, but does not execute the query.</span></span> <span data-ttu-id="f925a-110">STATISTICS XML は、クエリの実行時クエリ実行プラン情報を生成し、クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="f925a-110">STATISTICS XML generates run-time query execution plan information for a query, and executes the query.</span></span>  
  
3.  <span data-ttu-id="f925a-111">クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="f925a-111">Execute a query.</span></span> <span data-ttu-id="f925a-112">例:</span><span class="sxs-lookup"><span data-stu-id="f925a-112">Example:</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SET SHOWPLAN_XML ON;  
    GO  
    -- Execute a query.  
    SELECT BusinessEntityID   
    FROM HumanResources.Employee  
    WHERE NationalIDNumber = '509647174';  
    GO  
    SET SHOWPLAN_XML OFF;  
    ```  
  
4.  <span data-ttu-id="f925a-113">**[結果]** ペインで、クエリ プランを含む **[Microsoft SQL Server XML Showplan]** を右クリックし、 **[結果に名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f925a-113">In the **Results** pane, right-click the **Microsoft SQL Server XML Showplan** that contains the query plan, and then click **Save Results As**.</span></span>  
  
5.  <span data-ttu-id="f925a-114">**[** \<Grid or Text> **の結果を保存]** ダイアログ ボックスで、 **[保存の種類]** ボックスの **[すべてのファイル (\*.\*)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f925a-114">In the **Save** \<Grid or Text> **Results** dialog box, in the **Save as type** box, click **All files (\*.\*)**.</span></span>  
  
6.  <span data-ttu-id="f925a-115">**[ファイル名]** ボックスに \<name**>.sqlplan の形式で名前を入力し、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f925a-115">In the **File name** box provide a name, in the format \<name**>.sqlplan\*\*, and then click **Save**.</span></span>  
  
### <a name="to-save-an-execution-plan-by-using-sql-server-management-studio-options"></a><span data-ttu-id="f925a-116">SQL Server Management Studio のオプションを使用して実行プランを保存するには</span><span class="sxs-lookup"><span data-stu-id="f925a-116">To save an execution plan by using SQL Server Management Studio options</span></span>  
  
1.  <span data-ttu-id="f925a-117">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で、推定実行プランまたは実際の実行プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="f925a-117">Generate either an estimated execution plan or an actual execution plan by using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="f925a-118">詳細については、「 [推定実行プランの表示](display-the-estimated-execution-plan.md) 」または「 [実際の実行プランの表示](display-an-actual-execution-plan.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f925a-118">For more information, see [Display the Estimated Execution Plan](display-the-estimated-execution-plan.md) or [Display an Actual Execution Plan](display-an-actual-execution-plan.md).</span></span>  
  
2.  <span data-ttu-id="f925a-119">結果ペインの **[実行プラン]** タブで、グラフィカルな実行プランを右クリックし、 **[実行プランに名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f925a-119">In the **Execution plan** tab of the results pane, right-click the graphical execution plan, and choose **Save Execution Plan As**.</span></span>  
  
     <span data-ttu-id="f925a-120">代わりに、 **[ファイル]** メニューの **[実行プランに名前を付けて保存]** をクリックしてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="f925a-120">As an alternative, you can also choose **Save Execution Plan As** on the **File** menu.</span></span>  
  
3.  <span data-ttu-id="f925a-121">**[名前を付けて保存]** ダイアログ ボックスで、 **[ファイルの種類]** が **[実行プラン ファイル (\*.sqlplan)]** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f925a-121">In the **Save As** dialog box, make sure that the **Save as type** is set to **Execution Plan Files (\*.sqlplan)**.</span></span>  
  
4.  <span data-ttu-id="f925a-122">**[ファイル名]** ボックスに \<name**>.sqlplan の形式で名前を入力し、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f925a-122">In the **File name** box provide a name, in the format \<name**>.sqlplan\*\*, and then click **Save**.</span></span>  
  
### <a name="to-open-a-saved-xml-query-plan-in-sql-server-management-studio"></a><span data-ttu-id="f925a-123">保存した XML クエリ プランを SQL Server Management Studio で開くには</span><span class="sxs-lookup"><span data-stu-id="f925a-123">To open a saved XML query plan in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="f925a-124">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で **[ファイル]** メニューの **[開く]** をポイントし、 **[ファイル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f925a-124">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **File** menu, choose **Open**, and then click **File**.</span></span>  
  
2.  <span data-ttu-id="f925a-125">**[ファイルを開く]** ダイアログ ボックスで **[ファイルの種類]** を **[実行プラン ファイル (\*.sqlplan)]** に設定し、保存済みの XML クエリ プラン ファイルだけを表示します。</span><span class="sxs-lookup"><span data-stu-id="f925a-125">In the **Open File** dialog box, set **Files of type** to **Execution Plan Files (\*.sqlplan)** to produce a filtered list of saved XML query plan files.</span></span>  
  
3.  <span data-ttu-id="f925a-126">表示する XML クエリ プラン ファイルを選択し、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f925a-126">Select the XML query plan file that you want to view, and click **Open**.</span></span>  
  
     <span data-ttu-id="f925a-127">代わりに、Windows エクスプローラーで、拡張子が **.sqlplan**のファイルをダブルクリックしてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="f925a-127">As an alternative, in Windows Explorer, double-click a file with extension **.sqlplan**.</span></span> <span data-ttu-id="f925a-128">プランが、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で開かれます。</span><span class="sxs-lookup"><span data-stu-id="f925a-128">The plan opens in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f925a-129">参照</span><span class="sxs-lookup"><span data-stu-id="f925a-129">See Also</span></span>  
 <span data-ttu-id="f925a-130">[SET SHOWPLAN_XML &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-showplan-xml-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f925a-130">[SET SHOWPLAN_XML &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-showplan-xml-transact-sql) </span></span>  
 [<span data-ttu-id="f925a-131">SET STATISTICS XML &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f925a-131">SET STATISTICS XML &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-statistics-xml-transact-sql)  
  
  
