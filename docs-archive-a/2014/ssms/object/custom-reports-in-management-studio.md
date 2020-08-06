---
title: Management Studio におけるカスタム レポート | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.summary.new.custom.report.f1
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 1ba3f758-f39b-4f5f-91ca-516cedc78979
author: stevestein
ms.author: sstein
ms.openlocfilehash: bc93157100738610c8576f0af40e75613c3cff62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630771"
---
# <a name="custom-reports-in-management-studio"></a><span data-ttu-id="fa57f-102">Management Studio におけるカスタム レポート</span><span class="sxs-lookup"><span data-stu-id="fa57f-102">Custom Reports in Management Studio</span></span>
  <span data-ttu-id="fa57f-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]では、 [!INCLUDE[msCoName](../../includes/msconame-md.md)]で作成された一連の標準レポートが多数のオブジェクト エクスプローラー ノードに表示されます。</span><span class="sxs-lookup"><span data-stu-id="fa57f-103">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], many Object Explorer nodes display a set of standard reports that are created by [!INCLUDE[msCoName](../../includes/msconame-md.md)].</span></span> <span data-ttu-id="fa57f-104">これらのレポートは、要求されることの多いサーバー情報を要約表示できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="fa57f-104">These reports summarize typically requested server information.</span></span> <span data-ttu-id="fa57f-105">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 以降は、管理者が [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で作成されたカスタム レポートを [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]から実行できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="fa57f-105">Starting with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2, administrators can run custom reports that were created in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] from [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="fa57f-106">実装</span><span class="sxs-lookup"><span data-stu-id="fa57f-106">Implementation</span></span>  
 <span data-ttu-id="fa57f-107">カスタム レポートはレポート定義言語 (RDL) を使用して作成し、レポート定義 (.rdl) ファイルとして保存します。</span><span class="sxs-lookup"><span data-stu-id="fa57f-107">Custom reports are stored as report definition (.rdl) files and are created by using Report Definition Language (RDL).</span></span> <span data-ttu-id="fa57f-108">RDL には、レポートのデータ取得情報とレイアウト情報が XML 形式で含まれています。</span><span class="sxs-lookup"><span data-stu-id="fa57f-108">RDL contains data retrieval and layout information for a report in an XML format.</span></span> <span data-ttu-id="fa57f-109">RDL はオープン スキーマです。</span><span class="sxs-lookup"><span data-stu-id="fa57f-109">RDL is an open schema.</span></span> <span data-ttu-id="fa57f-110">開発者は、属性や要素を追加して RDL を拡張することができます。</span><span class="sxs-lookup"><span data-stu-id="fa57f-110">Developers can extend RDL with additional attributes and elements.</span></span> <span data-ttu-id="fa57f-111">レポートは、任意の有効な [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントをレポート内で実行できます。</span><span class="sxs-lookup"><span data-stu-id="fa57f-111">Reports can execute any valid [!INCLUDE[tsql](../../includes/tsql-md.md)] statement within the report.</span></span>  
  
 <span data-ttu-id="fa57f-112">オブジェクト エクスプローラーがサーバーに接続されている場合、オブジェクト エクスプローラーで現在選択されている内容のコンテキストでカスタム レポートを実行できます (ただし、そのノードのレポート パラメーターがレポートで参照されている必要があります)。</span><span class="sxs-lookup"><span data-stu-id="fa57f-112">If Object Explorer is connected to a server, custom reports can execute in the context of the current Object Explorer selection if the reports reference report parameters of that node.</span></span> <span data-ttu-id="fa57f-113">これにより、現在のデータベースなど現在のコンテキストをレポートで使用することができます。あるいは、カスタム レポートに含まれている [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントに特定のデータベースを使用するなどの形態で、一貫したコンテキストをレポートで使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="fa57f-113">This enables a report to use the current context, such as the current database; or a consistent context, such as specifying a designated database as part of the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that is contained in the custom report.</span></span>  
  
## <a name="running-a-custom-report"></a><span data-ttu-id="fa57f-114">カスタム レポートの実行</span><span class="sxs-lookup"><span data-stu-id="fa57f-114">Running a Custom Report</span></span>  
 <span data-ttu-id="fa57f-115">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] では次の方法でカスタム レポートを実行できます。</span><span class="sxs-lookup"><span data-stu-id="fa57f-115">You can run a custom report in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] in the following ways:</span></span>  
  
