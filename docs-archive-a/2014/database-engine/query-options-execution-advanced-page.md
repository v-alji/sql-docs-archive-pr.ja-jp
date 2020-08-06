---
title: '[クエリオプション] の [実行] ([詳細設定] ページ)Microsoft Docs'
ms.prod: sql-server-2014
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.advanced.f1
ms.assetid: 661595ce-99b9-4316-ad80-ed04002d04d5
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: ''
ms.date: 09/03/2019
ms.openlocfilehash: 5b6ab8cc3c788e27946ddb68a3c926e8f926ebd7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736739"
---
# <a name="query-options-execution-advanced-page"></a><span data-ttu-id="d9be1-102">[クエリ オプション] の [実行] ([詳細設定] ページ)</span><span class="sxs-lookup"><span data-stu-id="d9be1-102">Query Options Execution (Advanced Page)</span></span>

  <span data-ttu-id="d9be1-103">**SET** ステートメントを使用する際には、さまざまなオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d9be1-103">A variety of options are available using the **SET** statement.</span></span> <span data-ttu-id="d9be1-104">このページを使用して Microsoft SQL Server クエリを実行する**SET**オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="d9be1-104">Use this page to specify a **SET** option to run Microsoft SQL Server queries.</span></span> <span data-ttu-id="d9be1-105">各オプションの詳細については、SQL Server オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9be1-105">For detailed information on each of these options, see SQL Server Books Online.</span></span>
  
<span data-ttu-id="d9be1-106">**SET NOCOUNT**結果セットのメッセージとして、行数のカウントを返しません。</span><span class="sxs-lookup"><span data-stu-id="d9be1-106">**SET NOCOUNT** Doesn't return the count of the number of rows, as a message with the result set.</span></span> <span data-ttu-id="d9be1-107">既定では、このオプションはオフになっています。</span><span class="sxs-lookup"><span data-stu-id="d9be1-107">This option is cleared by default.</span></span>

<span data-ttu-id="d9be1-108">**NOEXEC の設定**クエリを実行しません。</span><span class="sxs-lookup"><span data-stu-id="d9be1-108">**SET NOEXEC** Doesn't run the query.</span></span> <span data-ttu-id="d9be1-109">既定では、このオプションはオフになっています。</span><span class="sxs-lookup"><span data-stu-id="d9be1-109">This option is cleared by default.</span></span>

<span data-ttu-id="d9be1-110">**SET PARSEONLY**各クエリの構文をチェックしますが、クエリは実行しません。</span><span class="sxs-lookup"><span data-stu-id="d9be1-110">**SET PARSEONLY** Checks the syntax of each query but Doesn't run the queries.</span></span> <span data-ttu-id="d9be1-111">既定では、このオプションはオフになっています。</span><span class="sxs-lookup"><span data-stu-id="d9be1-111">This option is cleared by default.</span></span>  

<span data-ttu-id="d9be1-112">**CONCAT_NULL_YIELDS_NULL の設定**このチェックボックスをオンにすると、既存の値とを連結するクエリは、 `NULL` 常にを `NULL` 結果として返します。</span><span class="sxs-lookup"><span data-stu-id="d9be1-112">**SET CONCAT_NULL_YIELDS_NULL** When this check box is selected, queries that concatenate an existing value with a `NULL`, always return a `NULL` as the result.</span></span> <span data-ttu-id="d9be1-113">このチェック ボックスがオフの場合、既存の値と `NULL` を連結するクエリは、既存の値を返します。</span><span class="sxs-lookup"><span data-stu-id="d9be1-113">When this check box is cleared, an existing value concatenated with a `NULL`, returns the existing value.</span></span> <span data-ttu-id="d9be1-114">既定では、このオプションはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="d9be1-114">This option is selected by default.</span></span>

<span data-ttu-id="d9be1-115">**ARITHABORT の設定**このチェックボックスがオンの場合、 `INSERT` 式の `DELETE` 評価中に、、または `UPDATE` ステートメントで算術エラー (オーバーフロー、0による除算、またはドメインエラー) が発生すると、クエリまたはバッチは終了します。</span><span class="sxs-lookup"><span data-stu-id="d9be1-115">**SET ARITHABORT** When this check box is selected, when an `INSERT`, `DELETE` or `UPDATE` statement encounters an arithmetic error (overflow, divide-by-zero, or a domain error) during expression evaluation the query or batch is terminated.</span></span> <span data-ttu-id="d9be1-116">このチェック ボックスがオフの場合、可能であればその値に対して  `NULL` が与えられ、クエリが続行されます。さらに、結果にメッセージが含められます。</span><span class="sxs-lookup"><span data-stu-id="d9be1-116">When this check box is cleared, a `NULL` is provided for that value if possible, the query continues, and a message is included with the result.</span></span> <span data-ttu-id="d9be1-117">この動作の詳細については、オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9be1-117">See Books Online for a more extensive description of this behavior.</span></span> <span data-ttu-id="d9be1-118">既定では、このオプションはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="d9be1-118">This option is selected by default.</span></span>
  
