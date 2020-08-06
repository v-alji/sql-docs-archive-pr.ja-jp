---
title: Integration Services (SSIS) と Studio の環境 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- studio environments [Integration Services]
- tools [Integration Services], Business Intelligence Development Studio
- Business Intelligence Development Studio, Integration Services in
- SQL Server Management Studio [Integration Services]
- SSIS, studio environments
- SQL Server Integration Services, studio environments
- tools [Integration Services], SQL Server Management Studio
ms.assetid: 4eb73e65-d9f3-4ac6-a408-abfa85afc537
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bfe0cf7ef482dce3870db8c730c597daf1d539e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641134"
---
# <a name="integration-services-ssis-and-studio-environments"></a><span data-ttu-id="a98b5-102">Integration Services (SSIS) と Studio の環境</span><span class="sxs-lookup"><span data-stu-id="a98b5-102">Integration Services (SSIS) and Studio Environments</span></span>
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="a98b5-103">には、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]と組み合わせて活用できる 2 つの "Studio" が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a98b5-103">includes two studios for working with [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="a98b5-104">1 つは、ビジネス ソリューションに必要な[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] パッケージを開発するための [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] です。</span><span class="sxs-lookup"><span data-stu-id="a98b5-104">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for developing the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages that a business solution requires.</span></span> [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="a98b5-105">の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを使ってパッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="a98b5-105">provides the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in which you create packages.</span></span>  
  
-   <span data-ttu-id="a98b5-106">もう 1 つは、運用環境でパッケージを管理するための[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] です。</span><span class="sxs-lookup"><span data-stu-id="a98b5-106">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] for managing packages in a production environment.</span></span>  
  
## <a name="sql-server-data-tools"></a><span data-ttu-id="a98b5-107">SQL Server Data Tools</span><span class="sxs-lookup"><span data-stu-id="a98b5-107">SQL Server Data Tools</span></span>  
 <span data-ttu-id="a98b5-108">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]を使用すると、次のタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="a98b5-108">Working in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], you can perform the following tasks:</span></span>  
  
-   <span data-ttu-id="a98b5-109">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードを実行し、変換元のデータを変換先にコピーする基本パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="a98b5-109">Run the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard to create basic packages that copy data from a source to a destination.</span></span>  
  
-   <span data-ttu-id="a98b5-110">複雑な制御フロー、データ フロー、イベント ドリブン手法、およびログ記録が含まれるパッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="a98b5-110">Create packages that include complex control flow, data flow, event-driven logic, and logging.</span></span>  
  
-   <span data-ttu-id="a98b5-111">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーのトラブルシューティングと監視機能、および [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]のデバック機能を使用して、パッケージをテストおよびデバッグします。</span><span class="sxs-lookup"><span data-stu-id="a98b5-111">Test and debug packages by using the troubleshooting and monitoring features in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, and the debugging features in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="a98b5-112">パッケージとパッケージ オブジェクトのプロパティを、実行時に更新する構成を作成します。</span><span class="sxs-lookup"><span data-stu-id="a98b5-112">Create configurations that update the properties of packages and package objects at run time.</span></span>  
  
-   <span data-ttu-id="a98b5-113">パッケージとその依存関係を別のコンピューターにインストールする、配置ユーティリティを作成します。</span><span class="sxs-lookup"><span data-stu-id="a98b5-113">Create a deployment utility that can install packages and their dependencies on other computers.</span></span>  
  
-   <span data-ttu-id="a98b5-114">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の msdb データベース、[!INCLUDE[ssIS](../includes/ssis-md.md)] パッケージ ストア、およびファイル システムに、パッケージのコピーを保存します。</span><span class="sxs-lookup"><span data-stu-id="a98b5-114">Save copies of packages to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb database, the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Store, and the file system.</span></span>  
  
 <span data-ttu-id="a98b5-115">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]の詳細については、「 [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a98b5-115">For more information about [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], see [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686.aspx).</span></span>  
  
## <a name="sql-server-management-studio"></a><span data-ttu-id="a98b5-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a98b5-116">SQL Server Management Studio</span></span>  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="a98b5-117">の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスを利用して、パッケージの管理、実行中のパッケージの監視、および [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] オブジェクトと [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オブジェクトの影響とデータ系列の決定を行います。</span><span class="sxs-lookup"><span data-stu-id="a98b5-117">provides the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service that you use to manage packages, monitor running packages, and determine impact and data lineage for [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects.</span></span>  
  
 <span data-ttu-id="a98b5-118">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]を使用すると、次のタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="a98b5-118">Working in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], you can perform the following tasks:</span></span>  
  
-   <span data-ttu-id="a98b5-119">わかりやすい方法でパッケージを整理するために、フォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="a98b5-119">Create folders to organize packages in a way that is meaningful to your organization.</span></span>  
  
-   <span data-ttu-id="a98b5-120">パッケージ実行ユーティリティを使用して、ローカル コンピューター上に格納されているパッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="a98b5-120">Run packages that are stored on the local computer by using the Execute Package utility.</span></span>  
  
-   <span data-ttu-id="a98b5-121">パッケージ実行ユーティリティを実行して、 **dtexec** コマンド プロンプト ユーティリティ (dtexec.exe) の実行時に使用するコマンド ラインを生成します。</span><span class="sxs-lookup"><span data-stu-id="a98b5-121">Run the Execute Package utility to generate a command line to use when you run the **dtexec** command prompt utility (dtexec.exe).</span></span>  
  
-   <span data-ttu-id="a98b5-122">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の msdb データベース、[!INCLUDE[ssIS](../includes/ssis-md.md)] パッケージ ストア、およびファイル システムのパッケージをインポートおよびエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="a98b5-122">Import and export packages to and from the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb database, the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Store, and the file system.</span></span>  
  
