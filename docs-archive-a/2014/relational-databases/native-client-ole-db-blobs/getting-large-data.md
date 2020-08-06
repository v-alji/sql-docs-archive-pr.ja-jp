---
title: 大きなデータの取得 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- DBPROP_ACCESSORDER property
- SQL Server Native Client OLE DB provider, BLOBs
- large data, OLE objects
ms.assetid: a31c5632-96aa-483f-a307-004c5149fbc0
author: rothja
ms.author: jroth
ms.openlocfilehash: 38602df026d2e752a758672dde23a59a26ad4917
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741926"
---
# <a name="getting-large-data"></a><span data-ttu-id="e4d4f-102">大きなデータの取得</span><span class="sxs-lookup"><span data-stu-id="e4d4f-102">Getting Large Data</span></span>
  <span data-ttu-id="e4d4f-103">一般に、コンシューマーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ISequentialStream**インターフェイスポインターによって参照されていないデータを処理する他のコードから、Native Client OLE DB プロバイダーストレージオブジェクトを作成するコードを分離する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4d4f-103">In general, consumers should isolate code that creates a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider storage object from other code that handles data not referenced through an **ISequentialStream** interface pointer.</span></span>  
  
 <span data-ttu-id="e4d4f-104">このトピックでは、次の関数で使用可能な機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="e4d4f-104">This topic refers to functionality available with the following functions:</span></span>  
  
-   <span data-ttu-id="e4d4f-105">IRowset:GetData</span><span class="sxs-lookup"><span data-stu-id="e4d4f-105">IRowset:GetData</span></span>  
  
-   <span data-ttu-id="e4d4f-106">IRow::GetColumns</span><span class="sxs-lookup"><span data-stu-id="e4d4f-106">IRow::GetColumns</span></span>  
  
-   <span data-ttu-id="e4d4f-107">ICommand::Execute</span><span class="sxs-lookup"><span data-stu-id="e4d4f-107">ICommand::Execute</span></span>  
  
 <span data-ttu-id="e4d4f-108">DBPROP_ACCESSORDER プロパティ (行セットプロパティグループ) が DBPROPVAL_AO_SEQUENTIAL または DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS のいずれかの値に設定されている場合、コンシューマーは**GetNextRows**メソッドの呼び出しで1行のデータのみをフェッチする必要があります。これは、BLOB データがバッファリングされていないためです。</span><span class="sxs-lookup"><span data-stu-id="e4d4f-108">If the DBPROP_ACCESSORDER property (in the rowset property group) is set to either of the values DBPROPVAL_AO_SEQUENTIAL or DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS, the consumer should fetch only a single row of data in a call to the **GetNextRows** method because BLOB data is not buffered.</span></span> <span data-ttu-id="e4d4f-109">DBPROP_ACCESSORDER の値を DBPROPVAL_AO_RANDOM に設定した場合は、**GetNextRows** で複数行のデータをフェッチできます。</span><span class="sxs-lookup"><span data-stu-id="e4d4f-109">If the value of DBPROP_ACCESSORDER is set to DBPROPVAL_AO_RANDOM, the consumer can fetch multiple rows of data in **GetNextRows**.</span></span>  
  
 <span data-ttu-id="e4d4f-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンシューマーによって要求されるまで、から大きなデータを取得しません。</span><span class="sxs-lookup"><span data-stu-id="e4d4f-110">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not retrieve large data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] until requested to do so by the consumer.</span></span> <span data-ttu-id="e4d4f-111">コンシューマーは、すべての短いデータを 1 つのアクセサーにバインドし、次に 1 つ以上の一時アクセサーを使用して、必要に応じて大きなデータ値を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4d4f-111">The consumer should bind all short data in one accessor, and then use one or more temporary accessors to retrieve large data values as required.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4d4f-112">例</span><span class="sxs-lookup"><span data-stu-id="e4d4f-112">Example</span></span>  
 <span data-ttu-id="e4d4f-113">次の例では、大きなデータ値を 1 つの列から取得します。</span><span class="sxs-lookup"><span data-stu-id="e4d4f-113">This example retrieves a large data value from a single column:</span></span>  
  
