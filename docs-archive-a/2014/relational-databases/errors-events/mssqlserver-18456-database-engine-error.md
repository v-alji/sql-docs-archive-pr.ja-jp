---
title: MSSQLSERVER_18456 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18456 (Database Engine error)
ms.assetid: c417631d-be1f-42e0-8844-9f92c77e11f7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f5addb6bfb9d056d9f1796749ae629d4150102a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715350"
---
# <a name="mssqlserver_18456"></a><span data-ttu-id="2d321-102">MSSQLSERVER_18456</span><span class="sxs-lookup"><span data-stu-id="2d321-102">MSSQLSERVER_18456</span></span>
    
## <a name="details"></a><span data-ttu-id="2d321-103">詳細</span><span class="sxs-lookup"><span data-stu-id="2d321-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2d321-104">製品名</span><span class="sxs-lookup"><span data-stu-id="2d321-104">Product Name</span></span>|<span data-ttu-id="2d321-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2d321-105">SQL Server</span></span>|  
|<span data-ttu-id="2d321-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2d321-106">Event ID</span></span>|<span data-ttu-id="2d321-107">18456</span><span class="sxs-lookup"><span data-stu-id="2d321-107">18456</span></span>|  
|<span data-ttu-id="2d321-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="2d321-108">Event Source</span></span>|<span data-ttu-id="2d321-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2d321-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2d321-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="2d321-110">Component</span></span>|<span data-ttu-id="2d321-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2d321-111">SQLEngine</span></span>|  
|<span data-ttu-id="2d321-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="2d321-112">Symbolic Name</span></span>|<span data-ttu-id="2d321-113">LOGON_FAILED</span><span class="sxs-lookup"><span data-stu-id="2d321-113">LOGON_FAILED</span></span>|  
|<span data-ttu-id="2d321-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="2d321-114">Message Text</span></span>|<span data-ttu-id="2d321-115">ユーザー '%.\*ls'.%.\*ls はログインできませんでした</span><span class="sxs-lookup"><span data-stu-id="2d321-115">Login failed for user '%.\*ls'.%.\*ls</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2d321-116">説明</span><span class="sxs-lookup"><span data-stu-id="2d321-116">Explanation</span></span>  
 <span data-ttu-id="2d321-117">無効なパスワードまたはユーザー名の使用による認証の失敗によって接続の試行が拒否された場合、クライアントに次のようのメッセージが表示されます。"ユーザー '<user_name>' はログインできませんでした。</span><span class="sxs-lookup"><span data-stu-id="2d321-117">When a connection attempt is rejected because of an authentication failure that involves a bad password or user name, a message similar to the following is returned to the client:  "Login failed for user '<user_name>'.</span></span> <span data-ttu-id="2d321-118">(Microsoft SQL Server、エラー:18456)"。</span><span class="sxs-lookup"><span data-stu-id="2d321-118">(Microsoft SQL Server, Error: 18456)".</span></span>  
  
 <span data-ttu-id="2d321-119">クライアントに返される追加情報には、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="2d321-119">Additional information returned to the client includes the following:</span></span>  
  
 <span data-ttu-id="2d321-120">"ユーザー '<user_name>' はログインできませんでした。</span><span class="sxs-lookup"><span data-stu-id="2d321-120">"Login failed for user '<user_name>'.</span></span> <span data-ttu-id="2d321-121">(.Net SqlClient Data Provider)"</span><span class="sxs-lookup"><span data-stu-id="2d321-121">(.Net SqlClient Data Provider)"</span></span>  
  
 -----------------------------\-  
  
 <span data-ttu-id="2d321-122">"サーバー名: <computer_name>"</span><span class="sxs-lookup"><span data-stu-id="2d321-122">"Server Name: <computer_name>"</span></span>  
  
 <span data-ttu-id="2d321-123">"エラー番号:18456"</span><span class="sxs-lookup"><span data-stu-id="2d321-123">"Error Number: 18456"</span></span>  
  
 <span data-ttu-id="2d321-124">"重大度:14"</span><span class="sxs-lookup"><span data-stu-id="2d321-124">"Severity: 14"</span></span>  
  
 <span data-ttu-id="2d321-125">"状態:1"</span><span class="sxs-lookup"><span data-stu-id="2d321-125">"State: 1"</span></span>  
  
 <span data-ttu-id="2d321-126">"行番号:65536"</span><span class="sxs-lookup"><span data-stu-id="2d321-126">"Line Number: 65536"</span></span>  
  
 <span data-ttu-id="2d321-127">次のメッセージが返されることもあります。</span><span class="sxs-lookup"><span data-stu-id="2d321-127">The following message might also be returned:</span></span>  
  
 <span data-ttu-id="2d321-128">"メッセージ 18456、レベル 14、状態 1、サーバー <computer_name>、行 1"</span><span class="sxs-lookup"><span data-stu-id="2d321-128">"Msg 18456, Level 14, State 1, Server <computer_name>, Line 1"</span></span>  
  
 <span data-ttu-id="2d321-129">"ユーザー '<user_name>' はログインできませんでした。"</span><span class="sxs-lookup"><span data-stu-id="2d321-129">"Login failed for user '<user_name>'."</span></span>  
  
