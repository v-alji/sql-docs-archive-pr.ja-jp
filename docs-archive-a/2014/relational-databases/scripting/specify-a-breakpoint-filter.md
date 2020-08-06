---
title: ブレークポイント フィルターの指定
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint filter
ms.assetid: 7bf1dddd-7b0b-4c47-8a7b-28a5569b4fa5
author: rothja
ms.author: jroth
ms.openlocfilehash: 9fc320397da1bddc0d28191c359c4d311b23e044
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641583"
---
# <a name="specify-a-breakpoint-filter"></a><span data-ttu-id="b8355-102">ブレークポイント フィルターの指定</span><span class="sxs-lookup"><span data-stu-id="b8355-102">Specify a Breakpoint Filter</span></span>
  <span data-ttu-id="b8355-103">ブレークポイント フィルターは、ブレークポイントが指定したコンピューター、オペレーティング システム プロセス、およびスレッドだけで動作するように制限します。</span><span class="sxs-lookup"><span data-stu-id="b8355-103">A breakpoint filter limits the breakpoint to acting only on specified computers, operating system processes, and threads.</span></span> <span data-ttu-id="b8355-104">通常、ブレークポイント フィルターは、並列アプリケーションをデバッグするときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="b8355-104">Breakpoint filters are typically used when debugging parallel applications.</span></span>  
  
##  <a name="filter-considerations"></a><a name="BKMK_ActionConsiderations"></a> <span data-ttu-id="b8355-105">フィルターに関する注意点</span><span class="sxs-lookup"><span data-stu-id="b8355-105">Filter Considerations</span></span>  
 <span data-ttu-id="b8355-106">[!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトおよびストアド プロシージャは並列アプリケーションではないため、ブレークポイント フィルターは [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーでは通常使用されません。</span><span class="sxs-lookup"><span data-stu-id="b8355-106">Breakpoint filters are not typically used with the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger because [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts and stored procedures are not parallel applications.</span></span>  
  
#### <a name="to-specify-a-breakpoint-filter"></a><span data-ttu-id="b8355-107">ブレークポイント フィルターを指定するには</span><span class="sxs-lookup"><span data-stu-id="b8355-107">To Specify a Breakpoint Filter</span></span>  
  
1.  <span data-ttu-id="b8355-108">エディター ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[フィルター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b8355-108">In the editor window, right-click the breakpoint glyph, and then click **Filter** on the shortcut menu.</span></span>  
  
     <span data-ttu-id="b8355-109">または</span><span class="sxs-lookup"><span data-stu-id="b8355-109">-or-</span></span>  
  
     <span data-ttu-id="b8355-110">**[ブレークポイント]** ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[フィルター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b8355-110">In the **Breakpoints** window, right-click the breakpoint glyph, and then click **Filter** on the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="b8355-111">**[ブレークポイント フィルター]** ダイアログ ボックスで、 **[フィルター]** ボックスを使用して、コンピューター名を指定するか、またはオペレーティング システム プロセスとスレッドを名前または ID 番号で指定します。</span><span class="sxs-lookup"><span data-stu-id="b8355-111">In the **Breakpoint Filters** dialog box, use the **Filter** box to specify computers by name, or operating system processes and threads by either name or ID number:</span></span>  
  
    -   <span data-ttu-id="b8355-112">`MachineName` は、データベース エンジンのインスタンスを実行しているコンピューターです。</span><span class="sxs-lookup"><span data-stu-id="b8355-112">`MachineName` is the computer running the instance of the Database Engine.</span></span>  
  
    -   <span data-ttu-id="b8355-113">`ProcessID` および `ProcessName` は、データベース エンジンのインスタンスを実行しているオペレーティング システム プロセスです。</span><span class="sxs-lookup"><span data-stu-id="b8355-113">`ProcessID`, and `ProcessName` are the operating system process running the instance of the Database Engine.</span></span>  
  
    -   <span data-ttu-id="b8355-114">`ThreadID` および `ThreadName` は、データベース エンジンのインスタンス内で [!INCLUDE[tsql](../../includes/tsql-md.md)] バッチ、プロシージャ、または関数を実行しているオペレーティング システム スレッドです。</span><span class="sxs-lookup"><span data-stu-id="b8355-114">`ThreadID` and `ThreadName` are the operating system thread running the [!INCLUDE[tsql](../../includes/tsql-md.md)] batch, procedure, or function in the instance of the Database Engine.</span></span>  
  
3.  <span data-ttu-id="b8355-115">**[OK]** をクリックして変更を適用するか、 **[キャンセル]** をクリックして変更を適用せずに終了します。</span><span class="sxs-lookup"><span data-stu-id="b8355-115">Click **OK** to implement the changes, or **Cancel** to exit without applying the changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8355-116">参照</span><span class="sxs-lookup"><span data-stu-id="b8355-116">See Also</span></span>  
 <span data-ttu-id="b8355-117">[ブレークポイント条件の指定](specify-a-breakpoint-condition.md) </span><span class="sxs-lookup"><span data-stu-id="b8355-117">[Specify a Breakpoint Condition](specify-a-breakpoint-condition.md) </span></span>  
 <span data-ttu-id="b8355-118">[ヒット カウントの指定](specify-a-hit-count.md) </span><span class="sxs-lookup"><span data-stu-id="b8355-118">[Specify a Hit Count](specify-a-hit-count.md) </span></span>  
 [<span data-ttu-id="b8355-119">ブレークポイント アクションの指定</span><span class="sxs-lookup"><span data-stu-id="b8355-119">Specify a Breakpoint Action</span></span>](specify-a-breakpoint-action.md)  
