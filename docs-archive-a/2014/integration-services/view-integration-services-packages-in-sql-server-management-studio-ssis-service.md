---
title: SQL Server Management Studio で Integration Services パッケージを表示する (SSIS サービス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- viewing packages
- connections [Integration Services], packages
ms.assetid: 783e653c-0f1f-45ed-b3ef-5ba07b019f27
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4ba86320f1b1a685eab6e80399f3e8c21bd110eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712122"
---
# <a name="view-integration-services-packages-in-sql-server-management-studio-ssis-service"></a><span data-ttu-id="52a43-102">SQL Server Management Studio で Integration Services パッケージを表示する (SSIS サービス)</span><span class="sxs-lookup"><span data-stu-id="52a43-102">View Integration Services Packages in SQL Server Management Studio (SSIS Service)</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="52a43-103">このトピックでは、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを管理するための Windows サービスである [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="52a43-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="52a43-104">では、以前のリリースの [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]との互換性を維持するために、このサービスをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="52a43-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="52a43-105">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]以降では、Integration Services サーバー上のパッケージなどのオブジェクトを管理できます。</span><span class="sxs-lookup"><span data-stu-id="52a43-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 <span data-ttu-id="52a43-106">この手順では、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] で [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] に接続して、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスが管理するパッケージの一覧を表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="52a43-106">This procedure describes how to connect to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and view a list of the packages that the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service manages.</span></span>  
  
### <a name="to-connect-to-integration-services"></a><span data-ttu-id="52a43-107">Integration Services に接続するには</span><span class="sxs-lookup"><span data-stu-id="52a43-107">To connect to Integration Services</span></span>  
  
1.  <span data-ttu-id="52a43-108">**[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、 **[Microsoft SQL Server]** の順にポイントし、 **[SQL Server Management Studio]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52a43-108">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="52a43-109">**[サーバーへの接続]** ダイアログ ボックスで、 **[サーバーの種類]** 一覧の **[Integration Services]** を選択し、 **[サーバー名]** ボックスにサーバー名を入力して **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52a43-109">In the **Connect to Server** dialog box, select **Integration Services** in the **Server type** list, provide a server name in the **Server name** box, and then click **Connect**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="52a43-110">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]に接続できない場合は、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスが実行されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="52a43-110">If you cannot connect to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is likely not running.</span></span> <span data-ttu-id="52a43-111">このサービスの状態を調べるには、 **[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、 **[Microsoft SQL Server]** 、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52a43-111">To learn the status of the service, click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span> <span data-ttu-id="52a43-112">左ペインで、 **[SQL Server のサービス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52a43-112">In the left pane, click **SQL Server Services**.</span></span> <span data-ttu-id="52a43-113">右ペインで、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスを見つけます。</span><span class="sxs-lookup"><span data-stu-id="52a43-113">In the right pane, find the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="52a43-114">サービスがまだ実行されていない場合は開始します。</span><span class="sxs-lookup"><span data-stu-id="52a43-114">Start the service if it is not already running.</span></span>  
  
     [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="52a43-115">が開きます。</span><span class="sxs-lookup"><span data-stu-id="52a43-115">opens.</span></span> <span data-ttu-id="52a43-116">既定では、Management Studio の左下隅にオブジェクト エクスプローラーが開きます。</span><span class="sxs-lookup"><span data-stu-id="52a43-116">By default the Object Explorer window is open and positioned in the lower-left corner of the studio.</span></span> <span data-ttu-id="52a43-117">オブジェクト エクスプローラーが開いていない場合は、 **[表示]** メニューの **[オブジェクト エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52a43-117">If Object Explorer is not open, click **Object Explorer** on the **View** menu.</span></span>  
  
### <a name="to-view-the-packages-that-integration-services-service-manages"></a><span data-ttu-id="52a43-118">Integration Services サービスが管理するパッケージを表示するには</span><span class="sxs-lookup"><span data-stu-id="52a43-118">To view the packages that Integration Services service manages</span></span>  
  
1.  <span data-ttu-id="52a43-119">オブジェクト エクスプローラーで、[格納されたパッケージ] フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="52a43-119">In Object Explorer, expand the Stored Packages folder.</span></span>  
  
2.  <span data-ttu-id="52a43-120">[格納されたパッケージ] サブフォルダーを展開して、パッケージを表示します。</span><span class="sxs-lookup"><span data-stu-id="52a43-120">Expand the Stored Packages subfolders to show packages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52a43-121">参照</span><span class="sxs-lookup"><span data-stu-id="52a43-121">See Also</span></span>  
 <span data-ttu-id="52a43-122">[SSIS サービス&#41;の Package Management &#40;](service/package-management-ssis-service.md) </span><span class="sxs-lookup"><span data-stu-id="52a43-122">[Package Management &#40;SSIS Service&#41;](service/package-management-ssis-service.md) </span></span>  
 <span data-ttu-id="52a43-123">[SQL Server Management Studio の使用 [SQL Server]](../database-engine/use-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="52a43-123">[Use SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md)</span></span>  
  
  
