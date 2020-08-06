---
title: 非同期操作の実行 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- initialization [SQL Server Native Client]
- database connections [SQL Server Native Client]
- data access [SQL Server Native Client], asynchronous operations
- connections [SQL Server Native Client]
- asynchronous operations [SQL Server Native Client]
- rowsets [SQL Server], initializing
- SQLNCLI, asynchronous operations
- SQL Server Native Client, asynchronous operations
ms.assetid: 8fbd84b4-69cb-4708-9f0f-bbdf69029bcc
author: rothja
ms.author: jroth
ms.openlocfilehash: 4f7e8f4481923cd7da537f921248865d4fff7280
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714262"
---
# <a name="performing-asynchronous-operations"></a><span data-ttu-id="71776-102">非同期操作の実行</span><span class="sxs-lookup"><span data-stu-id="71776-102">Performing Asynchronous Operations</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="71776-103">では、アプリケーションは非同期のデータベース操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="71776-103">allows applications to perform asynchronous database operations.</span></span> <span data-ttu-id="71776-104">非同期処理により、呼び出し側のスレッドをブロックしないで直ちに制御を返すことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="71776-104">Asynchronous processing enables methods to return immediately without blocking on the calling thread.</span></span> <span data-ttu-id="71776-105">これは、マルチスレッドの持つ能力と柔軟性を大きく引き出し、開発者が明示的にスレッドを作成したり、同期を処理する手間を省くことができる機能です。</span><span class="sxs-lookup"><span data-stu-id="71776-105">This allows much of the power and flexibility of multithreading, without requiring the developer to explicitly create threads or handle synchronization.</span></span> <span data-ttu-id="71776-106">アプリケーションは、データベース接続を初期化するときや、コマンドの実行結果を初期化するときに、非同期処理を要求します。</span><span class="sxs-lookup"><span data-stu-id="71776-106">Applications request asynchronous processing when initializing a database connection, or when initializing the result from the execution of a command.</span></span>  
  
