---
title: SQL Server データベース エンジンのインスタンスの非表示 | Microsoft Docs
ms.custom: ''
ms.date: 08/19/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], hiding instances
- hiding instances of Database Engine
ms.assetid: 392de21a-57fa-4a69-8237-ced8ca86ed1d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d2b3287c5d4d747ccb3511461341d5aed8ff765d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713506"
---
# <a name="hide-an-instance-of-sql-server-database-engine"></a><span data-ttu-id="92649-102">SQL Server データベース エンジンのインスタンスの非表示</span><span class="sxs-lookup"><span data-stu-id="92649-102">Hide an Instance of SQL Server Database Engine</span></span>
  <span data-ttu-id="92649-103">このトピックでは、SQL Server 構成マネージャーを使用して [!INCLUDE[ssDE](../../includes/ssde-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインスタンスを非表示にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="92649-103">This topic describes how to hide an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="92649-104">では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスを使用して、コンピューターにインストールされている [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスを列挙します。</span><span class="sxs-lookup"><span data-stu-id="92649-104">uses the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service to enumerate instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] installed on the computer.</span></span> <span data-ttu-id="92649-105">この機能により、クライアント アプリケーションはサーバーを参照できるようになり、クライアントは、同じコンピューター上にある [!INCLUDE[ssDE](../../includes/ssde-md.md)] の複数のインスタンスを区別できるようになります。</span><span class="sxs-lookup"><span data-stu-id="92649-105">This enables client applications to browse for a server, and helps clients distinguish between multiple instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on the same computer.</span></span> <span data-ttu-id="92649-106">次の手順に従い、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [参照] **ボタンを使用してこの** インスタンスを表示しようとするクライアント コンピューターに対して、SQL Server Browser サービスがそのインスタンスを公開しないようにできます。</span><span class="sxs-lookup"><span data-stu-id="92649-106">You can use the following procedure to prevent the SQL Server Browser service from exposing an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to client computers that try to locate the instance by using the **Browse** button.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="92649-107">SQL Server 構成マネージャーの使用</span><span class="sxs-lookup"><span data-stu-id="92649-107">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-hide-an-instance-of-the-sql-server-database-engine"></a><span data-ttu-id="92649-108">SQL Server データベース エンジンのインスタンスを非表示にするには</span><span class="sxs-lookup"><span data-stu-id="92649-108">To hide an instance of the SQL Server Database Engine</span></span>  
  
1.  <span data-ttu-id="92649-109">**SQL Server 構成マネージャー**で、 **[SQL Server ネットワークの構成]** を展開し、 **[** *\<server instance> のプロトコル]* を右クリックして、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="92649-109">In **SQL Server Configuration Manager**, expand **SQL Server Network Configuration**, right-click **Protocols for** *\<server instance>*, and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="92649-110">**[フラグ]** タブで **[HideInstance]** ボックスの一覧の **[はい]** を選択し、 **[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="92649-110">On the **Flags** tab, in the **HideInstance** box, select **Yes**, and then click **OK** to close the dialog box.</span></span> <span data-ttu-id="92649-111">この変更は、新しい接続ですぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="92649-111">The change takes effect immediately for new connections.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92649-112">解説</span><span class="sxs-lookup"><span data-stu-id="92649-112">Remarks</span></span>  
 <span data-ttu-id="92649-113">名前付きインスタンスを非表示にする場合、ブラウザー サービスが実行中でも、非表示のインスタンスに接続するための接続文字列でポート番号を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="92649-113">If you hide a named instance, you will need to provide the port number in the connection string to connect to the hidden instance, even if the browser service is running.</span></span> <span data-ttu-id="92649-114">名前付きの非表示のインスタンスに対しては、動的ポートではなく静的ポートを利用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="92649-114">We recommend that you use a static port instead of a dynamic port for the named hidden instance.</span></span>  
  <span data-ttu-id="92649-115">詳細については、「[特定の TCP ポートで受信待ちするようにサーバーを構成する方法 &#40;SQL Server 構成マネージャー&#41;](configure-a-server-to-listen-on-a-specific-tcp-port.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92649-115">For more information, see [Configure a Server to Listen on a Specific TCP Port &#40;SQL Server Configuration Manager&#41;](configure-a-server-to-listen-on-a-specific-tcp-port.md).</span></span>  
  
### <a name="clustering"></a><span data-ttu-id="92649-116">クラスタリング</span><span class="sxs-lookup"><span data-stu-id="92649-116">Clustering</span></span>  
 <span data-ttu-id="92649-117">クラスター化された名前付きインスタンスを非表示にすると、クラスター サービスは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に接続できないことがあります。</span><span class="sxs-lookup"><span data-stu-id="92649-117">If you hide a clustered named instance, cluster service may not be able to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="92649-118">これにより、クラスター インスタンスの **IsAlive** のチェックが失敗し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がオフラインになります。</span><span class="sxs-lookup"><span data-stu-id="92649-118">This will cause the cluster instance's **IsAlive** check to fail and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will go offline.</span></span> <span data-ttu-id="92649-119">インスタンス用に構成した静的ポートを反映するように、クラスター化されたインスタンスのすべてのノードで別名を作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="92649-119">We recommend that you create an alias in all the nodes of the clustered instance to reflect the static port that you configured for the instance.</span></span>  
 <span data-ttu-id="92649-120">詳細については、「[クライアントが使用するサーバーの別名の作成または削除 &#40;SQL Server 構成マネージャー&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92649-120">For more information, see [Create or Delete a Server Alias for Use by a Client &#40;SQL Server Configuration Manager&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md).</span></span>  
  
 <span data-ttu-id="92649-121">クラスター化された名前付きインスタンスを非表示にすると、**LastConnect** レジストリ キー (**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SNI11.0\LastConnect**) のポートが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のリッスンしているポートと異なる場合、クラスター サービスは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続できなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="92649-121">If you hide a clustered named instance, cluster service may not be able to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] if the **LastConnect** registry key (**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SNI11.0\LastConnect**) has a different port than the port that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is listening on.</span></span> <span data-ttu-id="92649-122">クラスター サービスが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に接続できない場合、次のようなエラーが表示されることがあります:</span><span class="sxs-lookup"><span data-stu-id="92649-122">If the cluster service is unable to make a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you might see an error similar to the following:</span></span>  
<span data-ttu-id="92649-123">**イベント ID:1001:イベント名:フェールオーバー クラスタリング リソース デッドロック。**</span><span class="sxs-lookup"><span data-stu-id="92649-123">**Event ID: 1001: Event Name: Failover clustering resource deadlock.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92649-124">参照</span><span class="sxs-lookup"><span data-stu-id="92649-124">See Also</span></span>  
 <span data-ttu-id="92649-125">[サーバー ネットワークの構成](server-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="92649-125">[Server Network Configuration](server-network-configuration.md) </span></span>  
 <span data-ttu-id="92649-126">[SQL 仮想サーバーのクライアント接続の説明](https://support.microsoft.com/kb/273673) </span><span class="sxs-lookup"><span data-stu-id="92649-126">[Description of SQL Virtual Server client connections](https://support.microsoft.com/kb/273673) </span></span>  
 [<span data-ttu-id="92649-127">SQL Server 名前付きインスタンスに静的ポートを割り当て、一般的な落とし穴を回避する方法</span><span class="sxs-lookup"><span data-stu-id="92649-127">How to assign a static port to a SQL Server named instance - and avoid a common pitfall</span></span>](https://blogs.msdn.com/b/arvindsh/archive/2012/09/08/how-to-assign-a-static-port-to-a-sql-server-named-instance-and-avoid-a-common-pitfall.aspx)  
  
  
