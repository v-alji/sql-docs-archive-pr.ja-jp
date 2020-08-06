---
title: トランザクション アーティクルに変更を反映する方法の指定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, propagation methods
ms.assetid: a10c5001-22cc-4667-8f0b-3d0818dca2e9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 72d377ba89f1d393eab48bd9c918012b0f503f9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715181"
---
# <a name="specify-how-changes-are-propagated-for-transactional-articles"></a><span data-ttu-id="3cc86-102">トランザクション アーティクルに変更を反映する方法の指定</span><span class="sxs-lookup"><span data-stu-id="3cc86-102">Specify How Changes Are Propagated for Transactional Articles</span></span>
  <span data-ttu-id="3cc86-103">トランザクション レプリケーションを使用すると、パブリッシャーからサブスクライバーに変更を反映する方法を指定できます。</span><span class="sxs-lookup"><span data-stu-id="3cc86-103">Transactional replication allows you to specify how data changes are propagated from the Publisher to Subscribers.</span></span> <span data-ttu-id="3cc86-104">パブリッシュされた各テーブルに対して、次の 4 つの方法のいずれかを指定して、各操作 (INSERT、UPDATE、または DELETE) をサブスクライバーに反映できます。</span><span class="sxs-lookup"><span data-stu-id="3cc86-104">For each published table, you can specify one of four ways that each operation (INSERT, UPDATE, or DELETE) should be propagated to the Subscriber:</span></span>  
  
-   <span data-ttu-id="3cc86-105">トランザクション レプリケーションのスクリプトを作成し、その後、ストアド プロシージャを呼び出して変更をサブスクライバーに反映するように指定します (既定値)。</span><span class="sxs-lookup"><span data-stu-id="3cc86-105">Specify that transactional replication should script out and subsequently call a stored procedure to propagate changes to Subscribers (the default).</span></span>  
  
-   <span data-ttu-id="3cc86-106">INSERT、UPDATE、または DELETE ステートメントを使用して、変更が反映されるように指定します ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のサブスクライバーの既定値)。</span><span class="sxs-lookup"><span data-stu-id="3cc86-106">Specify that the change should be propagated using an INSERT, UPDATE, or DELETE statement (the default for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers).</span></span>  
  
-   <span data-ttu-id="3cc86-107">カスタム ストアド プロシージャを使用するように指定します。</span><span class="sxs-lookup"><span data-stu-id="3cc86-107">Specify that a custom stored procedure should be used.</span></span>  
  
