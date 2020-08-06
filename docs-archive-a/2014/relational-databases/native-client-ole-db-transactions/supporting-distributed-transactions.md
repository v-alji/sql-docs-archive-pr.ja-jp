---
title: 分散トランザクションのサポート | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- distributed transactions [OLE DB]
- MS DTC
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
- ITransactionJoin interface
- MS DTC, about distributed transaction support
ms.assetid: d250b43b-9260-4ea4-90cc-57d9a2f67ea7
author: rothja
ms.author: jroth
ms.openlocfilehash: 5a30a44dc007852922aa71685728b26e5bb872c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738245"
---
# <a name="supporting-distributed-transactions"></a><span data-ttu-id="e837a-102">分散トランザクションのサポート</span><span class="sxs-lookup"><span data-stu-id="e837a-102">Supporting Distributed Transactions</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="e837a-103">Native Client OLE DB プロバイダーのコンシューマーは、 **ITransactionJoin:: jointransaction**メソッドを使用して、Microsoft 分散トランザクションコーディネーター (MS DTC) によって調整された分散トランザクションに参加できます。</span><span class="sxs-lookup"><span data-stu-id="e837a-103">Native Client OLE DB provider consumers can use the **ITransactionJoin::JoinTransaction** method to participate in a distributed transaction coordinated by Microsoft Distributed Transaction Coordinator (MS DTC).</span></span>  
  
 <span data-ttu-id="e837a-104">MS DTC が公開する COM オブジェクトを使用すると、クライアントは、さまざまなデータ ストアに対する複数の接続にまたがってコーディネートされるトランザクションを起動したり、このトランザクションに参加することができます。</span><span class="sxs-lookup"><span data-stu-id="e837a-104">MS DTC exposes COM objects that allow clients to initiate and participate in coordinated transactions across multiple connections to a variety of data stores.</span></span> <span data-ttu-id="e837a-105">トランザクションを開始するために、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーコンシューマーは MS DTC **ITransactionDispenser**インターフェイスを使用します。</span><span class="sxs-lookup"><span data-stu-id="e837a-105">To initiate a transaction, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer uses the MS DTC **ITransactionDispenser** interface.</span></span> <span data-ttu-id="e837a-106">**ITransactionDispenser** の **BeginTransaction** メンバーは、分散トランザクション オブジェクト上の参照を返します。</span><span class="sxs-lookup"><span data-stu-id="e837a-106">The **BeginTransaction** member of **ITransactionDispenser** returns a reference on a distributed transaction object.</span></span> <span data-ttu-id="e837a-107">この参照は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **jointransaction**を使用して Native Client OLE DB プロバイダーに渡されます。</span><span class="sxs-lookup"><span data-stu-id="e837a-107">This reference is passed to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider using **JoinTransaction**.</span></span>  
  
 <span data-ttu-id="e837a-108">MS DTC は、分散トランザクションでの非同期のコミットとアボートをサポートします。</span><span class="sxs-lookup"><span data-stu-id="e837a-108">MS DTC supports asynchronous commit and abort on distributed transactions.</span></span> <span data-ttu-id="e837a-109">非同期トランザクションの状態を通知する場合、コンシューマーは、**ITransactionOutcomeEvents** インターフェイスを実装し、そのインターフェイスを MS DTC トランザクション オブジェクトに接続します。</span><span class="sxs-lookup"><span data-stu-id="e837a-109">For notification on asynchronous transaction status, the consumer implements the **ITransactionOutcomeEvents** interface and connects the interface to an MS DTC transaction object.</span></span>  
  
 <span data-ttu-id="e837a-110">分散トランザクションの場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、次のように**ITransactionJoin:: jointransaction**パラメーターを実装します。</span><span class="sxs-lookup"><span data-stu-id="e837a-110">For distributed transactions, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements **ITransactionJoin::JoinTransaction** parameters as follows.</span></span>  
  
