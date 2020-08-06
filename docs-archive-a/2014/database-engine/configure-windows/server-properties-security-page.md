---
title: サーバーのプロパティ ([セキュリティ] ページ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.security.f1
ms.assetid: b8a131c7-e7bd-4203-bf26-234f1ebfe622
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5f45c0a04a0d7cc627901d8de24175f1d63a99fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645845"
---
# <a name="server-properties-security-page"></a><span data-ttu-id="87159-102">[サーバーのプロパティ] ([セキュリティ] ページ)</span><span class="sxs-lookup"><span data-stu-id="87159-102">Server Properties (Security Page)</span></span>
  <span data-ttu-id="87159-103">このページを使用すると、サーバー セキュリティ オプションを表示したり変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="87159-103">Use this page to view or modify your server security options.</span></span>  
  
## <a name="server-authentication"></a><span data-ttu-id="87159-104">[サーバー認証]</span><span class="sxs-lookup"><span data-stu-id="87159-104">Server Authentication</span></span>  
 <span data-ttu-id="87159-105">**[Windows 認証モード]**</span><span class="sxs-lookup"><span data-stu-id="87159-105">**Windows Authentication mode**</span></span>  
 <span data-ttu-id="87159-106">Windows 認証を使用して、試行された接続を検証します。</span><span class="sxs-lookup"><span data-stu-id="87159-106">Uses Windows Authentication to validate attempted connections.</span></span> <span data-ttu-id="87159-107">セキュリティ モードが変更されたときに **sa** パスワードが空白の場合、ユーザーに **sa** パスワードの入力を求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="87159-107">If the **sa** password is blank when the security mode is being changed, the user is prompted to enter an **sa** password.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="87159-108">Windows 認証は、SQL Server 認証よりもはるかに安全性に優れています。</span><span class="sxs-lookup"><span data-stu-id="87159-108">Windows Authentication is much more secure than SQL Server Authentication.</span></span> <span data-ttu-id="87159-109">可能な場合は、Windows 認証を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="87159-109">When possible, you should use Windows Authentication.</span></span>  
  
 <span data-ttu-id="87159-110">**[SQL Server 認証モードと Windows 認証モード]**</span><span class="sxs-lookup"><span data-stu-id="87159-110">**SQL Server and Windows Authentication mode**</span></span>  
 <span data-ttu-id="87159-111">旧バージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]との互換性を維持するために、混合モード認証を使用して接続試行を検証します。</span><span class="sxs-lookup"><span data-stu-id="87159-111">Uses mixed mode authentication to verify attempted connections, for backward compatibility with earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="87159-112">セキュリティ モードが変更されたときに **sa** パスワードが空白の場合、ユーザーに **sa** パスワードの入力を求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="87159-112">If the **sa** password is blank when the security mode is being changed, the user is prompted to enter an **sa** password.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="87159-113">セキュリティ構成を変更するには、サービスを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="87159-113">Changing the security configuration requires a restart of the service.</span></span> <span data-ttu-id="87159-114">[サーバー認証] を [SQL Server 認証モードと Windows 認証モード] に変更する場合、SA アカウントは自動的に有効にはなりません。</span><span class="sxs-lookup"><span data-stu-id="87159-114">When changing the Server Authentication to SQL Server and Windows Authentication mode the SA account is not automatically enabled.</span></span> <span data-ttu-id="87159-115">SA アカウントを使用するには、ENABLE オプションを指定して [ALTER LOGIN](/sql/t-sql/statements/alter-login-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="87159-115">To use the SA account, execute [ALTER LOGIN](/sql/t-sql/statements/alter-login-transact-sql) with the ENABLE option.</span></span>  
  
## <a name="login-auditing"></a><span data-ttu-id="87159-116">[ログインの監査]</span><span class="sxs-lookup"><span data-stu-id="87159-116">Login Auditing</span></span>  
 <span data-ttu-id="87159-117">**なし**</span><span class="sxs-lookup"><span data-stu-id="87159-117">**None**</span></span>  
 <span data-ttu-id="87159-118">ログインの監査をオフにします。</span><span class="sxs-lookup"><span data-stu-id="87159-118">Turns off login auditing.</span></span>  
  
 <span data-ttu-id="87159-119">**[失敗したログインのみ]**</span><span class="sxs-lookup"><span data-stu-id="87159-119">**Failed logins only**</span></span>  
 <span data-ttu-id="87159-120">成功しなかったログインのみを監査します。</span><span class="sxs-lookup"><span data-stu-id="87159-120">Audits unsuccessful logins only.</span></span>  
  
 <span data-ttu-id="87159-121">**[成功したログインのみ]**</span><span class="sxs-lookup"><span data-stu-id="87159-121">**Successful logins only**</span></span>  
 <span data-ttu-id="87159-122">成功したログインのみを監査します。</span><span class="sxs-lookup"><span data-stu-id="87159-122">Audits successful logins only.</span></span>  
  
 <span data-ttu-id="87159-123">**[失敗したログインと成功したログインの両方]**</span><span class="sxs-lookup"><span data-stu-id="87159-123">**Both failed and successful logins**</span></span>  
 <span data-ttu-id="87159-124">すべてのログイン試行を監査します。</span><span class="sxs-lookup"><span data-stu-id="87159-124">Audits all login attempts.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="87159-125">監査レベルを変更するには、サービスを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="87159-125">Changing the audit level requires restarting the service.</span></span>  
  
## <a name="server-proxy-account"></a><span data-ttu-id="87159-126">[サーバーのプロキシ アカウント]</span><span class="sxs-lookup"><span data-stu-id="87159-126">Server Proxy Account</span></span>  
 <span data-ttu-id="87159-127">**[サーバーのプロキシ アカウントを有効にする]**</span><span class="sxs-lookup"><span data-stu-id="87159-127">**Enable server proxy account**</span></span>  
 <span data-ttu-id="87159-128">**xp_cmdshell**で使用されるアカウントを有効にします。</span><span class="sxs-lookup"><span data-stu-id="87159-128">Enables an account for use by **xp_cmdshell**.</span></span> <span data-ttu-id="87159-129">オペレーティング システム コマンドの実行中に、プロキシ アカウントを使用してログイン、サーバー ロール、データベース ロールの権限を借用します。</span><span class="sxs-lookup"><span data-stu-id="87159-129">Proxy accounts allow for the impersonation of logins, server roles, and database roles when an operating system command is being executed.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="87159-130">サーバー プロキシ アカウントで使用されるログインには、目的の操作を実行するための必要最低限の権限を与えます。</span><span class="sxs-lookup"><span data-stu-id="87159-130">The login used by the server proxy account should have the least privileges required to perform the intended work.</span></span> <span data-ttu-id="87159-131">プロキシ アカウントに過度の権限を与えると、悪意あるユーザーに利用され、システム セキュリティが脅かされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="87159-131">Excessive privileges for the proxy account could be used by a malicious user to compromise your system security.</span></span>  
  
 <span data-ttu-id="87159-132">**[プロキシ アカウント]**</span><span class="sxs-lookup"><span data-stu-id="87159-132">**Proxy account**</span></span>  
 <span data-ttu-id="87159-133">使用されるプロキシ アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="87159-133">Specify the proxy account used.</span></span>  
  
 <span data-ttu-id="87159-134">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="87159-134">**Password**</span></span>  
 <span data-ttu-id="87159-135">プロキシ アカウントのパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="87159-135">Specify the password for the proxy account.</span></span>  
  
## <a name="options"></a><span data-ttu-id="87159-136">Options</span><span class="sxs-lookup"><span data-stu-id="87159-136">Options</span></span>  
 <span data-ttu-id="87159-137">**[C2 監査トレースを有効にする]**</span><span class="sxs-lookup"><span data-stu-id="87159-137">**Enable C2 audit tracing**</span></span>  
 <span data-ttu-id="87159-138">ステートメントおよびオブジェクトへのアクセスの試行をすべて監査し、\MSSQL\Data ディレクトリ ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の既定のインスタンスの場合)、または \MSSQL$*instancename*\Data ディレクトリ ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の名前付きインスタンスの場合) のファイルに記録します。</span><span class="sxs-lookup"><span data-stu-id="87159-138">Audits all attempts to access statements and objects and records them to a file in the \MSSQL\Data directory for default instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or the \MSSQL$*instancename*\Data directory for named instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="87159-139">詳細については、「 [c2 audit mode サーバー構成オプション](c2-audit-mode-server-configuration-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87159-139">For more information, see [c2 audit mode Server Configuration Option](c2-audit-mode-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="87159-140">**[複数データベース間で所有権を連係する]**</span><span class="sxs-lookup"><span data-stu-id="87159-140">**Cross database ownership chaining**</span></span>  
 <span data-ttu-id="87159-141">オンにすると、データベースを複数データベースにまたがる所有権のソースまたはターゲットにすることができます。</span><span class="sxs-lookup"><span data-stu-id="87159-141">Select to allow the database to be the source or target of a cross-database ownership chain.</span></span> <span data-ttu-id="87159-142">詳細については、「 [cross db ownership chaining サーバー構成オプション](cross-db-ownership-chaining-server-configuration-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87159-142">For more information, see [cross db ownership chaining Server Configuration Option](cross-db-ownership-chaining-server-configuration-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87159-143">参照</span><span class="sxs-lookup"><span data-stu-id="87159-143">See Also</span></span>  
 [<span data-ttu-id="87159-144">サーバー構成オプション &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="87159-144">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
