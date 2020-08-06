---
title: トランザクション レプリケーションにおけるパブリッシング ストアド プロシージャの実行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- articles [SQL Server replication], stored procedures and
- transactional replication, publishing stored procedure execution
ms.assetid: f4686f6f-c224-4f07-a7cb-92f4dd483158
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0fb5c40db46772cabcb5d1df19e03aced749e1c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738185"
---
# <a name="publishing-stored-procedure-execution-in-transactional-replication"></a><span data-ttu-id="b7ace-102">トランザクション レプリケーションにおけるパブリッシング ストアド プロシージャの実行</span><span class="sxs-lookup"><span data-stu-id="b7ace-102">Publishing Stored Procedure Execution in Transactional Replication</span></span>
  <span data-ttu-id="b7ace-103">パブリッシャー側で実行され、パブリッシュされたテーブルに影響を与えるストアド プロシージャがある場合、それらのストアド プロシージャをストアド プロシージャ実行アーティクルとしてパブリケーションに含めることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="b7ace-103">If you have one or more stored procedures that execute at the Publisher and affect published tables, consider including those stored procedures in your publication as stored procedure execution articles.</span></span> <span data-ttu-id="b7ace-104">プロシージャの定義 (CREATE PROCEDURE ステートメント) はサブスクリプションが初期化されるときにサブスクライバーにレプリケートされます。プロシージャがパブリッシャーで実行されるときに、レプリケーションは対応するプロシージャをサブスクライバーで実行します。</span><span class="sxs-lookup"><span data-stu-id="b7ace-104">The definition of the procedure (the CREATE PROCEDURE statement) is replicated to the Subscriber when the subscription is initialized; when the procedure is executed at the Publisher, replication executes the corresponding procedure at the Subscriber.</span></span> <span data-ttu-id="b7ace-105">これにより、各行の個別の変更のレプリケーションが回避されてプロシージャの実行のみがレプリケートされるため、大量のバッチ操作が実行される場合にはパフォーマンスが著しく向上します。</span><span class="sxs-lookup"><span data-stu-id="b7ace-105">This can provide significantly better performance for cases where large batch operations are performed, because only the procedure execution is replicated, bypassing the need to replicate the individual changes for each row.</span></span> <span data-ttu-id="b7ace-106">たとえば、パブリケーション データベースで次のストアド プロシージャを作成するとします。</span><span class="sxs-lookup"><span data-stu-id="b7ace-106">For example, assume you create the following stored procedure in the publication database:</span></span>  
  
```  
CREATE PROC give_raise AS  
UPDATE EMPLOYEES SET salary = salary * 1.10  
```  
  
 <span data-ttu-id="b7ace-107">このプロシージャでは、社内 10,000 人の各従業員に 10% の昇給を行います。</span><span class="sxs-lookup"><span data-stu-id="b7ace-107">This procedure gives each of the 10,000 employees in your company a 10 percent pay increase.</span></span> <span data-ttu-id="b7ace-108">パブリッシャーでこのストアド プロシージャを実行すると、各従業員の基本給が更新されます。</span><span class="sxs-lookup"><span data-stu-id="b7ace-108">When you execute this stored procedure at the Publisher, it updates the salary for each employee.</span></span> <span data-ttu-id="b7ace-109">ストアド プロシージャの実行をレプリケートしない場合、この更新は大規模な何段階ものトランザクションとしてサブスクライバーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="b7ace-109">Without the replication of stored procedure execution, the update would be sent to Subscribers as a large, multi-step transaction:</span></span>  
  
```  
BEGIN TRAN  
UPDATE EMPLOYEES SET salary = salary * 1.10 WHERE PK = 'emp 1'  
UPDATE EMPLOYEES SET salary = salary * 1.10 WHERE PK = 'emp 2'  
```  
  
 <span data-ttu-id="b7ace-110">これが 10,000 件の更新分について繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="b7ace-110">And this repeats for 10,000 updates.</span></span>  
  
 <span data-ttu-id="b7ace-111">ストアド プロシージャの実行をレプリケートする場合、レプリケーションは、サブスクライバー側でストアド プロシージャを実行するコマンドのみを送信します。すべての更新をディストリビューション データベースに書き込んでからネットワークを経由してサブスクライバーに送信する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b7ace-111">With the replication of stored procedure execution, replication sends only the command to execute the stored procedure at the Subscriber, rather than writing all the updates to the distribution database and then sending them over the network to the Subscriber:</span></span>  
  
