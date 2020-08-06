---
title: Analysis Services データベースをアタッチおよびデタッチする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.ssms.detachdatabase.f1
- sql12.asvs.ssms.attachdatabase.f1
- sql12.asvs.ssmsimbi.AttachDatabase.f1
- sql12.asvs.ssmsimbi.DetachDatabase.f1
helpviewer_keywords:
- databases [Analysis Services], attach
- databases [Analysis Services], detach
ms.assetid: 41887413-2d47-49b8-8614-553cb799fb18
author: minewiskan
ms.author: owend
ms.openlocfilehash: cd72277970605691e06f3baacf167ea135343b3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645217"
---
# <a name="attach-and-detach-analysis-services-databases"></a><span data-ttu-id="571e2-102">Analysis Services データベースのインポートとデタッチ</span><span class="sxs-lookup"><span data-stu-id="571e2-102">Attach and Detach Analysis Services Databases</span></span>
  <span data-ttu-id="571e2-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のデータベース管理者 (DBA) がデータベースを一時的にオフラインにした後、そのデータベースを同じサーバー インスタンスまたは別のサーバー インスタンス上でオンラインに戻すことは少なくありません。</span><span class="sxs-lookup"><span data-stu-id="571e2-103">There are often situations when an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database administrator (dba) wants to take a database offline for a period, and then bring that database back online on the same server instance, or on a different one.</span></span> <span data-ttu-id="571e2-104">こうした状況は、パフォーマンス向上のためにデータベースを別のディスクに移動したり、データベース拡張のための領域を確保したり、製品をアップグレードしたりするなど、ビジネス上のニーズによって頻繁に発生します。</span><span class="sxs-lookup"><span data-stu-id="571e2-104">These situations are often driven by business needs, such as moving the database to a different disk for better performance, gaining room for database growth, or to upgrade a product.</span></span> <span data-ttu-id="571e2-105">このような状況だけでなくさまざまな場合に、`Attach` コマンドと `Detach` コマンドを使用することによって、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の DBA は、データベースをオフラインにした後、簡単にオンラインに戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="571e2-105">For all those cases and more, the `Attach` and `Detach` commands enable the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dba to take the database offline and bring it back online with little effort.</span></span>  
  
## <a name="attach-and-detach-commands"></a><span data-ttu-id="571e2-106">Attach コマンドと Detach コマンド</span><span class="sxs-lookup"><span data-stu-id="571e2-106">Attach and Detach commands</span></span>  
 <span data-ttu-id="571e2-107">`Attach` コマンドを使用すると、オフラインになっているデータベースをオンラインにすることができます。</span><span class="sxs-lookup"><span data-stu-id="571e2-107">The `Attach` command enables you to bring online a database that was taken offline.</span></span> <span data-ttu-id="571e2-108">データベースは元のサーバー インスタンスにでも、別のインスタンスにでもアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="571e2-108">You can attach the database to the original server instance, or to another instance.</span></span> <span data-ttu-id="571e2-109">データベースをアタッチする場合、データベースに **ReadWriteMode** 設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="571e2-109">When you attach a database the user can specify the **ReadWriteMode** setting for the database.</span></span> <span data-ttu-id="571e2-110">`Detach` コマンドを使用すると、データベースをサーバーからオフラインにすることができます。</span><span class="sxs-lookup"><span data-stu-id="571e2-110">The `Detach` command enables you to take offline a database from the server.</span></span>  
  
