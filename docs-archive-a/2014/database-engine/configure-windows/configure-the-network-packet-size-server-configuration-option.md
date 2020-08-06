---
title: network packet size サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default packet size
- size [SQL Server], packets
- packets [SQL Server], size
- network packet size option
ms.assetid: 236985bf-fc4a-4a57-98f7-a71ef977fd7b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 69e5963675349bceff6a0ee022f6dc28da03db59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715694"
---
# <a name="configure-the-network-packet-size-server-configuration-option"></a><span data-ttu-id="fca41-102">network packet size サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="fca41-102">Configure the network packet size Server Configuration Option</span></span>
  <span data-ttu-id="fca41-103">このトピック `network packet size` で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、またはを使用して、のサーバー構成オプションを構成する方法について説明し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="fca41-103">This topic describes how to configure the `network packet size` server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="fca41-104">オプションは、 `network packet size` ネットワーク全体で使用されるパケットサイズ (バイト単位) を設定します。</span><span class="sxs-lookup"><span data-stu-id="fca41-104">The `network packet size` option sets the packet size (in bytes) that is used across the whole network.</span></span> <span data-ttu-id="fca41-105">パケットとは、固定サイズのデータのチャンクで、クライアントとサーバー間で要求および結果を転送します。</span><span class="sxs-lookup"><span data-stu-id="fca41-105">Packets are the fixed-size chunks of data that transfer requests and results between clients and servers.</span></span> <span data-ttu-id="fca41-106">既定のパケット サイズは 4,096 バイトです。</span><span class="sxs-lookup"><span data-stu-id="fca41-106">The default packet size is 4,096 bytes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fca41-107">パフォーマンスの向上が明確でない限り、パケット サイズは変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="fca41-107">Do not change the packet size unless you are certain that it will improve performance.</span></span> <span data-ttu-id="fca41-108">多くのアプリケーションでは、既定のパケット サイズが最適です。</span><span class="sxs-lookup"><span data-stu-id="fca41-108">For most applications, the default packet size is best.</span></span>  
  
 <span data-ttu-id="fca41-109">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="fca41-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="fca41-110">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="fca41-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fca41-111">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="fca41-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="fca41-112">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="fca41-112">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="fca41-113">Security</span><span class="sxs-lookup"><span data-stu-id="fca41-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="fca41-114">**以下を使用して network packet size オプションを構成するには:**</span><span class="sxs-lookup"><span data-stu-id="fca41-114">**To configure the network packet size option, using:**</span></span>  
  
     [<span data-ttu-id="fca41-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fca41-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="fca41-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fca41-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="fca41-117">**補足情報:** [network packet size オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="fca41-117">**Follow Up:**  [After you configure the network packet size option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fca41-118">はじめに</span><span class="sxs-lookup"><span data-stu-id="fca41-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="fca41-119">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="fca41-119">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="fca41-120">暗号化された接続の最大ネットワーク パケット サイズは 16,383 バイトです。</span><span class="sxs-lookup"><span data-stu-id="fca41-120">The maximum network packet size for encrypted connections is 16,383 bytes.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="fca41-121">推奨事項</span><span class="sxs-lookup"><span data-stu-id="fca41-121">Recommendations</span></span>  
  
-   <span data-ttu-id="fca41-122">このオプションは詳細設定オプションであるため、熟練したデータベース管理者または認定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術者だけが変更するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="fca41-122">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="fca41-123">アプリケーションで一括コピー操作を行ったり、大量の text 型または image 型のデータを送受信する場合は、パケット サイズを既定値より大きくすると、ネットワークの読み取りと書き込みの操作が少なくなるので効率が向上することがあります。</span><span class="sxs-lookup"><span data-stu-id="fca41-123">If an application does bulk copy operations or sends or receives large amounts of text or image data, a packet size larger than the default might improve efficiency because it results in fewer network read-and-write operations.</span></span> <span data-ttu-id="fca41-124">アプリケーションで送受信する情報量が少ない場合は、パケット サイズを 512 バイトに設定できます。これは、ほとんどのデータ転送に十分なサイズです。</span><span class="sxs-lookup"><span data-stu-id="fca41-124">If an application sends and receives small amounts of information, the packet size can be set to 512 bytes, which is sufficient for most data transfers.</span></span>  
  
-   <span data-ttu-id="fca41-125">異なるネットワーク プロトコルを使用しているシステムでは、最も一般的に使用されるプロトコル向けのサイズに network packet size を設定します。</span><span class="sxs-lookup"><span data-stu-id="fca41-125">On systems that are using different network protocols, set network packet size to the size for the most common protocol used.</span></span> <span data-ttu-id="fca41-126">ネットワーク プロトコルで大きなパケットがサポートされるときは、network packet size オプションを設定することでネットワーク パフォーマンスを向上できます。</span><span class="sxs-lookup"><span data-stu-id="fca41-126">The network packet size option improves network performance when network protocols support larger packets.</span></span> <span data-ttu-id="fca41-127">クライアント アプリケーションはこの値をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="fca41-127">Client applications can override this value.</span></span>  
  
-   <span data-ttu-id="fca41-128">OLE DB 関数、ODBC (Open Database Connectivity) 関数、および DB-Library 関数を呼び出して、パケット サイズの変更を要求することもできます。</span><span class="sxs-lookup"><span data-stu-id="fca41-128">You can also call OLE DB, Open Database Connectivity (ODBC), and DB-Library functions request a change the packet size.</span></span> <span data-ttu-id="fca41-129">要求されたパケット サイズにサーバーが対応できない場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] からクライアントに警告メッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="fca41-129">If the server cannot support the requested packet size, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] will send a warning message to the client.</span></span> <span data-ttu-id="fca41-130">環境によっては、パケット サイズを変更すると、次のような通信リンク エラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="fca41-130">In some circumstances, changing the packet size might lead to a communication link failure, such as the following:</span></span>  
  
     `Native Error: 233, no process is on the other end of the pipe.`  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fca41-131">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="fca41-131">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fca41-132">Permissions</span><span class="sxs-lookup"><span data-stu-id="fca41-132">Permissions</span></span>  
 <span data-ttu-id="fca41-133">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="fca41-133">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="fca41-134">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="fca41-134">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="fca41-135">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="fca41-135">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="fca41-136">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="fca41-136">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-network-packet-size-option"></a><span data-ttu-id="fca41-137">network packet size オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="fca41-137">To configure the network packet size option</span></span>  
  
1.  <span data-ttu-id="fca41-138">オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fca41-138">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="fca41-139">**[詳細設定]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fca41-139">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="fca41-140">**[ネットワーク]** の **[ネットワーク パケット サイズ]** ボックスに値を指定します。</span><span class="sxs-lookup"><span data-stu-id="fca41-140">Under **Network**, select a value for the **Network Packet Size** box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="fca41-141">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="fca41-141">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-network-packet-size-option"></a><span data-ttu-id="fca41-142">network packet size オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="fca41-142">To configure the network packet size option</span></span>  
  
1.  <span data-ttu-id="fca41-143">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="fca41-143">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="fca41-144">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fca41-144">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="fca41-145">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fca41-145">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="fca41-146">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して、 `network packet size` オプションの値を `6500` バイトに設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fca41-146">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `network packet size` option to `6500` bytes.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'network packet size', 6500 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="fca41-147">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fca41-147">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-network-packet-size-option"></a><a name="FollowUp"></a><span data-ttu-id="fca41-148">補足情報: network packet size オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="fca41-148">Follow Up: After you configure the network packet size option</span></span>  
 <span data-ttu-id="fca41-149">新しい設定は、サーバーを再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="fca41-149">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fca41-150">参照</span><span class="sxs-lookup"><span data-stu-id="fca41-150">See Also</span></span>  
 <span data-ttu-id="fca41-151">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fca41-151">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="fca41-152">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fca41-152">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="fca41-153">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fca41-153">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