-   <span data-ttu-id="3cc86-108">この操作がサブスクライバーで実行されないように指定します。</span><span class="sxs-lookup"><span data-stu-id="3cc86-108">Specify that this action should not be performed at any Subscriber.</span></span> <span data-ttu-id="3cc86-109">その種類のトランザクションはレプリケートされません。</span><span class="sxs-lookup"><span data-stu-id="3cc86-109">Transactions of that type are not replicated.</span></span>  
  
 <span data-ttu-id="3cc86-110">既定では、トランザクション レプリケーションが、各サブスクライバーにインストールされているストアド プロシージャのセットを使用して、変更をサブスクライバーに伝達します。</span><span class="sxs-lookup"><span data-stu-id="3cc86-110">By default, transactional replication propagates changes to Subscribers through a set of stored procedures that are installed on each Subscriber.</span></span> <span data-ttu-id="3cc86-111">パブリッシャーでテーブルに挿入、更新、または削除が発生した場合、各操作はサブスクライバーでのストアド プロシージャへの呼び出しに翻訳されます。</span><span class="sxs-lookup"><span data-stu-id="3cc86-111">When an insert, update or delete occurs on a table at the Publisher, the operation is translated into a call to a stored procedure at the Subscriber.</span></span> <span data-ttu-id="3cc86-112">ストアド プロシージャは、テーブル内の列にマップされるパラメーターを受け入れ、それらの列がサブスクライバーで変更されることを許可します。</span><span class="sxs-lookup"><span data-stu-id="3cc86-112">The stored procedure accepts parameters that map to the columns in the table, allowing those columns to be changed at the Subscriber.</span></span>  
  
 <span data-ttu-id="3cc86-113">データの変更をトランザクション アーティクルに反映する方法を設定するには、「 [データの変更をトランザクション アーティクルに反映する方法の設定](../publish/set-the-propagation-method-for-data-changes-to-transactional-articles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3cc86-113">To set the propagation method for data changes to transactional articles, see [Set the Propagation Method for Data Changes to Transactional Articles](../publish/set-the-propagation-method-for-data-changes-to-transactional-articles.md).</span></span>  
  
## <a name="default-and-custom-stored-procedures"></a><span data-ttu-id="3cc86-114">既定のストアド プロシージャとカスタム ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="3cc86-114">Default and custom stored procedures</span></span>  
 <span data-ttu-id="3cc86-115">各テーブル アーティクルに対して、既定でレプリケーションによって作成されるのは、次の 3 つのプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="3cc86-115">The three procedures that replication creates by default for each table article are:</span></span>  
  
-   <span data-ttu-id="3cc86-116">**sp_MSins_\<** *tablename* **>** 。挿入処理を行います。</span><span class="sxs-lookup"><span data-stu-id="3cc86-116">**sp_MSins_\<** *tablename* **>**, which handles inserts.</span></span>  
  
-   <span data-ttu-id="3cc86-117">**sp_MSupd_\<** *tablename* **>** 。更新処理を行います。</span><span class="sxs-lookup"><span data-stu-id="3cc86-117">**sp_MSupd_\<** *tablename* **>**, which handles updates.</span></span>  
  
-   <span data-ttu-id="3cc86-118">**sp_MSdel_\<** *tablename* **>** 。削除処理を行います。</span><span class="sxs-lookup"><span data-stu-id="3cc86-118">**sp_MSdel_\<** *tablename* **>**, which handles deletes.</span></span>  
  
 <span data-ttu-id="3cc86-119">このプロシージャで使用される **\<***tablename***>** は、アーティクルがパブリケーションにどのように追加されたか、およびサブスクリプション データベースに所有者が異なるものの同じ名前のテーブルが含まれているかどうかに応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="3cc86-119">The **\<***tablename***>** used in the procedure depends on how the article was added to the publication and whether the subscription database contains a table of the same name with a different owner.</span></span>  
  
 <span data-ttu-id="3cc86-120">これらのすべてのプロシージャは、パブリケーションにアーティクルを追加するときに指定したカスタム プロシージャと置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="3cc86-120">Any of these procedures can be replaced with a custom procedure that you specify when adding an article to a publication.</span></span> <span data-ttu-id="3cc86-121">カスタム プロシージャは、サブスクライバーでの行の更新時にデータを監査テーブルに挿入するなど、アプリケーションにカスタム ロジックが必要な場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="3cc86-121">Custom procedures are used if an application requires custom logic, such as inserting data into an audit table when a row is updated at a Subscriber.</span></span> <span data-ttu-id="3cc86-122">カスタム ストアド プロシージャの指定の詳細については、上記のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3cc86-122">For more information about specifying custom stored procedures, see the how to topics listed above.</span></span>  
  
 <span data-ttu-id="3cc86-123">既定のレプリケーション プロシージャまたはカスタム プロシージャを指定した場合は、各プロシージャに対する呼び出し構文も指定します (既定のプロシージャを使用する場合は、レプリケーションによって既定値が選択されます)。</span><span class="sxs-lookup"><span data-stu-id="3cc86-123">If you specify the default replication procedures or custom procedures, you also specify call syntax for each procedure (replication selects defaults if you use the default procedures).</span></span> <span data-ttu-id="3cc86-124">呼び出し構文によって、プロシージャに提供されたパラメーターの構造、および各データの変更と共にサブスクライバーに送信される情報の量が決定されます。</span><span class="sxs-lookup"><span data-stu-id="3cc86-124">The call syntax determines the structure of the parameters provided to the procedure and how much information is sent to the Subscriber with each data change.</span></span> <span data-ttu-id="3cc86-125">詳細については、このトピックの「ストアド プロシージャの呼び出し構文」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3cc86-125">For more information, see the section "Call Syntax for Stored Procedures" in this topic.</span></span>  
  
### <a name="considerations-for-using-custom-stored-procedures"></a><span data-ttu-id="3cc86-126">カスタム ストアド プロシージャの使用に関する注意点</span><span class="sxs-lookup"><span data-stu-id="3cc86-126">Considerations for Using Custom Stored Procedures</span></span>  
 <span data-ttu-id="3cc86-127">カスタム ストアド プロシージャを使用する場合は、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="3cc86-127">Keep the following considerations in mind when using custom stored procedures:</span></span>  
  
-   <span data-ttu-id="3cc86-128">ストアド プロシージャ内でロジックをサポートする必要があります。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] はカスタム ロジックをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="3cc86-128">You must support the logic in the stored procedure; [!INCLUDE[msCoName](../../../includes/msconame-md.md)] does not provide support for custom logic.</span></span>  
  
