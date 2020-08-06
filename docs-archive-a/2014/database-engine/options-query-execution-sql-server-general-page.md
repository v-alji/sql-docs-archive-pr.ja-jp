---
title: '[オプション] ([クエリ実行]-SQL Server-[全般] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryExecution.SqlServer.SqlExecutionGeneral
ms.assetid: 3f8d59bc-3f97-4e5d-8b86-5ac670d20780
author: rothja
ms.author: jroth
ms.openlocfilehash: eaa95293636d02674fb720dcd1b8146279f78e72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644605"
---
# <a name="options-query-execution-sql-server-general-page"></a><span data-ttu-id="d8810-102">[オプション] ([クエリ実行]-SQL Server-[全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="d8810-102">Options (Query Execution-SQL Server-General Page)</span></span>
  <span data-ttu-id="d8810-103">このページを使用すると、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] クエリを実行するためのオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d8810-103">Use this page to specify the options for running [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries.</span></span> <span data-ttu-id="d8810-104">これらのオプションに加えられた変更は、新しい [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] クエリだけに適用されます。</span><span class="sxs-lookup"><span data-stu-id="d8810-104">Changes to these options are only applied to new [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries.</span></span> <span data-ttu-id="d8810-105">現在のクエリのオプションを変更するには、**[クエリ]** メニューの **[クエリ オプション]** をクリックするか、[[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] クエリ] ウィンドウで右クリックし、**[クエリ オプション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d8810-105">To change the options for a current query, click **Query Options** on the **Query** menu, or in a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Query window right-click and select **Query Options**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d8810-106">Options</span><span class="sxs-lookup"><span data-stu-id="d8810-106">Options</span></span>  
 <span data-ttu-id="d8810-107">**SET ROWCOUNT**</span><span class="sxs-lookup"><span data-stu-id="d8810-107">**SET ROWCOUNT**</span></span>  
 <span data-ttu-id="d8810-108">既定値の 0 は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] がすべての結果を受け取るまで待機することを意味します。</span><span class="sxs-lookup"><span data-stu-id="d8810-108">The default value of 0 indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will wait for results until all results are received.</span></span> <span data-ttu-id="d8810-109">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] が指定された行数を取得した後にクエリを停止するように設定するには、0 より大きい値を指定します。</span><span class="sxs-lookup"><span data-stu-id="d8810-109">Provide a value greater than 0 if you want [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to halt the query after obtaining the specified number of rows.</span></span> <span data-ttu-id="d8810-110">このオプションをオフにして、すべての行が返されるようにするには、SET ROWCOUNT 0 を指定してください。</span><span class="sxs-lookup"><span data-stu-id="d8810-110">To turn this option off (so that all rows are returned), specify SET ROWCOUNT 0.</span></span>  
  
 <span data-ttu-id="d8810-111">**SET TEXTSIZE**</span><span class="sxs-lookup"><span data-stu-id="d8810-111">**SET TEXTSIZE**</span></span>  
 <span data-ttu-id="d8810-112">既定値の 2,147,483,647 バイトは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] が `text` データ フィールドおよび `ntext` データ フィールドの上限まで、完全なデータ フィールドを提供することを示します。</span><span class="sxs-lookup"><span data-stu-id="d8810-112">The default value of 2,147,483,647 bytes indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will provide complete data fields up to the limit of `text` and `ntext` data fields.</span></span> <span data-ttu-id="d8810-113">大きな値の場合に結果を制限するには、これより小さなサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="d8810-113">Provide a smaller number to limit results in the case of large values.</span></span> <span data-ttu-id="d8810-114">指定されたサイズよりも大きい列は切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="d8810-114">Columns greater than the number provided will be truncated.</span></span>  
  
 <span data-ttu-id="d8810-115">**[実行タイムアウト]**</span><span class="sxs-lookup"><span data-stu-id="d8810-115">**Execution time-out**</span></span>  
 <span data-ttu-id="d8810-116">**[新しい接続]** ダイアログ ボックスに既定値を設定します。</span><span class="sxs-lookup"><span data-stu-id="d8810-116">Sets the default value in the **New Connection** dialog box.</span></span> <span data-ttu-id="d8810-117">このスピン ボックスは、クエリを取り消す前に待機する秒数を [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] に指示するために使用します。</span><span class="sxs-lookup"><span data-stu-id="d8810-117">Use this spin box to tell [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] the number of seconds to wait before canceling the query.</span></span> <span data-ttu-id="d8810-118">値0は待機時間が無期限であるか、タイムアウトがないことを示します。新しいインストールでは、この値は0です。</span><span class="sxs-lookup"><span data-stu-id="d8810-118">A value of 0 indicates an infinite wait, or no time-out. This value is 0 on a new installation.</span></span>  
  
 <span data-ttu-id="d8810-119">**[バッチ区切り記号]**</span><span class="sxs-lookup"><span data-stu-id="d8810-119">**Batch separator**</span></span>  
 <span data-ttu-id="d8810-120">[!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントをバッチに分けるために使用する単語を入力します。</span><span class="sxs-lookup"><span data-stu-id="d8810-120">Type a word that you use to separate [!INCLUDE[tsql](../includes/tsql-md.md)] statements into batches.</span></span> <span data-ttu-id="d8810-121">既定値は GO です。</span><span class="sxs-lookup"><span data-stu-id="d8810-121">The default is GO.</span></span>  
  
 <span data-ttu-id="d8810-122">**[既定で、新しいクエリを SQLCMD モードで開始する]**</span><span class="sxs-lookup"><span data-stu-id="d8810-122">**By default, open new queries in SQLCMD Mode**</span></span>  
 <span data-ttu-id="d8810-123">新しいクエリを SQLCMD モードで開始するには、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="d8810-123">Select this check box to open new queries in SQLCMD mode.</span></span> <span data-ttu-id="d8810-124">SQLCMD モードに関する情報については、「[クエリ エディターによる SQLCMD スクリプトの編集](../relational-databases/scripting/edit-sqlcmd-scripts-with-query-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8810-124">For more information about SQLCMD mode, see [Edit SQLCMD Scripts with Query Editor](../relational-databases/scripting/edit-sqlcmd-scripts-with-query-editor.md).</span></span>  
  
 <span data-ttu-id="d8810-125">このオプションを選択する場合は、次の制限事項に注意してください。</span><span class="sxs-lookup"><span data-stu-id="d8810-125">When you select this option, be aware of the following limitations:</span></span>  
  
-   <span data-ttu-id="d8810-126">[!INCLUDE[ssDE](../includes/ssde-md.md)] クエリ エディターの IntelliSense が無効になります。</span><span class="sxs-lookup"><span data-stu-id="d8810-126">IntelliSense in the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor is turned off.</span></span>  
  
-   <span data-ttu-id="d8810-127">クエリ エディターはコマンド ラインから実行できないため、変数などのコマンド ライン パラメーターを渡すことができません。</span><span class="sxs-lookup"><span data-stu-id="d8810-127">Because Query Editor does not run from the command line, you cannot pass in command-line parameters such as variables.</span></span>  
  
-   <span data-ttu-id="d8810-128">クエリ エディターはオペレーティング システムのプロンプトに応答できないため、対話型のステートメントを実行しないように注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8810-128">Because Query Editor cannot respond to operating-system prompts, you must be careful not to run interactive statements.</span></span>  
  
 <span data-ttu-id="d8810-129">**既定値にリセット**</span><span class="sxs-lookup"><span data-stu-id="d8810-129">**Reset to Default**</span></span>  
 <span data-ttu-id="d8810-130">クリックすると、このページ上のすべての値が元の既定値にリセットされます。</span><span class="sxs-lookup"><span data-stu-id="d8810-130">Click to reset all values on this page to the original default values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8810-131">参照</span><span class="sxs-lookup"><span data-stu-id="d8810-131">See Also</span></span>  
 [<span data-ttu-id="d8810-132">sqlcmd Utility</span><span class="sxs-lookup"><span data-stu-id="d8810-132">sqlcmd Utility</span></span>](../tools/sqlcmd-utility.md)  
  
  