<span data-ttu-id="d9be1-119">**SHOWPLAN_TEXT の設定**このチェックボックスをオンにすると、クエリごとにクエリプランがテキスト形式で返されます。</span><span class="sxs-lookup"><span data-stu-id="d9be1-119">**SET SHOWPLAN_TEXT** When this check box is selected, the query plan is returned in text form with each query.</span></span> <span data-ttu-id="d9be1-120">既定では、このオプションはオフになっています。</span><span class="sxs-lookup"><span data-stu-id="d9be1-120">This option is cleared by default.</span></span>
  
<span data-ttu-id="d9be1-121">**SET STATISTICS TIME**このチェックボックスをオンにすると、各クエリに対して時間統計が返されます。</span><span class="sxs-lookup"><span data-stu-id="d9be1-121">**SET STATISTICS TIME** When this check box is selected, the time statistics are returned with each query.</span></span> <span data-ttu-id="d9be1-122">既定では、このオプションはオフになっています。</span><span class="sxs-lookup"><span data-stu-id="d9be1-122">This option is cleared by default.</span></span>
  
<span data-ttu-id="d9be1-123">**SET STATISTICS IO**このチェックボックスをオンにすると、各クエリに対して入出力 (i/o) に関する統計情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="d9be1-123">**SET STATISTICS IO** When this check box is selected, statistics regarding input/output (I/O) are returned with each query.</span></span> <span data-ttu-id="d9be1-124">既定では、このオプションはオフになっています。</span><span class="sxs-lookup"><span data-stu-id="d9be1-124">This option is cleared by default.</span></span>
  
