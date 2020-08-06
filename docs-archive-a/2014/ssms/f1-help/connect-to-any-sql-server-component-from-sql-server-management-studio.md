---
title: SQL Server Management Studio | から任意の SQL Server コンポーネントに接続します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], SQL Server Management Studio
- saving connections
- components [SQL Server], connections
- SQL Server Management Studio [SQL Server], connections
ms.assetid: 5eeb41bd-b25b-4d3b-a005-a7d9e4b5978e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9cd3e185ea6f289a2a6db46cdca2cb310fefbcf9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717253"
---
# <a name="connect-to-any-sql-server-component-from-sql-server-management-studio"></a><span data-ttu-id="8aa53-102">SQL Server Management Studio から SQL Server コンポーネントへの接続</span><span class="sxs-lookup"><span data-stu-id="8aa53-102">Connect to Any SQL Server Component from SQL Server Management Studio</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="8aa53-103">には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の各コンポーネントを管理する機能があります。</span><span class="sxs-lookup"><span data-stu-id="8aa53-103">provides functionality for managing every component of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8aa53-104">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用して、以下のコンポーネントに接続します。</span><span class="sxs-lookup"><span data-stu-id="8aa53-104">Use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to connect to:</span></span>  
  
-   <span data-ttu-id="8aa53-105">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="8aa53-105">An instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="8aa53-106">[https://login.microsoftonline.com/consumers/]([!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)])</span><span class="sxs-lookup"><span data-stu-id="8aa53-106">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="8aa53-107">[https://login.microsoftonline.com/consumers/]([!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)])</span><span class="sxs-lookup"><span data-stu-id="8aa53-107">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="8aa53-108">[https://login.microsoftonline.com/consumers/]([!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)])</span><span class="sxs-lookup"><span data-stu-id="8aa53-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="8aa53-109">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] では、データ ソースへの接続を確立していなくてもクエリの編集は行えますが、他のほとんどのタスクの場合には接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="8aa53-109">Although [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] allows you to work with queries without first establishing a connection to a data source, most other tasks require a connection.</span></span> [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="8aa53-110">では **[サーバーへの接続]** ダイアログ ボックスを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントへの接続プロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="8aa53-110">provides the **Connect to Server** dialog box to configure connection properties to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span> <span data-ttu-id="8aa53-111">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] の起動時には **[サーバーへの接続]** ダイアログ ボックスが表示され、サーバーへの接続を求められます。</span><span class="sxs-lookup"><span data-stu-id="8aa53-111">When [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] starts, it opens the **Connect to Server** dialog box and prompts you to connect to a server.</span></span> <span data-ttu-id="8aa53-112">**[サーバーへの接続]** ダイアログ ボックスには最後に使用したときの接続設定が保持されます。</span><span class="sxs-lookup"><span data-stu-id="8aa53-112">The **Connect to Server** dialog box retains the connection settings from the last time it was used.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8aa53-113">この機能をオフにして、接続を自動的に開始しないようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="8aa53-113">This feature can be turned off so no connection is automatically initiated.</span></span> <span data-ttu-id="8aa53-114">詳細については、「 [データベース エンジン サービスのスタートアップ オプション](../../database-engine/configure-windows/database-engine-service-startup-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8aa53-114">For more information, see [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md).</span></span>  
  
## <a name="saving-connections"></a><span data-ttu-id="8aa53-115">接続の保存</span><span class="sxs-lookup"><span data-stu-id="8aa53-115">Saving Connections</span></span>  
 <span data-ttu-id="8aa53-116">登録済みサーバーで特定のサーバーへの接続を保存することや、ソリューション エクスプローラーでプロジェクトの接続を保存することができます。</span><span class="sxs-lookup"><span data-stu-id="8aa53-116">You can save connections to specific servers in Registered Servers, or you can save connections in projects with Solution Explorer.</span></span>  
  
### <a name="saving-connections-in-registered-servers"></a><span data-ttu-id="8aa53-117">登録済みサーバーでの接続の保存</span><span class="sxs-lookup"><span data-stu-id="8aa53-117">Saving Connections in Registered Servers</span></span>  
 <span data-ttu-id="8aa53-118">サーバーを登録すると、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] によって [登録済みサーバー] に接続情報が保存されます。</span><span class="sxs-lookup"><span data-stu-id="8aa53-118">When you register a server, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] saves the connection information in Registered Servers.</span></span> <span data-ttu-id="8aa53-119">登録済みサーバーに接続するには、[登録済みサーバー] 内のサーバー名をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="8aa53-119">To connect to a registered server, double-click the server name in Registered Servers.</span></span> <span data-ttu-id="8aa53-120">サーバーへの接続が行われ、オブジェクト エクスプローラーにそのサーバーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8aa53-120">Object Explorer then opens a connection to the server.</span></span>  
  
### <a name="saving-connections-in-solution-explorer"></a><span data-ttu-id="8aa53-121">ソリューション エクスプローラーでの接続の保存</span><span class="sxs-lookup"><span data-stu-id="8aa53-121">Saving Connections in Solution Explorer</span></span>  
 <span data-ttu-id="8aa53-122">ソリューション エクスプローラーでは、プロジェクト内に、関連するクエリ、スクリプト、接続、その他の関連情報を格納することができます。</span><span class="sxs-lookup"><span data-stu-id="8aa53-122">Solution Explorer allows you to store related queries, scripts, connections, and other associated information in a project.</span></span> <span data-ttu-id="8aa53-123">スクリプト プロジェクトには **[接続]** というノードがあり、ここに 1 つ以上の接続を保存できます。</span><span class="sxs-lookup"><span data-stu-id="8aa53-123">Each script project contains a node called **Connections**, where you can save one or more connections.</span></span> <span data-ttu-id="8aa53-124">接続を追加するには、 **[接続]** を右クリックして、 **[新しい接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8aa53-124">To add a connection, right-click **Connections**, and then click **New Connection**.</span></span> <span data-ttu-id="8aa53-125">保存した接続にアクセスするには、 **[接続]** を展開して対象の接続をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="8aa53-125">To access a saved connection, expand **Connections** and double-click the connection.</span></span> [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="8aa53-126">によって、その接続に関連付けられたクエリ ウィンドウが開かれます。</span><span class="sxs-lookup"><span data-stu-id="8aa53-126">opens a query window associated with that connection.</span></span> <span data-ttu-id="8aa53-127">スクリプトを保存すると、そのスクリプトには特定の接続との関連が保持されます。</span><span class="sxs-lookup"><span data-stu-id="8aa53-127">When saved, scripts retain their association to a specific connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aa53-128">参照</span><span class="sxs-lookup"><span data-stu-id="8aa53-128">See Also</span></span>  
 <span data-ttu-id="8aa53-129">[SQL Server Management Studio を使用する](../sql-server-management-studio-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="8aa53-129">[Use SQL Server Management Studio](../sql-server-management-studio-ssms.md) </span></span>  
 <span data-ttu-id="8aa53-130">[[オブジェクト エクスプローラー]](../object/object-explorer.md)</span><span class="sxs-lookup"><span data-stu-id="8aa53-130">[Object Explorer](../object/object-explorer.md)</span></span>  
  
  