## <a name="opening-and-closing-a-database-connection"></a><span data-ttu-id="71776-107">データベース接続の開閉</span><span class="sxs-lookup"><span data-stu-id="71776-107">Opening and Closing a Database Connection</span></span>  
 <span data-ttu-id="71776-108">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーを使用する場合、データソースオブジェクトを非同期に初期化するように設計されたアプリケーションでは、 **IDBInitialize:: initialize**を呼び出す前に DBPROP_INIT_ASYNCH プロパティで DBPROPVAL_ASYNCH_INITIALIZE ビットを設定できます。</span><span class="sxs-lookup"><span data-stu-id="71776-108">When using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider, applications designed to initialize a data source object asynchronously can set the DBPROPVAL_ASYNCH_INITIALIZE bit in the DBPROP_INIT_ASYNCH property prior to calling **IDBInitialize::Initialize**.</span></span> <span data-ttu-id="71776-109">このプロパティが設定されると、プロバイダーは **Initialize** の呼び出しからすぐに制御を戻し、操作が直ちに完了した場合は S_OK、初期化が非同期に続行される場合は DB_S_ASYNCHRONOUS を返します。</span><span class="sxs-lookup"><span data-stu-id="71776-109">When this property is set, the provider returns immediately from the call to **Initialize** with either S_OK, if the operation has completed immediately, or DB_S_ASYNCHRONOUS, if the initialization is continuing asynchronously.</span></span> <span data-ttu-id="71776-110">アプリケーションでは、データソースオブジェクトの**IdbasISSAsynchStatus chstatus**インターフェイスまたは[ISSAsynchStatus](../../native-client-ole-db-interfaces/issasynchstatus-ole-db.md)インターフェイスを照会してから、 **Idbas/chstatus:: GetStatus**または[ISSAsynchStatus:: WaitForAsynchCompletion](../../native-client-ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md)を呼び出して初期化の状態を取得できます。</span><span class="sxs-lookup"><span data-stu-id="71776-110">Applications can query for the **IDBAsynchStatus** or [ISSAsynchStatus](../../native-client-ole-db-interfaces/issasynchstatus-ole-db.md)interface on the data source object, and then call **IDBAsynchStatus::GetStatus** or[ISSAsynchStatus::WaitForAsynchCompletion](../../native-client-ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md) to get the status of the initialization.</span></span>  
  
 <span data-ttu-id="71776-111">また、DBPROPSET_SQLSERVERROWSET プロパティ セットに SSPROP_ISSAsynchStatus プロパティが追加されています。</span><span class="sxs-lookup"><span data-stu-id="71776-111">In addition, the SSPROP_ISSAsynchStatus property has been added to the DBPROPSET_SQLSERVERROWSET property set.</span></span> <span data-ttu-id="71776-112">**ISSAsynchStatus** インターフェイスをサポートするプロバイダーは、値 VARIANT_TRUE を指定してこのプロパティを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="71776-112">Providers that support the **ISSAsynchStatus** interface must implement this property with a value of VARIANT_TRUE.</span></span>  
  
 <span data-ttu-id="71776-113">**IDBAsynchStatus::Abort** または [ISSAsynchStatus::Abort](../../native-client-ole-db-interfaces/issasynchstatus-abort-ole-db.md) を呼び出すと、非同期 **Initialize** 呼び出しを中止できます。</span><span class="sxs-lookup"><span data-stu-id="71776-113">**IDBAsynchStatus::Abort** or [ISSAsynchStatus::Abort](../../native-client-ole-db-interfaces/issasynchstatus-abort-ole-db.md) can be called to cancel the asynchronous **Initialize** call.</span></span> <span data-ttu-id="71776-114">コンシューマーは、明示的にデータ ソースの非同期の初期化を要求できます。</span><span class="sxs-lookup"><span data-stu-id="71776-114">The consumer must explicitly request Asynchronous Data Source Initialization.</span></span> <span data-ttu-id="71776-115">この要求を行わない場合、**IDBInitialize::Initialize** はデータ ソース オブジェクトが完全に初期化されるまで、制御を戻しません。</span><span class="sxs-lookup"><span data-stu-id="71776-115">Otherwise, **IDBInitialize::Initialize** does not return until the data source object is completely initialized.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="71776-116">接続プールに使用されるデータソースオブジェクトは**ISSAsynchStatus** 、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの ISSAsynchStatus インターフェイスを呼び出すことができません。</span><span class="sxs-lookup"><span data-stu-id="71776-116">Data source objects used for connection pooling cannot call the **ISSAsynchStatus** interface in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span> <span data-ttu-id="71776-117">**ISSAsynchStatus** インターフェイスは、プールされたデータ ソース オブジェクトには公開されません。</span><span class="sxs-lookup"><span data-stu-id="71776-117">The **ISSAsynchStatus** interface is not exposed for pooled data source objects.</span></span>  
