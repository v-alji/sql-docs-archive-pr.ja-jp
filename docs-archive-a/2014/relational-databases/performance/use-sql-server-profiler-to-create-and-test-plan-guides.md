---
title: SQL Server Profiler を使用したプラン ガイドの作成とテスト | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- checking plan guides
- plan guides [SQL Server], testing
- plan guides [SQL Server], SQL Server Profiler
- matching queries to plan guides [SQL Server]
- testing plan guides
- SQL Server Profiler, plan guides
- plan guides [SQL Server], creating
- capturing query text [SQL Server]
- verifying plan guides
- Profiler [SQL Server Profiler], plan guides
- query-to-plan guide matching [SQL Server]
ms.assetid: 7018dbf0-1a1a-411a-88af-327bedf9cfbd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 543905343d74c9fbabe5f671d9021657ea5f76b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716273"
---
# <a name="use-sql-server-profiler-to-create-and-test-plan-guides"></a><span data-ttu-id="af297-102">SQL Server Profiler を使用したプラン ガイドの作成とテスト</span><span class="sxs-lookup"><span data-stu-id="af297-102">Use SQL Server Profiler to Create and Test Plan Guides</span></span>
  <span data-ttu-id="af297-103">プラン ガイドを作成するとき、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] sp_create_plan_guide *ストアド プロシージャの* statement_text **引数に使用するために、** を使用して正確なクエリ テキストをキャプチャできます。</span><span class="sxs-lookup"><span data-stu-id="af297-103">When you are creating a plan guide, you can use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to capture the exact query text for use in the *statement_text* argument of the **sp_create_plan_guide** stored procedure.</span></span> <span data-ttu-id="af297-104">これにより、コンパイル時にプラン ガイドをクエリに一致させることができます。</span><span class="sxs-lookup"><span data-stu-id="af297-104">This helps make sure that the plan guide will be matched to the query at compile time.</span></span> <span data-ttu-id="af297-105">プラン ガイドを作成した後、プラン ガイドが実際にクエリに一致することをテストするためにも [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用できます。</span><span class="sxs-lookup"><span data-stu-id="af297-105">After the plan guide is created, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] can also be used to test that the plan guide is, in fact, being matched to the query.</span></span> <span data-ttu-id="af297-106">通常、クエリがプラン ガイドに一致することを確認するには、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用してプラン ガイドをテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="af297-106">Generally, you should test plan guides by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to verify that your query is being matched to your plan guide.</span></span>  
  
## <a name="capturing-query-text-by-using-sql-server-profiler"></a><span data-ttu-id="af297-107">SQL Server Profiler を使用したクエリ テキストのキャプチャ</span><span class="sxs-lookup"><span data-stu-id="af297-107">Capturing Query Text by Using SQL Server Profiler</span></span>  
 <span data-ttu-id="af297-108">クエリを実行し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]に送信されたテキストを正確にキャプチャすると、そのクエリ テキストに正確に一致する SQL 型または TEMPLATE 型のプラン ガイドを作成できます。</span><span class="sxs-lookup"><span data-stu-id="af297-108">If you run a query and capture the text exactly as it was submitted to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can create a plan guide of type SQL or TEMPLATE that will match the query text exactly.</span></span> <span data-ttu-id="af297-109">これにより、このプラン ガイドをクエリ オプティマイザーに使用させることができます。</span><span class="sxs-lookup"><span data-stu-id="af297-109">This makes sure that the plan guide is used by the query optimizer.</span></span>  
  
 <span data-ttu-id="af297-110">スタンドアロン バッチとしてアプリケーションから送信される次のクエリについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="af297-110">Consider the following query that is submitted by an application as a stand-alone batch:</span></span>  
  
