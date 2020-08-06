---
title: WMI 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], WMI
- connection managers [Integration Services], WMI
- WMI connection manager [Integration Services]
ms.assetid: fbfa4ba7-3d0d-4d6b-94ad-50741a88d03d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f15aefb0ed112f1d5b7bb05421750b6689a11339
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641825"
---
# <a name="wmi-connection-manager"></a><span data-ttu-id="fc61c-102">WMI 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="fc61c-102">WMI Connection Manager</span></span>
  <span data-ttu-id="fc61c-103">WMI 接続マネージャーを使用すると、パッケージは Windows Management Instrumentation (WMI) を使用して、企業環境の情報を管理できます。</span><span class="sxs-lookup"><span data-stu-id="fc61c-103">A WMI connection manager enables a package to use Windows Management Instrumentation (WMI) to manage information in an enterprise environment.</span></span> <span data-ttu-id="fc61c-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に含まれる Web サービス タスクでは、WMI 接続マネージャーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="fc61c-104">The Web Service task that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes uses a WMI connection manager.</span></span>  
  
 <span data-ttu-id="fc61c-105">WMI 接続マネージャーをパッケージに追加すると、は、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 実行時に wmi 接続を解決する接続マネージャーを作成し、接続マネージャーのプロパティを設定して、接続マネージャーをパッケージのコレクションに追加し `Connections` ます。</span><span class="sxs-lookup"><span data-stu-id="fc61c-105">When you add a WMI connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to a WMI connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span> <span data-ttu-id="fc61c-106">接続マネージャーの `ConnectionManagerType` プロパティは、`WMI` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="fc61c-106">The `ConnectionManagerType` property of the connection manager is set to `WMI`.</span></span>  
  
## <a name="configuration-of-the-wmi-connection-manager"></a><span data-ttu-id="fc61c-107">WMI 接続マネージャーの構成</span><span class="sxs-lookup"><span data-stu-id="fc61c-107">Configuration of the WMI Connection Manager</span></span>  
 <span data-ttu-id="fc61c-108">WMI 接続マネージャーは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="fc61c-108">You can configure a WMI connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="fc61c-109">サーバーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="fc61c-109">Specify the name of a server.</span></span>  
  
-   <span data-ttu-id="fc61c-110">サーバー上の名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="fc61c-110">Specify a namespace on the server.</span></span>  
  
-   <span data-ttu-id="fc61c-111">サーバーに接続する認証モードを選択します。</span><span class="sxs-lookup"><span data-stu-id="fc61c-111">Select the authentication mode for connecting to the server.</span></span>  
  
 <span data-ttu-id="fc61c-112">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="fc61c-112">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="fc61c-113">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティについては、「 [[WMI 接続マネージャー エディター]](../wmi-connection-manager-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc61c-113">For information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [WMI Connection Manager Editor](../wmi-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="fc61c-114">プログラムによる接続マネージャーの構成については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」と「 [プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)に設定されます。</span><span class="sxs-lookup"><span data-stu-id="fc61c-114">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc61c-115">参照</span><span class="sxs-lookup"><span data-stu-id="fc61c-115">See Also</span></span>  
 <span data-ttu-id="fc61c-116">[Web サービスタスク](../control-flow/web-service-task.md) </span><span class="sxs-lookup"><span data-stu-id="fc61c-116">[Web Service Task](../control-flow/web-service-task.md) </span></span>  
 [<span data-ttu-id="fc61c-117">Integration Services &#40;SSIS&#41; の接続</span><span class="sxs-lookup"><span data-stu-id="fc61c-117">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
