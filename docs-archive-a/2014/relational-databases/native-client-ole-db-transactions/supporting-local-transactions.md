---
title: ローカル トランザクションのサポート | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- autocommit mode
- transactions [OLE DB]
- ITransactionLocal interface
- SQL Server Native Client OLE DB provider, transactions
- local transactions [OLE DB]
ms.assetid: 78f2e5fc-b6fb-4eda-9f71-991a4d6c4902
author: rothja
ms.author: jroth
ms.openlocfilehash: a9bc11a038e56517aa42619117c371c1319b9ffe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643787"
---
# <a name="supporting-local-transactions"></a><span data-ttu-id="db794-102">ローカル トランザクションのサポート</span><span class="sxs-lookup"><span data-stu-id="db794-102">Supporting Local Transactions</span></span>
  <span data-ttu-id="db794-103">セッションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのローカルトランザクションのトランザクションスコープを区切ります。</span><span class="sxs-lookup"><span data-stu-id="db794-103">A session delimits transaction scope for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider local transaction.</span></span> <span data-ttu-id="db794-104">コンシューマーの指示によっ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] て、Native client OLE DB プロバイダーがの接続されたインスタンスに要求を送信すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 要求は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native client OLE DB プロバイダーの作業単位になります。</span><span class="sxs-lookup"><span data-stu-id="db794-104">When, at the direction of a consumer, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider submits a request to a connected instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the request constitutes a unit of work for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span> <span data-ttu-id="db794-105">ローカルトランザクションでは、1つの Native Client OLE DB プロバイダーセッションで、1つまたは複数の作業単位が常にラップさ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] れます。</span><span class="sxs-lookup"><span data-stu-id="db794-105">Local transactions always wrap one or more units of work on a single [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider session.</span></span>  
  
 <span data-ttu-id="db794-106">既定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの自動コミットモードを使用すると、1つの作業単位がローカルトランザクションのスコープとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="db794-106">Using the default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider autocommit mode, a single unit of work is treated as the scope of a local transaction.</span></span> <span data-ttu-id="db794-107">ローカル トランザクションに参加するのは、1 単位のみです。</span><span class="sxs-lookup"><span data-stu-id="db794-107">Only one unit participates in the local transaction.</span></span> <span data-ttu-id="db794-108">セッションが作成されると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、セッションのトランザクションを開始します。</span><span class="sxs-lookup"><span data-stu-id="db794-108">When a session is created, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider begins a transaction for the session.</span></span> <span data-ttu-id="db794-109">作業単位の処理が正常に完了すると、その作業がコミットされます。</span><span class="sxs-lookup"><span data-stu-id="db794-109">Upon successful completion of a work unit, the work is committed.</span></span> <span data-ttu-id="db794-110">失敗すると、開始された作業がすべてロールバックされ、エラーがコンシューマーに報告されます。</span><span class="sxs-lookup"><span data-stu-id="db794-110">On failure, any work begun is rolled back and the error is reported to the consumer.</span></span> <span data-ttu-id="db794-111">どちらの場合も、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、すべての作業がトランザクション内で実行されるように、セッションの新しいローカルトランザクションを開始します。</span><span class="sxs-lookup"><span data-stu-id="db794-111">In either case, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider begins a new local transaction for the session so that all work is conducted within a transaction.</span></span>  
  
 <span data-ttu-id="db794-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーコンシューマーは、 **ITransactionLocal**インターフェイスを使用して、ローカルトランザクションスコープをより細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="db794-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer can direct more precise control over local transaction scope by using the **ITransactionLocal** interface.</span></span> <span data-ttu-id="db794-113">コンシューマーのセッションがトランザクションを開始すると、トランザクションの開始時点から、最終的に **Commit** または **Abort** メソッドが呼び出されるまでのセッションの作業単位すべてが、1 つのアトミックな単位として扱われます。</span><span class="sxs-lookup"><span data-stu-id="db794-113">When a consumer session initiates a transaction, all session work units between the transaction start point and the eventual **Commit** or **Abort** method calls are treated as an atomic unit.</span></span> <span data-ttu-id="db794-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、コンシューマーに指示されたときにトランザクションを暗黙的に開始します。</span><span class="sxs-lookup"><span data-stu-id="db794-114">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implicitly begins a transaction when directed to do so by the consumer.</span></span> <span data-ttu-id="db794-115">コンシューマーがモードの保持を要求しないと、セッションは親のトランザクション レベルの動作 (通常は、自動コミット モード) に戻ります。</span><span class="sxs-lookup"><span data-stu-id="db794-115">If the consumer does not request retention, the session reverts to parent transaction-level behavior, most commonly autocommit mode.</span></span>  
  
 <span data-ttu-id="db794-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーでは、次のように**ITransactionLocal:: starttransaction**パラメーターがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="db794-116">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports **ITransactionLocal::StartTransaction** parameters as follows.</span></span>  
  
|<span data-ttu-id="db794-117">パラメーター</span><span class="sxs-lookup"><span data-stu-id="db794-117">Parameter</span></span>|<span data-ttu-id="db794-118">説明</span><span class="sxs-lookup"><span data-stu-id="db794-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="db794-119">*isoLevel*[in]</span><span class="sxs-lookup"><span data-stu-id="db794-119">*isoLevel*[in]</span></span>|<span data-ttu-id="db794-120">このトランザクションで使用する分離レベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="db794-120">The isolation level to be used with this transaction.</span></span> <span data-ttu-id="db794-121">ローカルトランザクションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは次の機能をサポートします。</span><span class="sxs-lookup"><span data-stu-id="db794-121">In local transactions, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports the following:</span></span><br /><br /> <span data-ttu-id="db794-122">-ISOLATIONLEVEL_UNSPECIFIED</span><span class="sxs-lookup"><span data-stu-id="db794-122">-   ISOLATIONLEVEL_UNSPECIFIED</span></span><br /><span data-ttu-id="db794-123">-ISOLATIONLEVEL_CHAOS</span><span class="sxs-lookup"><span data-stu-id="db794-123">-   ISOLATIONLEVEL_CHAOS</span></span><br /><span data-ttu-id="db794-124">-ISOLATIONLEVEL_READUNCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="db794-124">-   ISOLATIONLEVEL_READUNCOMMITTED</span></span><br /><span data-ttu-id="db794-125">-ISOLATIONLEVEL_READCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="db794-125">-   ISOLATIONLEVEL_READCOMMITTED</span></span><br /><span data-ttu-id="db794-126">-ISOLATIONLEVEL_REPEATABLEREAD</span><span class="sxs-lookup"><span data-stu-id="db794-126">-   ISOLATIONLEVEL_REPEATABLEREAD</span></span><br /><span data-ttu-id="db794-127">-ISOLATIONLEVEL_CURSORSTABILITY</span><span class="sxs-lookup"><span data-stu-id="db794-127">-   ISOLATIONLEVEL_CURSORSTABILITY</span></span><br /><span data-ttu-id="db794-128">-ISOLATIONLEVEL_REPEATABLEREAD</span><span class="sxs-lookup"><span data-stu-id="db794-128">-   ISOLATIONLEVEL_REPEATABLEREAD</span></span><br /><span data-ttu-id="db794-129">-ISOLATIONLEVEL_SERIALIZABLE</span><span class="sxs-lookup"><span data-stu-id="db794-129">-   ISOLATIONLEVEL_SERIALIZABLE</span></span><br /><span data-ttu-id="db794-130">-ISOLATIONLEVEL_ISOLATED</span><span class="sxs-lookup"><span data-stu-id="db794-130">-   ISOLATIONLEVEL_ISOLATED</span></span><br /><span data-ttu-id="db794-131">-ISOLATIONLEVEL_SNAPSHOT**注意:** 以降では [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 、データベースのバージョン管理が有効になっているかどうかにかかわらず、ISOLATIONLEVEL_SNAPSHOT は*isoLevel*引数に対して有効です。</span><span class="sxs-lookup"><span data-stu-id="db794-131">-   ISOLATIONLEVEL_SNAPSHOT **Note:**  Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], ISOLATIONLEVEL_SNAPSHOT is valid for the *isoLevel* argument whether or not versioning is enabled for the database.</span></span> <span data-ttu-id="db794-132">ただし、ユーザーがステートメントを実行する際に、バージョン管理が有効か、データベースが読み取り専用の場合は、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="db794-132">However, an error will occur if the user attempts to execute a statement and versioning is not enabled and/or the database is not read-only.</span></span> <span data-ttu-id="db794-133">また、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] より前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続している場合に、*isoLevel* に ISOLATIONLEVEL_SNAPSHOT を指定すると、XACT_E_ISOLATIONLEVEL エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="db794-133">In addition, the error XACT_E_ISOLATIONLEVEL will occur if ISOLATIONLEVEL_SNAPSHOT is specified as the *isoLevel* when connected to a version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] earlier than [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>|  
|<span data-ttu-id="db794-134">*isoFlags*[in]</span><span class="sxs-lookup"><span data-stu-id="db794-134">*isoFlags*[in]</span></span>|<span data-ttu-id="db794-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、0以外の値に対してエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="db794-135">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns an error for any value other than zero.</span></span>|  
|<span data-ttu-id="db794-136">*pOtherOptions*[in]</span><span class="sxs-lookup"><span data-stu-id="db794-136">*pOtherOptions*[in]</span></span>|<span data-ttu-id="db794-137">NULL 以外の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、インターフェイスから options オブジェクトを要求します。</span><span class="sxs-lookup"><span data-stu-id="db794-137">If not NULL, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider requests the options object from the interface.</span></span> <span data-ttu-id="db794-138">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、オプションオブジェクトの*ultimeout*メンバーが0でない場合に XACT_E_NOTIMEOUT を返します。</span><span class="sxs-lookup"><span data-stu-id="db794-138">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns XACT_E_NOTIMEOUT if the options object's *ulTimeout* member is not zero.</span></span> <span data-ttu-id="db794-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、 *szdescription*メンバーの値を無視します。</span><span class="sxs-lookup"><span data-stu-id="db794-139">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider ignores the value of the *szDescription* member.</span></span>|  
|<span data-ttu-id="db794-140">*pulTransactionLevel*[out]</span><span class="sxs-lookup"><span data-stu-id="db794-140">*pulTransactionLevel*[out]</span></span>|<span data-ttu-id="db794-141">NULL 以外の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、トランザクションの入れ子になったレベルを返します。</span><span class="sxs-lookup"><span data-stu-id="db794-141">If not NULL, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns the nested level of the transaction.</span></span>|  
  
 <span data-ttu-id="db794-142">ローカルトランザクションの場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、次のように**ITransaction:: Abort**パラメーターを実装します。</span><span class="sxs-lookup"><span data-stu-id="db794-142">For local transactions, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements **ITransaction::Abort** parameters as follows.</span></span>  
  
|<span data-ttu-id="db794-143">パラメーター</span><span class="sxs-lookup"><span data-stu-id="db794-143">Parameter</span></span>|<span data-ttu-id="db794-144">説明</span><span class="sxs-lookup"><span data-stu-id="db794-144">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="db794-145">*pboidReason*[in]</span><span class="sxs-lookup"><span data-stu-id="db794-145">*pboidReason*[in]</span></span>|<span data-ttu-id="db794-146">設定しても無視されます。</span><span class="sxs-lookup"><span data-stu-id="db794-146">Ignored if set.</span></span> <span data-ttu-id="db794-147">NULL を指定しても問題ありません。</span><span class="sxs-lookup"><span data-stu-id="db794-147">Can safely be NULL.</span></span>|  
|<span data-ttu-id="db794-148">*fRetaining*[in]</span><span class="sxs-lookup"><span data-stu-id="db794-148">*fRetaining*[in]</span></span>|<span data-ttu-id="db794-149">TRUE のときは、セッションの新しいトランザクションが暗黙的に開始されます。</span><span class="sxs-lookup"><span data-stu-id="db794-149">When TRUE, a new transaction is implicitly begun for the session.</span></span> <span data-ttu-id="db794-150">このトランザクションは、コンシューマーがコミットまたは終了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="db794-150">The transaction must be committed or terminated by the consumer.</span></span> <span data-ttu-id="db794-151">FALSE の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、セッションの自動コミットモードに戻ります。</span><span class="sxs-lookup"><span data-stu-id="db794-151">When FALSE, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider reverts to autocommit mode for the session.</span></span>|  
|<span data-ttu-id="db794-152">*fAsync*[in]</span><span class="sxs-lookup"><span data-stu-id="db794-152">*fAsync*[in]</span></span>|<span data-ttu-id="db794-153">非同期中止は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="db794-153">Asynchronous abort is not supported by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span> <span data-ttu-id="db794-154">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]値が FALSE でない場合、Native Client OLE DB プロバイダーは XACT_E_NOTSUPPORTED を返します。</span><span class="sxs-lookup"><span data-stu-id="db794-154">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns XACT_E_NOTSUPPORTED if the value is not FALSE.</span></span>|  
  
 <span data-ttu-id="db794-155">ローカルトランザクションの場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、次のように**ITransaction:: Commit**パラメーターを実装します。</span><span class="sxs-lookup"><span data-stu-id="db794-155">For local transactions, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements **ITransaction::Commit** parameters as follows.</span></span>  
  