## <a name="attach-and-detach-usage"></a><span data-ttu-id="571e2-111">Attach と Detach の使用方法</span><span class="sxs-lookup"><span data-stu-id="571e2-111">Attach and Detach Usage</span></span>  
 <span data-ttu-id="571e2-112">`Attach` コマンドは、既存のデータベース構造をオンラインにする際に使用します。</span><span class="sxs-lookup"><span data-stu-id="571e2-112">The `Attach` command is used to bring online an existing database structure.</span></span> <span data-ttu-id="571e2-113">データベースを `ReadWrite` モードでアタッチする場合は、1 つのサーバー インスタンスに 1 回だけアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="571e2-113">If the database is attached in `ReadWrite` mode, it can be attached only one time to a server instance.</span></span> <span data-ttu-id="571e2-114">一方、データベースを `ReadOnly` モードでアタッチする場合は、異なるサーバー インスタンスに複数回アタッチできます。</span><span class="sxs-lookup"><span data-stu-id="571e2-114">However, if the database is attached in `ReadOnly` mode, it can be attached multiple times to different server instances.</span></span> <span data-ttu-id="571e2-115">ただし、同じデータベースを同じサーバー インスタンスに複数回アタッチすることはできません。</span><span class="sxs-lookup"><span data-stu-id="571e2-115">However, the same database cannot be attached more than one time to the same server instance.</span></span> <span data-ttu-id="571e2-116">同じデータベースを複数回アタッチしようとすると、データを別のフォルダーにコピーした場合でも、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="571e2-116">An error is raised when an attempt is made to attach the same database more than one time, even if the data has been copied to separate folders.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="571e2-117">データベースをデタッチする際にパスワードが必要だった場合は、そのデータベースをアタッチする際にも同じパスワードが必要になります。</span><span class="sxs-lookup"><span data-stu-id="571e2-117">If a password was required to detach the database, the same password is required to attach the database.</span></span>  
  
 <span data-ttu-id="571e2-118">`Detach` コマンドは、既存のデータベース構造をオフラインにする際に使用します。</span><span class="sxs-lookup"><span data-stu-id="571e2-118">The `Detach` command is used to take offline an existing database structure.</span></span> <span data-ttu-id="571e2-119">データベースをデタッチする場合は、パスワードを指定して、機密性のあるメタデータを保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="571e2-119">When a database is detached, you should provide a password to protect confidential metadata.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="571e2-120">データ ファイルの内容を保護するには、フォルダー、サブフォルダー、およびデータ ファイルのアクセス制御リストを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="571e2-120">To protect the content of the data files, you should use an access control list for the folder, subfolders, and data files.</span></span>  
  
 <span data-ttu-id="571e2-121">データベースをデタッチする場合、サーバーでは次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="571e2-121">When you detach a database, the server follows these steps.</span></span>  
  
