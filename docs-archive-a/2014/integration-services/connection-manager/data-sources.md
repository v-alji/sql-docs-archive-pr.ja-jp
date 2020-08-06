---
title: データ ソース | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data sources [Integration Services], about data sources
ms.assetid: 7ac81612-9822-470f-8d0f-a1dc96142fe3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a52889627dbe61254ac1359ae97f25ee8521b6e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642231"
---
# <a name="data-sources"></a><span data-ttu-id="04029-102">ソリューション エクスプローラー</span><span class="sxs-lookup"><span data-stu-id="04029-102">Data Sources</span></span>
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="04029-103">には、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージで使用できるデザイン時のオブジェクト (データ ソース) が用意されています。</span><span class="sxs-lookup"><span data-stu-id="04029-103">includes a design-time object that you can use in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages: the data source.</span></span>  
  
 <span data-ttu-id="04029-104">データ ソース オブジェクトは接続への参照であり、少なくとも接続文字列とデータ ソース識別子が含まれています。</span><span class="sxs-lookup"><span data-stu-id="04029-104">A data source object is a reference to a connection, and at a minimum, it includes a connection string and a data source identifier.</span></span> <span data-ttu-id="04029-105">また、説明、名前、ユーザー名、パスワードなどの追加メタデータを含むこともできます。</span><span class="sxs-lookup"><span data-stu-id="04029-105">It can also include additional metadata such a description, a name, a user name, and a password.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="04029-106">データ ソースは、パッケージ配置モデルを使用するように構成されているプロジェクトにのみ追加できます。</span><span class="sxs-lookup"><span data-stu-id="04029-106">You can add data sources only to projects that are configured to use the package deployment model.</span></span> <span data-ttu-id="04029-107">プロジェクト配置モデルを使用するようにプロジェクトが構成されている場合は、データ ソースを使用する代わりに、プロジェクト レベルで作成された接続マネージャーを使用して接続を共有します。</span><span class="sxs-lookup"><span data-stu-id="04029-107">If a project is configured to use the project deployment model, you use connection managers created at the project level to share connections, in place of using data sources.</span></span>  
>   
>  <span data-ttu-id="04029-108">配置モデルの詳細については、「 [Deployment of Projects and Packages](../packages/deploy-integration-services-ssis-projects-and-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04029-108">For more information about the deployment models, see [Deployment of Projects and Packages](../packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span> <span data-ttu-id="04029-109">プロジェクト配置モデルへのプロジェクトの変換の詳細については、「 [Integration Services サーバーへのプロジェクトの配置](../deploy-projects-to-integration-services-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04029-109">For more information about converting a project to the project deployment model, see [Deploy Projects to Integration Services Server](../deploy-projects-to-integration-services-server.md).</span></span>  
  
 <span data-ttu-id="04029-110">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージでデータ ソースを使用する場合、次の利点があります。</span><span class="sxs-lookup"><span data-stu-id="04029-110">The advantages of using data sources in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages include the following:</span></span>  
  
-   <span data-ttu-id="04029-111">データ ソースにはプロジェクト スコープがあるため、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクト内で作成されたデータ ソースは、そのプロジェクト内のすべてのパッケージで利用できます。</span><span class="sxs-lookup"><span data-stu-id="04029-111">A data source has project scope, which means that a data source created in an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project is available to all the packages in the project.</span></span> <span data-ttu-id="04029-112">データ ソースを一度定義すると、複数パッケージの接続マネージャーで参照できます。</span><span class="sxs-lookup"><span data-stu-id="04029-112">A data source can be defined one time and then referenced by connection managers in multiple packages.</span></span>  
  
-   <span data-ttu-id="04029-113">データ ソースは、データ ソース オブジェクトと、そのパッケージ参照との間を同期します。</span><span class="sxs-lookup"><span data-stu-id="04029-113">A data source offers synchronization between the data source object and its package references.</span></span> <span data-ttu-id="04029-114">データ ソースとそのデータ ソースを参照するパッケージが同じプロジェクトに存在する場合、データ ソース参照の接続文字列のプロパティは、データ ソースが変更されるときに自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="04029-114">If the data source and the packages that reference it reside in the same project, the connection string property of the data source references is automatically updated when the data source changes.</span></span>  
  
## <a name="reference-data-sources"></a><span data-ttu-id="04029-115">データ ソースを参照する</span><span class="sxs-lookup"><span data-stu-id="04029-115">Reference Data Sources</span></span>  
 <span data-ttu-id="04029-116">データ ソース オブジェクトを [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトに追加するには、 **ソリューション エクスプローラー** で **[データ ソース]** フォルダーを右クリックし、 **[新しいデータ ソース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="04029-116">To add a data source object to an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project, right-click the **Data Sources** folder in **Solution Explorer** and then click **New Data Source**.</span></span> <span data-ttu-id="04029-117">アイテムが **[データ ソース]** フォルダーに追加されます。</span><span class="sxs-lookup"><span data-stu-id="04029-117">The item is added to the **Data Sources** folder.</span></span> <span data-ttu-id="04029-118">別のプロジェクトで作成されたデータ ソース オブジェクトを使用する場合は、まず、そのデータ ソース オブジェクトをプロジェクトに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04029-118">If you want to use data source objects that were created in other projects, you must first add them to the project.</span></span>  
  
 <span data-ttu-id="04029-119">パッケージ内でデータ ソース オブジェクトを使用するには、そのデータ ソース オブジェクトを参照する接続マネージャーをパッケージに追加します。</span><span class="sxs-lookup"><span data-stu-id="04029-119">You use a data source object in a package by adding a connection manager that references the data source object to the package.</span></span> <span data-ttu-id="04029-120">パッケージ制御フローおよびデータ フローを構築する前に接続マネージャーをパッケージに追加するか、制御フローまたはデータ フローを構築する手順の中で接続マネージャーを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="04029-120">You can add it to the package before you build the package control flow and data flows, or as a step in constructing the control flow or data flow.</span></span>  
  
 <span data-ttu-id="04029-121">データ ソース オブジェクトはデータ ソースへの単純な接続を表し、参照するデータ ストア内のオブジェクトへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="04029-121">A data source object represents a simple connection to a data source and provides access to the objects in the data store that it references.</span></span> <span data-ttu-id="04029-122">たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の AdventureWorks サンプル データベースに接続するデータ ソース オブジェクトには、データベースにある 60 のテーブルすべてが含まれます。</span><span class="sxs-lookup"><span data-stu-id="04029-122">For example, a data source object that connects to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]AdventureWorks Sample Database includes all 60 tables from the database.</span></span>  
  
 <span data-ttu-id="04029-123">データ ソースと、そのデータ ソースを参照する接続マネージャーとの間に、依存関係はありません。</span><span class="sxs-lookup"><span data-stu-id="04029-123">There is no dependency between a data source and the connection managers that reference it.</span></span> <span data-ttu-id="04029-124">データ ソースがプロジェクトの一部ではなくなった場合でも、パッケージは引き続き有効です。接続の種類や接続文字列などのデータ ソースに関する情報は、パッケージ定義に含まれているためです。</span><span class="sxs-lookup"><span data-stu-id="04029-124">If a data source is no longer part of the project, the packages continue to be valid, because information about the data source, such as its connection type and connection string, is included in the package definition.</span></span>  
  
  