|<span data-ttu-id="db794-156">パラメーター</span><span class="sxs-lookup"><span data-stu-id="db794-156">Parameter</span></span>|<span data-ttu-id="db794-157">説明</span><span class="sxs-lookup"><span data-stu-id="db794-157">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="db794-158">*fRetaining*[in]</span><span class="sxs-lookup"><span data-stu-id="db794-158">*fRetaining*[in]</span></span>|<span data-ttu-id="db794-159">TRUE のときは、セッションの新しいトランザクションが暗黙的に開始されます。</span><span class="sxs-lookup"><span data-stu-id="db794-159">When TRUE, a new transaction is implicitly begun for the session.</span></span> <span data-ttu-id="db794-160">このトランザクションは、コンシューマーがコミットまたは終了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="db794-160">The transaction must be committed or terminated by the consumer.</span></span> <span data-ttu-id="db794-161">FALSE の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、セッションの自動コミットモードに戻ります。</span><span class="sxs-lookup"><span data-stu-id="db794-161">When FALSE, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider reverts to autocommit mode for the session.</span></span>|  
|<span data-ttu-id="db794-162">*grfTC*[in]</span><span class="sxs-lookup"><span data-stu-id="db794-162">*grfTC*[in]</span></span>|<span data-ttu-id="db794-163">非同期およびフェーズ1の戻り値は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="db794-163">Asynchronous and phase one returns are not supported by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span> <span data-ttu-id="db794-164">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、XACTTC_SYNC 以外の値に対して XACT_E_NOTSUPPORTED を返します。</span><span class="sxs-lookup"><span data-stu-id="db794-164">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns XACT_E_NOTSUPPORTED for any value other than XACTTC_SYNC.</span></span>|  
|<span data-ttu-id="db794-165">*grfRM*[in]</span><span class="sxs-lookup"><span data-stu-id="db794-165">*grfRM*[in]</span></span>|<span data-ttu-id="db794-166">0 を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="db794-166">Must be 0.</span></span>|  
  
 <span data-ttu-id="db794-167">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セッションの Native Client OLE DB プロバイダーの行セットは、行セットのプロパティ DBPROP_ABORTPRESERVE および DBPROP_COMMITPRESERVE の値に基づいて、ローカルのコミットまたは中止操作で保持されます。</span><span class="sxs-lookup"><span data-stu-id="db794-167">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider rowsets on the session are preserved on a local commit or abort operation based on the values of the rowset properties DBPROP_ABORTPRESERVE and DBPROP_COMMITPRESERVE.</span></span> <span data-ttu-id="db794-168">既定では、これらのプロパティは両方とも VARIANT_FALSE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。また、セッションのすべての Native Client OLE DB プロバイダー行セットは、abort または commit 操作後に失われます。</span><span class="sxs-lookup"><span data-stu-id="db794-168">By default, these properties are both VARIANT_FALSE and all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider rowsets on the session are lost following an abort or commit operation.</span></span>  
  
 <span data-ttu-id="db794-169">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーには、 **ITransactionObject**インターフェイスが実装されていません。</span><span class="sxs-lookup"><span data-stu-id="db794-169">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not implement the **ITransactionObject** interface.</span></span> <span data-ttu-id="db794-170">このインターフェイスへの参照を取得しようとすると、コンシューマーは E_NOINTERFACE を返します。</span><span class="sxs-lookup"><span data-stu-id="db794-170">A consumer attempt to retrieve a reference on the interface returns E_NOINTERFACE.</span></span>  
  
 <span data-ttu-id="db794-171">次の例では、**ITransactionLocal** を使用します。</span><span class="sxs-lookup"><span data-stu-id="db794-171">This example uses **ITransactionLocal**.</span></span>  
  
