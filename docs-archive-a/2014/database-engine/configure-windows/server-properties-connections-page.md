---
title: サーバーのプロパティ ([接続] ページ) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.connections.f1
ms.assetid: 33be8ac5-12dd-4b8a-99e0-68261c219dd2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 80943bc542209fd34cf83e8db7aa76becd04194a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738707"
---
# <a name="server-properties-connections-page"></a><span data-ttu-id="05801-102">[サーバーのプロパティ] ([接続] ページ)</span><span class="sxs-lookup"><span data-stu-id="05801-102">Server Properties (Connections Page)</span></span>
  <span data-ttu-id="05801-103">このページを使用すると、接続オプションを表示したり変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="05801-103">Use this page to view or modify your connection options.</span></span>  
  
## <a name="connections"></a><span data-ttu-id="05801-104">接続</span><span class="sxs-lookup"><span data-stu-id="05801-104">Connections</span></span>  
 <span data-ttu-id="05801-105">**[コンカレント接続の最大数 (0 = 無制限)]**</span><span class="sxs-lookup"><span data-stu-id="05801-105">**Maximum number of concurrent connections (0 = unlimited)**</span></span>  
 <span data-ttu-id="05801-106">0 以外の値に設定した場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で許可される接続の数を制限します。</span><span class="sxs-lookup"><span data-stu-id="05801-106">If set to a value other than zero, limits the number of connections that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will allow.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="05801-107">この値を 1 や 2 などの小さい値に設定することにより、管理者が接続してサーバー管理できないように指定できます。ただし、専用管理者接続には常に接続できます。</span><span class="sxs-lookup"><span data-stu-id="05801-107">Setting this to a small value, such as 1 or 2, can prevent administrators from connecting to administer the server; however, the Dedicated Admin Connection can always connect.</span></span>  
  
## <a name="default-connection-options"></a><span data-ttu-id="05801-108">[既定の接続オプション]</span><span class="sxs-lookup"><span data-stu-id="05801-108">Default Connection Options</span></span>  
 <span data-ttu-id="05801-109">**Default connection options**</span><span class="sxs-lookup"><span data-stu-id="05801-109">**Default connection options**</span></span>  
 <span data-ttu-id="05801-110">次の表に示すような既定の接続オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="05801-110">Specifies the default connection options, as described in the following table.</span></span>  
  
