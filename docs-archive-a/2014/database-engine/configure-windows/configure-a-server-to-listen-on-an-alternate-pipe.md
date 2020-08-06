---
title: 代替パイプをリッスンするようにサーバーを構成する (SQL Server 構成マネージャー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Named Pipes [SQL Server], configuring
- listening [SQL Server], pipes
- pipes [SQL Server], alternate
- alternate pipes [SQL Server]
ms.assetid: 914f7491-e2be-4b0d-b3aa-fe5409cdbafa
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 57d70cf4cd1d7474b895aeb8cb144c885e8a0f99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632104"
---
# <a name="configure-a-server-to-listen-on-an-alternate-pipe-sql-server-configuration-manager"></a><span data-ttu-id="85853-102">代替パイプをリッスンするサーバーの構成 (SQL Server 構成マネージャー)</span><span class="sxs-lookup"><span data-stu-id="85853-102">Configure a Server to Listen on an Alternate Pipe (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="85853-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で SQL Server 構成マネージャーを使用して、代替パイプをリッスンするようにサーバーを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="85853-103">This topic describes how to configure a server to listen on an alternate pipe in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="85853-104">既定では、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] の既定のインスタンスは、名前付きパイプ \\\\.\pipe\sql\query をリッスンします。</span><span class="sxs-lookup"><span data-stu-id="85853-104">By default, the default instance of [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] listens on named pipe \\\\.\pipe\sql\query.</span></span> <span data-ttu-id="85853-105">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] および [!INCLUDE[ssEW](../../includes/ssew-md.md)] の名前付きインスタンスは、他のパイプをリッスンします。</span><span class="sxs-lookup"><span data-stu-id="85853-105">Named instances of [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and [!INCLUDE[ssEW](../../includes/ssew-md.md)] listen on other pipes.</span></span>  
  
 <span data-ttu-id="85853-106">クライアント アプリケーションを使用して特定の名前付きパイプに接続するには、次の 3 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="85853-106">There are three ways to connect to a specific named pipe with a client application:</span></span>  
  
-   <span data-ttu-id="85853-107">サーバーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスを実行します。</span><span class="sxs-lookup"><span data-stu-id="85853-107">Run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service on the server.</span></span>  
  
-   <span data-ttu-id="85853-108">クライアントで、名前付きパイプを指定して別名を作成します。</span><span class="sxs-lookup"><span data-stu-id="85853-108">Create an alias on the client, specifying the named pipe.</span></span>  
  
-   <span data-ttu-id="85853-109">クライアントで、カスタム接続文字列を使用して接続するように指定します。</span><span class="sxs-lookup"><span data-stu-id="85853-109">Program the client to connect using a custom connection string.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="85853-110">SQL Server 構成マネージャーの使用</span><span class="sxs-lookup"><span data-stu-id="85853-110">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-configure-the-named-pipe-used-by-the-sql-server-database-engine"></a><span data-ttu-id="85853-111">SQL Server データベース エンジンによって使用される名前付きパイプを構成するには</span><span class="sxs-lookup"><span data-stu-id="85853-111">To configure the named pipe used by the SQL Server Database Engine</span></span>  
  
1.  <span data-ttu-id="85853-112">SQL Server 構成マネージャーのコンソール ペインで、 **[SQL Server ネットワークの構成]** を展開し、 **[** *\<instance name> のプロトコル]* を展開します。</span><span class="sxs-lookup"><span data-stu-id="85853-112">In SQL Server Configuration Manager, in the console pane, expand **SQL Server Network Configuration**, and then click expand **Protocols for** *\<instance name>*.</span></span>  
  
2.  <span data-ttu-id="85853-113">詳細ペインで **[名前付きパイプ]** を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="85853-113">In the details pane, right-click **Named Pipes**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="85853-114">**[プロトコル]** タブで、 **[パイプ名]** ボックスに [!INCLUDE[ssDE](../../includes/ssde-md.md)] によってリッスンされるパイプを入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="85853-114">On the **Protocol** tab, in the **Pipe Name** box, type the pipe you want the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to listen on, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="85853-115">コンソール ペインで、 **[再起動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="85853-115">In the console pane, click **SQL Server Services**.</span></span>  
  
5.  <span data-ttu-id="85853-116">詳細ペインで、 **[SQL Server (** \<instance name> **)]** を右クリックします。 **[再起動]** をクリックして、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を停止し、再起動します。</span><span class="sxs-lookup"><span data-stu-id="85853-116">In the details pane, right-click **SQL Server (**\<instance name>**)** and then click **Restart**, to stop and restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="85853-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が代替パイプをリッスンしている場合、クライアント アプリケーションを使用して特定の名前付きパイプに接続するには次の 3 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="85853-117">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is listening on an alternate pipe, there are three ways to connect to a specific named pipe with a client application:</span></span>  
  
-   <span data-ttu-id="85853-118">サーバーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスを実行します。</span><span class="sxs-lookup"><span data-stu-id="85853-118">Run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service on the server.</span></span>  
  
-   <span data-ttu-id="85853-119">クライアントで、名前付きパイプを指定して別名を作成します。</span><span class="sxs-lookup"><span data-stu-id="85853-119">Create an alias on the client, specifying the named pipe.</span></span>  
  
-   <span data-ttu-id="85853-120">クライアントで、カスタム接続文字列を使用して接続するように指定します。</span><span class="sxs-lookup"><span data-stu-id="85853-120">Program the client to connect using a custom connection string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85853-121">参照</span><span class="sxs-lookup"><span data-stu-id="85853-121">See Also</span></span>  
 <span data-ttu-id="85853-122">[クライアントが使用するサーバーの別名の作成または削除 &#40;SQL Server 構成マネージャー&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md) </span><span class="sxs-lookup"><span data-stu-id="85853-122">[Create or Delete a Server Alias for Use by a Client &#40;SQL Server Configuration Manager&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md) </span></span>  
 [<span data-ttu-id="85853-123">サーバー ネットワークの構成</span><span class="sxs-lookup"><span data-stu-id="85853-123">Server Network Configuration</span></span>](server-network-configuration.md)  
  
  
