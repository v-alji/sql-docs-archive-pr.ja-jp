---
title: Integration Services サーバーで実行されているパッケージの表示と停止 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], managing
- managing running packages [Integration Services]
- packages [Integration Services], running
- running package [Integration Services], managing
ms.assetid: 11bf44e6-f6b0-475f-b816-40e914dbac80
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6e63839d4ab5d8d50f7d86eea05c8d58107d6799
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644530"
---
# <a name="viewing-and-stopping-packages-running-on-the-integration-services-server"></a><span data-ttu-id="5d3e5-102">Integration Services サーバーで実行中のパッケージの表示と停止</span><span class="sxs-lookup"><span data-stu-id="5d3e5-102">Viewing and Stopping Packages Running on the Integration Services Server</span></span>
  <span data-ttu-id="5d3e5-103">`SSISDB` データベースでは、ユーザーに表示されない内部テーブルに実行履歴を格納します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-103">The `SSISDB` database stores execution history in internal tables that are not visible to users.</span></span> <span data-ttu-id="5d3e5-104">ただし、必要な情報は、パブリック ビューに対してクエリを実行することで公開されます。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-104">However it exposes the information that you need through public views that you can query.</span></span> <span data-ttu-id="5d3e5-105">また、パッケージに関連した一般的なタスクを実行するために呼び出すことができるストアド プロシージャも用意されています。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-105">It also provides stored procedures that you can call to perform common tasks related to packages.</span></span>  
  
 <span data-ttu-id="5d3e5-106">通常、サーバー上の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] オブジェクトは [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]で管理します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-106">Typically you manage [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] objects on the server in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="5d3e5-107">また、データベース ビューに対してクエリを実行し、ストアド プロシージャを直接呼び出すことや、マネージド API を呼び出すカスタム コードを記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-107">However you can also query the database views and call the stored procedures directly, or write custom code that calls the managed API.</span></span> [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="5d3e5-108">およびマネージド API では、ビューに対してクエリを実行し、多くのタスクを実行するストアド プロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-108">and the managed API query the views and call the stored procedures to perform many of their tasks.</span></span> <span data-ttu-id="5d3e5-109">たとえば、サーバーで現在実行中の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージの一覧を表示し、必要に応じてパッケージの停止を要求できます。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-109">For example, you can view the list of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages that are currently running on the server, and request packages to stop if you have to.</span></span>  
  
## <a name="viewing-the-list-of-running-packages"></a><span data-ttu-id="5d3e5-110">実行中のパッケージの一覧の表示</span><span class="sxs-lookup"><span data-stu-id="5d3e5-110">Viewing the List of Running Packages</span></span>  
 <span data-ttu-id="5d3e5-111">**[アクティブな操作]** ダイアログ ボックスでは、サーバーで現在実行中のパッケージの一覧を表示できます。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-111">You can view the list of packages that are currently running on the server in the **Active Operations** dialog box.</span></span> <span data-ttu-id="5d3e5-112">詳しくは、「 [Active Operations Dialog Box](../../2014/integration-services/active-operations-dialog-box.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-112">For more information, see [Active Operations Dialog Box](../../2014/integration-services/active-operations-dialog-box.md).</span></span>  
  
 <span data-ttu-id="5d3e5-113">実行中のパッケージの一覧を表示するその他の方法については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-113">For information about the other methods that you can use to view the list of running packages, see the following topics.</span></span>  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="5d3e5-114">アクセス</span><span class="sxs-lookup"><span data-stu-id="5d3e5-114">access</span></span>  
 <span data-ttu-id="5d3e5-115">サーバーで実行中のパッケージの一覧を表示するには、ステータスが 2 のパッケージに対してビュー [catalog.executions (SSISDB データベース)](/sql/integration-services/system-views/catalog-executions-ssisdb-database) をクエリします。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-115">To view the list of packages that are running on the server, query the view, [catalog.executions &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database) for packages that have a status of 2.</span></span>  
  
 <span data-ttu-id="5d3e5-116">マネージド API を使用したプログラムによるアクセス</span><span class="sxs-lookup"><span data-stu-id="5d3e5-116">Programmatic access through the managed API</span></span>  
 <span data-ttu-id="5d3e5-117"><xref:Microsoft.SqlServer.Management.IntegrationServices> 名前空間とそのクラスのトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-117">See the <xref:Microsoft.SqlServer.Management.IntegrationServices> namespace and its classes.</span></span>  
  
## <a name="stopping-a-running-package"></a><span data-ttu-id="5d3e5-118">実行中のパッケージの停止</span><span class="sxs-lookup"><span data-stu-id="5d3e5-118">Stopping a Running Package</span></span>  
 <span data-ttu-id="5d3e5-119">**[アクティブな操作]** ダイアログ ボックスでは、実行中のパッケージを停止するよう要求できます。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-119">You can request a running package to stop in the **Active Operations** dialog box.</span></span> <span data-ttu-id="5d3e5-120">詳しくは、「 [Active Operations Dialog Box](../../2014/integration-services/active-operations-dialog-box.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-120">For more information, see [Active Operations Dialog Box](../../2014/integration-services/active-operations-dialog-box.md).</span></span>  
  
 <span data-ttu-id="5d3e5-121">実行中のパッケージを停止するその他の方法については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-121">For information about the other methods that you can use to stop a running package, see the following topics.</span></span>  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="5d3e5-122">アクセス</span><span class="sxs-lookup"><span data-stu-id="5d3e5-122">access</span></span>  
 <span data-ttu-id="5d3e5-123">サーバーで実行中のパッケージを停止するには、ストアド プロシージャ [catalog.stop_operation (SSISDB データベース)](/sql/integration-services/system-stored-procedures/catalog-stop-operation-ssisdb-database) を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-123">To stop a package that is running on the server, call the stored procedure, [catalog.stop_operation &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-stop-operation-ssisdb-database).</span></span>  
  
 <span data-ttu-id="5d3e5-124">マネージド API を使用したプログラムによるアクセス</span><span class="sxs-lookup"><span data-stu-id="5d3e5-124">Programmatic access through the managed API</span></span>  
 <span data-ttu-id="5d3e5-125"><xref:Microsoft.SqlServer.Management.IntegrationServices> 名前空間とそのクラスのトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-125">See the <xref:Microsoft.SqlServer.Management.IntegrationServices> namespace and its classes.</span></span>  
  
## <a name="viewing-the-history-of-packages-that-have-run"></a><span data-ttu-id="5d3e5-126">実行したパッケージの履歴の表示</span><span class="sxs-lookup"><span data-stu-id="5d3e5-126">Viewing the History of Packages That Have Run</span></span>  
 <span data-ttu-id="5d3e5-127">実行したパッケージの履歴を [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]で確認するには、 **[すべての実行]** レポートを使用します。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-127">To view the history of packages that have run in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], use the **All Executions** report.</span></span> <span data-ttu-id="5d3e5-128">**[すべての実行]** レポートとその他の標準レポートの詳細については、「 [Integration Services サーバーのレポート](../../2014/integration-services/reports-for-the-integration-services-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-128">For more information on the **All Executions** report and other standard reports, see [Reports for the Integration Services Server](../../2014/integration-services/reports-for-the-integration-services-server.md).</span></span>  
  
 <span data-ttu-id="5d3e5-129">実行中のパッケージの履歴を表示するその他の方法については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-129">For information about the other methods that you can use to view the history of running packages, see the following topics.</span></span>  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="5d3e5-130">アクセス</span><span class="sxs-lookup"><span data-stu-id="5d3e5-130">access</span></span>  
 <span data-ttu-id="5d3e5-131">実行したパッケージに関する情報を表示するには、ビュー [catalog.executions (SSISDB データベース)](/sql/integration-services/system-views/catalog-executions-ssisdb-database) をクエリします。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-131">To view information about packages that have run, query the view, [catalog.executions &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database).</span></span>  
  
 <span data-ttu-id="5d3e5-132">マネージド API を使用したプログラムによるアクセス</span><span class="sxs-lookup"><span data-stu-id="5d3e5-132">Programmatic access through the managed API</span></span>  
 <span data-ttu-id="5d3e5-133"><xref:Microsoft.SqlServer.Management.IntegrationServices> 名前空間とそのクラスのトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5d3e5-133">See the <xref:Microsoft.SqlServer.Management.IntegrationServices> namespace and its classes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d3e5-134">参照</span><span class="sxs-lookup"><span data-stu-id="5d3e5-134">See Also</span></span>  
 <span data-ttu-id="5d3e5-135">[プロジェクトとパッケージの実行](packages/run-integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="5d3e5-135">[Execution of Projects and Packages](packages/run-integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="5d3e5-136">パッケージ実行のレポートのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="5d3e5-136">Troubleshooting Reports for Package Execution</span></span>](troubleshooting/troubleshooting-reports-for-package-execution.md)  
  
  
