---
title: オプション (テキストエディター、Transact-sql-IntelliSense) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.SQL.Advanced
- VS.ToolsOptionsPages.Text_Editor.SQL_Server_Tools.Advanced
dev_langs:
- TSQL
ms.assetid: 1855d916-5bf9-4d94-b0fb-9f9bb05ff950
author: rothja
ms.author: jroth
ms.openlocfilehash: 2d8f9c865516dc5e4c0ddadbdc908a9b4c8ec366
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642955"
---
# <a name="options-text-editor-transact-sql-intellisense"></a><span data-ttu-id="daee8-102">オプション (テキストエディター、Transact-sql-IntelliSense)</span><span class="sxs-lookup"><span data-stu-id="daee8-102">Options (Text Editor-Transact-SQL-IntelliSense)</span></span>
  <span data-ttu-id="daee8-103">**[オプション]** ダイアログ ボックスを使用すると、[!INCLUDE[ssDE](../includes/ssde-md.md)] クエリ エディターの IntelliSense の設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="daee8-103">The **Options** dialog box lets you change the IntelliSense settings for the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor.</span></span> <span data-ttu-id="daee8-104">この設定を変更するには、**[ツール]** メニューの **[オプション]** をクリックし、**[テキスト エディター]** フォルダー、**[Transact-SQL]** フォルダーの順に展開し、**[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="daee8-104">These settings are available when, on the **Tools** menu, you click **Options**, expand the **Text Editor** folder, expand the **Transact-SQL** folder, and then click **Advanced**.</span></span>  
  
## <a name="transact-sql-intellisense-settings"></a><span data-ttu-id="daee8-105">[Transact-SQL IntelliSense の設定]</span><span class="sxs-lookup"><span data-stu-id="daee8-105">Transact-SQL IntelliSense Settings</span></span>  
 <span data-ttu-id="daee8-106">[!INCLUDE[ssDE](../includes/ssde-md.md)] クエリ エディターの IntelliSense のオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="daee8-106">Specifies the IntelliSense options for the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor.</span></span>  
  
### <a name="enable-intellisense"></a><span data-ttu-id="daee8-107">[IntelliSense を有効にする]</span><span class="sxs-lookup"><span data-stu-id="daee8-107">Enable IntelliSense</span></span>  
 <span data-ttu-id="daee8-108">IntelliSense 機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="daee8-108">Enables the IntelliSense features.</span></span> <span data-ttu-id="daee8-109">このボックスをオフにすると、特定の IntelliSense オプションを使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="daee8-109">When this box is not selected, the specific IntelliSense options are unavailable.</span></span> <span data-ttu-id="daee8-110">既定では、このチェック ボックスはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="daee8-110">By default, this check box is selected.</span></span>  
  
 <span data-ttu-id="daee8-111">**[エラーに下線を引く]**</span><span class="sxs-lookup"><span data-stu-id="daee8-111">**Underline errors**</span></span>  
 <span data-ttu-id="daee8-112">クエリ ウィンドウで [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントの構文エラーとセマンティック エラーを識別します。</span><span class="sxs-lookup"><span data-stu-id="daee8-112">Identifies syntax and semantic errors in [!INCLUDE[tsql](../includes/tsql-md.md)] statements in the query window.</span></span> <span data-ttu-id="daee8-113">すべてのエラーと警告が赤で表示されます。</span><span class="sxs-lookup"><span data-stu-id="daee8-113">All errors and warnings appear in red.</span></span> <span data-ttu-id="daee8-114">エラーと警告は、IntelliSense が実装されている [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントについてのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="daee8-114">Errors and warnings are supported only for the [!INCLUDE[tsql](../includes/tsql-md.md)] statements for which IntelliSense has been implemented.</span></span> <span data-ttu-id="daee8-115">既定では、このチェック ボックスはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="daee8-115">By default, this check box is selected.</span></span>  
  
 <span data-ttu-id="daee8-116">**[ステートメントのアウトラインを表示する]**</span><span class="sxs-lookup"><span data-stu-id="daee8-116">**Outline statements**</span></span>  
 <span data-ttu-id="daee8-117">ファイルが開いているときにアウトライン機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="daee8-117">Enables the outlining feature when a file is opened.</span></span> <span data-ttu-id="daee8-118">これにより、[!INCLUDE[tsql](../includes/tsql-md.md)] コードの折りたたみ可能なブロックが作成されます。</span><span class="sxs-lookup"><span data-stu-id="daee8-118">This creates collapsible blocks of [!INCLUDE[tsql](../includes/tsql-md.md)] code.</span></span> <span data-ttu-id="daee8-119">既定では、このチェック ボックスはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="daee8-119">By default, this check box is selected.</span></span>  
  
 <span data-ttu-id="daee8-120">**[スクリプトの最大サイズ]**</span><span class="sxs-lookup"><span data-stu-id="daee8-120">**Maximum script size**</span></span>  
 <span data-ttu-id="daee8-121">IntelliSense 機能が無効になるサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="daee8-121">Specifies the size at which IntelliSense functionality is disabled.</span></span> <span data-ttu-id="daee8-122">スクリプトが指定したサイズを超えると、警告メッセージが出され、</span><span class="sxs-lookup"><span data-stu-id="daee8-122">If a script exceeds the specified size, a warning message is issued.</span></span> <span data-ttu-id="daee8-123">そのエディター ウィンドウでコードの色分けを除くすべての IntelliSense 機能が無効になります。</span><span class="sxs-lookup"><span data-stu-id="daee8-123">All IntelliSense features, except color coding, are disabled for that editor window.</span></span> <span data-ttu-id="daee8-124">十分な量のテキストが削除されて制限内までスクリプトのサイズが縮小されると、IntelliSense が再度有効になります。</span><span class="sxs-lookup"><span data-stu-id="daee8-124">IntelliSense is reenabled when enough text is deleted to reduce the script size to under the limit.</span></span> <span data-ttu-id="daee8-125">サイズの大きいスクリプトに対して IntelliSense を有効にすると、速度の遅いコンピューターではパフォーマンスが低下することがあります。</span><span class="sxs-lookup"><span data-stu-id="daee8-125">Enabling IntelliSense for large script sizes can decrease performance on slow computers.</span></span> <span data-ttu-id="daee8-126">指定できるサイズは、100 KB、500 KB、1 MB、2 MB、および無制限です。</span><span class="sxs-lookup"><span data-stu-id="daee8-126">The allowed sizes are 100 KB, 500 KB, 1 MB, 2 MB, and Unlimited.</span></span> <span data-ttu-id="daee8-127">既定値は 1 MB です。</span><span class="sxs-lookup"><span data-stu-id="daee8-127">The default is 1 MB.</span></span>  
  
 <span data-ttu-id="daee8-128">**[組み込み関数名の文字種]**</span><span class="sxs-lookup"><span data-stu-id="daee8-128">**Casing for built-in function names**</span></span>  
 <span data-ttu-id="daee8-129">入力候補一覧に含まれている組み込み [!INCLUDE[tsql](../includes/tsql-md.md)] 関数の名前に大文字 (DATEADD など) と小文字 (dateadd など) のどちらを使用するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="daee8-129">Specifies whether the names of built-in [!INCLUDE[tsql](../includes/tsql-md.md)] functions that are included in completion lists use uppercase letters, such as DATEADD; or lowercase letters, such as dateadd.</span></span> <span data-ttu-id="daee8-130">使用中の [!INCLUDE[tsql](../includes/tsql-md.md)] コーディング規則に最適なオプションを選択してください。</span><span class="sxs-lookup"><span data-stu-id="daee8-130">Select the option that best matches the [!INCLUDE[tsql](../includes/tsql-md.md)] coding conventions that you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daee8-131">参照</span><span class="sxs-lookup"><span data-stu-id="daee8-131">See Also</span></span>  
 [<span data-ttu-id="daee8-132">IntelliSense のトラブルシューティング &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="daee8-132">Troubleshooting IntelliSense &#40;SQL Server Management Studio&#41;</span></span>](../relational-databases/scripting/troubleshooting-intellisense.md)  
  
  