```  
HRESULT GetUnboundData  
    (  
    IRowset* pIRowset,  
    HROW hRow,  
    ULONG nCol,   
    BYTE* pUnboundData  
    )  
    {  
    UINT                cbRow = sizeof(IUnknown*) + sizeof(ULONG);  
    BYTE*               pRow = new BYTE[cbRow];  
  
    DBOBJECT            dbobject;  
  
    IAccessor*          pIAccessor = NULL;  
    HACCESSOR           haccessor;  
  
    DBBINDING           dbbinding;  
    ULONG               ulbindstatus;  
  
    ULONG               dwStatus;  
    ISequentialStream*  pISequentialStream;  
    ULONG               cbRead;  
  
    HRESULT             hr;  
  
    // Set up the DBOBJECT structure.  
    dbobject.dwFlags = STGM_READ;  
    dbobject.iid = IID_ISequentialStream;  
  
    // Create the DBBINDING, requesting a storage-object pointer from  
    // The SQL Server Native Client OLE DB provider.  
    dbbinding.iOrdinal = nCol;  
    dbbinding.obValue = 0;  
    dbbinding.obStatus = sizeof(IUnknown*);  
    dbbinding.obLength = 0;  
    dbbinding.pTypeInfo = NULL;  
    dbbinding.pObject = &dbobject;  
    dbbinding.pBindExt = NULL;  
    dbbinding.dwPart = DBPART_VALUE | DBPART_STATUS;  
    dbbinding.dwMemOwner = DBMEMOWNER_CLIENTOWNED;  
    dbbinding.eParamIO = DBPARAMIO_NOTPARAM;  
    dbbinding.cbMaxLen = 0;  
    dbbinding.dwFlags = 0;  
    dbbinding.wType = DBTYPE_IUNKNOWN;  
    dbbinding.bPrecision = 0;  
    dbbinding.bScale = 0;  
  
    if (FAILED(hr = pIRowset->  
        QueryInterface(IID_IAccessor, (void**) &pIAccessor)))  
        {  
        // Process QueryInterface failure.  
        return (hr);  
        }  
  
    // Create the accessor.  
    if (FAILED(hr = pIAccessor->CreateAccessor(DBACCESSOR_ROWDATA, 1,  
        &dbbinding, 0, &haccessor, &ulbindstatus)))  
        {  
        // Process error from CreateAccessor.  
        pIAccessor->Release();  
        return (hr);  
        }  
  
    // Read and process BLOCK_SIZE bytes at a time.  
    if (SUCCEEDED(hr = pIRowset->GetData(hRow, haccessor, pRow)))  
        {  
        dwStatus = *((ULONG*) (pRow + dbbinding.obStatus));  
  
        if (dwStatus == DBSTATUS_S_ISNULL)  
            {  
            // Process NULL data  
            }  
        else if (dwStatus == DBSTATUS_S_OK)  
            {  
            pISequentialStream = *((ISequentialStream**)   
                (pRow + dbbinding.obValue));  
  
            do  
                {  
                if (SUCCEEDED(hr =  
                    pISequentialStream->Read(pUnboundData,  
                    BLOCK_SIZE, &cbRead)))  
                    {  
                    pUnboundData += cbRead;  
                    }  
                }  
            while (SUCCEEDED(hr) && cbRead >= BLOCK_SIZE);  
  
            pISequentialStream->Release();  
            }  
        }  
    else  
        {  
        // Process error from GetData.  
        }  
  
    pIAccessor->ReleaseAccessor(haccessor, NULL);  
    pIAccessor->Release();  
    delete [] pRow;  
  
    return (hr);  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4d4f-114">参照</span><span class="sxs-lookup"><span data-stu-id="e4d4f-114">See Also</span></span>  
 <span data-ttu-id="e4d4f-115">[Blob と OLE オブジェクト](blobs-and-ole-objects.md) </span><span class="sxs-lookup"><span data-stu-id="e4d4f-115">[BLOBs and OLE Objects](blobs-and-ole-objects.md) </span></span>  
 [<span data-ttu-id="e4d4f-116">大きな値をとるデータ型の使用</span><span class="sxs-lookup"><span data-stu-id="e4d4f-116">Using Large Value Types</span></span>](../native-client/features/using-large-value-types.md)  
  
  