-   <span data-ttu-id="3cc86-129">レプリケーションによって使用されるトランザクションの競合を防ぐため、カスタム プロシージャでは明示的なトランザクションを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="3cc86-129">In order to avoid conflicts with the transactions used by replication, explicit transactions should not be used in custom procedures.</span></span>  
  
-   <span data-ttu-id="3cc86-130">サブスクライバーにおけるスキーマは、通常、パブリッシャーにおけるスキーマと同一になりますが、列フィルターが使用されている場合は、パブリッシャーのスキーマのサブセットにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="3cc86-130">The schema at the Subscriber is typically identical to the schema at the Publisher, but can also be a subset of the Publisher schema if column filtering is used.</span></span> <span data-ttu-id="3cc86-131">ただし、サブスクライバーのスキーマがパブリッシャーのスキーマのサブセットにならないように、データを移動するときにスキーマを変換する必要がある場合は、 [!INCLUDE[ssISCurrent](../../../includes/ssiscurrent-md.md)] を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3cc86-131">However, if you need to transform the schema as the data is moved such that the schema on the Subscriber is not a subset of the schema on the Publisher, [!INCLUDE[ssISCurrent](../../../includes/ssiscurrent-md.md)] is the recommended solution.</span></span> <span data-ttu-id="3cc86-132">詳細については、「 [SQL Server Integration Services](../../../integration-services/sql-server-integration-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3cc86-132">For more information, see [SQL Server Integration Services](../../../integration-services/sql-server-integration-services.md).</span></span>  
  
-   <span data-ttu-id="3cc86-133">スキーマの変更をパブリッシュされたテーブルに加える場合は、カスタム プロシージャを再生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3cc86-133">If you make schema changes to a published table, the custom procedures must be regenerated.</span></span> <span data-ttu-id="3cc86-134">詳細については、「[カスタム トランザクション プロシージャの再生成によるスキーマ変更の反映](transactional-articles-regenerate-to-reflect-schema-changes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3cc86-134">For more information, see [Regenerate Custom Transactional Procedures to Reflect Schema Changes](transactional-articles-regenerate-to-reflect-schema-changes.md).</span></span>  
  
-   <span data-ttu-id="3cc86-135">ディストリビューション エージェントの **-SubscriptionStreams** パラメーターに対して 1 を超える値を使用した場合は、主キー列に対する更新が成功したことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3cc86-135">If you use a value greater than 1 for **-SubscriptionStreams** parameter of the Distribution Agent, you must ensure that updates to primary key columns are successful.</span></span> <span data-ttu-id="3cc86-136">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="3cc86-136">For example:</span></span>  
  
    ```  
    update ... set pk = 2 where pk = 1 -- update 1  
    update ... set pk = 3 where pk = 2 -- update 2  
    ```  
  
     <span data-ttu-id="3cc86-137">ディストリビューション エージェントが複数の接続を使用する場合、次の 2 つの更新は、さまざまな接続を経由してレプリケートされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3cc86-137">If the Distribution Agent uses more than one connection, these two updates might be replicated over different connections.</span></span> <span data-ttu-id="3cc86-138">最初に update 1 が適用される場合は、問題は発生しません。最初に update 2 が適用された場合は、update 1 がまだ発生していないため、"0 行処理されました" というメッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="3cc86-138">If update 1 is applied first, there is no problem; if update 2 is applied first it will return '0 rows affected' because update 1 has not yet occurred.</span></span> <span data-ttu-id="3cc86-139">既定のプロシージャでは、更新による影響を受ける行がない場合にエラーを発生させることによって、このような状況を処理します。</span><span class="sxs-lookup"><span data-stu-id="3cc86-139">This situation is handled in the default procedures by raising an error if no rows are affected on an update:</span></span>  
  
    ```  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sys.sp_MSreplraiserror 20598  
    ```  
  
     <span data-ttu-id="3cc86-140">エラーの発生によって、ディストリビューション エージェントでは単一の接続による更新の再試行が強制的に行われ、この処理は正常に実行されます。</span><span class="sxs-lookup"><span data-stu-id="3cc86-140">Raising the error forces the Distribution Agent to retry the updates over a single connection, which will succeed.</span></span> <span data-ttu-id="3cc86-141">カスタム ストアド プロシージャには、これと同様のロジックを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="3cc86-141">Custom stored procedures must include similar logic.</span></span>  
  