-   <span data-ttu-id="fa57f-116">オブジェクト エクスプローラーでノードを右クリックし、 **[レポート]** をポイントして、 **[カスタム レポート]** を左クリックします。</span><span class="sxs-lookup"><span data-stu-id="fa57f-116">Right-click a node in Object Explorer, point to **Reports** and left-click **Custom Reports**.</span></span> <span data-ttu-id="fa57f-117">**[ファイルを開く]** ダイアログ ボックスで .rdl ファイルを含むフォルダーを見つけ、適切なレポート ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="fa57f-117">In the **Open File** dialog box, locate a folder that contains .rdl files, and then open the appropriate report file.</span></span>  
  
-   <span data-ttu-id="fa57f-118">オブジェクト エクスプローラーでノードを右クリックして、 **[レポート]** 、 **[カスタム レポート]** の順にポイントし、最近使用したファイル一覧からカスタム レポートを選択します。</span><span class="sxs-lookup"><span data-stu-id="fa57f-118">Right-click a node in Object Explorer, point to **Reports**, point to **Custom Reports**, and then select a custom report from the most recently used file list.</span></span>  
  
## <a name="limitations"></a><span data-ttu-id="fa57f-119">制限事項</span><span class="sxs-lookup"><span data-stu-id="fa57f-119">Limitations</span></span>  
 <span data-ttu-id="fa57f-120">カスタム レポートを操作する場合は、次の制限事項に注意してください。</span><span class="sxs-lookup"><span data-stu-id="fa57f-120">When you work with custom reports, consider the following limitations:</span></span>  
  