```  
EXEC give_raise  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b7ace-112">ストアド プロシージャのレプリケーションは、すべてのアプリケーションに適しているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="b7ace-112">Stored procedure replication is not appropriate for all applications.</span></span> <span data-ttu-id="b7ace-113">サブスクライバーとは異なる行のセットがパブリッシャーに存在するようにアーティクルが行方向でフィルター選択される場合、両方で同じストアド プロシージャを実行すると異なる結果が返ります。</span><span class="sxs-lookup"><span data-stu-id="b7ace-113">If an article is filtered horizontally, so that there are different sets of rows at the Publisher than at the Subscriber, executing the same stored procedure at both returns different results.</span></span> <span data-ttu-id="b7ace-114">同様に、レプリケートされていない別のテーブルのサブクエリに基づいた更新の場合、パブリッシャー側とサブスクライバー側の両方で同じストアド プロシージャを実行しても異なる結果が返ります。</span><span class="sxs-lookup"><span data-stu-id="b7ace-114">Similarly, if an update is based on a subquery of another, nonreplicated table, executing the same stored procedure at both the Publisher and Subscriber returns different results.</span></span>  
  
 <span data-ttu-id="b7ace-115">**ストアド プロシージャの実行をパブリッシュするには**</span><span class="sxs-lookup"><span data-stu-id="b7ace-115">**To publish the execution of a stored procedure**</span></span>  
  
-   <span data-ttu-id="b7ace-116">SQL Server Management Studio: [トランザクション パブリケーションでストアド プロシージャの実行をパブリッシュする方法 &#40;SQL Server Management Studio&#41;](../publish/publish-execution-of-stored-procedure-in-transactional-publication.md)</span><span class="sxs-lookup"><span data-stu-id="b7ace-116">SQL Server Management Studio: [Publish the Execution of a Stored Procedure in a Transactional Publication &#40;SQL Server Management Studio&#41;](../publish/publish-execution-of-stored-procedure-in-transactional-publication.md)</span></span>  
  
-   <span data-ttu-id="b7ace-117">レプリケーション Transact-sql プログラミング: [transact-sql&#41;を実行 sp_addarticle &#40;](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) 、パラメーターに ' serializable proc exec ' (推奨) または ' proc exec ' の値を指定し **@type** ます。</span><span class="sxs-lookup"><span data-stu-id="b7ace-117">Replication Transact-SQL Programming: execute [sp_addarticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) and specify a value of 'serializable proc exec' (recommended) or 'proc exec' for the parameter **@type**.</span></span> <span data-ttu-id="b7ace-118">アーティクルの定義の詳細については、「[Define an Article](../publish/define-an-article.md)」 (アーティクルの定義) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7ace-118">For more information about defining articles, see [Define an Article](../publish/define-an-article.md).</span></span>  
  
## <a name="modifying-the-procedure-at-the-subscriber"></a><span data-ttu-id="b7ace-119">サブスクライバーでのプロシージャの変更</span><span class="sxs-lookup"><span data-stu-id="b7ace-119">Modifying the Procedure at the Subscriber</span></span>  
 <span data-ttu-id="b7ace-120">既定では、パブリッシャー上のストアド プロシージャの定義は各サブスクライバーに反映されます。</span><span class="sxs-lookup"><span data-stu-id="b7ace-120">By default, the stored procedure definition at the Publisher is propagated to each Subscriber.</span></span> <span data-ttu-id="b7ace-121">ただし、サブスクライバーでストアド プロシージャを変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="b7ace-121">However, you can also modify the stored procedure at the Subscriber.</span></span> <span data-ttu-id="b7ace-122">これは、パブリッシャーとサブスクライバーで異なるロジックを実行する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="b7ace-122">This is useful if you want different logic to be executed at the Publisher and Subscriber.</span></span> <span data-ttu-id="b7ace-123">たとえば、2 つの関数を持つパブリッシャー上のストアド プロシージャ、 **sp_big_delete**を考えてみます。このストアド プロシージャはレプリケートされたテーブル **big_table1** から 100 万行を削除し、レプリケートされていないテーブル **big_table2**を更新します。</span><span class="sxs-lookup"><span data-stu-id="b7ace-123">For example, consider **sp_big_delete**, a stored procedure at the Publisher that has two functions: it deletes 1,000,000 rows from the replicated table **big_table1** and updates the nonreplicated table **big_table2**.</span></span> <span data-ttu-id="b7ace-124">ネットワーク リソースの需要を削減するには、 **sp_big_delete**をパブリッシュすることによって、100 万行の削除をストアド プロシージャとして反映する方が効率的です。</span><span class="sxs-lookup"><span data-stu-id="b7ace-124">To reduce the demand on network resources, you should propagate the 1 million row delete as a stored procedure by publishing **sp_big_delete**.</span></span> <span data-ttu-id="b7ace-125">サブスクライバーでは、100 万行だけを削除し、 **big_table2** への更新を実行しないように **sp_big_delete**を変更できます。</span><span class="sxs-lookup"><span data-stu-id="b7ace-125">At the Subscriber, you can modify **sp_big_delete** to delete only the 1 million rows and not perform the subsequent update to **big_table2**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b7ace-126">既定では、パブリッシャーで ALTER PROCEDURE を使用して行われたすべての変更はサブスクライバーに反映されます。</span><span class="sxs-lookup"><span data-stu-id="b7ace-126">By default, any changes made using ALTER PROCEDURE at the Publisher are propagated to the Subscriber.</span></span> <span data-ttu-id="b7ace-127">これを防ぐには、ALTER PROCEDURE を実行する前に、スキーマの変更の反映を無効にしてください。</span><span class="sxs-lookup"><span data-stu-id="b7ace-127">To prevent this, disable the propagation of schema changes before executing ALTER PROCEDURE.</span></span> <span data-ttu-id="b7ace-128">スキーマ変更の詳細については、「[パブリケーション データベースでのスキーマの変更](../publish/make-schema-changes-on-publication-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7ace-128">For information about schema changes, see [Make Schema Changes on Publication Databases](../publish/make-schema-changes-on-publication-databases.md).</span></span>  
  
## <a name="types-of-stored-procedure-execution-articles"></a><span data-ttu-id="b7ace-129">ストアド プロシージャ実行アーティクルの種類</span><span class="sxs-lookup"><span data-stu-id="b7ace-129">Types of Stored Procedure Execution Articles</span></span>  
 <span data-ttu-id="b7ace-130">ストアド プロシージャの実行をパブリッシュするには、シリアル化可能なプロシージャ実行アーティクルとプロシージャ実行アーティクルの 2 種類の方法があります。</span><span class="sxs-lookup"><span data-stu-id="b7ace-130">There are two different ways in which the execution of a stored procedure can be published: serializable procedure execution article and procedure execution article.</span></span>  
  
-   <span data-ttu-id="b7ace-131">シリアル化可能オプションでは、プロシージャがシリアル化可能なトランザクションのコンテキスト内で実行される場合にのみ、プロシージャの実行がレプリケートされるため、このオプションをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b7ace-131">The serializable option is recommended because it replicates the procedure execution only if the procedure is executed within the context of a serializable transaction.</span></span> <span data-ttu-id="b7ace-132">ストアド プロシージャがシリアル化可能なトランザクションの外から実行される場合、パブリッシュされたテーブルのデータに対する変更は一連の DML ステートメントとしてレプリケートされます。</span><span class="sxs-lookup"><span data-stu-id="b7ace-132">If the stored procedure is executed from outside a serializable transaction, changes to data in published tables are replicated as a series of DML statements.</span></span> <span data-ttu-id="b7ace-133">この動作により、サブスクライバー上のデータとパブリッシャー上のデータの一貫性が保たれます。</span><span class="sxs-lookup"><span data-stu-id="b7ace-133">This behavior contributes to making data at the Subscriber consistent with data at the Publisher.</span></span> <span data-ttu-id="b7ace-134">これは、たとえば大規模なクリーンアップ操作などの、バッチ操作に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="b7ace-134">This is especially useful for batch operations, such as large cleanup operations.</span></span>  
  
-   <span data-ttu-id="b7ace-135">プロシージャ実行オプションを使用すると、ストアド プロシージャ内の個々のステートメントが成功したかどうかにかかわらず、すべてのサブスクライバーに実行がレプリケートされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b7ace-135">With the procedure execution option, it is possible that execution could be replicated to all Subscribers regardless of whether individual statements in the stored procedure were successful.</span></span> <span data-ttu-id="b7ace-136">さらに、ストアド プロシージャによって生じるデータの変更は複数のトランザクションで発生する可能性があるので、サブスクライバー上のデータとパブリッシャー上のデータに一貫性がなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b7ace-136">Furthermore, because changes made to data by the stored procedure can occur within multiple transactions, data at the Subscribers might not be consistent with data at the Publisher.</span></span> <span data-ttu-id="b7ace-137">このような問題に対処するには、サブスクライバーが読み取り専用であることと、READ UNCOMMITTED より高い分離レベルを使用していることが必要です。</span><span class="sxs-lookup"><span data-stu-id="b7ace-137">To address these issues, it is required that Subscribers are read-only and that you use an isolation level greater than read uncommitted.</span></span> <span data-ttu-id="b7ace-138">READ UNCOMMITTED を使用する場合、パブリッシュされたテーブルのデータに対する変更は一連の DML ステートメントとしてレプリケートされます。</span><span class="sxs-lookup"><span data-stu-id="b7ace-138">If you use read uncommitted, changes to data in published tables are replicated as a series of DML statements.</span></span>  
  
 <span data-ttu-id="b7ace-139">次の例は、プロシージャのレプリケーションを、シリアル化可能なプロシージャ アーティクルとして設定することの利点を示します。</span><span class="sxs-lookup"><span data-stu-id="b7ace-139">The following example illustrates why it is recommended that you set up replication of procedures as serializable procedure articles.</span></span>  
  
```  
BEGIN TRANSACTION T1  
SELECT @var = max(col1) FROM tableA  
UPDATE tableA SET col2 = <value>   
   WHERE col1 = @var   
  