### <a name="call-syntax-for-stored-procedures"></a><span data-ttu-id="3cc86-142">ストアド プロシージャの呼び出し構文</span><span class="sxs-lookup"><span data-stu-id="3cc86-142">Call syntax for stored procedures</span></span>  
 <span data-ttu-id="3cc86-143">トランザクション レプリケーションで使用されるプロシージャを呼び出すために使用される構文には、5 つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="3cc86-143">There are five options for the syntax used to call the procedures used by transactional replication:</span></span>  
  
-   <span data-ttu-id="3cc86-144">CALL 構文。</span><span class="sxs-lookup"><span data-stu-id="3cc86-144">CALL syntax.</span></span> <span data-ttu-id="3cc86-145">挿入、更新、および削除に使用できます。</span><span class="sxs-lookup"><span data-stu-id="3cc86-145">Can be used for inserts, updates, and deletes.</span></span> <span data-ttu-id="3cc86-146">既定では、レプリケーションは挿入と削除に対してこの構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="3cc86-146">By default, replication uses this syntax for inserts and deletes.</span></span>  
  
-   <span data-ttu-id="3cc86-147">SCALL 構文。</span><span class="sxs-lookup"><span data-stu-id="3cc86-147">SCALL syntax.</span></span> <span data-ttu-id="3cc86-148">更新のみに使用できます。</span><span class="sxs-lookup"><span data-stu-id="3cc86-148">Can be used for updates only.</span></span> <span data-ttu-id="3cc86-149">既定では、レプリケーションは更新に対してこの構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="3cc86-149">By default, replication uses this syntax for updates.</span></span>  
  
-   <span data-ttu-id="3cc86-150">MCALL 構文。</span><span class="sxs-lookup"><span data-stu-id="3cc86-150">MCALL syntax.</span></span> <span data-ttu-id="3cc86-151">更新のみに使用できます。</span><span class="sxs-lookup"><span data-stu-id="3cc86-151">Can be used for updates only.</span></span>  
  
-   <span data-ttu-id="3cc86-152">XCALL 構文。</span><span class="sxs-lookup"><span data-stu-id="3cc86-152">XCALL syntax.</span></span> <span data-ttu-id="3cc86-153">更新と削除に使用できます。</span><span class="sxs-lookup"><span data-stu-id="3cc86-153">Can be used for updates and deletes.</span></span>  
  
-   <span data-ttu-id="3cc86-154">VCALL。</span><span class="sxs-lookup"><span data-stu-id="3cc86-154">VCALL.</span></span> <span data-ttu-id="3cc86-155">更新可能なサブスクリプションに対して使用されます。</span><span class="sxs-lookup"><span data-stu-id="3cc86-155">Used for updatable subscriptions.</span></span> <span data-ttu-id="3cc86-156">内部使用のみです。</span><span class="sxs-lookup"><span data-stu-id="3cc86-156">Internal use only.</span></span>  
  
 <span data-ttu-id="3cc86-157">サブスクライバーに反映されるデータの量は、各方法で異なります。</span><span class="sxs-lookup"><span data-stu-id="3cc86-157">Each method differs in the amount of data that is propagated to the Subscriber.</span></span> <span data-ttu-id="3cc86-158">たとえば、SCALL は、更新によって実際に影響を受ける列だけに対する値の中でデータを渡します。</span><span class="sxs-lookup"><span data-stu-id="3cc86-158">For example, SCALL passes in values only for the columns that are actually affected by an update.</span></span> <span data-ttu-id="3cc86-159">対照的に、XCALL は、更新によって影響を受けるかどうかに関係なくすべての列、および各列のすべての古いデータ値を必要とします。</span><span class="sxs-lookup"><span data-stu-id="3cc86-159">XCALL, by contrast, requires all columns (whether affected by an update or not) and all the old data values for each column.</span></span> <span data-ttu-id="3cc86-160">多くの場合、SCALL は更新に適していますが、アプリケーションが更新中にすべてのデータ値を必要とする場合は、XCALL を更新に対して使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="3cc86-160">In many cases, SCALL is appropriate for updates, but if your application requires all the data values during an update, XCALL allows for this.</span></span>  
  
