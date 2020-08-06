---
title: MSSQLSERVER_916 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 916 (Database Engine error)
ms.assetid: 73eb6581-99fe-49a5-9b42-e239d7ffe27f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ee67c1e2f67c3c7903c67082ec3793d9d9820061
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640002"
---
# <a name="mssqlserver_916"></a><span data-ttu-id="c6fd2-102">MSSQLSERVER_916</span><span class="sxs-lookup"><span data-stu-id="c6fd2-102">MSSQLSERVER_916</span></span>
    
## <a name="details"></a><span data-ttu-id="c6fd2-103">詳細</span><span class="sxs-lookup"><span data-stu-id="c6fd2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c6fd2-104">製品名</span><span class="sxs-lookup"><span data-stu-id="c6fd2-104">Product Name</span></span>|<span data-ttu-id="c6fd2-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c6fd2-105">SQL Server</span></span>|  
|<span data-ttu-id="c6fd2-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="c6fd2-106">Event ID</span></span>|<span data-ttu-id="c6fd2-107">916</span><span class="sxs-lookup"><span data-stu-id="c6fd2-107">916</span></span>|  
|<span data-ttu-id="c6fd2-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="c6fd2-108">Event Source</span></span>|<span data-ttu-id="c6fd2-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c6fd2-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c6fd2-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="c6fd2-110">Component</span></span>|<span data-ttu-id="c6fd2-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c6fd2-111">SQLEngine</span></span>|  
|<span data-ttu-id="c6fd2-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="c6fd2-112">Symbolic Name</span></span>|<span data-ttu-id="c6fd2-113">NOTUSER</span><span class="sxs-lookup"><span data-stu-id="c6fd2-113">NOTUSER</span></span>|  
|<span data-ttu-id="c6fd2-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="c6fd2-114">Message Text</span></span>|<span data-ttu-id="c6fd2-115">現在のセキュリティ コンテキストでは、サーバー プリンシパル "%.\*ls" はデータベース "%.\*ls" にアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="c6fd2-115">The server principal "%.\*ls" is not able to access the database "%.\*ls" under the current security context.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c6fd2-116">説明</span><span class="sxs-lookup"><span data-stu-id="c6fd2-116">Explanation</span></span>  
 <span data-ttu-id="c6fd2-117">ログインに、指定されたデータベースに接続するために必要な権限がありません。</span><span class="sxs-lookup"><span data-stu-id="c6fd2-117">The login does not have sufficient permissions to connect to the named database.</span></span> <span data-ttu-id="c6fd2-118">この [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続することができ、データベースの特定の権限を持っていないログインには、guest ユーザーの権限が与えられます。</span><span class="sxs-lookup"><span data-stu-id="c6fd2-118">Logins that can connect to this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] but that do not have specific permissions in a database receive the permissions of the guest user.</span></span> <span data-ttu-id="c6fd2-119">これは、1 つのデータベース内のユーザーが、権限を持たない別のデータベースに接続することを防ぐためのセキュリティ措置です。</span><span class="sxs-lookup"><span data-stu-id="c6fd2-119">This is a security measure to prevent users in one database from connecting to other databases where they do not have privileges.</span></span> <span data-ttu-id="c6fd2-120">このエラー メッセージは、指定されたデータベースに対する CONNECT 権限を guest ユーザーが持っていないため、TRUSTWORTHY プロパティが設定されないときに生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c6fd2-120">This error message can occur when the guest user does not have CONNECT permission to the named database and the trustworthy property is not set.</span></span> <span data-ttu-id="c6fd2-121">このエラー メッセージは、指定されたデータベースに対する CONNECT 権限を guest ユーザーが持っていないときに生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c6fd2-121">This error message can occur when the guest user does not have CONNECT permission to the named database.</span></span>  
  
 <span data-ttu-id="c6fd2-122">msdb データベースに対する CONNECT 権限が拒否または取り消された場合、オブジェクト エクスプローラーから各データベースのポリシー ベースの管理の状態を表示しようとすると、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でこのエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c6fd2-122">When CONNECT permission to the msdb database is denied or revoked, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] can receive this error when Object Explorer tries to show the Policy Based Management status of each database.</span></span> <span data-ttu-id="c6fd2-123">オブジェクト エクスプローラーでは、現在のログインの権限を使用して、この情報を取得するために msdb データベースに対してクエリを実行します。このとき、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="c6fd2-123">Object Explorer uses the permissions of the current login to query the msdb database for this information, which causes the error.</span></span> <span data-ttu-id="c6fd2-124">また、次のエラー メッセージも表示されます。</span><span class="sxs-lookup"><span data-stu-id="c6fd2-124">The following error message also occurs:</span></span>  
  
 <span data-ttu-id="c6fd2-125">この要求のデータを取得できませんでした。</span><span class="sxs-lookup"><span data-stu-id="c6fd2-125">Failed to retrieve data for this request.</span></span> <span data-ttu-id="c6fd2-126">(Microsoft.SqlServer.Management.Sdk.Sfc)</span><span class="sxs-lookup"><span data-stu-id="c6fd2-126">(Microsoft.SqlServer.Management.Sdk.Sfc)</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c6fd2-127">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="c6fd2-127">User Action</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="c6fd2-128">このセキュリティ措置を回避する前に、各種データベースで認証されているユーザーについて明確に把握している必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6fd2-128">Before circumventing this security measure be sure to have a clear understanding of users are authenticated in various databases.</span></span> <span data-ttu-id="c6fd2-129">次の方法を実行すると、あるデータベースへの接続権限を持つユーザーが他のデータベースに接続できるようになり、悪意のあるユーザーにデータが公開される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c6fd2-129">The following methods may allow users that have permissions in one database to connect to other databases which could expose data to a malicious user.</span></span> <span data-ttu-id="c6fd2-130">包含データベースが有効化されている場合は、次の手順を実行すると、1 つのデータベースのデータベース所有者が、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス上で別のデータベースへのアクセス権を付与できるようになることがあります。</span><span class="sxs-lookup"><span data-stu-id="c6fd2-130">When contained databases are enabled, the following steps can allow database owners in one database to grant access to other database on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="c6fd2-131">次のいずれかの方法でデータベースに接続できます。</span><span class="sxs-lookup"><span data-stu-id="c6fd2-131">You can connect to the database in one of the following ways:</span></span>  
  