>   
>  <span data-ttu-id="71776-118">アプリケーションが明示的にカーソル エンジンの使用を設定している場合、**IOpenRowset::OpenRowset** と **IMultipleResults::GetResult** は非同期処理をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="71776-118">If an application explicitly forces use of the cursor engine, **IOpenRowset::OpenRowset** and **IMultipleResults::GetResult** will not support asynchronous processing.</span></span>  
>   
>  <span data-ttu-id="71776-119">また、リモート処理プロキシ/スタブ dll (MDAC 2.8) は、Native Client の**ISSAsynchStatus**インターフェイスを呼び出すことができません [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="71776-119">In addition, the remoting proxy/stub dll (in MDAC 2.8) cannot call the **ISSAsynchStatus** interface in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="71776-120">**ISSAsynchStatus** インターフェイスは、リモート処理経由では公開されません。</span><span class="sxs-lookup"><span data-stu-id="71776-120">The **ISSAsynchStatus** interface is not exposed through remoting.</span></span>  
>   
>  <span data-ttu-id="71776-121">サービス コンポーネントは、**ISSAsynchStatus** をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="71776-121">Service Components do not support **ISSAsynchStatus**.</span></span>  
  
## <a name="execution-and-rowset-initialization"></a><span data-ttu-id="71776-122">実行と行セットの初期化</span><span class="sxs-lookup"><span data-stu-id="71776-122">Execution and Rowset Initialization</span></span>  
 <span data-ttu-id="71776-123">コマンドの実行結果を非同期に開くようデザインされているアプリケーションは、DBPROP_ROWSET_ASYNCH プロパティに DBPROPVAL_ASYNCH_INITIALIZE ビットを設定できます。</span><span class="sxs-lookup"><span data-stu-id="71776-123">Applications designed to asynchronously open the result from the execution of a command can set the DBPROPVAL_ASYNCH_INITIALIZE bit in the DBPROP_ROWSET_ASYNCH property.</span></span> <span data-ttu-id="71776-124">**IDBInitialize::Initialize**、**ICommand::Execute**、**IOpenRowset::OpenRowset** または **IMultipleResults::GetResult** を呼び出す前にこのビットを設定するときは、*riid* 引数を IID_IDBAsynchStatus、IID_ISSAsynchStatus、または IID_IUnknown に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="71776-124">When setting this bit prior to calling **IDBInitialize::Initialize**, **ICommand::Execute**, **IOpenRowset::OpenRowset** or **IMultipleResults::GetResult**, the *riid* argument must be set to IID_IDBAsynchStatus, IID_ISSAsynchStatus, or IID_IUnknown.</span></span>  
  
 <span data-ttu-id="71776-125">メソッドはすぐに制御を戻し、行セットの初期化が直ちに完了した場合は S_OK、行セットの初期化が非同期に続行される場合は DB_S_ASYNCHRONOUS を返して、*ppRowset* を行セット上の要求されたインターフェイスに設定します。</span><span class="sxs-lookup"><span data-stu-id="71776-125">The method returns immediately with S_OK if the rowset initialization completes immediately, or with DB_S_ASYNCHRONOUS if the rowset continues initializing asynchronously, with *ppRowset* set to the requested interface on the rowset.</span></span> <span data-ttu-id="71776-126">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーの場合、このインターフェイスには**IdbasISSAsynchStatus chstatus**または**ISSAsynchStatus**のみを指定できます。</span><span class="sxs-lookup"><span data-stu-id="71776-126">For the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider, this interface can only be **IDBAsynchStatus** or **ISSAsynchStatus**.</span></span> <span data-ttu-id="71776-127">このインターフェイスは、行セットが完全に初期化されるまでは中断状態にあるかのように動作し、**IID_IDBAsynchStatus** または **IID_ISSAsynchStatus** 以外のインターフェイスに対して **QueryInterface** が呼び出された場合、E_NOINTERFACE を返すことがあります。</span><span class="sxs-lookup"><span data-stu-id="71776-127">Until the rowset is fully initialized, this interface behaves as if it were in a suspended state, and calling **QueryInterface** for interfaces other than **IID_IDBAsynchStatus** or **IID_ISSAsynchStatus** may return E_NOINTERFACE.</span></span> <span data-ttu-id="71776-128">コンシューマーが明示的に非同期処理を要求しない限り、行セットは同期的に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="71776-128">Unless the consumer explicitly requests asynchronous processing, the rowset is initialized synchronously.</span></span> <span data-ttu-id="71776-129">**IDBAsynchStaus::GetStatus** または **ISSAsynchStatus::WaitForAsynchCompletion** が非同期操作が完了したことを示す値を返した場合、要求したすべてのインターフェイスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="71776-129">All requested interfaces are available when **IDBAsynchStaus::GetStatus** or **ISSAsynchStatus::WaitForAsynchCompletion** returns with the indication that asynchronous operation is complete.</span></span> <span data-ttu-id="71776-130">これは、必ずしも行セットに完全にデータが格納されたことを意味するものではありませんが、行セットは完成し、完全に機能します。</span><span class="sxs-lookup"><span data-stu-id="71776-130">This does not necessarily mean that the rowset is fully populated, but it is complete and fully functional.</span></span>  
  
 <span data-ttu-id="71776-131">実行されたコマンドが行セットを返さない場合でも、このコマンドは、**IDBAsynchStatus** をサポートするオブジェクトを直ちに返します。</span><span class="sxs-lookup"><span data-stu-id="71776-131">If the executed command does not return a rowset, it still returns immediately with an object that supports **IDBAsynchStatus**.</span></span>  
  
 <span data-ttu-id="71776-132">非同期コマンドの実行により複数の結果を取得する必要がある場合は、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="71776-132">If you need to get multiple results from asynchronous command execution, you should:</span></span>  
  
-   <span data-ttu-id="71776-133">コマンドを実行する前に、DBPROP_ROWSET_ASYNCH プロパティに DBPROPVAL_ASYNCH_INITIALIZE ビットを設定します。</span><span class="sxs-lookup"><span data-stu-id="71776-133">Set the DBPROPVAL_ASYNCH_INITIALIZE bit of the DBPROP_ROWSET_ASYNCH property, before executing the command.</span></span>  
  
-   <span data-ttu-id="71776-134">**ICommand::Execute** を呼び出し、**IMultipleResults** を要求します。</span><span class="sxs-lookup"><span data-stu-id="71776-134">Call **ICommand::Execute**, and request **IMultipleResults**.</span></span>  
  
 <span data-ttu-id="71776-135">その結果、**QueryInterface** を使用して複数の結果のインターフェイスをクエリすることで、**IDBAsynchStatus** および **ISSAsynchStatus** インターフェイスを取得できるようになります。</span><span class="sxs-lookup"><span data-stu-id="71776-135">The **IDBAsynchStatus** and **ISSAsynchStatus** interfaces can then be obtained by querying the multiple results interface using **QueryInterface**.</span></span>  
  
 <span data-ttu-id="71776-136">コマンドの実行が完了すると、**IMultipleResults** を通常どおり使用できます。ただし、非同期処理の場合は 1 つだけ例外があり、DB_S_ASYNCHRONOUS が返される可能性があります。この場合、**IDBAsynchStatus** または **ISSAsynchStatus** を使用して、操作が完了しているかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="71776-136">When the command has finished executing, **IMultipleResults** can be used as normal, with one exception from the synchronous case: DB_S_ASYNCHRONOUS may be returned, in which case **IDBAsynchStatus** or **ISSAsynchStatus** can be used to determine when the operation is complete.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="71776-137">例</span><span class="sxs-lookup"><span data-stu-id="71776-137">Examples</span></span>  
 <span data-ttu-id="71776-138">次の例では、アプリケーションが非ブロッキング メソッドを呼び出し、いくつか他の処理を実行し、制御を戻して結果を処理します。</span><span class="sxs-lookup"><span data-stu-id="71776-138">In the following example, the application calls a non-blocking method, does some other processing, and then returns to process the results.</span></span> <span data-ttu-id="71776-139">**ISSAsynchStatus::WaitForAsynchCompletion** は、非同期実行操作が完了するか、*dwMilisecTimeOut* により指定された時間が経過するまで、内部イベント オブジェクト上で待機します。</span><span class="sxs-lookup"><span data-stu-id="71776-139">**ISSAsynchStatus::WaitForAsynchCompletion** waits on the internal event object until the asynchronously executing operation is done or the amount of time specified by *dwMilisecTimeOut* is passed.</span></span>  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
  
DBPROPSET CmdPropset[1];  
DBPROP CmdProperties[1];  
  
CmdPropset[0].rgProperties = CmdProperties;  
CmdPropset[0].cProperties = 1;  
CmdPropset[0].guidPropertySet = DBPROPSET_ROWSET;  
  
// Set asynch mode for command.  
CmdProperties[0].dwPropertyID = DBPROP_ROWSET_ASYNCH;  
CmdProperties[0].vValue.vt = VT_I4;  
CmdProperties[0].vValue.lVal = DBPROPVAL_ASYNCH_INITIALIZE;  
CmdProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
  
hr = pICommandProps->SetProperties(1, CmdPropset);  
  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work here...  
  
   hr = pISSAsynchStatus->WaitForAsynchCompletion(dwMilisecTimeOut);  
   if ( hr == S_OK)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
      pISSAsynchStatus->Release();  
   }  
}  
```  
  
 <span data-ttu-id="71776-140">**ISSAsynchStatus::WaitForAsynchCompletion** は、非同期実行操作が完了するか、*dwMilisecTimeOut* の値が示す時間が経過するまで、内部イベント オブジェクト上で待機します。</span><span class="sxs-lookup"><span data-stu-id="71776-140">**ISSAsynchStatus::WaitForAsynchCompletion** waits on the internal event object until the asynchronously executing operation is done or the *dwMilisecTimeOut* value is passed.</span></span>  
  
 <span data-ttu-id="71776-141">次の例は、複数の結果セットを返す非同期処理のコードです。</span><span class="sxs-lookup"><span data-stu-id="71776-141">The following example shows asynchronous processing with multiple result sets:</span></span>  
  
```  
DBPROP CmdProperties[1];  
  
