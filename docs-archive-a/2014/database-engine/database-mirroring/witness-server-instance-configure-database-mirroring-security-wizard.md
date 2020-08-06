---
title: ミラーリング監視サーバー インスタンス (データベース ミラーリング セキュリティ構成ウィザード) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.witnsrvr.f1
ms.assetid: b5763663-984a-473b-93a3-6cd3322ad41c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fcea7d39e1bc2c6161b5c6e1edd4852d9fdeb073
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634024"
---
# <a name="witness-server-instance-configure-database-mirroring-security-wizard"></a><span data-ttu-id="e1e60-102">[ミラーリング監視サーバー インスタンス] (データベース ミラーリング セキュリティ構成ウィザード)</span><span class="sxs-lookup"><span data-stu-id="e1e60-102">Witness Server Instance (Configure Database Mirroring Security Wizard)</span></span>
  <span data-ttu-id="e1e60-103">このページを使用すると、セッションのミラーリング監視サーバーとして機能するサーバー インスタンスの情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e1e60-103">Use this page to specify information about the server instance that is to serve as the witness for the session.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e1e60-104">ミラーリング監視サーバー インスタンスは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="e1e60-104">A witness server instance is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e1e60-105">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1e60-105">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="e1e60-106">**SQL Server Management Studio を使用してデータベース ミラーリングを構成するには**</span><span class="sxs-lookup"><span data-stu-id="e1e60-106">**To configure database mirroring by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="e1e60-107">Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="e1e60-107">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="e1e60-108">データベース ミラーリング セキュリティ構成ウィザードの起動 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="e1e60-108">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="e1e60-109">Options</span><span class="sxs-lookup"><span data-stu-id="e1e60-109">Options</span></span>  
 <span data-ttu-id="e1e60-110">**[ミラーリング監視サーバー インスタンス]**</span><span class="sxs-lookup"><span data-stu-id="e1e60-110">**Witness server instance**</span></span>  
 <span data-ttu-id="e1e60-111">**[データベースのプロパティ]** ダイアログ ボックスの **[ミラー化]** ページで、ミラーリング監視サーバー インスタンスが既に指定されている場合、そのインスタンスが表示されます。詳細については、「[[データベースのプロパティ] &#40;[ミラーリング] ページ&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1e60-111">If a witness server instance is already specified (on the **Mirroring** page of the **Database Properties** dialog box), that instance is displayed (for more information, see [Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)).</span></span>  
  
 <span data-ttu-id="e1e60-112">それ以外の場合、このリスト ボックスには現在のサーバーの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e1e60-112">Otherwise, this list box displays the name of the current server.</span></span> <span data-ttu-id="e1e60-113">プリンシパル サーバー インスタンスまたはミラー サーバー インスタンスと同じ名前をミラーリング監視サーバー インスタンスに指定しないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="e1e60-113">Be aware that the witness server instance cannot be the same as the principal or mirror server instances.</span></span>  
  
 <span data-ttu-id="e1e60-114">**のインスタンスに接続するときには、**</span><span class="sxs-lookup"><span data-stu-id="e1e60-114">**Connect**</span></span>  
 <span data-ttu-id="e1e60-115">ミラーリング監視サーバー インスタンスが指定されていない場合、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e1e60-115">If a witness server instance has not been specified, click **Connect**.</span></span> <span data-ttu-id="e1e60-116">**[サーバーへの接続]** ダイアログ ボックスが表示されます。ここでサーバー インスタンスを指定し、接続を確立できます。</span><span class="sxs-lookup"><span data-stu-id="e1e60-116">This displays the **Connect to Server** dialog box in which you can specify the server instance and establish a connection.</span></span>  
  
 <span data-ttu-id="e1e60-117">インスタンスが指定されていても、エンドポイントが存在するかどうかをチェックできる権限を持つ接続がない場合には、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e1e60-117">If the instance has been specified, but the wizard lacks a connection with sufficient permission to check for the existence of the endpoint, click **Connect**.</span></span> <span data-ttu-id="e1e60-118">**[サーバーへの接続]** ダイアログ ボックスが表示されます。この場合、サーバー インスタンスは選択されており、変更できません。</span><span class="sxs-lookup"><span data-stu-id="e1e60-118">This displays the **Connect to Server** dialog box with the server instance pre-selected and unchangeable.</span></span> <span data-ttu-id="e1e60-119">十分な権限を持つドメイン アカウントを指定して、サーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="e1e60-119">Specify a domain account with sufficient permission, and connect to the server instance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e1e60-120">データベース ミラーリング セキュリティ構成ウィザードは、 **[サーバーへの接続]** ダイアログ ボックスで指定された資格情報を使ってサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="e1e60-120">When connecting to the server instance, the Configure Database Mirroring Security Wizard uses the credentials provided in the **Connect to Server** dialog box.</span></span> <span data-ttu-id="e1e60-121">これらは、ミラーリング セッションの資格情報とは異なります。ミラーリング セッションでは、サーバー インスタンスをサービスとして実行している開始アカウントの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e1e60-121">These are different from the credentials of a mirroring session, which uses the credentials of the startup account where the server instance is running as a service.</span></span>  
  
 <span data-ttu-id="e1e60-122">**リスナー ポート**</span><span class="sxs-lookup"><span data-stu-id="e1e60-122">**Listener Port**</span></span>  
 <span data-ttu-id="e1e60-123">このオプションでは、このサーバー インスタンスに対するミラーリング エンドポイントが存在するかどうかに応じて、次のような内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e1e60-123">The behavior of this option depends on whether the mirroring endpoint exists for this server instance, as follows:</span></span>  
  
-   <span data-ttu-id="e1e60-124">サーバー インスタンスに対するリスナー ポートが存在しない場合、 **[ポート]** テキスト ボックスにはポート番号 5022 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e1e60-124">If the listener port does not exist for the server instance, port number 5022 is displayed in the **Port** text box.</span></span> <span data-ttu-id="e1e60-125">使用可能な任意のポート番号を入力できます (7022 など)。</span><span class="sxs-lookup"><span data-stu-id="e1e60-125">You can enter any available port number, such as, 7022.</span></span>  
  
-   <span data-ttu-id="e1e60-126">ミラーリング エンドポイントが既に存在する場合、そのエンドポイントからのポート番号が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e1e60-126">When the mirroring endpoint already exists, the port number from the endpoint is displayed.</span></span> <span data-ttu-id="e1e60-127">ポートを変更する必要がある場合は、ALTER ENDPOINT ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="e1e60-127">If you need to change that port, use an ALTER ENDPOINT statement.</span></span> <span data-ttu-id="e1e60-128">詳細については、「 [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1e60-128">For more information, see [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e1e60-129">ポート番号は必須です。</span><span class="sxs-lookup"><span data-stu-id="e1e60-129">A port number is required.</span></span>  
  
 <span data-ttu-id="e1e60-130">**エンドポイント名**</span><span class="sxs-lookup"><span data-stu-id="e1e60-130">**Endpoint name**</span></span>  
 <span data-ttu-id="e1e60-131">このサーバー インスタンスのミラーリング エンドポイントが存在する場合、ここにエンドポイント名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e1e60-131">If the mirroring endpoint exists for this server instance, the endpoint name is displayed here.</span></span> <span data-ttu-id="e1e60-132">エンドポイントが存在しない場合には、エンドポイントの名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e1e60-132">If the endpoint does not exist, you can specify the name of the endpoint.</span></span>  
  
 <span data-ttu-id="e1e60-133">**[このエンドポイントから送られるデータを暗号化する]**</span><span class="sxs-lookup"><span data-stu-id="e1e60-133">**Encrypt data sent through this endpoint**</span></span>  
 <span data-ttu-id="e1e60-134">既定で、暗号化は有効になっています。</span><span class="sxs-lookup"><span data-stu-id="e1e60-134">By default, encryption is enabled.</span></span> <span data-ttu-id="e1e60-135">暗号化が有効な場合、暗号化は必須です (サポートされるだけではありません)。暗号化オプションにはすべて既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e1e60-135">When enabled, encryption is required (not merely supported) and uses the default values for all of the encryption options.</span></span> <span data-ttu-id="e1e60-136">詳細については、「[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1e60-136">For more information, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span>  
  
 <span data-ttu-id="e1e60-137">暗号化を無効にするには、チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="e1e60-137">To disable encryption, clear the check box.</span></span> <span data-ttu-id="e1e60-138">暗号化を再度有効にするには、チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="e1e60-138">To re-enable encryption, select the check box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1e60-139">参照</span><span class="sxs-lookup"><span data-stu-id="e1e60-139">See Also</span></span>  
 <span data-ttu-id="e1e60-140">[データベース ミラーリング エンドポイント &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e1e60-140">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="e1e60-141">[データベース プロパティ &#40;[ミラーリング] ページ&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="e1e60-141">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="e1e60-142">[Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="e1e60-142">[Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span></span>  
 <span data-ttu-id="e1e60-143">[データベース ミラーリング モニターの起動 &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="e1e60-143">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="e1e60-144">[データベース ミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e1e60-144">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="e1e60-145">データベース ミラーリング監視サーバー</span><span class="sxs-lookup"><span data-stu-id="e1e60-145">Database Mirroring Witness</span></span>](database-mirroring-witness.md)  
  
  