```  
SELECT COUNT(*) AS c  
FROM Sales.SalesOrderHeader AS h  
INNER JOIN Sales.SalesOrderDetail AS d  
  ON h.SalesOrderID = d.SalesOrderID  
WHERE h.OrderDate BETWEEN '20000101' and '20050101';  
```  
  
 <span data-ttu-id="af297-111">マージ結合操作を使用してこのクエリを実行する必要がありますが、クエリでマージ結合を使用しないことを SHOWPLAN が示しているとします。</span><span class="sxs-lookup"><span data-stu-id="af297-111">Suppose you want this query to execute using a merge join operation, but SHOWPLAN indicates that the query is not using a merge join.</span></span> <span data-ttu-id="af297-112">アプリケーションでクエリを直接変更することはできませんが、代わりにプラン ガイドを作成して、コンパイル時に MERGE JOIN クエリ ヒントがクエリに追加されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="af297-112">You cannot change the query directly in the application, so instead you create a plan guide to specify that the MERGE JOIN query hint be appended to the query at compile time.</span></span>  
  
 <span data-ttu-id="af297-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が受信したクエリのテキストを正確にキャプチャするには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="af297-113">To capture the text of the query exactly as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] receives it, follow these steps:</span></span>  
  
1.  <span data-ttu-id="af297-114">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] トレースを開始し、イベントの種類として **SQL:BatchStarting** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="af297-114">Start a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] trace, making sure that the **SQL:BatchStarting** event type is selected.</span></span>  
  
2.  <span data-ttu-id="af297-115">アプリケーションでクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="af297-115">Have the application run the query.</span></span>  
  
3.  <span data-ttu-id="af297-116">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] トレースを一時停止します。</span><span class="sxs-lookup"><span data-stu-id="af297-116">Pause the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] Trace.</span></span>  
  
4.  <span data-ttu-id="af297-117">クエリに対応する **SQL:BatchStarting** イベントをクリックします。</span><span class="sxs-lookup"><span data-stu-id="af297-117">Click the **SQL:BatchStarting** event that corresponds to the query.</span></span>  
  
5.  <span data-ttu-id="af297-118">イベントを右クリックして **[イベント データの抽出]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="af297-118">Right-click and select **Extract Event Data**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="af297-119">SQL Server Profiler のトレース ウィンドウ内の下のペインで、バッチ テキストを選択してコピーすることは避けてください。</span><span class="sxs-lookup"><span data-stu-id="af297-119">Do not try to copy the batch text by selecting it from the lower pane of the Profiler trace window.</span></span> <span data-ttu-id="af297-120">作成するプラン ガイドが元のバッチと一致しなくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="af297-120">This might cause the plan guide that you create to not match the original batch.</span></span>  
  
6.  <span data-ttu-id="af297-121">ファイルにイベント データを保存します。</span><span class="sxs-lookup"><span data-stu-id="af297-121">Save the event data to a file.</span></span> <span data-ttu-id="af297-122">バッチ テキストが保存されます。</span><span class="sxs-lookup"><span data-stu-id="af297-122">This is the batch text.</span></span>  
  
7.  <span data-ttu-id="af297-123">メモ帳でバッチ テキスト ファイルを開き、テキストをクリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="af297-123">Open the batch text file in Notepad and copy the text to the copy and paste buffer.</span></span>  
  