// Set asynch mode for command.  
CmdProperties[0].dwPropertyID = DBPROP_ROWSET_ASYNCH;  
CmdProperties[0].vValue.vt = VT_I4;  
CmdProperties[0].vValue.lVal = DBPROPVAL_ASYNCH_INITIALIZE;  
  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_IMultipleResults,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pIMultipleResults);  
  
// Use GetResults for ISSAsynchStatus.  
hr = pIMultipleResults->GetResult(IID_ISSAsynchStatus, (void **) &pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work here...  
  
   hr = pISSAsynchStatus->WaitForAsynchCompletion(dwMilisecTimeOut);  
   if (hr == S_OK)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
      pISSAsynchStatus->Release();  
   }  
}  
```  
  
 <span data-ttu-id="71776-142">ブロックを防ぐため、次の例のように、クライアントでは実行中の非同期操作の状態を確認できます。</span><span class="sxs-lookup"><span data-stu-id="71776-142">To prevent blocking, the client can check the status of a running asynchronous operation, as in the following example:</span></span>  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);   
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   do{  
      // Do some work...  
      hr = pISSAsynchStatus->GetStatus(DB_NULL_HCHAPTER, DBASYNCHOP_OPEN, NULL, NULL, &ulAsynchPhase, NULL);  
   }while (DBASYNCHPHASE_COMPLETE != ulAsynchPhase)  
   if SUCCEEDED(hr)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
   }  
   pIDBAsynchStatus->Release();  
}  
```  
  
 <span data-ttu-id="71776-143">次の例は、現在実行中の非同期操作を中止する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="71776-143">The following example demonstrates how you can cancel the currently running asynchronous operation:</span></span>  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work...  
   hr = pISSAsynchStatus->Abort(DB_NULL_HCHAPTER, DBASYNCHOP_OPEN);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="71776-144">参照</span><span class="sxs-lookup"><span data-stu-id="71776-144">See Also</span></span>  
 <span data-ttu-id="71776-145">[SQL Server Native Client の機能](sql-server-native-client-features.md) </span><span class="sxs-lookup"><span data-stu-id="71776-145">[SQL Server Native Client Features](sql-server-native-client-features.md) </span></span>  
 <span data-ttu-id="71776-146">[行セットのプロパティと動作](../../native-client-ole-db-rowsets/rowset-properties-and-behaviors.md) </span><span class="sxs-lookup"><span data-stu-id="71776-146">[Rowset Properties and Behaviors](../../native-client-ole-db-rowsets/rowset-properties-and-behaviors.md) </span></span>  
 [<span data-ttu-id="71776-147">ISSAsynchStatus &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="71776-147">ISSAsynchStatus &#40;OLE DB&#41;</span></span>](../../native-client-ole-db-interfaces/issasynchstatus-ole-db.md)  
  
  