#### <a name="call-syntax"></a><span data-ttu-id="3cc86-161">CALL 構文</span><span class="sxs-lookup"><span data-stu-id="3cc86-161">CALL Syntax</span></span>  
 <span data-ttu-id="3cc86-162">INSERT ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="3cc86-162">INSERT stored procedures</span></span>  
 <span data-ttu-id="3cc86-163">INSERT ステートメントを処理するストアド プロシージャには、すべての列に挿入する値が渡されます。</span><span class="sxs-lookup"><span data-stu-id="3cc86-163">Stored procedures handling INSERT statements will be passed the inserted values for all columns:</span></span>  
  
```  
c1, c2, c3,... cn  
```  
  
 <span data-ttu-id="3cc86-164">UPDATE ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="3cc86-164">UPDATE stored procedures</span></span>  
 <span data-ttu-id="3cc86-165">UPDATE ステートメントを処理するストアド プロシージャには、アーティクルで定義されているすべての列を更新する値、およびその後に主キー列の元の値が渡されます (どの列が変更されたかは、判別されません)。</span><span class="sxs-lookup"><span data-stu-id="3cc86-165">Stored procedures handling UPDATE statements will be passed the updated values for all columns defined in the article, followed by the original values for the primary key columns (no attempt is made to determine which columns were changed.):</span></span>  
  
```  
c1, c2, c3,... cn, pkc1, pkc2, pkc3,... pkcn  
```  
  
 <span data-ttu-id="3cc86-166">DELETE ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="3cc86-166">DELETE stored procedures</span></span>  
 <span data-ttu-id="3cc86-167">DELETE ステートメントを処理するストアド プロシージャには、主キー列の値が渡されます。</span><span class="sxs-lookup"><span data-stu-id="3cc86-167">Stored procedures handling DELETE statements will be passed values for the primary key columns:</span></span>  
  
```  
pkc1, pkc2, pkc3,... pkcn  
```  
  
#### <a name="scall-syntax"></a><span data-ttu-id="3cc86-168">SCALL 構文</span><span class="sxs-lookup"><span data-stu-id="3cc86-168">SCALL Syntax</span></span>  
 <span data-ttu-id="3cc86-169">UPDATE ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="3cc86-169">UPDATE stored procedures</span></span>  
 <span data-ttu-id="3cc86-170">UPDATE ステートメントを処理するストアド プロシージャには、変更された列のみを更新する値、その後に主キー列の元の値、および変更された列を示すビットマスク (`binary(n)`) パラメーターが渡されます。</span><span class="sxs-lookup"><span data-stu-id="3cc86-170">Stored procedures handling UPDATE statements will be passed the updated values only for those columns that have changed, followed by the original values for the primary key columns, followed by a bitmask (`binary(n)`) parameter that indicates the changed columns.</span></span> <span data-ttu-id="3cc86-171">次の例では、列 2 (c2) は変更されていません。</span><span class="sxs-lookup"><span data-stu-id="3cc86-171">In the following example, column 2 (c2) has not changed:</span></span>  
  
```  
c1, , c3,... cn, pkc1, pkc2, pkc3,... pkcn, bitmask  
```  
  
#### <a name="mcall-syntax"></a><span data-ttu-id="3cc86-172">MCALL 構文</span><span class="sxs-lookup"><span data-stu-id="3cc86-172">MCALL Syntax</span></span>  
 <span data-ttu-id="3cc86-173">UPDATE ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="3cc86-173">UPDATE stored procedures</span></span>  
 <span data-ttu-id="3cc86-174">UPDATE ステートメントを処理するストアド プロシージャには、アーティクルで定義されているすべての列を更新する値、その後に主キー列の元の値、および変更された列を示すビットマスク (`binary(n)`) パラメーターが渡されます。</span><span class="sxs-lookup"><span data-stu-id="3cc86-174">Stored procedures handling UPDATE statements will be passed the updated values for all columns defined in the article, followed by the original values for the primary key columns, followed by a bitmask (`binary(n)`) parameter that indicates the changed columns:</span></span>  
  
```  
c1, c2, c3,... cn, pkc1, pkc2, pkc3,... pkcn, bitmask  
```  
  
#### <a name="xcall-syntax"></a><span data-ttu-id="3cc86-175">XCALL 構文</span><span class="sxs-lookup"><span data-stu-id="3cc86-175">XCALL Syntax</span></span>  
 <span data-ttu-id="3cc86-176">UPDATE ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="3cc86-176">UPDATE stored procedures</span></span>  
 <span data-ttu-id="3cc86-177">UPDATE ステートメントを処理するストアド プロシージャには、アーティクルで定義されているすべての列の元の値 (前イメージ) が渡され、その後にアーティクルで定義されているすべての列の更新された値 (後イメージ) が渡されます。</span><span class="sxs-lookup"><span data-stu-id="3cc86-177">Stored procedures handling UPDATE statements will be passed the original values (the before image) for all columns defined in the article, followed by the updated values (the after image) for all columns defined in the article:</span></span>  
  
