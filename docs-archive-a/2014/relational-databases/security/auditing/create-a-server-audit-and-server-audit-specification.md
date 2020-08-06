---
title: サーバー監査およびサーバー監査の仕様を作成する方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.SQLAUDIT.FILTER.F1
- sql12.swb.sqlaudit.srvaudit.general.f1
- sql12.swb.sqlaudit.general.f1
helpviewer_keywords:
- server audit [SQL Server]
- audits [SQL Server], specification
ms.assetid: 6624b1ab-7ec8-44ce-8292-397edf644394
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: a648a975ae9f2c4139a8ebd584f6998f4d0fa1a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716194"
---
# <a name="create-a-server-audit-and-server-audit-specification"></a><span data-ttu-id="31172-102">サーバー監査およびサーバー監査の仕様を作成する方法</span><span class="sxs-lookup"><span data-stu-id="31172-102">Create a Server Audit and Server Audit Specification</span></span>
  <span data-ttu-id="31172-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、サーバー監査またはサーバー監査仕様を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="31172-103">This topic describes how to create a server audit and server audit specification in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="31172-104">*のインスタンスや* データベースの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 監査 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、システムで発生するイベントの追跡およびログ記録が行われます。</span><span class="sxs-lookup"><span data-stu-id="31172-104">*Auditing* an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database involves tracking and logging events that occur on the system.</span></span> <span data-ttu-id="31172-105">*SQL Server Audit* オブジェクトは、監視するサーバー レベルまたはデータベース レベルのアクションおよびアクションのグループの 1 つのインスタンスを収集します。</span><span class="sxs-lookup"><span data-stu-id="31172-105">The *SQL Server Audit* object collects a single instance of server- or database-level actions and groups of actions to monitor.</span></span> <span data-ttu-id="31172-106">監査は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス レベルで行われます。</span><span class="sxs-lookup"><span data-stu-id="31172-106">The audit is at the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance level.</span></span> <span data-ttu-id="31172-107">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスごとに複数の監査を使用できます。</span><span class="sxs-lookup"><span data-stu-id="31172-107">You can have multiple audits per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="31172-108">*サーバー監査の仕様* オブジェクトは監査に属しています。</span><span class="sxs-lookup"><span data-stu-id="31172-108">The *Server Audit Specification* object belongs to an audit.</span></span> <span data-ttu-id="31172-109">サーバー監査の仕様は監査ごとに 1 つ作成できます。これは、サーバー監査の仕様も監査も [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスのスコープで作成されるためです。</span><span class="sxs-lookup"><span data-stu-id="31172-109">You can create one server audit specification per audit, because both are created at the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance scope.</span></span> <span data-ttu-id="31172-110">詳しくは、「[SQL Server Audit &#40;データベース エンジン&#41;](sql-server-audit-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31172-110">For more information, see [SQL Server Audit &#40;Database Engine&#41;](sql-server-audit-database-engine.md).</span></span>  
  
 <span data-ttu-id="31172-111">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="31172-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="31172-112">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="31172-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="31172-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="31172-113">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="31172-114">Security</span><span class="sxs-lookup"><span data-stu-id="31172-114">Security</span></span>](#Security)  
  
-   <span data-ttu-id="31172-115">**次のものを使用してサーバー監査およびサーバー監査の仕様を作成するには:**</span><span class="sxs-lookup"><span data-stu-id="31172-115">**To create a server audit and server audit specification, using:**</span></span>  
  
     [<span data-ttu-id="31172-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="31172-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="31172-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="31172-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="31172-118">はじめに</span><span class="sxs-lookup"><span data-stu-id="31172-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="31172-119">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="31172-119">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="31172-120">サーバー監査仕様を作成するには、対象の監査が事前に存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="31172-120">An audit must exist before creating a server audit specification for it.</span></span> <span data-ttu-id="31172-121">サーバー監査仕様は作成されたとき無効な状態です。</span><span class="sxs-lookup"><span data-stu-id="31172-121">When a server audit specification is created, it is in a disabled state.</span></span>  
  
-   <span data-ttu-id="31172-122">CREATE SERVER AUDIT ステートメントはトランザクションのスコープ内にあります。</span><span class="sxs-lookup"><span data-stu-id="31172-122">The CREATE SERVER AUDIT statement is in a transaction's scope.</span></span> <span data-ttu-id="31172-123">トランザクションがロールバックされると、ステートメントもロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="31172-123">If the transaction is rolled back, the statement is also rolled back.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="31172-124">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="31172-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="31172-125">Permissions</span><span class="sxs-lookup"><span data-stu-id="31172-125">Permissions</span></span>  
  
-   <span data-ttu-id="31172-126">サーバー監査を作成、変更、または削除する場合、プリンシパルには、ALTER ANY SERVER AUDIT または CONTROL SERVER の権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="31172-126">To create, alter, or drop a server audit, principals require the ALTER ANY SERVER AUDIT or the CONTROL SERVER permission.</span></span>  
  
-   <span data-ttu-id="31172-127">ALTER ANY SERVER AUDIT 権限を持つユーザーは、サーバー監査の仕様を作成し、任意の監査にバインドできます。</span><span class="sxs-lookup"><span data-stu-id="31172-127">Users with the ALTER ANY SERVER AUDIT permission can create server audit specifications and bind them to any audit.</span></span>  
  
-   <span data-ttu-id="31172-128">サーバー監査仕様の作成後は、CONTROL SERVER または ALTER ANY SERVER AUDIT 権限を持つプリンシパル、sysadmin アカウント、またはその監査への明示的なアクセス権を持つプリンシパルがその仕様を表示できます。</span><span class="sxs-lookup"><span data-stu-id="31172-128">After a server audit specification is created, it can be viewed by principals with the CONTROL SERVER or ALTER ANY SERVER AUDIT permissions, the sysadmin account, or principals having explicit access to the audit.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="31172-129">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="31172-129">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-server-audit"></a><span data-ttu-id="31172-130">サーバー監査を作成するには</span><span class="sxs-lookup"><span data-stu-id="31172-130">To create a server audit</span></span>  
  
1.  <span data-ttu-id="31172-131">オブジェクト エクスプローラーで、 **[セキュリティ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="31172-131">In Object Explorer, expand the **Security** folder.</span></span>  
  
2.  <span data-ttu-id="31172-132">**[監査]** フォルダーを右クリックし、 **[新しい監査]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="31172-132">Right-click the **Audits** folder and select **New Audit...**.</span></span>  
  
     <span data-ttu-id="31172-133">**[監査の作成]** ダイアログ ボックスの **[全般]** ページでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="31172-133">The following options are available on the **General** page of the **Create Audit** dialog box.</span></span>  
  
     <span data-ttu-id="31172-134">**[監査名]**</span><span class="sxs-lookup"><span data-stu-id="31172-134">**Audit name**</span></span>  
     <span data-ttu-id="31172-135">監査の名前。</span><span class="sxs-lookup"><span data-stu-id="31172-135">The name of the audit.</span></span> <span data-ttu-id="31172-136">これは、新しい監査を作成すると自動的に生成されますが、編集可能です。</span><span class="sxs-lookup"><span data-stu-id="31172-136">This is generated automatically when you create a new audit but is editable.</span></span>  
  
     <span data-ttu-id="31172-137">**[処理の遅延 (ミリ秒)]**</span><span class="sxs-lookup"><span data-stu-id="31172-137">**Queue delay (in milliseconds)**</span></span>  
     <span data-ttu-id="31172-138">監査アクションの処理が強制されるまでの時間 (ミリ秒単位) を指定します。</span><span class="sxs-lookup"><span data-stu-id="31172-138">Specifies the amount of time in milliseconds that can elapse before audit actions are forced to be processed.</span></span>  <span data-ttu-id="31172-139">値 0 は同期配信を表します。</span><span class="sxs-lookup"><span data-stu-id="31172-139">A value of 0 indicates synchronous delivery.</span></span> <span data-ttu-id="31172-140">既定の最小値は **1000** (1 秒) です。</span><span class="sxs-lookup"><span data-stu-id="31172-140">The default minimum value is **1000** (1 second).</span></span> <span data-ttu-id="31172-141">最大値は 2,147,483,647 (2,147,483.647 秒、つまり 24 日、20 時間、31 分、23.647 秒) です。</span><span class="sxs-lookup"><span data-stu-id="31172-141">The maximum is 2,147,483,647 (2,147,483.647 seconds or 24 days, 20 hours, 31 minutes, 23.647 seconds).</span></span>  
  
     <span data-ttu-id="31172-142">**[監査ログ エラー発生時]**</span><span class="sxs-lookup"><span data-stu-id="31172-142">**On Audit Log Failure:**</span></span>  
     <span data-ttu-id="31172-143">**続行**</span><span class="sxs-lookup"><span data-stu-id="31172-143">**Continue**</span></span>  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="31172-144">操作を続行します。</span><span class="sxs-lookup"><span data-stu-id="31172-144">operations continue.</span></span> <span data-ttu-id="31172-145">監査レコードは保持されません。</span><span class="sxs-lookup"><span data-stu-id="31172-145">Audit records are not retained.</span></span> <span data-ttu-id="31172-146">監査はイベントのログ記録を試行し続け、エラー状態が解決されると、記録を再開します。</span><span class="sxs-lookup"><span data-stu-id="31172-146">The audit continues to attempt to log events and will resume if the failure condition is resolved.</span></span> <span data-ttu-id="31172-147">**[続行]** オプションを選択すると、セキュリティ ポリシーに違反する可能性がある、監査されない活動を許すおそれがあります。</span><span class="sxs-lookup"><span data-stu-id="31172-147">Selecting the **Continue** option can allow unaudited activity which could violate your security policies.</span></span> <span data-ttu-id="31172-148">完全な監査を維持することより、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] の操作を続行することの方が重要である場合に、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="31172-148">Select this option when continuing operation of the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] is more important than maintaining a complete audit.</span></span> <span data-ttu-id="31172-149">これは既定値です。</span><span class="sxs-lookup"><span data-stu-id="31172-149">This is the default selection.</span></span>  
  
     <span data-ttu-id="31172-150">**[サーバーのシャットダウン]**</span><span class="sxs-lookup"><span data-stu-id="31172-150">**Shut down server**</span></span>  
     <span data-ttu-id="31172-151">監査対象に書き込みを行うサーバー インスタンスが監査対象にデータを書き込むことができない場合に、サーバーを強制的にシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="31172-151">Forces a server shut down when the server instance writing to the target cannot write data to the audit target.</span></span> <span data-ttu-id="31172-152">これを発行するログインには、`SHUTDOWN` 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="31172-152">The login issuing this must have the `SHUTDOWN` permission.</span></span> <span data-ttu-id="31172-153">ログオンにこの権限がない場合、この機能は失敗し、エラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="31172-153">If the logon does not have this permission, this function will fail and an error message will be raised.</span></span> <span data-ttu-id="31172-154">監査イベントは発生しません。</span><span class="sxs-lookup"><span data-stu-id="31172-154">No audited events occur.</span></span> <span data-ttu-id="31172-155">監査エラーによってシステムのセキュリティまたは整合性が阻害される可能性がある場合に、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="31172-155">Select this option when an audit failure could compromise the security or integrity of the system.</span></span>  
  
     <span data-ttu-id="31172-156">**[失敗の操作]**</span><span class="sxs-lookup"><span data-stu-id="31172-156">**Fail operation**</span></span>  
     <span data-ttu-id="31172-157">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit が監査ログを出力できないとき、そのままではデータベース アクションが原因で、監査イベントが発生する場合、そのデータベース アクションを失敗させます。</span><span class="sxs-lookup"><span data-stu-id="31172-157">In cases where the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit cannot write to the audit log this option causes database actions to fail if they would otherwise cause audited events.</span></span> <span data-ttu-id="31172-158">監査イベントは発生しません。</span><span class="sxs-lookup"><span data-stu-id="31172-158">No audited events occur.</span></span> <span data-ttu-id="31172-159">監査イベントを発生させないアクションは続行できます。</span><span class="sxs-lookup"><span data-stu-id="31172-159">Actions which do not cause audited events can continue.</span></span> <span data-ttu-id="31172-160">監査はイベントのログ記録を試行し続け、エラー状態が解決されると、記録を再開します。</span><span class="sxs-lookup"><span data-stu-id="31172-160">The audit continues to attempt to log events and will resume if the failure condition is resolved.</span></span> <span data-ttu-id="31172-161">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]へのフル アクセスより、完全な監査の維持の方が重要である場合に、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="31172-161">Select this option when maintaining a complete audit is more important than full access to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="31172-162">監査が失敗状態のとき、専用管理者接続は、監査イベントの実行を継続できます。</span><span class="sxs-lookup"><span data-stu-id="31172-162">When the audit is in a failed state, the Dedicated Administrator Connection can continue to perform audited events.</span></span>  
  
     <span data-ttu-id="31172-163">**[監査の出力先]** の一覧</span><span class="sxs-lookup"><span data-stu-id="31172-163">**Audit destination** list</span></span>  
     <span data-ttu-id="31172-164">監査データの出力先を指定します。</span><span class="sxs-lookup"><span data-stu-id="31172-164">Specifies the target for auditing data.</span></span> <span data-ttu-id="31172-165">バイナリ ファイル、Windows アプリケーション ログ、または Windows セキュリティ ログを指定できます。</span><span class="sxs-lookup"><span data-stu-id="31172-165">The available options are a binary file, the Windows Application log, or the Windows Security log.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="31172-166">は、Windows で追加の設定を行わないと Windows セキュリティ ログに書き込むことができません。</span><span class="sxs-lookup"><span data-stu-id="31172-166">cannot write to the Windows Security log without configuring additional settings in Windows.</span></span> <span data-ttu-id="31172-167">詳細については、「 [セキュリティ ログへの SQL サーバー監査イベントの書き込み](write-sql-server-audit-events-to-the-security-log.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31172-167">For more information, see [Write SQL Server Audit Events to the Security Log](write-sql-server-audit-events-to-the-security-log.md).</span></span>  
  
     <span data-ttu-id="31172-168">**[ファイル パス]**</span><span class="sxs-lookup"><span data-stu-id="31172-168">**File path**</span></span>  
     <span data-ttu-id="31172-169">**[監査の出力先]** にファイルが指定されている場合に、監査データが書き込まれるフォルダーの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="31172-169">Specifies the location of the folder where audit data is written when the **Audit destination** is a file.</span></span>  
  
     <span data-ttu-id="31172-170">**省略記号 (...)**</span><span class="sxs-lookup"><span data-stu-id="31172-170">**Ellipsis (...)**</span></span>  
     <span data-ttu-id="31172-171">[**フォルダーの検索-**_server_name_ ] ダイアログボックスを開き、ファイルパスを指定するか、監査ファイルが書き込まれるフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="31172-171">Opens the **Locate Folder -**_server_name_ dialog box to specify a file path or create a folder where the audit file is written.</span></span>  
  
     <span data-ttu-id="31172-172">**[監査ファイルの最大限度]**</span><span class="sxs-lookup"><span data-stu-id="31172-172">**Audit File Maximum Limit:**</span></span>  
     <span data-ttu-id="31172-173">**[ロールオーバー ファイルの最大数]**</span><span class="sxs-lookup"><span data-stu-id="31172-173">**Maximum rollover files**</span></span>  
     <span data-ttu-id="31172-174">監査ファイルがその最大数に達すると、最も古い監査ファイルが新しいファイルの内容で上書きされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="31172-174">Specifies that, when the maximum number of audit files is reached, the oldest audit files are overwritten by new file content.</span></span>  
  
     <span data-ttu-id="31172-175">**[最大ファイル]**</span><span class="sxs-lookup"><span data-stu-id="31172-175">**Maximum files**</span></span>  
     <span data-ttu-id="31172-176">監査ファイル数が上限に達すると、追加の監査イベントを生成させるアクションが失敗し、エラーが発生することを指定します。</span><span class="sxs-lookup"><span data-stu-id="31172-176">Specifies that, when the maximum number of audit files is reached, any action that causes additional audit events to be generated will fail with an error.</span></span>  
  
     <span data-ttu-id="31172-177">**[無制限]** チェック ボックス</span><span class="sxs-lookup"><span data-stu-id="31172-177">**Unlimited** check box</span></span>  
     <span data-ttu-id="31172-178">**[ロールオーバー ファイルの最大数]** の **[無制限]** チェック ボックスがオンの場合、作成される監査ファイルの数は制限されません。</span><span class="sxs-lookup"><span data-stu-id="31172-178">When the **Unlimited** check box under **Maximum rollover files** is selected, there is no limit imposed on the number of audit files that will be created.</span></span> <span data-ttu-id="31172-179">**[無制限]** チェック ボックスは既定でオンになり、 **[ロールオーバー ファイルの最大数]** と **[最大ファイル数]** の両方の選択に適用されます。</span><span class="sxs-lookup"><span data-stu-id="31172-179">The **Unlimited** check box is selected by default and applies to both the **Maximum rollover files** and **Maximum files** selections.</span></span>  
  
     <span data-ttu-id="31172-180">**[ファイルの数]** ボックス</span><span class="sxs-lookup"><span data-stu-id="31172-180">**Number of files** box</span></span>  
     <span data-ttu-id="31172-181">作成する監査ファイル数を指定します (2,147,483,647 まで)。</span><span class="sxs-lookup"><span data-stu-id="31172-181">Specifies the number of audit files to be created, up to 2,147,483,647.</span></span> <span data-ttu-id="31172-182">このオプションは、 **[無制限]** がオフの場合にのみ利用可能です。</span><span class="sxs-lookup"><span data-stu-id="31172-182">This option is only available if **Unlimited** is unchecked.</span></span>  
  
     <span data-ttu-id="31172-183">**[最大ファイル サイズ]**</span><span class="sxs-lookup"><span data-stu-id="31172-183">**Maximum file size**</span></span>  
     <span data-ttu-id="31172-184">監査ファイルの最大サイズをメガバイト (MB)、ギガバイト (GB)、またはテラバイト (TB) 単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="31172-184">Specifies the maximum size for an audit file in either megabytes (MB), gigabytes (GB), or terabytes (TB).</span></span> <span data-ttu-id="31172-185">1024 MB ～ 2,147,483,647 TB の範囲で指定できます。</span><span class="sxs-lookup"><span data-stu-id="31172-185">You can specify between 1024 MB and 2,147,483,647 TB.</span></span> <span data-ttu-id="31172-186">**[無制限]** チェック ボックスをオンにした場合、ファイルのサイズに制限は設定されません。</span><span class="sxs-lookup"><span data-stu-id="31172-186">Selecting the **Unlimited** check box does not place a limit on the size of the file.</span></span> <span data-ttu-id="31172-187">1024 MB 未満の値を指定すると、失敗し、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="31172-187">Specifying a value lower than 1024 MB will fail, returning an error.</span></span> <span data-ttu-id="31172-188">既定では、 **[無制限]** チェック ボックスはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="31172-188">The **Unlimited** check box is selected by default.</span></span>  
  
     <span data-ttu-id="31172-189">**[ディスク領域を予約する]** チェック ボックス</span><span class="sxs-lookup"><span data-stu-id="31172-189">**Reserve disk space** check box</span></span>  
     <span data-ttu-id="31172-190">指定した最大ファイル サイズと等しい領域が、ディスク上に事前に割り当てられるように指定します。</span><span class="sxs-lookup"><span data-stu-id="31172-190">Specifies that space is pre-allocated on the disk equal to the specified maximum file size.</span></span> <span data-ttu-id="31172-191">この設定は、 **[最大ファイル サイズ]** の **[無制限]** チェック ボックスがオフの場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="31172-191">This setting can only be used if the **Unlimited** check box under **Maximum file size** is not selected.</span></span> <span data-ttu-id="31172-192">既定では、このチェック ボックスはオフになっています。</span><span class="sxs-lookup"><span data-stu-id="31172-192">This check box is not selected by default.</span></span>  
  
3.  <span data-ttu-id="31172-193">オプションで、 **[フィルター]** ページでサーバー監査に対する述語または `WHERE` 句を入力して、 **[全般]** ページからは使用できない追加オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="31172-193">Optionally, on the **Filter** page, enter a predicate, or `WHERE` clause, to the server audit to specify additional options not available from the **General** page.</span></span> <span data-ttu-id="31172-194">述語はかっこで囲みます。たとえば、 `(object_name = 'EmployeesTable')`と指定します。</span><span class="sxs-lookup"><span data-stu-id="31172-194">Enclose the predicate in parentheses; for example: `(object_name = 'EmployeesTable')`.</span></span>  
  
4.  <span data-ttu-id="31172-195">オプションの選択が完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31172-195">When you are finished selecting options, click **OK**.</span></span>  
  
#### <a name="to-create-a-server-audit-specification"></a><span data-ttu-id="31172-196">サーバー監査仕様を作成するには</span><span class="sxs-lookup"><span data-stu-id="31172-196">To create a server audit specification</span></span>  
  
1.  <span data-ttu-id="31172-197">オブジェクト エクスプローラーで、プラス記号をクリックして **[セキュリティ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="31172-197">In Object Explorer, click the plus sign to expand the **Security** folder.</span></span>  
  
2.  <span data-ttu-id="31172-198">**[サーバー監査の仕様]** フォルダーを右クリックし、 **[新しいサーバー監査の仕様]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="31172-198">Right-click the **Server Audit Specifications** folder and select **New Server Audit Specification...**.</span></span>  
  
     <span data-ttu-id="31172-199">**[サーバー監査の仕様の作成]** ダイアログ ボックスで、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="31172-199">The following options are available on the **Create Server Audit Specification** dialog box.</span></span>  
  
     <span data-ttu-id="31172-200">**名前**</span><span class="sxs-lookup"><span data-stu-id="31172-200">**Name**</span></span>  
     <span data-ttu-id="31172-201">サーバー監査の仕様の名前。</span><span class="sxs-lookup"><span data-stu-id="31172-201">The name of the server audit specification.</span></span> <span data-ttu-id="31172-202">この名前は、新しいサーバー監査の仕様を作成すると自動的に生成されますが、編集可能です。</span><span class="sxs-lookup"><span data-stu-id="31172-202">This is generated automatically when you create a new server audit specification but is editable.</span></span>  
  
     <span data-ttu-id="31172-203">**監査**</span><span class="sxs-lookup"><span data-stu-id="31172-203">**Audit**</span></span>  
     <span data-ttu-id="31172-204">既存のサーバー監査の名前。</span><span class="sxs-lookup"><span data-stu-id="31172-204">The name of an existing server audit.</span></span> <span data-ttu-id="31172-205">監査の名前を入力するか、一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="31172-205">Either type in the name of the audit or select it from the list.</span></span>  
  
     <span data-ttu-id="31172-206">**[監査アクションの種類]**</span><span class="sxs-lookup"><span data-stu-id="31172-206">**Audit Action Type**</span></span>  
     <span data-ttu-id="31172-207">キャプチャするサーバー レベルの監査アクション グループと監査アクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="31172-207">Specifies the server-level audit action groups and audit actions to capture.</span></span> <span data-ttu-id="31172-208">サーバー レベルの監査アクション グループと監査アクションの一覧、およびそれらに含まれるイベントの説明については、「 [SQL Server 監査のアクション グループとアクション](sql-server-audit-action-groups-and-actions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31172-208">For the list of server-level audit action groups and audit actions and a description of the events they contain, see [SQL Server Audit Action Groups and Actions](sql-server-audit-action-groups-and-actions.md).</span></span>  
  
     <span data-ttu-id="31172-209">**[オブジェクト スキーマ]**</span><span class="sxs-lookup"><span data-stu-id="31172-209">**Object Schema**</span></span>  
     <span data-ttu-id="31172-210">指定した **[オブジェクト名]** のスキーマを表示します。</span><span class="sxs-lookup"><span data-stu-id="31172-210">Displays the schema for the specified **Object Name**.</span></span>  
  
     <span data-ttu-id="31172-211">**[オブジェクト名]**</span><span class="sxs-lookup"><span data-stu-id="31172-211">**Object Name**</span></span>  
     <span data-ttu-id="31172-212">監査するオブジェクトの名前。</span><span class="sxs-lookup"><span data-stu-id="31172-212">The name of the object to audit.</span></span> <span data-ttu-id="31172-213">これは監査アクションにのみ使用できます。監査グループには適用されません。</span><span class="sxs-lookup"><span data-stu-id="31172-213">This is only available for audit actions; it does not apply to audit groups.</span></span>  
  
     <span data-ttu-id="31172-214">**省略記号 (...)**</span><span class="sxs-lookup"><span data-stu-id="31172-214">**Ellipsis (...)**</span></span>  
     <span data-ttu-id="31172-215">指定した **[監査アクションの種類]** に基づいて、使用可能なオブジェクトを参照して選択するための **[オブジェクトの選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="31172-215">Opens the **Select Objects** dialog to browse for and select an available object, based on the specified **Audit Action Type**.</span></span>  
  
     <span data-ttu-id="31172-216">**[プリンシパル名]**</span><span class="sxs-lookup"><span data-stu-id="31172-216">**Principal Name**</span></span>  
     <span data-ttu-id="31172-217">監査対象のオブジェクトで監査をフィルター選択するためのアカウント。</span><span class="sxs-lookup"><span data-stu-id="31172-217">The account to filter the audit by for the object being audited.</span></span>  
  
     <span data-ttu-id="31172-218">**省略記号 (...)**</span><span class="sxs-lookup"><span data-stu-id="31172-218">**Ellipsis (...)**</span></span>  
     <span data-ttu-id="31172-219">指定した **[オブジェクト名]** に基づいて、使用可能なオブジェクトを参照して選択するための **[オブジェクトの選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="31172-219">Opens the **Select Objects** dialog to browse for and select an available object, based on the specified **Object Name**.</span></span>  
  
3.  <span data-ttu-id="31172-220">操作が終了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31172-220">When you are finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="31172-221">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="31172-221">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-server-audit"></a><span data-ttu-id="31172-222">サーバー監査を作成するには</span><span class="sxs-lookup"><span data-stu-id="31172-222">To create a server audit</span></span>  
  
1.  <span data-ttu-id="31172-223">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="31172-223">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="31172-224">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31172-224">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="31172-225">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31172-225">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates a server audit called "HIPAA_Audit" with a binary file as the target and no options.  
    CREATE SERVER AUDIT HIPAA_Audit  
        TO FILE ( FILEPATH ='\\SQLPROD_1\Audit\' );  
    ```  
  
#### <a name="to-create-a-server-audit-specification"></a><span data-ttu-id="31172-226">サーバー監査仕様を作成するには</span><span class="sxs-lookup"><span data-stu-id="31172-226">To create a server audit specification</span></span>  
  
1.  <span data-ttu-id="31172-227">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="31172-227">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="31172-228">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31172-228">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="31172-229">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31172-229">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    /*Creates a server audit specification called "HIPAA_Audit_Specification" that audits failed logins for the SQL Server audit "HIPAA_Audit" created above.  
    */  
  
    CREATE SERVER AUDIT SPECIFICATION HIPAA_Audit_Specification  
    FOR SERVER AUDIT HIPAA_Audit  
        ADD (FAILED_LOGIN_GROUP);  
    GO  
    -- Enables the audit.   
  
    ALTER SERVER AUDIT HIPAA_Audit  
    WITH (STATE = ON);  
    GO  
    ```  
  
 <span data-ttu-id="31172-230">詳細については、「[CREATE SERVER AUDIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-transact-sql)」および「[CREATE SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-specification-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31172-230">For more information, see [CREATE SERVER AUDIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-transact-sql) and [CREATE SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-specification-transact-sql).</span></span>  
  
  