-   <span data-ttu-id="c6fd2-132">指定されたデータベースにアクセスするための権限を特定のログインに許可します。</span><span class="sxs-lookup"><span data-stu-id="c6fd2-132">Grant the specific login access to the named database.</span></span> <span data-ttu-id="c6fd2-133">次の例では、`Adventure-Works\Larry` データベースにアクセスするための権限をログイン `msdb` に許可します。</span><span class="sxs-lookup"><span data-stu-id="c6fd2-133">The following example grants the login `Adventure-Works\Larry` access to the `msdb` database.</span></span>  
  
     <span data-ttu-id="c6fd2-134">USE msdb ;</span><span class="sxs-lookup"><span data-stu-id="c6fd2-134">USE msdb ;</span></span>  
  
     <span data-ttu-id="c6fd2-135">GO</span><span class="sxs-lookup"><span data-stu-id="c6fd2-135">GO</span></span>  
  
     <span data-ttu-id="c6fd2-136">GRANT CONNECT TO [Adventure-Works\Larry] ;</span><span class="sxs-lookup"><span data-stu-id="c6fd2-136">GRANT CONNECT TO [Adventure-Works\Larry] ;</span></span>  
  
-   <span data-ttu-id="c6fd2-137">エラー メッセージで指定されたデータベースに対する CONNECT 権限を guest ユーザーに許可します。</span><span class="sxs-lookup"><span data-stu-id="c6fd2-137">Grant the CONNECT permission to the database named in the error message for the guest user.</span></span> <span data-ttu-id="c6fd2-138">次の例では、`CONNECT` データベースに対する `msdb` 権限を、`guest` ユーザーに許可します。</span><span class="sxs-lookup"><span data-stu-id="c6fd2-138">The following example grants the `CONNECT` permission to the `msdb` database for the user `guest`.</span></span>  
  
     <span data-ttu-id="c6fd2-139">USE msdb ;</span><span class="sxs-lookup"><span data-stu-id="c6fd2-139">USE msdb ;</span></span>  
  
     <span data-ttu-id="c6fd2-140">GO</span><span class="sxs-lookup"><span data-stu-id="c6fd2-140">GO</span></span>  
  
     <span data-ttu-id="c6fd2-141">GRANT CONNECT TO guest ;</span><span class="sxs-lookup"><span data-stu-id="c6fd2-141">GRANT CONNECT TO guest ;</span></span>  
  
-   <span data-ttu-id="c6fd2-142">ユーザーを認証したデータベースの TRUSTWORTHY プロパティを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c6fd2-142">Enable the TRUSTWORTHY property on the database that has authenticated the user.</span></span>  
  
     `ALTER DATABASE AdventureWorks SET TRUSTWORTHY ON;`  
  
  
