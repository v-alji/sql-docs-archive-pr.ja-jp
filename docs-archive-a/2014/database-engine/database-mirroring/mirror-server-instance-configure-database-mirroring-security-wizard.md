---
title: '[ミラー サーバー インスタンス] (データベース ミラーリング セキュリティ構成ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.mirrorsrvr.f1
ms.assetid: 53223432-615e-440f-904d-925d33ec2144
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 889e62af592d8d23f2aca0d752f1c7f535df883a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742554"
---
# <a name="mirror-server-instance-configure-database-mirroring-security-wizard"></a><span data-ttu-id="8da88-102">[ミラー サーバー インスタンス] (データベース ミラーリング セキュリティ構成ウィザード)</span><span class="sxs-lookup"><span data-stu-id="8da88-102">Mirror Server Instance (Configure Database Mirroring Security Wizard)</span></span>
  <span data-ttu-id="8da88-103">このページを使用すると、ミラー データベースを持つサーバー インスタンスに関する情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8da88-103">Use this page to specify information about the server instance with the mirror database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8da88-104">ミラー サーバー インスタンスでは、プリンシパル サーバー インスタンスと同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のエディション (Standard または Enterprise) を実行している必要があります。</span><span class="sxs-lookup"><span data-stu-id="8da88-104">The mirror server instance must be running the same edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], either Standard or Enterprise, as the principal server instance.</span></span> <span data-ttu-id="8da88-105">また、ワークロードの処理能力が同程度のシステム上で運用することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8da88-105">Also, we strongly recommend that they run on comparable systems that can handle identical workloads.</span></span>  
  
 <span data-ttu-id="8da88-106">**SQL Server Management Studio を使用してデータベース ミラーリングを構成するには**</span><span class="sxs-lookup"><span data-stu-id="8da88-106">**To configure database mirroring by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="8da88-107">Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="8da88-107">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="8da88-108">データベース ミラーリング セキュリティ構成ウィザードの起動 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="8da88-108">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="8da88-109">Options</span><span class="sxs-lookup"><span data-stu-id="8da88-109">Options</span></span>  
 <span data-ttu-id="8da88-110">**[ミラー サーバー インスタンス]**</span><span class="sxs-lookup"><span data-stu-id="8da88-110">**Mirror server instance**</span></span>  
 <span data-ttu-id="8da88-111">**[データベースのプロパティ]** ダイアログ ボックスの **[ミラー化]** ページで、ミラー サーバー インスタンスが既に指定されている場合、そのインスタンスが表示されます。詳細については、「[[データベースのプロパティ] &#40;[ミラーリング] ページ&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8da88-111">If a mirror server instance is already specified (on the **Mirroring** page of the **Database Properties** dialog box), that instance is displayed; for more information, see [Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md).</span></span>  
  
 <span data-ttu-id="8da88-112">まだ指定されていない場合は、ミラー サーバー インスタンスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="8da88-112">Otherwise, enter the name of the mirror server instance.</span></span> <span data-ttu-id="8da88-113">プリンシパル サーバー インスタンスと同じ名前をミラー サーバー インスタンスに指定しないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="8da88-113">Note that the mirror server instance cannot be the same as the principal server instance.</span></span>  
  
 <span data-ttu-id="8da88-114">**のインスタンスに接続するときには、**</span><span class="sxs-lookup"><span data-stu-id="8da88-114">**Connect**</span></span>  
 <span data-ttu-id="8da88-115">ミラー サーバー インスタンスが指定されていない場合、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8da88-115">If a mirror server instance has not been specified, click **Connect**.</span></span> <span data-ttu-id="8da88-116">**[サーバーへの接続]** ダイアログ ボックスが表示されます。ここでサーバー インスタンスを指定し、接続を確立できます。</span><span class="sxs-lookup"><span data-stu-id="8da88-116">This displays the **Connect to Server** dialog box in which you can specify the server instance and establish a connection.</span></span>  
  
 <span data-ttu-id="8da88-117">インスタンスが指定されていても、エンドポイントが存在するかどうかをチェックできる権限を持つ接続がない場合には、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8da88-117">If the instance has been specified, but the wizard lacks a connection with sufficient permission to check for the existence of the endpoint, click **Connect**.</span></span> <span data-ttu-id="8da88-118">**[サーバーへの接続]** ダイアログ ボックスが表示されます。この場合、サーバー インスタンスは選択されており、変更できません。</span><span class="sxs-lookup"><span data-stu-id="8da88-118">This displays the **Connect to Server** dialog box with the server instance pre-selected and unchangeable.</span></span> <span data-ttu-id="8da88-119">十分な権限を持つドメイン アカウントを指定して、サーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="8da88-119">Specify a domain account with sufficient permission, and connect to the server instance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8da88-120">データベース ミラーリング セキュリティ構成ウィザードは、 **[サーバーへの接続]** ダイアログ ボックスで指定された資格情報を使ってサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="8da88-120">When connecting to the server instance, the Configure Database Mirroring Security Wizard uses the credentials provided in the **Connect to Server** dialog box.</span></span> <span data-ttu-id="8da88-121">これらは、ミラーリング セッションの資格情報とは異なります。ミラーリング セッションでは、サーバー インスタンスをサービスとして実行している開始アカウントの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="8da88-121">These are different from the credentials of a mirroring session, which uses the credentials of the startup account where the server instance is running as a service.</span></span>  
  
 <span data-ttu-id="8da88-122">**リスナー ポート**</span><span class="sxs-lookup"><span data-stu-id="8da88-122">**Listener Port**</span></span>  
 <span data-ttu-id="8da88-123">このオプションでは、このサーバー インスタンスに対するミラーリング エンドポイントが存在するかどうかに応じて、次のような内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8da88-123">The behavior of this option depends on whether the mirroring endpoint exists for this server instance, as follows:</span></span>  
  
-   <span data-ttu-id="8da88-124">サーバー インスタンスに対するリスナー ポートが存在しない場合、 **[リスナー ポート]** テキスト ボックスにポート番号 5022 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8da88-124">If a listener port does not exist for the server instance, port number 5022 is displayed in the **Port** text box.</span></span> <span data-ttu-id="8da88-125">使用可能な任意のポート番号を入力できます (7022 など)。</span><span class="sxs-lookup"><span data-stu-id="8da88-125">You can use any available port number, such as 7022.</span></span>  
  
-   <span data-ttu-id="8da88-126">ミラーリング エンドポイントが既に存在する場合、そのエンドポイントからのポート番号が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8da88-126">When the mirroring endpoint already exists, the port number from that endpoint is displayed.</span></span> <span data-ttu-id="8da88-127">ポートを変更する必要がある場合は、ALTER ENDPOINT コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8da88-127">If you need to change the port, use an ALTER ENDPOINT command.</span></span> <span data-ttu-id="8da88-128">詳細については、「 [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8da88-128">For more information, see [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8da88-129">ポート番号は必須です。</span><span class="sxs-lookup"><span data-stu-id="8da88-129">A port number is required.</span></span>  
  
 <span data-ttu-id="8da88-130">**エンドポイント名**</span><span class="sxs-lookup"><span data-stu-id="8da88-130">**Endpoint name**</span></span>  
 <span data-ttu-id="8da88-131">このサーバー インスタンスのミラーリング エンドポイントが存在する場合、ここにエンドポイント名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8da88-131">If the mirroring endpoint exists for this server instance, the endpoint name is displayed here.</span></span> <span data-ttu-id="8da88-132">エンドポイントが存在しない場合には、エンドポイントの名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8da88-132">If the endpoint does not exist, you can specify the name of the endpoint.</span></span>  
  
 <span data-ttu-id="8da88-133">**[このエンドポイントから送られるデータを暗号化する]**</span><span class="sxs-lookup"><span data-stu-id="8da88-133">**Encrypt data sent through this endpoint**</span></span>  
 <span data-ttu-id="8da88-134">既定で、暗号化は有効になっています。</span><span class="sxs-lookup"><span data-stu-id="8da88-134">By default, encryption is enabled.</span></span> <span data-ttu-id="8da88-135">暗号化が有効な場合、暗号化は必須です (サポートされるだけではありません)。暗号化オプションにはすべて既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="8da88-135">When enabled, encryption is required (not merely supported) and uses the default values for all of the encryption options.</span></span> <span data-ttu-id="8da88-136">詳細については、「[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8da88-136">For more information, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span>  
  
 <span data-ttu-id="8da88-137">暗号化を無効にするには、チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="8da88-137">To disable encryption, clear the check box.</span></span> <span data-ttu-id="8da88-138">暗号化を再度有効にするには、チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="8da88-138">To re-enable encryption, select the check box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8da88-139">参照</span><span class="sxs-lookup"><span data-stu-id="8da88-139">See Also</span></span>  
 <span data-ttu-id="8da88-140">[データベース ミラーリング エンドポイント &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8da88-140">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="8da88-141">[データベース プロパティ &#40;[ミラーリング] ページ&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="8da88-141">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="8da88-142">[Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="8da88-142">[Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span></span>  
 <span data-ttu-id="8da88-143">[データベース ミラーリング モニターの起動 &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="8da88-143">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="8da88-144">データベース ミラーリング &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8da88-144">Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