8.  <span data-ttu-id="af297-124">プラン ガイドを作成し、**@stmt**引数に指定する引用符 ( **@stmt** ') 内にコピーしたテキストを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="af297-124">Create the plan guide and paste the copied text inside the quotation marks (**''**) specified for the **@stmt** argument.</span></span> <span data-ttu-id="af297-125">引数内の単一引用符をエスケープするには、その **@stmt** 前に別の単一引用符を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af297-125">You must escape any single quotation marks in the **@stmt** argument by preceding them with another single quotation mark.</span></span> <span data-ttu-id="af297-126">単一引用符を挿入する際は、別の文字を追加したり削除したりしないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="af297-126">Be careful not to add or remove any other characters when you insert these single quotation marks.</span></span> <span data-ttu-id="af297-127">たとえば、日付リテラル **'** 20000101 **'** は、 **''** 20000101 **''** として区切る必要があります。</span><span class="sxs-lookup"><span data-stu-id="af297-127">For example, the date literal **'** 20000101 **'** must be delimited as **''** 20000101 **''**.</span></span>  
  
 <span data-ttu-id="af297-128">次に、このプラン ガイドを示します。</span><span class="sxs-lookup"><span data-stu-id="af297-128">Here is the plan guide:</span></span>  
  
```  
EXEC sp_create_plan_guide   
    @name = N'MyGuide1',  
    @stmt = N'<paste the text copied from the batch text file here>',  
    @type = N'SQL',  
    @module_or_batch = NULL,  
    @params = NULL,  
    @hints = N'OPTION (MERGE JOIN)';  
```  
  
## <a name="testing-plan-guides-by-using-sql-server-profiler"></a><span data-ttu-id="af297-129">SQL Server Profiler を使用したプラン ガイドのテスト</span><span class="sxs-lookup"><span data-stu-id="af297-129">Testing Plan Guides by Using SQL Server Profiler</span></span>  
 <span data-ttu-id="af297-130">プラン ガイドがクエリに一致することを確認するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="af297-130">To verify that a plan guide is being matched to a query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="af297-131">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] トレースを開始し、イベントの種類として **Showplan XML** が選択されていることを確認します ( **[Performance]** ノードの下にあります)。</span><span class="sxs-lookup"><span data-stu-id="af297-131">Start a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] trace, making certain that the **Showplan XML** event type is selected (located under the **Performance** node).</span></span>  
  
2.  <span data-ttu-id="af297-132">アプリケーションでクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="af297-132">Have the application run the query.</span></span>  
  
3.  <span data-ttu-id="af297-133">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] トレースを一時停止します。</span><span class="sxs-lookup"><span data-stu-id="af297-133">Pause the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] Trace.</span></span>  
  
4.  <span data-ttu-id="af297-134">影響するクエリの **Showplan XML** イベントを検索します。</span><span class="sxs-lookup"><span data-stu-id="af297-134">Find the **Showplan XML** event for the affected query.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="af297-135">**Showplan XML for Query Compile** イベントは使用できません。</span><span class="sxs-lookup"><span data-stu-id="af297-135">The **Showplan XML for Query Compile** event cannot be used.</span></span> <span data-ttu-id="af297-136">**PlanGuideDB** はそのイベントに存在しません。</span><span class="sxs-lookup"><span data-stu-id="af297-136">**PlanGuideDB** does not exist in that event.</span></span>  
  
5.  <span data-ttu-id="af297-137">プラン ガイドが OBJECT 型または SQL 型の場合は、 **Showplan XML** イベントに、クエリと一致させるプラン ガイドの **PlanGuideDB** 属性と **PlanGuideName** 属性が含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="af297-137">If the plan guide is of type OBJECT or SQL, verify that the **Showplan XML** event contains the **PlanGuideDB** and **PlanGuideName** attributes for the plan guide that you expected to match the query.</span></span> <span data-ttu-id="af297-138">または、TEMPLATE プラン ガイドの場合は、 **Showplan XML** イベントに、クエリと一致させるプラン ガイドの **TemplatePlanGuideDB** 属性と **TemplatePlanGuideName** 属性が含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="af297-138">Or, in the case of a TEMPLATE plan guide, verify that the **Showplan XML** event contains the **TemplatePlanGuideDB** and **TemplatePlanGuideName** attributes for the expected plan guide.</span></span> <span data-ttu-id="af297-139">これにより、プラン ガイドが機能していることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="af297-139">This verifies that the plan guide is working.</span></span> <span data-ttu-id="af297-140">これらの属性は、プランの **\<StmtSimple>** 要素に含まれます。</span><span class="sxs-lookup"><span data-stu-id="af297-140">These attributes are contained under the **\<StmtSimple>** element of the plan.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af297-141">参照</span><span class="sxs-lookup"><span data-stu-id="af297-141">See Also</span></span>  
 [<span data-ttu-id="af297-142">sp_create_plan_guide &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af297-142">sp_create_plan_guide &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)  
  
  