|<span data-ttu-id="e837a-111">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e837a-111">Parameter</span></span>|<span data-ttu-id="e837a-112">説明</span><span class="sxs-lookup"><span data-stu-id="e837a-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e837a-113">*punkTransactionCoord*</span><span class="sxs-lookup"><span data-stu-id="e837a-113">*punkTransactionCoord*</span></span>|<span data-ttu-id="e837a-114">MS DTC トランザクション オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e837a-114">A pointer to an MS DTC transaction object.</span></span>|  
|<span data-ttu-id="e837a-115">*IsoLevel*</span><span class="sxs-lookup"><span data-stu-id="e837a-115">*IsoLevel*</span></span>|<span data-ttu-id="e837a-116">Native Client OLE DB プロバイダーによって無視さ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] れます。</span><span class="sxs-lookup"><span data-stu-id="e837a-116">Ignored by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span> <span data-ttu-id="e837a-117">MS DTC によりコーディネートされるトランザクションの分離レベルは、コンシューマーが MS DTC からトランザクション オブジェクトを取得するときに決まります。</span><span class="sxs-lookup"><span data-stu-id="e837a-117">The isolation level for MS DTC-coordinated transactions is determined when the consumer acquires a transaction object from MS DTC.</span></span>|  
|<span data-ttu-id="e837a-118">*IsoFlags*</span><span class="sxs-lookup"><span data-stu-id="e837a-118">*IsoFlags*</span></span>|<span data-ttu-id="e837a-119">0 を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e837a-119">Must be 0.</span></span> <span data-ttu-id="e837a-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]他の値がコンシューマーによって指定されている場合、Native Client OLE DB プロバイダーは XACT_E_NOISORETAIN を返します。</span><span class="sxs-lookup"><span data-stu-id="e837a-120">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns XACT_E_NOISORETAIN if any other value is specified by the consumer.</span></span>|  
|<span data-ttu-id="e837a-121">*POtherOptions*</span><span class="sxs-lookup"><span data-stu-id="e837a-121">*POtherOptions*</span></span>|<span data-ttu-id="e837a-122">NULL 以外の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、インターフェイスから options オブジェクトを要求します。</span><span class="sxs-lookup"><span data-stu-id="e837a-122">If not NULL, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider requests the options object from the interface.</span></span> <span data-ttu-id="e837a-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、オプションオブジェクトの*ultimeout*メンバーが0でない場合に XACT_E_NOTIMEOUT を返します。</span><span class="sxs-lookup"><span data-stu-id="e837a-123">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns XACT_E_NOTIMEOUT if the options object's *ulTimeout* member is not zero.</span></span> <span data-ttu-id="e837a-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、 *szdescription*メンバーの値を無視します。</span><span class="sxs-lookup"><span data-stu-id="e837a-124">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider ignores the value of the *szDescription* member.</span></span>|  
  
 <span data-ttu-id="e837a-125">次の例では、MS DTC を使用してトランザクションをコーディネートします。</span><span class="sxs-lookup"><span data-stu-id="e837a-125">This example coordinates transaction by using MS DTC.</span></span>  
  
```  
// Interfaces used in the example.  
IDBCreateSession*       pIDBCreateSession   = NULL;  
ITransactionJoin*       pITransactionJoin   = NULL;  
IDBCreateCommand*       pIDBCreateCommand   = NULL;  
IRowset*                pIRowset            = NULL;  
  
// Transaction dispenser and transaction from MS DTC.  
ITransactionDispenser*  pITransactionDispenser = NULL;  
ITransaction*           pITransaction       = NULL;  
  
    HRESULT             hr;  
  
// Get the command creation interface for the session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
// Get a transaction dispenser object from MS DTC and  
// start a transaction.  
if (FAILED(hr = DtcGetTransactionManager(NULL, NULL,  
    IID_ITransactionDispenser, 0, 0, NULL,  
    (void**) &pITransactionDispenser)))  
    {  
    // Process error message from MS DTC, release any references,  
    // and then return.  
    }  
if (FAILED(hr = pITransactionDispenser->BeginTransaction(  
    NULL, ISOLATIONLEVEL_READCOMMITTED, ISOFLAG_RETAIN_DONTCARE,  
    NULL, &pITransaction)))  
    {  
    // Process error message from MS DTC, release any references,  
    // and then return.  
    }  
  
// Join the transaction.  
if (FAILED(pIDBCreateCommand->QueryInterface(IID_ITransactionJoin,  
    (void**) &pITransactionJoin)))  
    {  
    // Process failure to get an interface, release any references, and  
    // then return.  
    }  
if (FAILED(pITransactionJoin->JoinTransaction(  
    (IUnknown*) pITransaction, 0, 0, NULL)))  
    {  
    // Process join failure, release any references, and then return.  
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
    // Get error from update, then abort.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, 0, 0)))  
        {  
        // Get error from failed commit.  
        //  
        // If a distributed commit fails, application logic could  
        // analyze failure and retry. In this example, terminate. The   
        // consumer must resolve this somehow.  
        pITransaction->Abort(NULL, FALSE, FALSE);  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Un-enlist from the distributed transaction by setting   
// the transaction object pointer to NULL.  
if (FAILED(pITransactionJoin->JoinTransaction(  
    (IUnknown*) NULL, 0, 0, NULL)))  
    {  
    // Process failure, and then return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a><span data-ttu-id="e837a-126">参照</span><span class="sxs-lookup"><span data-stu-id="e837a-126">See Also</span></span>  
 [<span data-ttu-id="e837a-127">トランザクション</span><span class="sxs-lookup"><span data-stu-id="e837a-127">Transactions</span></span>](transactions.md)  
  
  
