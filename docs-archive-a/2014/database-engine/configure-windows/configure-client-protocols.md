---
title: クライアント プロトコルの構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default protocols
- network protocols [SQL Server], client configuration
- TCP/IP [SQL Server], client protocols
- disabling client protocols
- ordering protocols [SQL Server]
- protocols [SQL Server], order for client computers
- configure client protocols
- client protocols [SQL Server]
- protocols [SQL Server], client configuration
ms.assetid: 3dfa2702-ba65-43b4-a777-6727846e133a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2eb223815c3e3af50813e02d3ded60573c327155
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645858"
---
# <a name="configure-client-protocols"></a><span data-ttu-id="69502-102">クライアント プロトコルの構成</span><span class="sxs-lookup"><span data-stu-id="69502-102">Configure Client Protocols</span></span>
  <span data-ttu-id="69502-103">このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 構成マネージャーを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でクライアント アプリケーションによって使用されるクライアント プロトコルを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="69502-103">This topic describes how to configure client protocols used by client applications in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="69502-104">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、TCP/IP ネットワーク プロトコルおよび名前付きパイプ プロトコルを介したクライアント通信をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="69502-104">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supports client communication with the TCP/IP network protocol and the named pipes protocol.</span></span> <span data-ttu-id="69502-105">クライアントが、同じコンピューター上で[!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続している場合は、共有メモリ プロトコルも使用できます。</span><span class="sxs-lookup"><span data-stu-id="69502-105">The shared memory protocol is also available if the client is connecting to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on the same computer.</span></span> <span data-ttu-id="69502-106">プロトコルの選択には、3 つの一般的な方法があります。</span><span class="sxs-lookup"><span data-stu-id="69502-106">There are three common methods of selecting the protocol.</span></span>  
  
-   <span data-ttu-id="69502-107">すべてのクライアント アプリケーションを、同じネットワーク プロトコルを使用するように構成します。これを行うには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーでプロトコルの順序を設定します。</span><span class="sxs-lookup"><span data-stu-id="69502-107">Configure all client applications to use the same network protocol by setting the protocol order in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
-   <span data-ttu-id="69502-108">1 つのクライアント アプリケーションを、異なるネットワーク プロトコルを使用するように構成します。これを行うには、別名を作成します。</span><span class="sxs-lookup"><span data-stu-id="69502-108">Configure a single client application to use a different network protocol by creating an alias.</span></span> <span data-ttu-id="69502-109">詳細については、「[クライアントが使用するサーバーの別名の作成または削除 &#40;SQL Server 構成マネージャー&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69502-109">For more information, see [Create or Delete a Server Alias for Use by a Client &#40;SQL Server Configuration Manager&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md).</span></span>  
  
-   <span data-ttu-id="69502-110">sqlcmd.exe など、一部のクライアント アプリケーションでは、接続文字列の一部としてプロトコルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="69502-110">Some client applications, such as sqlcmd.exe, can specify the protocol as part of the connection string.</span></span> <span data-ttu-id="69502-111">詳細については、「[sqlcmd によるデータベース エンジンへの接続](../../relational-databases/scripting/sqlcmd-connect-to-the-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69502-111">For more information, see [Connect to the Database Engine With sqlcmd](../../relational-databases/scripting/sqlcmd-connect-to-the-database-engine.md).</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="69502-112">SQL Server 構成マネージャーの使用</span><span class="sxs-lookup"><span data-stu-id="69502-112">Using SQL Server Configuration Manager</span></span>  
  
###  <a name="to-enable-or-disable-a-client-protocol"></a><a name="EnableDisable"></a> <span data-ttu-id="69502-113">クライアント プロトコルを有効または無効にするには</span><span class="sxs-lookup"><span data-stu-id="69502-113">To enable or disable a client protocol</span></span>  
  
1.  <span data-ttu-id="69502-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーで、 **[SQL Server Native Client の構成]** を展開し、 **[クライアント プロトコル]** を右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="69502-114">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, expand **SQL Server Native Client Configuration**, right-click **Client Protocols**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="69502-115">プロトコルを有効にするには、 **[無効なプロトコル]** ボックスでプロトコルをクリックし、 **[有効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="69502-115">Click a protocol in the **Disabled Protocols** box, and then click **Enable**, to enable a protocol.</span></span>  
  
3.  <span data-ttu-id="69502-116">プロトコルを無効にするには、 **[有効なプロトコル]** ボックスでプロトコルをクリックし、 **[無効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="69502-116">Click a protocol in the **Enabled Protocols** box, and then click **Disable**, to disable a protocol.</span></span>  
  
###  <a name="to-change-the-default-protocol-or-the-protocol-order-for-client-computers"></a><a name="ChangeDefault"></a> <span data-ttu-id="69502-117">既定のプロトコル、またはクライアント コンピューターのプロトコルの順序を変更するには</span><span class="sxs-lookup"><span data-stu-id="69502-117">To change the default protocol or the protocol order for client computers</span></span>  
  
1.  <span data-ttu-id="69502-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーで、 **[SQL Server Native Client の構成]** を展開し、 **[クライアント プロトコル]** を右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="69502-118">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, expand **SQL Server Native Client Configuration**, right-click **Client Protocols**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="69502-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続するときに試行されるプロトコルの順序を変更するには、 **[有効なプロトコル]** ボックスで、**上へ移動**ボタンまたは**下へ移動**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="69502-119">In the **Enabled Protocols** box, click **Move Up** or **Move Down**, to change the order in which protocols are tried, when attempting to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="69502-120">**[有効なプロトコル]** ボックスの最上部に表示されているプロトコルが既定のプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="69502-120">The top protocol in the **Enabled Protocols** box is the default protocol.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="69502-121">構成マネージャーにより、サーバーの別名の構成や既定のクライアント ネットワーク ライブラリのレジストリ エントリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="69502-121">Configuration Manager creates registry entries for the server alias configurations and default client network library.</span></span> <span data-ttu-id="69502-122">ただし、このアプリケーションでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアント ネットワーク ライブラリもネットワーク プロトコルもインストールされません。</span><span class="sxs-lookup"><span data-stu-id="69502-122">However, the application does not install either the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client network libraries or the network protocols.</span></span> <span data-ttu-id="69502-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアント ネットワーク ライブラリは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ中にインストールされます。また、ネットワーク プロトコルは、Microsoft Windows セットアップの一部として (または**コントロール パネル**の **[ネットワーク接続]** を使用して) インストールされます。</span><span class="sxs-lookup"><span data-stu-id="69502-123">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client network libraries are installed during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup; the network protocols are installed as part of Microsoft Windows Setup (or through **Networks** in **Control Panel**).</span></span> <span data-ttu-id="69502-124">特定のネットワーク プロトコルは、Windows のセットアップ時にインストールされないことがあります。</span><span class="sxs-lookup"><span data-stu-id="69502-124">A particular network protocol may not be available as part of Windows Setup.</span></span> <span data-ttu-id="69502-125">そのようなネットワーク プロトコルのインストールの詳細については、製造元のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="69502-125">For more information about installing these network protocols, see the vendor documentation.</span></span>  
  
###  <a name="to-configure-a-client-to-use-tcpip"></a><a name="Configure"></a> <span data-ttu-id="69502-126">TCP/IP を使用するようにクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="69502-126">To configure a client to use TCP/IP</span></span>  
  
1.  <span data-ttu-id="69502-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーで、 **[SQL Server Native Client の構成]** を展開し、 **[クライアント プロトコル]** を右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="69502-127">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, expand **SQL Server Native Client Configuration**, right-click **Client Protocols**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="69502-128">**[有効なプロトコル]** ボックスで上矢印と下矢印をクリックして、SQL Server への接続を試行する際のプロトコルの試行順序を変更します。</span><span class="sxs-lookup"><span data-stu-id="69502-128">In the **Enabled Protocols** box, click the up and down arrows to change the order in which protocols are tried, when attempting to connect to SQL Server.</span></span> <span data-ttu-id="69502-129">**[有効なプロトコル]** ボックスの最上部に表示されているプロトコルが既定のプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="69502-129">The top protocol in the **Enabled Protocols** box is the default protocol.</span></span>  
  
 <span data-ttu-id="69502-130">共有メモリ プロトコルは、 **[共有メモリ プロトコルを有効にする]** チェック ボックスをオンにすることで、別個に有効にします。</span><span class="sxs-lookup"><span data-stu-id="69502-130">The shared memory protocol is enabled separately by checking the **Enabled Shared Memory Protocol** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69502-131">参照</span><span class="sxs-lookup"><span data-stu-id="69502-131">See Also</span></span>  
 [<span data-ttu-id="69502-132">remote login timeout サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="69502-132">Configure the remote login timeout Server Configuration Option</span></span>](configure-the-remote-login-timeout-server-configuration-option.md)  
  
  