|<span data-ttu-id="571e2-122">読み書き可能なデータベースのデタッチ</span><span class="sxs-lookup"><span data-stu-id="571e2-122">Detaching a read/write database</span></span>|<span data-ttu-id="571e2-123">読み取り専用データベースのデタッチ</span><span class="sxs-lookup"><span data-stu-id="571e2-123">Detaching a read-only database</span></span>|  
|--------------------------------------|-------------------------------------|  
|<span data-ttu-id="571e2-124">1) サーバーはデータベースに対する CommitExclusive ロックの要求を発行します</span><span class="sxs-lookup"><span data-stu-id="571e2-124">1) The server issues a request for a CommitExclusive Lock on the database</span></span><br /><span data-ttu-id="571e2-125">2) サーバーは、実行中のトランザクションすべてがコミットまたはロールバックされるまで待機します</span><span class="sxs-lookup"><span data-stu-id="571e2-125">2) The server waits until all ongoing transactions are either committed or rolled back</span></span><br /><span data-ttu-id="571e2-126">3) サーバーはデータベースのデタッチに必要なすべてのメタデータを構築します</span><span class="sxs-lookup"><span data-stu-id="571e2-126">3) The server builds all the metadata that it must have to detach the database</span></span><br /><span data-ttu-id="571e2-127">4) データベースは削除済みに設定されます</span><span class="sxs-lookup"><span data-stu-id="571e2-127">4) The database is marked as deleted</span></span><br /><span data-ttu-id="571e2-128">5) サーバーはトランザクションをコミットします</span><span class="sxs-lookup"><span data-stu-id="571e2-128">5) The server commits the transaction</span></span>|<span data-ttu-id="571e2-129">1) データベースは削除済みに設定されます</span><span class="sxs-lookup"><span data-stu-id="571e2-129">1) The database is marked as deleted</span></span><br /><span data-ttu-id="571e2-130">2) サーバーはトランザクションをコミットします</span><span class="sxs-lookup"><span data-stu-id="571e2-130">2) The server commits the transaction</span></span><br /><br /> <br /><br /> <span data-ttu-id="571e2-131">注: 読み取り専用データベースでは、デタッチ用のパスワードを変更できません。</span><span class="sxs-lookup"><span data-stu-id="571e2-131">Note: The detaching password cannot be changed for a read-only database.</span></span> <span data-ttu-id="571e2-132">アタッチされたデータベースに既にパスワードが含まれている場合にパスワード パラメーターを指定すると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="571e2-132">An error is raised if the password parameter is provided for an attached database that already contains a password.</span></span>|  
  
 <span data-ttu-id="571e2-133">`Attach` コマンドおよび `Detach` コマンドは 1 つの操作として実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="571e2-133">The `Attach` and `Detach` commands must be executed as single operations.</span></span> <span data-ttu-id="571e2-134">同じトランザクション内でその他の操作と組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="571e2-134">They cannot be combined with other operations in the same transaction.</span></span> <span data-ttu-id="571e2-135">また、 `Attach` コマンドと `Detach` コマンドはアトミックトランザクションコマンドです。</span><span class="sxs-lookup"><span data-stu-id="571e2-135">Also, the `Attach` and `Detach` commands are atomic transactional commands.</span></span> <span data-ttu-id="571e2-136">つまり、操作は成功するか失敗するかのどちらかになります。</span><span class="sxs-lookup"><span data-stu-id="571e2-136">This means the operation will either succeed or fail.</span></span> <span data-ttu-id="571e2-137">データベースは未完了の状態にしておくことはできません。</span><span class="sxs-lookup"><span data-stu-id="571e2-137">No database will be left in an uncompleted state.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="571e2-138">`Detach` コマンドを実行するには、サーバーまたはデータベースの管理者特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="571e2-138">Server or database administrator privileges are required to execute the `Detach` command.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="571e2-139">`Attach` コマンドを実行するには、サーバーの管理者特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="571e2-139">Server administrator privileges are required to execute the `Attach` command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="571e2-140">参照</span><span class="sxs-lookup"><span data-stu-id="571e2-140">See Also</span></span>  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <span data-ttu-id="571e2-141">[Microsoft.analysisservices.sharepoint.integration.dll \* のようになります。](/dotnet/api/microsoft.analysisservices.core.database.detach) </span><span class="sxs-lookup"><span data-stu-id="571e2-141">[Microsoft.AnalysisServices.Database.Detach\*](/dotnet/api/microsoft.analysisservices.core.database.detach) </span></span>  
 <span data-ttu-id="571e2-142">[Analysis Services データベースの移動](move-an-analysis-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="571e2-142">[Move an Analysis Services Database](move-an-analysis-services-database.md) </span></span>  
 <span data-ttu-id="571e2-143">[データベース ReadWriteModes](database-readwritemodes.md) </span><span class="sxs-lookup"><span data-stu-id="571e2-143">[Database ReadWriteModes](database-readwritemodes.md) </span></span>  
 <span data-ttu-id="571e2-144">[Analysis Services データベースを ReadOnly モードと ReadWrite モードの間で切り替える](switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md) </span><span class="sxs-lookup"><span data-stu-id="571e2-144">[Switch an Analysis Services database between ReadOnly and ReadWrite modes](switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md) </span></span>  
 <span data-ttu-id="571e2-145">[Detach 要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element) </span><span class="sxs-lookup"><span data-stu-id="571e2-145">[Detach Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element) </span></span>  
 [<span data-ttu-id="571e2-146">Attach 要素</span><span class="sxs-lookup"><span data-stu-id="571e2-146">Attach Element</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element)  
  
  
