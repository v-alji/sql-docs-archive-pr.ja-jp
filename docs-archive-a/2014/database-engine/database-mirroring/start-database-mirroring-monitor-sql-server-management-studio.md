---
title: データベース ミラーリング モニターの起動 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- monitoring database mirroring [SQL Server]
- Database Mirroring Monitor [SQL Server], starting
- database mirroring [SQL Server], monitoring
ms.assetid: 53165335-97ca-4f88-8e78-22f1839dee98
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 67c7b393b28d4d400535281c18c637146a5d8da7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631238"
---
# <a name="start-database-mirroring-monitor-sql-server-management-studio"></a><span data-ttu-id="f1ca4-102">データベース ミラーリング モニターの起動 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f1ca4-102">Start Database Mirroring Monitor (SQL Server Management Studio)</span></span>
  <span data-ttu-id="f1ca4-103">データベース ミラーリング モニターは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] モニターの一部であり、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]から起動します。</span><span class="sxs-lookup"><span data-stu-id="f1ca4-103">The Database Mirroring Monitor is part of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Monitor, which is launched from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f1ca4-104">データベース ミラーリング モニターは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="f1ca4-104">Database Mirroring Monitor is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f1ca4-105">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1ca4-105">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
### <a name="to-launch-the-database-mirroring-monitor"></a><span data-ttu-id="f1ca4-106">データベース ミラーリング モニターを起動するには</span><span class="sxs-lookup"><span data-stu-id="f1ca4-106">To launch the Database Mirroring Monitor</span></span>  
  
1.  <span data-ttu-id="f1ca4-107">プリンシパル サーバー インスタンスに接続した後、オブジェクト エクスプローラーでサーバー名をクリックして、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="f1ca4-107">After connecting to the principal server instance, in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="f1ca4-108">**[データベース]** を展開し、監視するデータベースをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1ca4-108">Expand **Databases**, and select the database to be monitored.</span></span>  
  
3.  <span data-ttu-id="f1ca4-109">データベースを右クリックして **[タスク]** を選択し、 **[データベース ミラーリング モニターの起動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1ca4-109">Right-click the database, select **Tasks**, and then click **Launch Database Mirroring Monitor**.</span></span>  
  
4.  <span data-ttu-id="f1ca4-110">**[データベース ミラーリング モニター]** ダイアログ ボックスで、 **[ミラー化されたデータベースの登録]** をクリックして 1 つまたは複数のミラー化されたデータベースを登録します。</span><span class="sxs-lookup"><span data-stu-id="f1ca4-110">In the **Database Mirroring Monitor** dialog box, click **Register Mirrored Database** to register one or more mirrored database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f1ca4-111">1 つのパートナーにデータベースを登録すると、そのデータベースは他のパートナーにも自動的に登録されます。</span><span class="sxs-lookup"><span data-stu-id="f1ca4-111">When you register a database at one partner, the database is automatically registered at the other partner.</span></span> <span data-ttu-id="f1ca4-112">モニターに他のパートナー インスタンス用の接続資格情報が既にある場合は、その情報が接続時に使用されます。</span><span class="sxs-lookup"><span data-stu-id="f1ca4-112">If the monitor already has connection credentials for the other partner instance, those are used to connect.</span></span> <span data-ttu-id="f1ca4-113">そのような接続資格情報がない場合、モニターは Windows 認証を使用して接続を試行します。</span><span class="sxs-lookup"><span data-stu-id="f1ca4-113">Otherwise the monitor attempts to connect using Windows Authentication.</span></span> <span data-ttu-id="f1ca4-114">いずれかのサーバー インスタンスへの接続に使用している資格情報を変更する場合は、 **[[OK] をクリックしたときに [サーバー インスタンスの接続管理] ダイアログ ボックスを表示する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1ca4-114">If you want to change the credentials used to connect to either server instance, click **Show the Manage Server Connections dialog box when I click OK**.</span></span>  
  
 <span data-ttu-id="f1ca4-115">データベース ミラーリング モニターの詳細については、「 [データベース ミラーリング モニターの概要](database-mirroring-monitor-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1ca4-115">For more information about Database Mirroring Monitor, see [Database Mirroring Monitor Overview](database-mirroring-monitor-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1ca4-116">参照</span><span class="sxs-lookup"><span data-stu-id="f1ca4-116">See Also</span></span>  
 <span data-ttu-id="f1ca4-117">[データベース ミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f1ca4-117">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="f1ca4-118">Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="f1ca4-118">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
  