<span data-ttu-id="d9be1-125">**トランザクション分離レベルの設定**READ COMMITTED トランザクション分離レベルは、既定で設定されています。</span><span class="sxs-lookup"><span data-stu-id="d9be1-125">**SET TRANSACTION ISOLATION LEVEL** The READ COMMITTED transaction isolation level is set by default.</span></span> <span data-ttu-id="d9be1-126">詳細については、「[SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9be1-126">For more information, see [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql).</span></span> <span data-ttu-id="d9be1-127">SNAPSHOT transaction 分離レベルは使用できません。</span><span class="sxs-lookup"><span data-stu-id="d9be1-127">SNAPSHOT transaction isolation level isn't available.</span></span> <span data-ttu-id="d9be1-128">SNAPSHOT 分離を使用するには、次の [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="d9be1-128">To use SNAPSHOT isolation, add the following [!INCLUDE[tsql](../includes/tsql-md.md)] statement:</span></span>
  
  ```sql
  SET TRANSACTION ISOLATION LEVEL SNAPSHOT;
  GO
  ```

<span data-ttu-id="d9be1-129">**デッドロックの優先度の設定**既定値の**Normal**では、デッドロックが発生したときに各クエリの優先順位を同じにすることができます。</span><span class="sxs-lookup"><span data-stu-id="d9be1-129">**SET DEADLOCK PRIORITY** The default value of **Normal** allows each query to have the same priority when a deadlock occurs.</span></span> <span data-ttu-id="d9be1-130">このクエリがデッドロックの競合で常に敗北し、終了されるクエリとして選択されるようにするには、ドロップダウン リストで優先度 [Low] を選択してください。</span><span class="sxs-lookup"><span data-stu-id="d9be1-130">Select the priority Low from the drop-down list, if you want this query to lose any deadlock conflict and be selected as the query to be terminated.</span></span>

<span data-ttu-id="d9be1-131">**ロックタイムアウトの設定**既定値の-1 は、トランザクションが完了するまでロックが保持されることを示します。</span><span class="sxs-lookup"><span data-stu-id="d9be1-131">**SET LOCK TIMEOUT** The default value of -1 indicates that locks are held until transactions are completed.</span></span> <span data-ttu-id="d9be1-132">値が 0 の場合は、待ち時間はありません。ロックがかかるとすぐにメッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="d9be1-132">A value of 0 means not to wait at all and return a message as soon as a lock is encountered.</span></span> <span data-ttu-id="d9be1-133">トランザクションを終了するまでのロックを 0 ミリ秒よりも長く保持する必要がある場合は、0 より大きい値を指定します。</span><span class="sxs-lookup"><span data-stu-id="d9be1-133">Provide a value of greater than 0 milliseconds to terminate a transaction if the locks for transaction must be held for greater than that time.</span></span>

<span data-ttu-id="d9be1-134">**QUERY_GOVERNOR_COST_LIMIT の設定**Query **governor cost limit**オプションを使用して、クエリを実行できる期間の上限を指定します。</span><span class="sxs-lookup"><span data-stu-id="d9be1-134">**SET QUERY_GOVERNOR_COST_LIMIT** Use the **query governor cost limit** option to specify an upper limit on the time period in which a query can run.</span></span> <span data-ttu-id="d9be1-135">クエリ コストとは、特定のハードウェア構成でクエリを完了するために必要とされる予測所要時間を秒単位で表したものです。</span><span class="sxs-lookup"><span data-stu-id="d9be1-135">Query cost refers to the estimated elapsed time, in seconds, required to complete a query on a specific hardware configuration.</span></span> <span data-ttu-id="d9be1-136">既定値の 0 は、クエリの実行に関して時間的制限がないことを示します。</span><span class="sxs-lookup"><span data-stu-id="d9be1-136">The default setting of 0 indicates no limit to the length of time a query will run</span></span>

<span data-ttu-id="d9be1-137">**プロバイダーメッセージヘッダー**を表示しないこのチェックボックスがオンの場合、プロバイダーからのステータスメッセージ (OLE DB プロバイダーなど) は表示されません。</span><span class="sxs-lookup"><span data-stu-id="d9be1-137">**Suppress provider message headers** When this check box is selected, status messages from the provider (such as the OLE DB provider) aren't displayed.</span></span> <span data-ttu-id="d9be1-138">既定では、このチェック ボックスはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="d9be1-138">This check box is selected by default.</span></span> <span data-ttu-id="d9be1-139">プロバイダー レベルで失敗するクエリのトラブルシューティングを行うときにプロバイダー メッセージを表示するには、このチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="d9be1-139">Clear this check box to see the provider messages when troubleshooting queries that may be failing at the provider level.</span></span>

<span data-ttu-id="d9be1-140">**クエリの実行後に切断する**このチェックボックスがオンの場合、SQL Server への接続は、クエリの完了後に終了します。</span><span class="sxs-lookup"><span data-stu-id="d9be1-140">**Disconnect after the query executes** When this check box is selected, the connection to SQL Server is terminated after the query completes.</span></span> <span data-ttu-id="d9be1-141">既定では、このオプションはオフになっています。</span><span class="sxs-lookup"><span data-stu-id="d9be1-141">This option is cleared by default.</span></span>

<span data-ttu-id="d9be1-142">**完了時刻を表示する**クエリの実行が完了した時刻を、クエリ結果または [メッセージ] タブで印刷できます。</span><span class="sxs-lookup"><span data-stu-id="d9be1-142">**Show completion time** Allows you to print the time at which the query execution completed either after the query results or in the messages tab.</span></span>

<span data-ttu-id="d9be1-143">**Always Encrypted 用の VBS enclaves の構成証明プロトコル**セキュリティで保護された enclaves で always Encrypted によって使用される、仮想化ベースのセキュリティ (VBS) enclaves の構成証明プロトコルを設定できます。</span><span class="sxs-lookup"><span data-stu-id="d9be1-143">**Attestation protocol for VBS enclaves for Always Encrypted** Allows you to set an attestation protocol for Virtualization Based Security (VBS) enclaves used by always Encrypted with secure enclaves.</span></span>

<span data-ttu-id="d9be1-144">現在サポートされている構成証明プロトコルは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d9be1-144">The current supported attestation protocols are:</span></span>

* <span data-ttu-id="d9be1-145">ホストガーディアンサービス-Windows ホストガーディアンサービス (HGS) を使用した構成証明プロトコル。</span><span class="sxs-lookup"><span data-stu-id="d9be1-145">Host Guardian Service - an attestation protocol using Windows Host Guardian Service (HGS).</span></span>

<span data-ttu-id="d9be1-146">詳細については、「 [Always Encrypted with secure enclaves](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-enclaves?view=sqlallproducts-allversions) And [Secure エンクレーブ構成証明](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-enclaves?view=sqlallproducts-allversions#secure-enclave-attestation)書」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9be1-146">For more information, see [Always Encrypted with secure enclaves](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-enclaves?view=sqlallproducts-allversions) and [Secure Enclave Attestation](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-enclaves?view=sqlallproducts-allversions#secure-enclave-attestation).</span></span>

<span data-ttu-id="d9be1-147">**[既定値にリセット]** このページ上のすべての値を元の既定値にリセットします。</span><span class="sxs-lookup"><span data-stu-id="d9be1-147">**Reset to Default** Resets all values on this page to the original default values.</span></span>