```  
old-c1, old-c2, old-c3,... old-cn, c1, c2, c3,... cn,  
```  
  
 <span data-ttu-id="3cc86-178">DELETE ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="3cc86-178">DELETE stored procedures</span></span>  
 <span data-ttu-id="3cc86-179">DELETE ステートメントを処理するストアド プロシージャには、アーティクルで定義されているすべての列の元の値 (前イメージ) が渡されます。</span><span class="sxs-lookup"><span data-stu-id="3cc86-179">Stored procedures handling DELETE statements will be passed the original (the before image) values for all columns defined in the article:</span></span>  
  
```  
old-c1, old-c2, old-c3,... old-cn  
```  
  
> [!NOTE]  
>  <span data-ttu-id="3cc86-180">XCALL は、 **text** 列および **image** 列の前イメージ値が NULL であるという前提で使用してください。</span><span class="sxs-lookup"><span data-stu-id="3cc86-180">When using XCALL, the before image values for **text** and **image** columns are expected to be NULL.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="3cc86-181">例</span><span class="sxs-lookup"><span data-stu-id="3cc86-181">Examples</span></span>  
 <span data-ttu-id="3cc86-182">次のプロシージャは、 `Vendor Table` サンプル データベース内の [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)] に対して作成された既定のプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="3cc86-182">The following procedures are the default procedures created for the `Vendor Table` in the [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)] sample database.</span></span>  
  
```  
--INSERT procedure using CALL syntax  
create procedure [sp_MSins_PurchasingVendor]   
  @c1 int,@c2 nvarchar(15),@c3 nvarchar(50),@c4 tinyint,@c5 bit,@c6 bit,@c7 nvarchar(1024),@c8 datetime  
as   
begin   
insert into [Purchasing].[Vendor]([VendorID]  
,[AccountNumber]  
,[Name]  
,[CreditRating]  
,[PreferredVendorStatus]  
,[ActiveFlag]  
,[PurchasingWebServiceURL]  
,[ModifiedDate])  
values (   
 @c1  
,@c2  
,@c3  
,@c4  
,@c5  
,@c6  
,@c7  
,@c8  
 )   
end  
go  
  
--UPDATE procedure using SCALL syntax  
create procedure [sp_MSupd_PurchasingVendor]   
 @c1 int = null,@c2 nvarchar(15) = null,@c3 nvarchar(50) = null,@c4 tinyint = null,@c5 bit = null,@c6 bit = null,@c7 nvarchar(1024) = null,@c8 datetime = null,@pkc1 int  
,@bitmap binary(2)  
as  
begin  
update [Purchasing].[Vendor] set   
 [AccountNumber] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [AccountNumber] end  
,[Name] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [Name] end  
,[CreditRating] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [CreditRating] end  
,[PreferredVendorStatus] = case substring(@bitmap,1,1) & 16 when 16 then @c5 else [PreferredVendorStatus] end  
,[ActiveFlag] = case substring(@bitmap,1,1) & 32 when 32 then @c6 else [ActiveFlag] end  
,[PurchasingWebServiceURL] = case substring(@bitmap,1,1) & 64 when 64 then @c7 else [PurchasingWebServiceURL] end  
,[ModifiedDate] = case substring(@bitmap,1,1) & 128 when 128 then @c8 else [ModifiedDate] end  
where [VendorID] = @pkc1  
if @@rowcount = 0  
    if @@microsoftversion>0x07320000  
        exec sp_MSreplraiserror 20598  
end  
go  
  
--DELETE procedure using CALL syntax  
create procedure [sp_MSdel_PurchasingVendor]   
  @pkc1 int  
as   
begin   
delete [Purchasing].[Vendor]  
where [VendorID] = @pkc1  
if @@rowcount = 0  
    if @@microsoftversion>0x07320000  
        exec sp_MSreplraiserror 20598  
end   
go  
```  
  
## <a name="see-also"></a><span data-ttu-id="3cc86-183">参照</span><span class="sxs-lookup"><span data-stu-id="3cc86-183">See Also</span></span>  
 [<span data-ttu-id="3cc86-184">Article Options for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="3cc86-184">Article Options for Transactional Replication</span></span>](article-options-for-transactional-replication.md)  
  
  