```  
// Interfaces used in the example.  
IDBCreateSession*   pIDBCreateSession   = NULL;  
ITransaction*       pITransaction       = NULL;  
IDBCreateCommand*   pIDBCreateCommand   = NULL;  
IRowset*            pIRowset            = NULL;  
  
HRESULT             hr;  
  
// Get the command creation and local transaction interfaces for the  
// session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
if (FAILED(hr = pIDBCreateCommand->QueryInterface(IID_ITransactionLocal,  
    (void**) &pITransaction)))  
    {  
    // Process error. Release any references and return.  
    }  
  
// Start the local transaction.  
if (FAILED(hr = ((ITransactionLocal*) pITransaction)->StartTransaction(  
    ISOLATIONLEVEL_REPEATABLEREAD, 0, NULL, NULL)))  
    {  
    // Process error from StartTransaction. Release any references and  
    // return.  
    }  
  
// Get data into a rowset, then update the data. Functions are not  
// illustrated in this example.  
if (FAILED(hr = ExecuteCommand(pIDBCreateCommand, &pIRowset)))  
    {  
    // Release any references and return.  
    }  
  
// If rowset data update fails, then terminate the transaction, else  
// commit. The example doesn't retain the rowset.  
if (FAILED(hr = UpdateDataInRowset(pIRowset, bDelayedUpdate)))  
    {  
    // Get error from update, then terminate.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, XACTTC_SYNC, 0)))  
        {  
        // Get error from failed commit.  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a><span data-ttu-id="db794-172">参照</span><span class="sxs-lookup"><span data-stu-id="db794-172">See Also</span></span>  
 <span data-ttu-id="db794-173">[トランザクション](transactions.md) </span><span class="sxs-lookup"><span data-stu-id="db794-173">[Transactions](transactions.md) </span></span>  
 [<span data-ttu-id="db794-174">スナップショット分離の使用</span><span class="sxs-lookup"><span data-stu-id="db794-174">Working with Snapshot Isolation</span></span>](../native-client/features/working-with-snapshot-isolation.md)  
  
  