## <a name="additional-error-information"></a><span data-ttu-id="2d321-130">エラーに関する追加情報</span><span class="sxs-lookup"><span data-stu-id="2d321-130">Additional Error Information</span></span>  
 <span data-ttu-id="2d321-131">セキュリティ向上のために、クライアントに返されるエラー メッセージでは、認証エラーの性質を意図的に非表示にしています。</span><span class="sxs-lookup"><span data-stu-id="2d321-131">To increase security, the error message that is returned to the client deliberately hides the nature of the authentication error.</span></span> <span data-ttu-id="2d321-132">ただし [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログでは、対応するエラーに、認証失敗条件と対応付けられるエラー状態が含まれています。</span><span class="sxs-lookup"><span data-stu-id="2d321-132">However, in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, a corresponding error contains an error state that maps to an authentication failure condition.</span></span> <span data-ttu-id="2d321-133">ログインできない理由を判断するには、エラー状態を次の一覧と比較してください。</span><span class="sxs-lookup"><span data-stu-id="2d321-133">Compare the error state to the following list to determine the reason for the login failure.</span></span>  
  
|<span data-ttu-id="2d321-134">State</span><span class="sxs-lookup"><span data-stu-id="2d321-134">State</span></span>|<span data-ttu-id="2d321-135">説明</span><span class="sxs-lookup"><span data-stu-id="2d321-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2d321-136">1</span><span class="sxs-lookup"><span data-stu-id="2d321-136">1</span></span>|<span data-ttu-id="2d321-137">エラー情報を表示できません。</span><span class="sxs-lookup"><span data-stu-id="2d321-137">Error information is not available.</span></span> <span data-ttu-id="2d321-138">通常、この状態は、エラーの詳細情報を受け取る権限がないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="2d321-138">This state usually means you do not have permission to receive the error details.</span></span> <span data-ttu-id="2d321-139">詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="2d321-139">Contact your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrator for more information.</span></span>|  
|<span data-ttu-id="2d321-140">2</span><span class="sxs-lookup"><span data-stu-id="2d321-140">2</span></span>|<span data-ttu-id="2d321-141">ユーザー ID が無効です。</span><span class="sxs-lookup"><span data-stu-id="2d321-141">User ID is not valid.</span></span>|  
|<span data-ttu-id="2d321-142">5</span><span class="sxs-lookup"><span data-stu-id="2d321-142">5</span></span>|<span data-ttu-id="2d321-143">ユーザー ID が無効です。</span><span class="sxs-lookup"><span data-stu-id="2d321-143">User ID is not valid.</span></span>|  
|<span data-ttu-id="2d321-144">6</span><span class="sxs-lookup"><span data-stu-id="2d321-144">6</span></span>|<span data-ttu-id="2d321-145">SQL Server 認証で Windows ログイン名を使用しようとしました。</span><span class="sxs-lookup"><span data-stu-id="2d321-145">An attempt was made to use a Windows login name with SQL Server Authentication.</span></span>|  
|<span data-ttu-id="2d321-146">7</span><span class="sxs-lookup"><span data-stu-id="2d321-146">7</span></span>|<span data-ttu-id="2d321-147">ログインが無効で、パスワードが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="2d321-147">Login is disabled, and the password is incorrect.</span></span>|  
|<span data-ttu-id="2d321-148">8</span><span class="sxs-lookup"><span data-stu-id="2d321-148">8</span></span>|<span data-ttu-id="2d321-149">パスワードが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="2d321-149">The password is incorrect.</span></span>|  
|<span data-ttu-id="2d321-150">9</span><span class="sxs-lookup"><span data-stu-id="2d321-150">9</span></span>|<span data-ttu-id="2d321-151">パスワードが無効です。</span><span class="sxs-lookup"><span data-stu-id="2d321-151">Password is not valid.</span></span>|  
|<span data-ttu-id="2d321-152">11</span><span class="sxs-lookup"><span data-stu-id="2d321-152">11</span></span>|<span data-ttu-id="2d321-153">ログインは有効ですが、サーバー アクセスに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="2d321-153">Login is valid, but server access failed.</span></span> <span data-ttu-id="2d321-154">このエラーで考えられる原因の 1 つは、Windows ユーザーがローカル管理者グループのメンバーとして [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] へのアクセス権限を持っている一方で、Windows から管理者資格情報が提供されないことです。</span><span class="sxs-lookup"><span data-stu-id="2d321-154">One possible cause of this error is when the Windows user has access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a member of the local administrators group, but Windows is not providing administrator credentials.</span></span> <span data-ttu-id="2d321-155">接続するには、 **[管理者として実行]** オプションを使用して接続プログラムを開始してから、その Windows ユーザーを特定のログインとして [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に追加します。</span><span class="sxs-lookup"><span data-stu-id="2d321-155">To connect, start the connecting program using the **Run as administrator** option, and then add the Windows user to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a specific login.</span></span>|  
|<span data-ttu-id="2d321-156">12</span><span class="sxs-lookup"><span data-stu-id="2d321-156">12</span></span>|<span data-ttu-id="2d321-157">ログインは有効なログインですが、サーバー アクセスに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="2d321-157">Login is valid login, but server access failed.</span></span>|  
|<span data-ttu-id="2d321-158">18</span><span class="sxs-lookup"><span data-stu-id="2d321-158">18</span></span>|<span data-ttu-id="2d321-159">パスワードを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d321-159">Password must be changed.</span></span>|  
  
 <span data-ttu-id="2d321-160">エラー状態は他にも存在し、予期しない内部処理エラーを示します。</span><span class="sxs-lookup"><span data-stu-id="2d321-160">Other error states exist and signify an unexpected internal processing error.</span></span>  
  
 <span data-ttu-id="2d321-161">**その他の特殊な原因**</span><span class="sxs-lookup"><span data-stu-id="2d321-161">**An additional unusual possible cause**</span></span>  
  
 <span data-ttu-id="2d321-162">エラーの理由として、 **"SQL 認証を使用したログインに失敗しました。サーバーは、Windows 認証専用に構成されています。**</span><span class="sxs-lookup"><span data-stu-id="2d321-162">The error reason **An attempt to login using SQL authentication failed. Server is configured for Windows authentication only.**</span></span> <span data-ttu-id="2d321-163">次の状況で返される場合があります。</span><span class="sxs-lookup"><span data-stu-id="2d321-163">can be returned in the following situations.</span></span>  
  
-   <span data-ttu-id="2d321-164">サーバーが混合モード認証で構成され、ODBC 接続で TCP プロトコルを使用し、接続でセキュリティ接続を使用することが明示的に指定されていない場合。</span><span class="sxs-lookup"><span data-stu-id="2d321-164">When the server is configured for mixed mode authentication, and an ODBC connection uses the TCP protocol, and the connection does not explicitly specify that the connection should use a trusted connection.</span></span>  
  
-   <span data-ttu-id="2d321-165">サーバーが混合認証モードで構成され、ODBC 接続で名前付きパイプが使用され、クライアントで名前付きパイプを開くために使用された資格情報が自動的にユーザーの権限を借用するために使用され、接続でセキュリティ接続を使用することが明示的に指定されていない場合。</span><span class="sxs-lookup"><span data-stu-id="2d321-165">When the server is configured for mixed mode authentication, and an ODBC connection uses named pipes, and the credentials the client used to open the named pipe are used to automatically impersonate the user, and the connection does not explicitly specify that the connection should use a trusted connection.</span></span>  
  
 <span data-ttu-id="2d321-166">この問題を解決するには、接続文字列に `TRUSTED_CONNECTION = TRUE` を含めます。</span><span class="sxs-lookup"><span data-stu-id="2d321-166">To resolve this issue, include `TRUSTED_CONNECTION = TRUE` in the connection string.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="2d321-167">例</span><span class="sxs-lookup"><span data-stu-id="2d321-167">Examples</span></span>  
 <span data-ttu-id="2d321-168">この例では、認証エラー状態は 8 です。</span><span class="sxs-lookup"><span data-stu-id="2d321-168">In this example, the authentication error state is 8.</span></span> <span data-ttu-id="2d321-169">これは、パスワードが正しくないことを示します。</span><span class="sxs-lookup"><span data-stu-id="2d321-169">This indicates that the password is incorrect.</span></span>  
  
|<span data-ttu-id="2d321-170">Date</span><span class="sxs-lookup"><span data-stu-id="2d321-170">Date</span></span>|<span data-ttu-id="2d321-171">source</span><span class="sxs-lookup"><span data-stu-id="2d321-171">Source</span></span>|<span data-ttu-id="2d321-172">Message</span><span class="sxs-lookup"><span data-stu-id="2d321-172">Message</span></span>|  
|----------|------------|-------------|  
|<span data-ttu-id="2d321-173">2007-12-05 20:12:56.34</span><span class="sxs-lookup"><span data-stu-id="2d321-173">2007-12-05 20:12:56.34</span></span>|<span data-ttu-id="2d321-174">ログオン</span><span class="sxs-lookup"><span data-stu-id="2d321-174">Logon</span></span>|<span data-ttu-id="2d321-175">エラー:18456、重大度:14、状態:8.</span><span class="sxs-lookup"><span data-stu-id="2d321-175">Error: 18456, Severity: 14, State: 8.</span></span>|  
|<span data-ttu-id="2d321-176">2007-12-05 20:12:56.34</span><span class="sxs-lookup"><span data-stu-id="2d321-176">2007-12-05 20:12:56.34</span></span>|<span data-ttu-id="2d321-177">ログオン</span><span class="sxs-lookup"><span data-stu-id="2d321-177">Logon</span></span>|<span data-ttu-id="2d321-178">ユーザー '<user_name>' はログインできませんでした。</span><span class="sxs-lookup"><span data-stu-id="2d321-178">Login failed for user '<user_name>'.</span></span> <span data-ttu-id="2d321-179">[CLIENT: \<ip address>]</span><span class="sxs-lookup"><span data-stu-id="2d321-179">[CLIENT: \<ip address>]</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="2d321-180">Windows 認証モードを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールし、後で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証モードと Windows 認証モードに変更すると、**sa** ログインは最初は無効になります。</span><span class="sxs-lookup"><span data-stu-id="2d321-180">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed using Windows Authentication mode and is later changed to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows Authentication mode, the **sa** login is initially disabled.</span></span> <span data-ttu-id="2d321-181">これにより、次の状態 7 のエラーが発生します。"ユーザー 'sa' はログインできませんでした。"**sa** ログインを有効にするには、「[サーバーの認証モードの変更](../../database-engine/configure-windows/change-server-authentication-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d321-181">This causes the state 7 error: "Login failed for user 'sa'." To enable the **sa** login, see [Change Server Authentication Mode](../../database-engine/configure-windows/change-server-authentication-mode.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2d321-182">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="2d321-182">User Action</span></span>  
 <span data-ttu-id="2d321-183">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用して接続しようとしている場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が混合モード認証で構成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2d321-183">If you are trying to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, verify that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured in Mixed Authentication Mode.</span></span>  
  
 <span data-ttu-id="2d321-184">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用して接続しようとしている場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインが存在し、そのログインのスペルを正しく入力していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2d321-184">If you are trying to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, verify that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login exists and that you have spelled it properly.</span></span>  
  
 <span data-ttu-id="2d321-185">Windows 認証を使用して接続しようとしている場合は、正しいドメインに適切にログインしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2d321-185">If you are trying to connect using Windows Authentication, verify that you are properly logged into the correct domain.</span></span>  
  
 <span data-ttu-id="2d321-186">エラーが状態 1 を示している場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="2d321-186">If your error indicates state 1, contact your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrator.</span></span>  
  
 <span data-ttu-id="2d321-187">管理者の資格情報を使用して接続する場合、 **[管理者として実行]** オプションを使用してアプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="2d321-187">If you are trying to connect using your administrator credentials, start you application by using the **Run as Administrator** option.</span></span> <span data-ttu-id="2d321-188">接続したら、Windows ユーザーを個別のログインとして追加します。</span><span class="sxs-lookup"><span data-stu-id="2d321-188">When connected, add your Windows user as an individual login.</span></span>  
  
 <span data-ttu-id="2d321-189">[!INCLUDE[ssDE](../../includes/ssde-md.md)]で包含データベースがサポートされる場合、包含データベース ユーザーへの移行後にそのログインが削除されていないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2d321-189">If the [!INCLUDE[ssDE](../../includes/ssde-md.md)] supports contained databases, confirm that the login was not deleted after migration to a contained database user.</span></span>  
  
 <span data-ttu-id="2d321-190">ローカルの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続している場合、**NT AUTHORITY\NETWORK SERVICE** で実行されているサービスからの接続は、コンピューターの完全修飾ドメイン名を使用して認証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d321-190">When connecting locally to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], connections from services running under **NT AUTHORITY\NETWORK SERVICE** must authenticate using the computers fully qualified domain name.</span></span> <span data-ttu-id="2d321-191">詳細については、このトピックの「[方法: ASP.NET で Network Service アカウントを使用してリソースにアクセスする方法](https://msdn.microsoft.com/library/ff647402.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d321-191">For more information, see [How To: Use the Network Service Account to Access Resources in ASP.NET](https://msdn.microsoft.com/library/ff647402.aspx)</span></span>  
  
  