BEGIN TRANSACTION T2  
INSERT tableA VALUES <values>  
COMMIT TRANSACTION T2  
```  
  
 <span data-ttu-id="b7ace-140">この例では、トランザクション T1 にある SELECT が、トランザクション T2 の INSERT よりも先に発生すると想定しています。</span><span class="sxs-lookup"><span data-stu-id="b7ace-140">In the previous example, it is assumed that the SELECT in transaction T1 happens before the INSERT in transaction T2.</span></span>  
  
 <span data-ttu-id="b7ace-141">このプロシージャが、シリアル化可能なトランザクション内で実行 (分離レベルを SERIALIZABLE に設定して実行) されないと、トランザクション T2 では T1 の SELECT ステートメントの範囲内に新しい行を挿入し、それを T1 より先にコミットすることが許可されます。</span><span class="sxs-lookup"><span data-stu-id="b7ace-141">If the procedure is not executed within a serializable transaction (with isolation level set to SERIALIZABLE), transaction T2 will be allowed to insert a new row within the range of the SELECT statement in T1 and it will commit before T1.</span></span> <span data-ttu-id="b7ace-142">これは、T1 よりも先にサブスクライバーで挿入が適用されることも意味します。</span><span class="sxs-lookup"><span data-stu-id="b7ace-142">This also means that it will be applied at the Subscriber before T1.</span></span> <span data-ttu-id="b7ace-143">サブスクライバーに T1 が適用されると、SELECT によってパブリッシャーとは異なる値が返される可能性があり、UPDATE からの出力が異なる結果になる可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="b7ace-143">When T1 is applied at the Subscriber, the SELECT can potentially return a different value than at the Publisher and can result in a different outcome from the UPDATE.</span></span>  
  
 <span data-ttu-id="b7ace-144">このプロシージャが、シリアル化可能なトランザクションの中で実行される場合には、トランザクション T2 で、T2 の SELECT ステートメントの範囲に挿入を行うことが許可されません。</span><span class="sxs-lookup"><span data-stu-id="b7ace-144">If the procedure is executed within a serializable transaction, transaction T2 will not be allowed to insert within the range covered by the SELECT statement in T2.</span></span> <span data-ttu-id="b7ace-145">T1 がコミットするまでブロックされて、サブスクライバーでの結果が同じになるようにします。</span><span class="sxs-lookup"><span data-stu-id="b7ace-145">It will be blocked until T1 commits ensuring the same results at the Subscriber.</span></span>  
  
 <span data-ttu-id="b7ace-146">シリアル化可能なトランザクション内でプロシージャを実行するときにはロックがより長く保持されるので、コンカレンシーが少なくなることもあります。</span><span class="sxs-lookup"><span data-stu-id="b7ace-146">Locks will be held longer when you execute the procedure within a serializable transaction and may result in reduced concurrency.</span></span>  
  
## <a name="the-xact_abort-setting"></a><span data-ttu-id="b7ace-147">XACT_ABORT の設定</span><span class="sxs-lookup"><span data-stu-id="b7ace-147">The XACT_ABORT Setting</span></span>  
 <span data-ttu-id="b7ace-148">ストアド プロシージャの実行をレプリケートする場合、ストアド プロシージャを実行するセッションの設定では XACT_ABORT を ON に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7ace-148">When replicating stored procedure execution, the setting for the session executing the stored procedure should specify XACT_ABORT ON.</span></span> <span data-ttu-id="b7ace-149">XACT_ABORT が OFF に設定されていて、パブリッシャーでプロシージャの実行中にエラーが発生した場合、サブスクライバーでも同じエラーが発生し、ディストリビューション エージェントは失敗します。</span><span class="sxs-lookup"><span data-stu-id="b7ace-149">If XACT_ABORT is set to OFF, and an error occurs during execution of the procedure at the Publisher, the same error will occur at the Subscriber, causing the Distribution Agent to fail.</span></span> <span data-ttu-id="b7ace-150">XACT_ABORT を  ON に指定すると、パブリッシャーでプロシージャの実行中にエラーが発生した場合、実行全体がロールバックされ、ディストリビューション エージェントの失敗を回避できます。</span><span class="sxs-lookup"><span data-stu-id="b7ace-150">Specifying XACT_ABORT ON ensures that any errors encountered during execution at the Publisher cause the entire execution to be rolled back, avoiding the Distribution Agent failure.</span></span> <span data-ttu-id="b7ace-151">XACT_ABORT 設定の詳細については、「[SET XACT_ABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-xact-abort-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7ace-151">For more information about setting XACT_ABORT, see [SET XACT_ABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-xact-abort-transact-sql).</span></span>  
  
 <span data-ttu-id="b7ace-152">XACT_ABORT を OFF に設定する必要がある場合は、ディストリビューション エージェントの **-SkipErrors** パラメーターを指定してください。</span><span class="sxs-lookup"><span data-stu-id="b7ace-152">If you require a setting of XACT_ABORT OFF, specify the **-SkipErrors** parameter for the Distribution Agent.</span></span> <span data-ttu-id="b7ace-153">これで、エラーが発生した場合でも、エージェントは引き続きサブスクライバーに変更を適用できます。</span><span class="sxs-lookup"><span data-stu-id="b7ace-153">This allows the agent to continue applying changes at the Subscriber even if an error is encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7ace-154">参照</span><span class="sxs-lookup"><span data-stu-id="b7ace-154">See Also</span></span>  
 [<span data-ttu-id="b7ace-155">Article Options for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="b7ace-155">Article Options for Transactional Replication</span></span>](article-options-for-transactional-replication.md)  
  
  