|<span data-ttu-id="05801-111">構成オプション</span><span class="sxs-lookup"><span data-stu-id="05801-111">Configuration option</span></span>|<span data-ttu-id="05801-112">説明</span><span class="sxs-lookup"><span data-stu-id="05801-112">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="05801-113">**[disable deferred constraint checking]**</span><span class="sxs-lookup"><span data-stu-id="05801-113">**disable deferred constraint checking**</span></span>|<span data-ttu-id="05801-114">中間制約チェックまたは遅延制約チェックを制御します。</span><span class="sxs-lookup"><span data-stu-id="05801-114">Controls interim or deferred constraint checking.</span></span>|  
|<span data-ttu-id="05801-115">**暗黙のトランザクション**</span><span class="sxs-lookup"><span data-stu-id="05801-115">**implicit transactions**</span></span>|<span data-ttu-id="05801-116">ステートメント実行時にトランザクションを暗黙的に開始するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="05801-116">Controls whether a transaction is started implicitly when a statement is run.</span></span>|  
|<span data-ttu-id="05801-117">**[cursor close on commit]**</span><span class="sxs-lookup"><span data-stu-id="05801-117">**cursor close on commit**</span></span>|<span data-ttu-id="05801-118">コミット実行後のカーソルの動作を制御します。</span><span class="sxs-lookup"><span data-stu-id="05801-118">Controls behavior of cursors after a commit operation has been performed.</span></span>|  
|<span data-ttu-id="05801-119">**[ansi warnings]**</span><span class="sxs-lookup"><span data-stu-id="05801-119">**ansi warnings**</span></span>|<span data-ttu-id="05801-120">集計警告の切り詰めと NULL を制御します。</span><span class="sxs-lookup"><span data-stu-id="05801-120">Controls truncation and NULL in aggregate warnings.</span></span>|  
|<span data-ttu-id="05801-121">**[ansi padding]**</span><span class="sxs-lookup"><span data-stu-id="05801-121">**ansi padding**</span></span>|<span data-ttu-id="05801-122">固定長変数の埋め込みを制御します。</span><span class="sxs-lookup"><span data-stu-id="05801-122">Controls padding of fixed-length variables.</span></span>|  
|<span data-ttu-id="05801-123">**[ANSI NULL]**</span><span class="sxs-lookup"><span data-stu-id="05801-123">**ansi nulls**</span></span>|<span data-ttu-id="05801-124">等価演算を使用する場合に `NULL` 処理を制御します。</span><span class="sxs-lookup"><span data-stu-id="05801-124">Controls `NULL` handling when using equality operators.</span></span>|  
|<span data-ttu-id="05801-125">**[arithmetic abort]**</span><span class="sxs-lookup"><span data-stu-id="05801-125">**arithmetic abort**</span></span>|<span data-ttu-id="05801-126">クエリ実行中にオーバーフローまたは 0 除算のエラーが発生した場合に、クエリを終了します。</span><span class="sxs-lookup"><span data-stu-id="05801-126">Terminates a query when an overflow or divide-by-zero error occurs during query execution.</span></span>|  
|<span data-ttu-id="05801-127">**[arithmetic ignore]**</span><span class="sxs-lookup"><span data-stu-id="05801-127">**arithmetic ignore**</span></span>|<span data-ttu-id="05801-128">クエリ実行中にオーバーフローまたは 0 除算エラーが発生した場合に、NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="05801-128">Returns NULL when an overflow or divide-by-zero error occurs during a query.</span></span>|  
|<span data-ttu-id="05801-129">**引用符で囲まれた識別子 (quoted identifier)**</span><span class="sxs-lookup"><span data-stu-id="05801-129">**quoted identifier**</span></span>|<span data-ttu-id="05801-130">式を評価するときに、単一引用符と二重引用符を区別します。</span><span class="sxs-lookup"><span data-stu-id="05801-130">Differentiates between single and double quotation marks when evaluating an expression.</span></span>|  
|<span data-ttu-id="05801-131">**[no count]**</span><span class="sxs-lookup"><span data-stu-id="05801-131">**no count**</span></span>|<span data-ttu-id="05801-132">各ステートメントの最後に返される、何行処理されたかを示すメッセージを表示しないようにします。</span><span class="sxs-lookup"><span data-stu-id="05801-132">Turns off the message returned at the end of each statement that states how many rows were affected.</span></span>|  
|<span data-ttu-id="05801-133">**[ANSI NULL Default On]**</span><span class="sxs-lookup"><span data-stu-id="05801-133">**ansi null default on**</span></span>|<span data-ttu-id="05801-134">ANSI 互換の NULL 値の許可属性を使用するようにセッションの動作を変更します。</span><span class="sxs-lookup"><span data-stu-id="05801-134">Alters the session's behavior to use ANSI compatibility for nullability.</span></span> <span data-ttu-id="05801-135">新しい列で、NULL 値を許可するかどうかが明示的に定義されていない場合は、NULL 値を許可するように定義されます。</span><span class="sxs-lookup"><span data-stu-id="05801-135">New columns defined without explicit nullability are defined to allow nulls.</span></span>|  
|<span data-ttu-id="05801-136">**[ANSI NULL Default Off]**</span><span class="sxs-lookup"><span data-stu-id="05801-136">**ansi null default off**</span></span>|<span data-ttu-id="05801-137">ANSI 互換の NULL 値の許可属性を使用しないようにセッションの動作を変更します。</span><span class="sxs-lookup"><span data-stu-id="05801-137">Alters the session's behavior not to use ANSI compatibility for nullability.</span></span> <span data-ttu-id="05801-138">新しい列で、NULL 値を許容するかどうかが明示的に定義されていない場合は、NULL を許可しないと定義されます。</span><span class="sxs-lookup"><span data-stu-id="05801-138">New columns defined without explicit nullability are defined not to allow nulls.</span></span>|  
|<span data-ttu-id="05801-139">**[concat null yields null]**</span><span class="sxs-lookup"><span data-stu-id="05801-139">**concat null yields null**</span></span>|<span data-ttu-id="05801-140">NULL 値を文字列と連結した場合に、NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="05801-140">Returns NULL when concatenating a NULL value with a string.</span></span>|  
|<span data-ttu-id="05801-141">**[numeric round abort]**</span><span class="sxs-lookup"><span data-stu-id="05801-141">**numeric round abort**</span></span>|<span data-ttu-id="05801-142">式の精度が低下した場合にエラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="05801-142">Generates an error when a loss of precision occurs in an expression.</span></span>|  
|<span data-ttu-id="05801-143">**[xact abort]**</span><span class="sxs-lookup"><span data-stu-id="05801-143">**xact abort**</span></span>|<span data-ttu-id="05801-144">Transact-SQL ステートメントで実行時エラーが発生した場合、トランザクションをロールバックします。</span><span class="sxs-lookup"><span data-stu-id="05801-144">Rolls back a transaction if a Transact-SQL statement raises a run-time error.</span></span>|  
  
 <span data-ttu-id="05801-145">接続オプションの詳細については、オンライン ブックで該当するオプションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="05801-145">For more information on connection options, search Books Online for the specific option.</span></span>  
  
