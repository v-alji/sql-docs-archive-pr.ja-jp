---
title: データベース エンジン サービスのスタートアップ オプション | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- single-user mode [SQL Server], startup option
- overriding default startup options
- minimal configuration mode [SQL Server], startup option
- default startup options
- temporarily override default startup options [SQL Server]
- startup options [SQL Server]
- starting SQL Server, options
ms.assetid: d373298b-f6cf-458a-849d-7083ecb54ef5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 844c0813453d371ed204dff6f8976f08bad63fe5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642284"
---
# <a name="database-engine-service-startup-options"></a><span data-ttu-id="c9769-102">データベース エンジン サービスのスタートアップ オプション</span><span class="sxs-lookup"><span data-stu-id="c9769-102">Database Engine Service Startup Options</span></span>
  <span data-ttu-id="c9769-103">スタートアップ オプションは、起動時に必要な特定のファイルの場所およびサーバー全体の状態を指定します。</span><span class="sxs-lookup"><span data-stu-id="c9769-103">Startup options designate certain file locations needed during startup, and specify some server wide conditions.</span></span> <span data-ttu-id="c9769-104">通常は、スタートアップ オプションを指定する必要はありません。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のトラブルシューティングを行う場合や、特殊な問題が発生し、スタートアップ オプションの使用を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] カスタマー サポートから指示された場合のみ指定します。</span><span class="sxs-lookup"><span data-stu-id="c9769-104">Most users do not need to specify startup options unless you are troubleshooting the [!INCLUDE[ssDE](../../includes/ssde-md.md)] or you have an unusual problem and are directed to use a startup option by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Customer Support.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="c9769-105">スタートアップ オプションを不適切に使用すると、サーバー パフォーマンスの低下を招くことや、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が起動しなくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="c9769-105">Improper use of startup options can affect server performance and can prevent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from starting.</span></span>  
  
