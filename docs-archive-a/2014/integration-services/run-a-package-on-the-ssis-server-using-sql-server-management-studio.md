---
title: SQL Server Management Studio | を使用して SSIS サーバーでパッケージを実行するMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 56dc1bf8-99d4-41dc-bdc4-f64f1ccfd688
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d17009988dea54621d4fd7ef542cf452bfe95c6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713238"
---
# <a name="run-a-package-on-the-ssis-server-using-sql-server-management-studio"></a><span data-ttu-id="8e390-102">SQL Server Management Studio を使用した SSIS サーバーでのパッケージの実行</span><span class="sxs-lookup"><span data-stu-id="8e390-102">Run a Package on the SSIS Server Using SQL Server Management Studio</span></span>
  <span data-ttu-id="8e390-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サーバーにプロジェクトを配置した後は、サーバーでパッケージを実行できます。</span><span class="sxs-lookup"><span data-stu-id="8e390-103">After you deploy your project to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, you can run the package on the server.</span></span>  
  
 <span data-ttu-id="8e390-104">操作レポートを使用して、サーバー上で実行されたパッケージまたは現在実行中のパッケージに関する情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="8e390-104">You can use operations reports to view information about packages that have run, or are currently running, on the server.</span></span> <span data-ttu-id="8e390-105">詳細については、「 [Reports for the Integration Services Server](../../2014/integration-services/reports-for-the-integration-services-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e390-105">For more information, see [Reports for the Integration Services Server](../../2014/integration-services/reports-for-the-integration-services-server.md).</span></span>  
  
### <a name="to-run-a-package-on-the-server-using-sql-server-management-studio"></a><span data-ttu-id="8e390-106">SQL Server Management Studio を使用してサーバーでパッケージを実行するには</span><span class="sxs-lookup"><span data-stu-id="8e390-106">To run a package on the server using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="8e390-107">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を開き、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] カタログが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="8e390-107">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and connect to the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that contains the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] catalog.</span></span>  
  
2.  <span data-ttu-id="8e390-108">オブジェクト エクスプローラーで、 **[Integration Services カタログ]** ノード、 **[SSISDB]** ノードの順に展開し、配置したプロジェクトに含まれるパッケージに移動します。</span><span class="sxs-lookup"><span data-stu-id="8e390-108">In Object Explorer, expand the **Integration Services Catalogs** node, expand the **SSISDB** node, and navigate to the package contained in the project you deployed.</span></span>  
  
3.  <span data-ttu-id="8e390-109">パッケージ名を右クリックし、 **[実行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8e390-109">Right-click the package name and select **Execute**.</span></span>  
  
4.  <span data-ttu-id="8e390-110">**[パッケージの実行]** ダイアログ ボックスの **[パラメーター]** タブ、 **[接続マネージャー]** タブ、 **[詳細設定]** タブの設定を使用して、パッケージの実行を構成します。</span><span class="sxs-lookup"><span data-stu-id="8e390-110">Configure the package execution by using the settings on the **Parameters**, **Connection Managers**, and **Advanced** tabs in the **Execute Package** dialog box.</span></span>  
  
5.  <span data-ttu-id="8e390-111">**[OK]** をクリックしてパッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="8e390-111">Click **OK** to run the package.</span></span>  
  
     <span data-ttu-id="8e390-112">または</span><span class="sxs-lookup"><span data-stu-id="8e390-112">-or-</span></span>  
  
     <span data-ttu-id="8e390-113">ストアド プロシージャを使用してパッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="8e390-113">Use stored procedures to run the package.</span></span> <span data-ttu-id="8e390-114">**[スクリプト]** をクリックして、実行のインスタンスを作成し、実行のインスタンスを開始する Transact-SQL ステートメントを生成します。</span><span class="sxs-lookup"><span data-stu-id="8e390-114">Click **Script** to generate the Transact-SQL statement that creates an instance of the execution and starts an instance of the execution.</span></span> <span data-ttu-id="8e390-115">ステートメントには catalog.create_execution、catalog.set_execution_parameter_value、および catalog.start_execution の各ストアド プロシージャの呼び出しが含まれています。</span><span class="sxs-lookup"><span data-stu-id="8e390-115">The statement includes a call to the catalog.create_execution, catalog.set_execution_parameter_value, and catalog.start_execution stored procedures.</span></span> <span data-ttu-id="8e390-116">これらのストアド プロシージャの詳細については、「[catalog.create_execution (SSISDB データベース)](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database)」、「[catalog.set_execution_parameter_value (SSISDB データベース)](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database)」、および「[catalog.start_execution (SSISDB データベース)](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8e390-116">For more information about these stored procedures, see [catalog.create_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database), [catalog.set_execution_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database), and [catalog.start_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database).</span></span>  
  
  