## <a name="remote-server-connections"></a><span data-ttu-id="05801-146">[リモート サーバー接続]</span><span class="sxs-lookup"><span data-stu-id="05801-146">Remote Server Connections</span></span>  
 <span data-ttu-id="05801-147">**[このサーバーへのリモート接続を許可する]**</span><span class="sxs-lookup"><span data-stu-id="05801-147">**Allow remote connections to this server**</span></span>  
 <span data-ttu-id="05801-148">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを実行するリモート サーバーからのストアド プロシージャの実行を制御します。</span><span class="sxs-lookup"><span data-stu-id="05801-148">Controls the execution of stored procedures from remote servers running instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="05801-149">このチェック ボックスをオンにすることは、 **sp_configureremote access** オプションを 1 に設定することと同じです。</span><span class="sxs-lookup"><span data-stu-id="05801-149">Selecting this check box has the same effect as setting the **sp_configureremote access** option to 1.</span></span> <span data-ttu-id="05801-150">このチェック ボックスをオフにすると、ストアド プロシージャはリモート サーバーから実行されません。</span><span class="sxs-lookup"><span data-stu-id="05801-150">Clearing it prevents execution of stored procedures from a remote server.</span></span>  
  
 <span data-ttu-id="05801-151">**[リモート クエリのタイムアウト (秒単位、0 = タイムアウトなし)]**</span><span class="sxs-lookup"><span data-stu-id="05801-151">**Remote query timeout (in seconds, 0 = no timeout)**</span></span>  
 <span data-ttu-id="05801-152">リモート操作の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] タイムアウトまでの時間 (秒) を指定します。既定は 600 秒 (10 分) 間の待機です。</span><span class="sxs-lookup"><span data-stu-id="05801-152">Specifies how long (in seconds) a remote operation may take before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] times out. The default is 600 seconds, or a 10-minute wait.</span></span>  
  
 <span data-ttu-id="05801-153">**[サーバー間通信で使用する分散トランザクションを要求する]**</span><span class="sxs-lookup"><span data-stu-id="05801-153">**Require distributed transactions for server-to-server communication**</span></span>  
 <span data-ttu-id="05801-154">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散トランザクション コーディネーター (MS DTC) トランザクションにより、サーバー間のプロシージャのアクションを保護します。</span><span class="sxs-lookup"><span data-stu-id="05801-154">Protects the actions of a server-to-server procedure through a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) transaction.</span></span> <span data-ttu-id="05801-155">詳細については、「 [remote proc trans サーバー構成オプションの構成](configure-the-remote-proc-trans-server-configuration-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05801-155">For more information, see [Configure the remote proc trans Server Configuration Option](configure-the-remote-proc-trans-server-configuration-option.md).</span></span>  
  
## <a name="property-page-display-options"></a><span data-ttu-id="05801-156">[プロパティ] ページの [表示] オプション</span><span class="sxs-lookup"><span data-stu-id="05801-156">Property Page Display Options</span></span>  
 <span data-ttu-id="05801-157">**[構成した値]**</span><span class="sxs-lookup"><span data-stu-id="05801-157">**Configured Values**</span></span>  
 <span data-ttu-id="05801-158">このペインの各オプションに構成されている値を表示します。</span><span class="sxs-lookup"><span data-stu-id="05801-158">Displays the configured values for the options on this pane.</span></span> <span data-ttu-id="05801-159">これらの値を変更した場合は、 **[実行中の値]** をクリックして、変更後の値が反映されているかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="05801-159">If you change these values, click **Running Values** to see whether the changes have taken effect.</span></span> <span data-ttu-id="05801-160">値が反映されていない場合は、最初に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05801-160">If they have not, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be restarted first.</span></span>  
  
 <span data-ttu-id="05801-161">**[実行中の値]**</span><span class="sxs-lookup"><span data-stu-id="05801-161">**Running Values**</span></span>  
 <span data-ttu-id="05801-162">このペイン上のオプションの、現在実行中の値を表示します。</span><span class="sxs-lookup"><span data-stu-id="05801-162">View the currently running values for the options on this pane.</span></span> <span data-ttu-id="05801-163">これらの値は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="05801-163">These values are read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05801-164">参照</span><span class="sxs-lookup"><span data-stu-id="05801-164">See Also</span></span>  
 <span data-ttu-id="05801-165">[クエリ実行 &#40;オプション: SQL Server: [詳細設定] ページ&#41;](../options-query-execution-sql-server-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="05801-165">[Options &#40;Query Execution:SQL Server:Advanced Page&#41;](../options-query-execution-sql-server-advanced-page.md) </span></span>  
 [<span data-ttu-id="05801-166">サーバー構成オプション &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="05801-166">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