## <a name="about-startup-options"></a><span data-ttu-id="c9769-106">スタートアップ オプションについて</span><span class="sxs-lookup"><span data-stu-id="c9769-106">About Startup Options</span></span>  
 <span data-ttu-id="c9769-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をインストールすると、セットアップが [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のレジストリに既定のスタートアップ オプションを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="c9769-107">When you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Setup writes a set of default startup options in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows registry.</span></span> <span data-ttu-id="c9769-108">これらのスタートアップ オプションを使用して、代替の master データベース ファイル、master データベース ログ ファイル、またはエラー ログ ファイルを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="c9769-108">You can use these startup options to specify an alternate master database file, master database log file, or error log file.</span></span> <span data-ttu-id="c9769-109">[!INCLUDE[ssDE](../../includes/ssde-md.md)] が必要なファイルを見つけることができない場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は起動しません。</span><span class="sxs-lookup"><span data-stu-id="c9769-109">If the [!INCLUDE[ssDE](../../includes/ssde-md.md)] cannot locate the necessary files, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will not start.</span></span>  
  
 <span data-ttu-id="c9769-110">スタートアップ オプションは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="c9769-110">Startup options can be set by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="c9769-111">詳しくは、「[サーバーのスタートアップ オプションの構成 &#40;SQL Server 構成マネージャー&#41;](scm-services-configure-server-startup-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9769-111">For information, see [Configure Server Startup Options &#40;SQL Server Configuration Manager&#41;](scm-services-configure-server-startup-options.md).</span></span>  
  
## <a name="list-of-startup-options"></a><span data-ttu-id="c9769-112">スタートアップ オプションの一覧</span><span class="sxs-lookup"><span data-stu-id="c9769-112">List of Startup Options</span></span>  
  
|<span data-ttu-id="c9769-113">既定のスタートアップ オプション</span><span class="sxs-lookup"><span data-stu-id="c9769-113">Default startup options</span></span>|<span data-ttu-id="c9769-114">説明</span><span class="sxs-lookup"><span data-stu-id="c9769-114">Description</span></span>|  
|-----------------------------|-----------------|  
|<span data-ttu-id="c9769-115">**-d**  *master_file_path*</span><span class="sxs-lookup"><span data-stu-id="c9769-115">**-d**  *master_file_path*</span></span>|<span data-ttu-id="c9769-116">master データベース ファイルの完全修飾パス (通常は、C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\master.mdf)。</span><span class="sxs-lookup"><span data-stu-id="c9769-116">Is the fully qualified path for the master database file (typically, C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\master.mdf).</span></span> <span data-ttu-id="c9769-117">このオプションを省略すると、レジストリ内にあるパラメーターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c9769-117">If you do not provide this option, the existing registry parameters are used.</span></span>|  
|<span data-ttu-id="c9769-118">**-e**  *error_log_path*</span><span class="sxs-lookup"><span data-stu-id="c9769-118">**-e**  *error_log_path*</span></span>|<span data-ttu-id="c9769-119">エラー ログ ファイルの完全修飾パス (通常は、C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\LOG\ERRORLOG) です。</span><span class="sxs-lookup"><span data-stu-id="c9769-119">Is the fully qualified path for the error log file (typically, C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\LOG\ERRORLOG).</span></span> <span data-ttu-id="c9769-120">このオプションを省略すると、レジストリ内にあるパラメーターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c9769-120">If you do not provide this option, the existing registry parameters are used.</span></span>|  
|<span data-ttu-id="c9769-121">**-l**  *master_log_path*</span><span class="sxs-lookup"><span data-stu-id="c9769-121">**-l**  *master_log_path*</span></span>|<span data-ttu-id="c9769-122">master データベース ログ ファイルの完全修飾パス (通常は、C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\mastlog.ldf)。</span><span class="sxs-lookup"><span data-stu-id="c9769-122">Is the fully qualified path for the master database log file (typically C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\mastlog.ldf).</span></span> <span data-ttu-id="c9769-123">このオプションを指定しない場合は、レジストリ内にあるパラメーターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c9769-123">If you do not specify this option, the existing registry parameters are used.</span></span>|  
  
|<span data-ttu-id="c9769-124">他のスタートアップ オプション</span><span class="sxs-lookup"><span data-stu-id="c9769-124">Other startup options</span></span>|<span data-ttu-id="c9769-125">説明</span><span class="sxs-lookup"><span data-stu-id="c9769-125">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="c9769-126">**-c**</span><span class="sxs-lookup"><span data-stu-id="c9769-126">**-c**</span></span>|<span data-ttu-id="c9769-127">コマンド プロンプトから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を起動する場合に、起動時間を短縮します。</span><span class="sxs-lookup"><span data-stu-id="c9769-127">Shortens startup time when starting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the command prompt.</span></span> <span data-ttu-id="c9769-128">通常、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] は、サービス コントロール マネージャーを呼び出すことにより、サービスとして起動します。</span><span class="sxs-lookup"><span data-stu-id="c9769-128">Typically, the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] starts as a service by calling the Service Control Manager.</span></span> <span data-ttu-id="c9769-129">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] は、コマンド プロンプトから起動した場合はサービスとして起動しないため、 **-c** を使用してこの手順を省略します。</span><span class="sxs-lookup"><span data-stu-id="c9769-129">Because the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] does not start as a service when starting from the command prompt, use **-c** to skip this step.</span></span>|  
|<span data-ttu-id="c9769-130">**-f**</span><span class="sxs-lookup"><span data-stu-id="c9769-130">**-f**</span></span>|<span data-ttu-id="c9769-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを最小構成で起動します。</span><span class="sxs-lookup"><span data-stu-id="c9769-131">Starts an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with minimal configuration.</span></span> <span data-ttu-id="c9769-132">設定値によりサーバーが起動できないとき (たとえば使用できるメモリが不足している場合) などに便利です。</span><span class="sxs-lookup"><span data-stu-id="c9769-132">This is useful if the setting of a configuration value (for example, over-committing memory) has prevented the server from starting.</span></span> <span data-ttu-id="c9769-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を最小構成モードで起動すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がシングル ユーザー モードになります。</span><span class="sxs-lookup"><span data-stu-id="c9769-133">Starting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in minimal configuration mode places [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode.</span></span> <span data-ttu-id="c9769-134">詳細については、後の **-m** の説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9769-134">For more information, see the description for **-m** that follows.</span></span>|  
|<span data-ttu-id="c9769-135">**-g**  *memory_to_reserve*</span><span class="sxs-lookup"><span data-stu-id="c9769-135">**-g**  *memory_to_reserve*</span></span>|<span data-ttu-id="c9769-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メモリ プール外の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセス内にメモリ割り当てに使用できる領域として残すメモリ容量を整数 (MB 単位) で指定します。</span><span class="sxs-lookup"><span data-stu-id="c9769-136">Specifies an integer number of megabytes (MB) of memory that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will leave available for memory allocations within the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process, but outside the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory pool.</span></span> <span data-ttu-id="c9769-137">メモリ プール外のメモリは、拡張プロシージャ .dll ファイル、分散クエリによって参照される OLE DB プロバイダー、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ステートメントで参照されるオートメーション オブジェクトなどのアイテムを読み込むために、 [!INCLUDE[tsql](../../includes/tsql-md.md)] によって使用される領域です。</span><span class="sxs-lookup"><span data-stu-id="c9769-137">The memory outside of the memory pool is the area used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for loading items, such as extended procedure .dll files, the OLE DB providers referenced by distributed queries, and automation objects referenced in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="c9769-138">既定値は 256 MB です。</span><span class="sxs-lookup"><span data-stu-id="c9769-138">The default is 256 MB.</span></span><br /><br /> <span data-ttu-id="c9769-139">このオプションを使用すると、メモリ割り当てを調整するうえで役に立つ場合がありますが、これは、アプリケーションが使用できる仮想メモリに対してオペレーティング システムが設定する制限値よりも物理メモリが多い場合だけです。</span><span class="sxs-lookup"><span data-stu-id="c9769-139">Use of this option might help tune memory allocation, but only when physical memory exceeds the configured limit set by the operating system on virtual memory available to applications.</span></span> <span data-ttu-id="c9769-140">このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に必要なメモリ容量が通常より多い大容量メモリ構成で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスの仮想アドレス空間全体が使用される場合に効果があります。</span><span class="sxs-lookup"><span data-stu-id="c9769-140">Use of this option might be appropriate in large memory configurations in which the memory usage requirements of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are atypical and the virtual address space of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process is totally in use.</span></span> <span data-ttu-id="c9769-141">このオプションを誤って使用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が起動しないことや、実行時エラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="c9769-141">Incorrect use of this option can lead to conditions under which an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] may not start or may encounter run-time errors.</span></span><br /><br /> <span data-ttu-id="c9769-142">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログに次の警告が記録されない限り、 **-g** パラメーターの既定値を使用してください。</span><span class="sxs-lookup"><span data-stu-id="c9769-142">Use the default for the **-g** parameter unless you see any of the following warnings in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log:</span></span><br /><br /> <span data-ttu-id="c9769-143">-"失敗した仮想割り当てバイト数: FAIL_VIRTUAL_RESERVE \<size> "</span><span class="sxs-lookup"><span data-stu-id="c9769-143">-"Failed Virtual Allocate Bytes: FAIL_VIRTUAL_RESERVE \<size>"</span></span><br /><br /> <span data-ttu-id="c9769-144">-"失敗した仮想割り当てバイト数: FAIL_VIRTUAL_COMMIT \<size> "</span><span class="sxs-lookup"><span data-stu-id="c9769-144">-"Failed Virtual Allocate Bytes: FAIL_VIRTUAL_COMMIT \<size>"</span></span><br /><br /> <span data-ttu-id="c9769-145">これらのメッセージは、拡張ストアド プロシージャ .dll ファイルやオートメション オブジェクトなどのアイテムの格納領域を確保するために [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メモリ プールの一部を解放しようとしていることを示している場合があります。</span><span class="sxs-lookup"><span data-stu-id="c9769-145">These messages might indicate that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is trying to free parts of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory pool in order to find space for items, such as extended stored procedure .dll files or automation objects.</span></span> <span data-ttu-id="c9769-146">その場合は、 **-g** スイッチによって確保するメモリ量を増やすことを検討してください。</span><span class="sxs-lookup"><span data-stu-id="c9769-146">In this case, consider increasing the amount of memory reserved by the **-g** switch.</span></span><br /><br /> <span data-ttu-id="c9769-147">既定値より小さい値を使用すると、SQL Server Memory Manager によって管理されるメモリ プールおよびスレッド スタックが利用できる容量が増えます。その結果、拡張ストアド プロシージャ、分散クエリ、またはオートメーション オブジェクトを多用しないシステムの、メモリ負荷の高い作業のパフォーマンスが向上することがあります。</span><span class="sxs-lookup"><span data-stu-id="c9769-147">Using a value lower than the default will increase the amount of memory available to the memory pool managed by the SQL Server Memory Manager and thread stacks; this may, in turn, provide some performance benefit to memory-intensive workloads in systems that do not use many extended stored procedures, distributed queries, or automation objects.</span></span>|  
|<span data-ttu-id="c9769-148">**-m**</span><span class="sxs-lookup"><span data-stu-id="c9769-148">**-m**</span></span>|<span data-ttu-id="c9769-149">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスをシングル ユーザー モードで起動します。</span><span class="sxs-lookup"><span data-stu-id="c9769-149">Starts an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode.</span></span> <span data-ttu-id="c9769-150">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスをシングル ユーザー モードで起動する場合、接続できるユーザーは 1 ユーザーのみで、CHECKPOINT プロセスは起動されません。</span><span class="sxs-lookup"><span data-stu-id="c9769-150">When you start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode, only a single user can connect, and the CHECKPOINT process is not started.</span></span> <span data-ttu-id="c9769-151">CHECKPOINT は、完了したトランザクションがディスク キャッシュからデータベース デバイスに定期的に書き込まれることを保証する機能です。</span><span class="sxs-lookup"><span data-stu-id="c9769-151">CHECKPOINT guarantees that completed transactions are regularly written from the disk cache to the database device.</span></span> <span data-ttu-id="c9769-152">一般的に、システム データベースを修復する必要がある問題が発生したときに、このオプションを使用します。sp_configure allow updates オプションが有効になります。</span><span class="sxs-lookup"><span data-stu-id="c9769-152">(Typically, this option is used if you experience problems with system databases that should be repaired.) Enables the sp_configure allow updates option.</span></span> <span data-ttu-id="c9769-153">既定では、allow updates は無効になっています。</span><span class="sxs-lookup"><span data-stu-id="c9769-153">By default, allow updates is disabled.</span></span> <span data-ttu-id="c9769-154">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をシングル ユーザー モードで起動すると、コンピューターのローカル Administrators グループのメンバーはすべて、固定サーバー ロール sysadmin のメンバーとして [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c9769-154">Starting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode enables any member of the computer's local Administrators group to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a member of the sysadmin fixed server role.</span></span> <span data-ttu-id="c9769-155">詳細については、「 [システム管理者がロックアウトされた場合の SQL Server への接続](connect-to-sql-server-when-system-administrators-are-locked-out.md)」を参照してください。シングル ユーザー モードの詳細については、「 [シングル ユーザー モードでの SQL Server の起動](start-sql-server-in-single-user-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9769-155">For more information, see [Connect to SQL Server When System Administrators Are Locked Out](connect-to-sql-server-when-system-administrators-are-locked-out.md). For more information about single-user mode, see [Start SQL Server in Single-User Mode](start-sql-server-in-single-user-mode.md).</span></span>|  
|<span data-ttu-id="c9769-156">**-m "クライアントアプリケーション名"**</span><span class="sxs-lookup"><span data-stu-id="c9769-156">**-m"Client Application Name"**</span></span>|<span data-ttu-id="c9769-157">**SQLCMD** または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で **-m** オプションを使用すると、接続を特定のクライアント アプリケーションに限定できます。</span><span class="sxs-lookup"><span data-stu-id="c9769-157">Limits the connections to a specified client application, when you use the **-m** option with **SQLCMD** or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="c9769-158">たとえば、 **-m"SQLCMD"** を使用すると、接続が、**SQLCMD** クライアント プログラムとして識別される必要がある単一の接続に限定されます。</span><span class="sxs-lookup"><span data-stu-id="c9769-158">For example, **-m"SQLCMD"** limits connections to a single connection and that connection must identify itself as the **SQLCMD** client program.</span></span> <span data-ttu-id="c9769-159">このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をシングル ユーザー モードで起動するときに、その唯一の接続を不明なクライアント アプリケーションによって使用されていた場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="c9769-159">Use this option when you are starting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode and an unknown client application is taking the only available connection.</span></span> <span data-ttu-id="c9769-160">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]のクエリ エディターを使用して接続するには、 **-m"Microsoft SQL Server Management Studio - Query"** を使用します。</span><span class="sxs-lookup"><span data-stu-id="c9769-160">To connect through the Query Editor in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], use **-m"Microsoft SQL Server Management Studio - Query"**.</span></span><br /><br /> <span data-ttu-id="c9769-161">クライアント アプリケーション名では大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="c9769-161">Client Application Name is case sensitive.</span></span><br /><br /> <span data-ttu-id="c9769-162">\*\* \* \* セキュリティ \* \* \*\*に関する注意このオプションをセキュリティ機能として使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="c9769-162">**\*\* Security Note \*\*** Do not use this option as a security feature.</span></span> <span data-ttu-id="c9769-163">クライアント アプリケーションの名前はクライアント アプリケーションによって接続文字列の一部として指定されるため、本当の名前が指定されるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="c9769-163">The client application provides the client application name, and can provide a false name as part of the connection string.</span></span>|  
|<span data-ttu-id="c9769-164">**-n**</span><span class="sxs-lookup"><span data-stu-id="c9769-164">**-n**</span></span>|<span data-ttu-id="c9769-165">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] イベントを記録する際に、Windows アプリケーション ログを使用しません。</span><span class="sxs-lookup"><span data-stu-id="c9769-165">Does not use the Windows application log to record [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events.</span></span> <span data-ttu-id="c9769-166">**-n** を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを起動する場合は、 **-e** スタートアップ オプションも使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c9769-166">If you start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with **-n**, we recommend that you also use the **-e** startup option.</span></span> <span data-ttu-id="c9769-167">このオプションを指定しないと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のイベントはログに記録されません。</span><span class="sxs-lookup"><span data-stu-id="c9769-167">Otherwise, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events are not logged.</span></span>|  
|<span data-ttu-id="c9769-168">**-s**</span><span class="sxs-lookup"><span data-stu-id="c9769-168">**-s**</span></span>|<span data-ttu-id="c9769-169">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の名前付きインスタンスの起動を可能にします。</span><span class="sxs-lookup"><span data-stu-id="c9769-169">Allows you to start a named instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c9769-170">**-s** パラメーターが設定されていない場合は、既定のインスタンスが起動されます。</span><span class="sxs-lookup"><span data-stu-id="c9769-170">Without the **-s** parameter set, the default instance will try to start.</span></span> <span data-ttu-id="c9769-171">**sqlservr.exe**を開始する前に、コマンド プロンプトで、インスタンスの適切な BINN ディレクトリに移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9769-171">You must switch to the appropriate BINN directory for the instance at a command prompt before starting **sqlservr.exe**.</span></span> <span data-ttu-id="c9769-172">たとえば、Instance1 がバイナリ用に \mssql$Instance1 を使用する場合、ユーザーは \mssql$Instance1\binn ディレクトリで **sqlservr.exe -s instance1**を起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9769-172">For example, if Instance1 were to use \mssql$Instance1 for its binaries, the user must be in the \mssql$Instance1\binn directory to start **sqlservr.exe -s instance1**.</span></span>|  
|<span data-ttu-id="c9769-173">**-T** *trace#*</span><span class="sxs-lookup"><span data-stu-id="c9769-173">**-T**  *trace#*</span></span>|<span data-ttu-id="c9769-174">指定された、有効なトレース フラグ (*trace#* ) を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを起動します。</span><span class="sxs-lookup"><span data-stu-id="c9769-174">Indicates that an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should be started with a specified trace flag (*trace#*) in effect.</span></span> <span data-ttu-id="c9769-175">トレース フラグを使用してサーバーが起動すると、標準的な動作とは異なります。</span><span class="sxs-lookup"><span data-stu-id="c9769-175">Trace flags are used to start the server with nonstandard behavior.</span></span> <span data-ttu-id="c9769-176">詳細については、「[トレース フラグ &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9769-176">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span><br /><br /> <span data-ttu-id="c9769-177">\*\* \* \* 重要 \* - \* \*\* **t**オプションを指定してトレースフラグを指定する場合は、大文字の "T" を使用してトレースフラグ番号を渡します。</span><span class="sxs-lookup"><span data-stu-id="c9769-177">**\*\* Important \*\*** When specifying a trace flag with the **-T** option, use an uppercase "T" to pass the trace flag number.</span></span> <span data-ttu-id="c9769-178">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は小文字の "t" を受け付けますが、これは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のサポート エンジニアのみが必要とする他の内部トレース フラグを設定するためのものです。</span><span class="sxs-lookup"><span data-stu-id="c9769-178">A lowercase "t" is accepted by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but this sets other internal trace flags that are required only by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support engineers.</span></span> <span data-ttu-id="c9769-179">コントロール パネルの起動ウィンドウで指定されているパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="c9769-179">(Parameters specified in the Control Panel startup window are not read.)</span></span>|  
|<span data-ttu-id="c9769-180">**-x**</span><span class="sxs-lookup"><span data-stu-id="c9769-180">**-x**</span></span>|<span data-ttu-id="c9769-181">次の監視機能を無効にします。</span><span class="sxs-lookup"><span data-stu-id="c9769-181">Disables the following monitoring features:</span></span><br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c9769-182">パフォーマンス モニター カウンター</span><span class="sxs-lookup"><span data-stu-id="c9769-182">performance monitor counters</span></span><br /><br /> <span data-ttu-id="c9769-183">CPU 時間とキャッシュ ヒット率統計の管理</span><span class="sxs-lookup"><span data-stu-id="c9769-183">Keeping CPU time and cache-hit ratio statistics</span></span><br /><br /> <span data-ttu-id="c9769-184">DBCC SQLPERF コマンドに関する情報の収集</span><span class="sxs-lookup"><span data-stu-id="c9769-184">Collecting information for the DBCC SQLPERF command</span></span><br /><br /> <span data-ttu-id="c9769-185">一部の動的管理ビューに関する情報の収集</span><span class="sxs-lookup"><span data-stu-id="c9769-185">Collecting information for some dynamic management views</span></span><br /><br /> <span data-ttu-id="c9769-186">拡張イベントの多数のイベント ポイント</span><span class="sxs-lookup"><span data-stu-id="c9769-186">Many extended-events event points</span></span><br /><br /> <br /><br /> <span data-ttu-id="c9769-187">\*\* \* \* 警告 \* - \* \*\* **x**スタートアップオプションを使用すると、のパフォーマンスと機能の問題を診断するために使用できる情報 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が大幅に減少します。</span><span class="sxs-lookup"><span data-stu-id="c9769-187">**\*\* Warning \*\*** When you use the **-x** startup option, the information that is available for you to diagnose performance and functional problems with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is greatly reduced.</span></span>|  
|<span data-ttu-id="c9769-188">**-E**</span><span class="sxs-lookup"><span data-stu-id="c9769-188">**-E**</span></span>|<span data-ttu-id="c9769-189">ファイル グループ内の各ファイルに割り当てられるエクステントの数を増やします。</span><span class="sxs-lookup"><span data-stu-id="c9769-189">Increases the number of extents that are allocated for each file in a filegroup.</span></span> <span data-ttu-id="c9769-190">このオプションは、インデックス スキャンまたはデータ スキャンを実行するユーザーの数が限られているデータ ウェアハウス アプリケーションで役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="c9769-190">This option may be helpful for data warehouse applications that have a limited number of users running index or data scans.</span></span> <span data-ttu-id="c9769-191">パフォーマンスに悪影響を及ぼす可能性があるため、他のアプリケーションでは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="c9769-191">It should not be used in other applications because it might adversely affect performance.</span></span> <span data-ttu-id="c9769-192">このオプションは、32 ビット リリースの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c9769-192">This option is not supported in 32-bit releases of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
  
## <a name="using-startup-options-for-troubleshooting"></a><span data-ttu-id="c9769-193">トラブルシューティングでのスタートアップ オプションの使用</span><span class="sxs-lookup"><span data-stu-id="c9769-193">Using Startup Options for Troubleshooting</span></span>  
 <span data-ttu-id="c9769-194">シングル ユーザー モードや最小構成モードなど、一部のスタートアップ オプションは、主にトラブルシューティングの際に使用されます。</span><span class="sxs-lookup"><span data-stu-id="c9769-194">Some startup options, such as single-user mode and minimal configuration mode, are principally used during troubleshooting.</span></span> <span data-ttu-id="c9769-195">トラブルシューティングのために **-m** オプションや **-f** オプションを使用してサーバーを起動する場合は、sqlservr.exe を手動で起動するときに、コマンド ラインから起動すると最も容易に起動できます。</span><span class="sxs-lookup"><span data-stu-id="c9769-195">Starting the server for troubleshooting with the **-m** or **-f** options is easiest at the command line, while manually starting sqlservr.exe.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c9769-196">**net start** を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を起動する場合、スタートアップ オプションではハイフン (-) の代わりにスラッシュ (/) を使用します。</span><span class="sxs-lookup"><span data-stu-id="c9769-196">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is started by using **net start**, startup options use a slash (/) instead of a hyphen (-).</span></span>  
  
## <a name="using-startup-options-during-normal-operations"></a><span data-ttu-id="c9769-197">通常の操作でのスタートアップ オプションの使用</span><span class="sxs-lookup"><span data-stu-id="c9769-197">Using Startup Options During Normal Operations</span></span>  
 <span data-ttu-id="c9769-198">スタートアップ オプションの一部は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を起動するたびに使用することが考えられます。</span><span class="sxs-lookup"><span data-stu-id="c9769-198">You may want to use some startup options every time you start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c9769-199">これらのオプション ( **-g**やトレースフラグを使用した起動など) は、Configuration Manager を使用して起動時のパラメーターを構成することによって、最も簡単に実行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] できます。</span><span class="sxs-lookup"><span data-stu-id="c9769-199">These options, such as **-g** or starting with a trace flag, are most easily done by configuring the startup parameters by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="c9769-200">これらのツールは、スタートアップ オプションをレジストリ キーとして保存するため、常にこれらのスタートアップ オプションを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を起動できます。</span><span class="sxs-lookup"><span data-stu-id="c9769-200">These tool saves the startup options as registry keys, enabling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to always start with the startup options.</span></span>  
  
## <a name="compatibility-support"></a><span data-ttu-id="c9769-201">互換性サポート</span><span class="sxs-lookup"><span data-stu-id="c9769-201">Compatibility Support</span></span>  
 <span data-ttu-id="c9769-202">**-h**  パラメーターは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c9769-202">The **-h**  parameter is not supported in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="c9769-203">このパラメーターは、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 32 ビットのインスタンスで AWE が有効になっている場合に、ホット アド メモリ メタデータ用の仮想メモリ アドレス空間を確保するために使用されていました。</span><span class="sxs-lookup"><span data-stu-id="c9769-203">This parameter was used in earlier versions of 32-bit instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to reserve virtual memory address space for Hot Add memory metadata when AWE is enabled.</span></span> <span data-ttu-id="c9769-204">詳細については、「[SQL Server 2014 で提供が中止された機能](../../getting-started/discontinued-sql-server-features-in-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9769-204">For more information, see [Discontinued SQL Server Features in SQL Server 2014](../../getting-started/discontinued-sql-server-features-in-sql-server-2014.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="c9769-205">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="c9769-205">Related Tasks</span></span>  
 [<span data-ttu-id="c9769-206">scan for startup procs サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="c9769-206">Configure the scan for startup procs Server Configuration Option</span></span>](configure-the-scan-for-startup-procs-server-configuration-option.md)  
  
 [<span data-ttu-id="c9769-207">データベース エンジン、SQL Server エージェント、SQL Server Browser サービスの開始、停止、一時停止、再開、および再起動</span><span class="sxs-lookup"><span data-stu-id="c9769-207">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>](start-stop-pause-resume-restart-sql-server-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="c9769-208">参照</span><span class="sxs-lookup"><span data-stu-id="c9769-208">See Also</span></span>  
 <span data-ttu-id="c9769-209">[CHECKPOINT &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/checkpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c9769-209">[CHECKPOINT &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/checkpoint-transact-sql) </span></span>  
 [<span data-ttu-id="c9769-210">sqlservr アプリケーション</span><span class="sxs-lookup"><span data-stu-id="c9769-210">sqlservr Application</span></span>](../../tools/sqlservr-application.md)  
  
  