-   <span data-ttu-id="fa57f-121">悪意あるコードが誤って実行されないようにするために、ファイル システムで .rdl ファイルが [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] に関連付けられていても、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でレポートの自動実行を構成できないようになっています。</span><span class="sxs-lookup"><span data-stu-id="fa57f-121">To prevent the unintended execution of malicious code, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] cannot be configured to automatically run a report, even if the file system is configured to associate .rdl files with [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="fa57f-122">レポートは、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] でプログラムから実行することも、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]のコマンド ラインから実行することもできません。</span><span class="sxs-lookup"><span data-stu-id="fa57f-122">Reports cannot be programmatically executed in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and cannot run from the command line through [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
-   <span data-ttu-id="fa57f-123">カスタム レポートは、意図した値が生成されないコンテキストでも実行できます。</span><span class="sxs-lookup"><span data-stu-id="fa57f-123">You can run custom reports in a context that does not produce the expected values.</span></span> <span data-ttu-id="fa57f-124">たとえば、レプリケーションに関係のないデータベースのコンテキストでレプリケーションに関するレポートを実行することも、正確なレポートの生成に必要な情報にアクセスする権限のないユーザーとしてレポートを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="fa57f-124">For example, you can run a report about replication in the context of a database that is not involved in replication, or run a report as a user who does not have permission to access information that is required to generate an accurate report.</span></span> <span data-ttu-id="fa57f-125">レポートの構造およびコンテキストの妥当性については、カスタム レポートの作成者が注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa57f-125">The creator of the custom report is responsible for the validity of the report structure and its context.</span></span>  
  
-   <span data-ttu-id="fa57f-126">カスタム レポートを標準レポートの一覧に追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="fa57f-126">You cannot add a custom report to the list of standard reports.</span></span>  
  
-   <span data-ttu-id="fa57f-127">レポートでのコード処理が、サーバーのパフォーマンスに影響することがあります。</span><span class="sxs-lookup"><span data-stu-id="fa57f-127">The code processed by the report might affect server performance.</span></span>  
  
-   <span data-ttu-id="fa57f-128">カスタム レポートではサブレポートがサポートされません。</span><span class="sxs-lookup"><span data-stu-id="fa57f-128">Custom reports will not support subreports.</span></span>  
  
-   <span data-ttu-id="fa57f-129">レポート内の各クエリのコマンド テキストを式で定義しないでください。</span><span class="sxs-lookup"><span data-stu-id="fa57f-129">The command text for each query within the report must not be defined through an expression.</span></span>  
  
-   <span data-ttu-id="fa57f-130">コマンド (クエリ) で使用されるクエリ パラメーターでは、1 つのレポート パラメーターのみを参照でき、式演算子は使用できません。</span><span class="sxs-lookup"><span data-stu-id="fa57f-130">Any query parameter that is used in a command (query) can only reference a single report parameter and cannot use any expression operators.</span></span>  
  
-   <span data-ttu-id="fa57f-131">レポート コマンド (クエリ) でサポートされるコマンドの種類は、テキストとストアド プロシージャのみです。</span><span class="sxs-lookup"><span data-stu-id="fa57f-131">Only Text and Stored Procedure command types are supported for report commands (queries).</span></span>  
  
-   <span data-ttu-id="fa57f-132">レポート フレームワークには、クエリのパラメーター エスケープ機能がありません。</span><span class="sxs-lookup"><span data-stu-id="fa57f-132">The report framework does not provide any parameter escaping for the queries.</span></span> <span data-ttu-id="fa57f-133">クエリの作成者は、クエリが SQL インジェクション攻撃を受けないことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa57f-133">Query authors must make sure that their queries are free from SQL injection attacks.</span></span>  
  
## <a name="managing-custom-reports"></a><span data-ttu-id="fa57f-134">カスタム レポートの管理</span><span class="sxs-lookup"><span data-stu-id="fa57f-134">Managing Custom Reports</span></span>  
 <span data-ttu-id="fa57f-135">カスタム レポートが多数ある場合は、適切な NTFS ファイル システム権限を持つファイル システム フォルダーを使用してカスタム レポートを整理することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fa57f-135">We recommend that users who have many custom reports organize them by using file system folders that have appropriate NTFS file system permissions.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="fa57f-136">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="fa57f-136">Permissions</span></span>  
 <span data-ttu-id="fa57f-137">カスタム レポートは、現在のユーザーの権限を使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="fa57f-137">Custom reports run by using the permissions of the current user.</span></span> <span data-ttu-id="fa57f-138">レポートで実行されるクエリが悪意あるユーザーによって変更されないようにするために、レポート ファイルが格納されるファイル システム フォルダーに権限を設定してアクセスを制限する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa57f-138">To prevent a malicious user from changing the queries run by the report, permissions on the file system folder that contains the report files should be set to restrict access.</span></span>  
  
 <span data-ttu-id="fa57f-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスによって使用されるユーザーとアカウントの両方に、レポート ファイルが格納されるファイル システム フォルダーへの読み取りアクセスが必要です。</span><span class="sxs-lookup"><span data-stu-id="fa57f-139">Both the user and the account that is used by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service require read access to the file system folder that contains the report files.</span></span>  
  
 <span data-ttu-id="fa57f-140">レポートには任意の有効な [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] コマンドを埋め込むことができますが、そのコマンドは実行されません。</span><span class="sxs-lookup"><span data-stu-id="fa57f-140">Any valid [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] command can be embedded in a report, but the command will not be executed.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="fa57f-141">レポートには任意の有効な [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを埋め込み、レポートから実行することができます。</span><span class="sxs-lookup"><span data-stu-id="fa57f-141">Any valid [!INCLUDE[tsql](../../includes/tsql-md.md)] statement can be embedded in and executed from a report.</span></span> <span data-ttu-id="fa57f-142">高い特権を持つユーザー アカウントでレポートを実行すると、このように埋め込まれた命令を容易に実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="fa57f-142">Running a report under a high-privileged user account makes it possible for any of these embedded instructions to execute without challenge.</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="fa57f-143">参照</span><span class="sxs-lookup"><span data-stu-id="fa57f-143">See Also</span></span>  
 <span data-ttu-id="fa57f-144">[カスタムレポートを Management Studio に追加する](add-a-custom-report-to-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="fa57f-144">[Add a Custom Report to Management Studio](add-a-custom-report-to-management-studio.md) </span></span>  
 <span data-ttu-id="fa57f-145">[抑制カスタムレポートの実行に関する警告](unsuppress-run-custom-report-warnings.md) </span><span class="sxs-lookup"><span data-stu-id="fa57f-145">[Unsuppress Run Custom Report Warnings](unsuppress-run-custom-report-warnings.md) </span></span>  
 [<span data-ttu-id="fa57f-146">カスタム レポートでのオブジェクト エクスプローラー ノード プロパティの使用</span><span class="sxs-lookup"><span data-stu-id="fa57f-146">Use Custom Reports with Object Explorer Node Properties</span></span>](use-custom-reports-with-object-explorer-node-properties.md)  
  
  
