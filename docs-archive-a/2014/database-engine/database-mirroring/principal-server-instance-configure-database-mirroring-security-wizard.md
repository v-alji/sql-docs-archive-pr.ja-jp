---
title: '[プリンシパル サーバー インスタンス] (データベース ミラーリング セキュリティ構成ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.principalsrvr.f1
ms.assetid: 58af27d7-c5dd-4669-be6b-b472bc2c8ef4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2632b5ffd5355065b4b5c1f905b3b6e5c5b6204d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716781"
---
# <a name="principal-server-instance-configure-database-mirroring-security-wizard"></a><span data-ttu-id="438d1-102">[プリンシパル サーバー インスタンス] (データベース ミラーリング セキュリティ構成ウィザード)</span><span class="sxs-lookup"><span data-stu-id="438d1-102">Principal Server Instance (Configure Database Mirroring Security Wizard)</span></span>
  <span data-ttu-id="438d1-103">このページを使用すると、プリンシパル データベースのサーバー インスタンスに関する情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="438d1-103">Use this page to specify information about the server instance of the principal database.</span></span> <span data-ttu-id="438d1-104">プリンシパル データベースは、ミラーリング セッションを開始するデータベースのコピーです。</span><span class="sxs-lookup"><span data-stu-id="438d1-104">The principal database is the copy of the database that begins the mirroring session.</span></span> <span data-ttu-id="438d1-105">セッションが開始された後は、プリンシパル データベースは、ユーザーが変更できるデータベースのコピーになります。</span><span class="sxs-lookup"><span data-stu-id="438d1-105">After the session has begun, the principal database is the copy of the database that accepts user changes.</span></span> <span data-ttu-id="438d1-106">フェールオーバーが発生するとプリンシパル ロールとミラーリング ロールが入れ替わるため、最初のプリンシパル データベースが途中でプリンシパル データベースでなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="438d1-106">(When a failover occurs, the principal and mirroring roles are swapped; therefore, the initial principal database might not remain the principal database.)</span></span>  
  
 <span data-ttu-id="438d1-107">**SQL Server Management Studio を使用してデータベース ミラーリングを構成するには**</span><span class="sxs-lookup"><span data-stu-id="438d1-107">**To configure database mirroring by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="438d1-108">Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="438d1-108">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="438d1-109">データベース ミラーリング セキュリティ構成ウィザードの起動 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="438d1-109">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="438d1-110">Options</span><span class="sxs-lookup"><span data-stu-id="438d1-110">Options</span></span>  
 <span data-ttu-id="438d1-111">**[プリンシパル サーバー インスタンス]**</span><span class="sxs-lookup"><span data-stu-id="438d1-111">**Principal server instance**</span></span>  
 <span data-ttu-id="438d1-112">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のデータベース ミラーリングは常にプリンシパル サーバーから構成されるため、必ず現在のサーバー インスタンスがプリンシパル サーバー インスタンスになります。</span><span class="sxs-lookup"><span data-stu-id="438d1-112">Because database mirroring in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is always configured from the principal server, the current server instance is always the principal server instance.</span></span>  
  
 <span data-ttu-id="438d1-113">**リスナー ポート**</span><span class="sxs-lookup"><span data-stu-id="438d1-113">**Listener Port**</span></span>  
 <span data-ttu-id="438d1-114">このオプションでは、このサーバー インスタンスに対するミラーリング エンドポイントが存在するかどうかに応じて、次のような内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="438d1-114">The behavior of this option depends on whether the mirroring endpoint exists for this server instance, as follows:</span></span>  
  
-   <span data-ttu-id="438d1-115">このサーバー インスタンスに対するリスナー ポートが存在しない場合、 **[ポート]** テキスト ボックスにポート番号 5022 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="438d1-115">If the listener port does not exist for this server instance, port number 5022 is displayed in the **Port** text box.</span></span> <span data-ttu-id="438d1-116">使用可能な任意のポート番号を入力できます (7022 など)。</span><span class="sxs-lookup"><span data-stu-id="438d1-116">You can use any available port number, such as, 7022.</span></span>  
  
-   <span data-ttu-id="438d1-117">ミラーリング エンドポイントが既に存在する場合、そのエンドポイントからのポート番号が表示されます。</span><span class="sxs-lookup"><span data-stu-id="438d1-117">When the mirroring endpoint already exists, the port number from the endpoint is displayed.</span></span> <span data-ttu-id="438d1-118">ポートを変更する必要がある場合は、ALTER ENDPOINT コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="438d1-118">If you need to change the port, use an ALTER ENDPOINT command.</span></span> <span data-ttu-id="438d1-119">詳細については、「 [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="438d1-119">For more information, see [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="438d1-120">ポート番号は必須です。</span><span class="sxs-lookup"><span data-stu-id="438d1-120">A port number is required.</span></span>  
  
 <span data-ttu-id="438d1-121">**エンドポイント名**</span><span class="sxs-lookup"><span data-stu-id="438d1-121">**Endpoint name**</span></span>  
 <span data-ttu-id="438d1-122">このサーバー インスタンスのミラーリング エンドポイントが存在する場合、ここにエンドポイント名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="438d1-122">If the mirroring endpoint exists for this server instance, the endpoint name is displayed here.</span></span> <span data-ttu-id="438d1-123">エンドポイントが存在しない場合には、エンドポイントの名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="438d1-123">If the endpoint does not exist, you can specify the name of the endpoint.</span></span>  
  
 <span data-ttu-id="438d1-124">**[このエンドポイントから送られるデータを暗号化する]**</span><span class="sxs-lookup"><span data-stu-id="438d1-124">**Encrypt data sent through this endpoint**</span></span>  
 <span data-ttu-id="438d1-125">既定で、暗号化は有効になっています。</span><span class="sxs-lookup"><span data-stu-id="438d1-125">By default, encryption is enabled.</span></span> <span data-ttu-id="438d1-126">暗号化が有効な場合、暗号化は必須です (サポートされるだけではありません)。暗号化オプションにはすべて既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="438d1-126">When enabled, encryption is required (not merely supported) and uses the default values for all of the encryption options.</span></span> <span data-ttu-id="438d1-127">詳細については、「[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="438d1-127">For more information, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span>  
  
 <span data-ttu-id="438d1-128">暗号化を無効にするには、チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="438d1-128">To disable encryption, clear the check box.</span></span> <span data-ttu-id="438d1-129">暗号化を再度有効にするには、チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="438d1-129">To re-enable encryption, select the check box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="438d1-130">参照</span><span class="sxs-lookup"><span data-stu-id="438d1-130">See Also</span></span>  
 <span data-ttu-id="438d1-131">[データベース ミラーリング エンドポイント &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="438d1-131">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="438d1-132">[データベース プロパティ &#40;[ミラーリング] ページ&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="438d1-132">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="438d1-133">[Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="438d1-133">[Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span></span>  
 <span data-ttu-id="438d1-134">[データベース ミラーリング モニターの起動 &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="438d1-134">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="438d1-135">データベース ミラーリング &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="438d1-135">Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
