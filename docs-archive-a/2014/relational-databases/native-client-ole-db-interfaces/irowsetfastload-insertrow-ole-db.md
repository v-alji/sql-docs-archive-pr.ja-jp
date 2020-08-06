---
title: IRowsetFastLoad::InsertRow (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IRowsetFastLoad::InsertRow (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- InsertRow method
ms.assetid: 594d3461-34d2-41e7-8ad4-bd2753601ab6
author: rothja
ms.author: jroth
ms.openlocfilehash: 4e9ea952f27574270ee333919f778814ff3de462
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644446"
---
# <a name="irowsetfastloadinsertrow-ole-db"></a><span data-ttu-id="981b8-102">IRowsetFastLoad::InsertRow (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="981b8-102">IRowsetFastLoad::InsertRow (OLE DB)</span></span>
  <span data-ttu-id="981b8-103">一括コピー行セットに行を追加します。</span><span class="sxs-lookup"><span data-stu-id="981b8-103">Adds a row to the bulk copy rowset.</span></span> <span data-ttu-id="981b8-104">サンプルについては、「[IRowsetFastLoad を使用したデータの一括コピー (OLE DB)](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)」と「[IROWSETFASTLOAD と ISEQUENTIALSTREAM を使用した SQL SERVER への BLOB データの送信 (OLE DB)](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="981b8-104">For samples, see [Bulk Copy Data Using IRowsetFastLoad &#40;OLE DB&#41;](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) and [Send BLOB Data to SQL SERVER Using IROWSETFASTLOAD and ISEQUENTIALSTREAM &#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="981b8-105">構文</span><span class="sxs-lookup"><span data-stu-id="981b8-105">Syntax</span></span>  
  
```  
  
HRESULT InsertRow(  
HACCESSOR  
hAccessor  
,  
void*  
pData  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="981b8-106">引数</span><span class="sxs-lookup"><span data-stu-id="981b8-106">Arguments</span></span>  
 <span data-ttu-id="981b8-107">*hAccessor*[in]</span><span class="sxs-lookup"><span data-stu-id="981b8-107">*hAccessor*[in]</span></span>  
 <span data-ttu-id="981b8-108">一括コピーの行データを定義するアクセサーのハンドルを指定します。</span><span class="sxs-lookup"><span data-stu-id="981b8-108">The handle of the accessor defining the row data for bulk copy.</span></span> <span data-ttu-id="981b8-109">参照されるアクセサーは行アクセサーで、データ値を保持するコンシューマー所有のメモリをバインドします。</span><span class="sxs-lookup"><span data-stu-id="981b8-109">The accessor referenced is a row accessor, binding consumer-owned memory containing data values.</span></span>  
  
 <span data-ttu-id="981b8-110">*pData*[in]</span><span class="sxs-lookup"><span data-stu-id="981b8-110">*pData*[in]</span></span>  
 <span data-ttu-id="981b8-111">データ値を保持するコンシューマー所有のメモリへのポインターを指定します。</span><span class="sxs-lookup"><span data-stu-id="981b8-111">A pointer to the consumer-owned memory containing data values.</span></span> <span data-ttu-id="981b8-112">詳細については、「[DBBINDING 構造体](https://go.microsoft.com/fwlink/?LinkId=65955)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="981b8-112">For more information, see [DBBINDING Structures](https://go.microsoft.com/fwlink/?LinkId=65955).</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="981b8-113">リターン コードの値</span><span class="sxs-lookup"><span data-stu-id="981b8-113">Return Code Values</span></span>  
 <span data-ttu-id="981b8-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="981b8-114">S_OK</span></span>  
 <span data-ttu-id="981b8-115">メソッドが成功しました。</span><span class="sxs-lookup"><span data-stu-id="981b8-115">The method succeeded.</span></span> <span data-ttu-id="981b8-116">すべての列のバインド状態値は、DBSTATUS_S_OK または DBSTATUS_S_NULL です。</span><span class="sxs-lookup"><span data-stu-id="981b8-116">Any bound status values for all columns have value DBSTATUS_S_OK or DBSTATUS_S_NULL.</span></span>  
  
 <span data-ttu-id="981b8-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="981b8-117">E_FAIL</span></span>  
 <span data-ttu-id="981b8-118">エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="981b8-118">An error occurred.</span></span> <span data-ttu-id="981b8-119">エラー情報は、行セットのエラー インターフェイスから参照できます。</span><span class="sxs-lookup"><span data-stu-id="981b8-119">Error information is available from the rowset's error interfaces.</span></span>  
  
 <span data-ttu-id="981b8-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="981b8-120">E_INVALIDARG</span></span>  
 <span data-ttu-id="981b8-121">*pData* 引数に NULL ポインターが設定されました。</span><span class="sxs-lookup"><span data-stu-id="981b8-121">The *pData* argument was set to a NULL pointer.</span></span>  
  
 <span data-ttu-id="981b8-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="981b8-122">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="981b8-123">SQLNCLI11 では、要求を完了するのに必要なメモリを割り当てることができませんでした。</span><span class="sxs-lookup"><span data-stu-id="981b8-123">SQLNCLI11 was unable to allocate sufficient memory to complete the request.</span></span>  
  
 <span data-ttu-id="981b8-124">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="981b8-124">E_UNEXPECTED</span></span>  
 <span data-ttu-id="981b8-125">既に [IRowsetFastLoad::Commit](irowsetfastload-commit-ole-db.md) メソッドによって無効になっている一括コピー行セットに対して呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="981b8-125">The method was called on a bulk copy rowset previously invalidated by the [IRowsetFastLoad::Commit](irowsetfastload-commit-ole-db.md) method.</span></span>  
  
 <span data-ttu-id="981b8-126">DB_E_BADACCESSORHANDLE </span><span class="sxs-lookup"><span data-stu-id="981b8-126">DB_E_BADACCESSORHANDLE</span></span>  
 <span data-ttu-id="981b8-127">コンシューマーが指定した *hAccessor* 引数が無効でした。</span><span class="sxs-lookup"><span data-stu-id="981b8-127">The *hAccessor* argument provided by the consumer was invalid.</span></span>  
  
 <span data-ttu-id="981b8-128">DB_E_BADACCESSORTYPE </span><span class="sxs-lookup"><span data-stu-id="981b8-128">DB_E_BADACCESSORTYPE</span></span>  
 <span data-ttu-id="981b8-129">指定されたアクセサーが行アクセサーではなかったか、コンシューマー所有のメモリが指定されませんでした。</span><span class="sxs-lookup"><span data-stu-id="981b8-129">The specified accessor was not a row accessor or did not specify consumer-owned memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="981b8-130">解説</span><span class="sxs-lookup"><span data-stu-id="981b8-130">Remarks</span></span>  
 <span data-ttu-id="981b8-131">コンシューマーデータを列のデータ型に変換するときにエラーが発生する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーから E_FAIL が返されます。</span><span class="sxs-lookup"><span data-stu-id="981b8-131">An error converting consumer data to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type for a column causes an E_FAIL return from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span> <span data-ttu-id="981b8-132">**InsertRow** メソッドを使用するか、**Commit** メソッドのみを使用して、データを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に転送できます。</span><span class="sxs-lookup"><span data-stu-id="981b8-132">Data can be transmitted to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on any **InsertRow** method or only on **Commit** method.</span></span> <span data-ttu-id="981b8-133">**InsertRow** メソッドを使用する場合、コンシューマー アプリケーションは、データ型変換エラーの通知を受け取るまで、誤ったデータを使用してこのメソッドを何回も呼び出す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="981b8-133">The consumer application can call the **InsertRow** method many times with erroneous data before it receives notice that a data type conversion error exists.</span></span> <span data-ttu-id="981b8-134">**Commit** メソッドでは、すべてのデータがコンシューマーにより正しく指定されたことが保証されるので、コンシューマーは適切に **Commit** を使用することで、必要に応じてデータを検証できます。</span><span class="sxs-lookup"><span data-stu-id="981b8-134">Because the **Commit** method ensures that all data is correctly specified by the consumer, the consumer can use the **Commit** method appropriately to validate data as necessary.</span></span>  
  
 <span data-ttu-id="981b8-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーの一括コピー行セットは書き込み専用です。</span><span class="sxs-lookup"><span data-stu-id="981b8-135">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider bulk copy rowsets are write-only.</span></span> <span data-ttu-id="981b8-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、行セットのコンシューマークエリを許可するメソッドを公開しません。</span><span class="sxs-lookup"><span data-stu-id="981b8-136">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes no methods allowing consumer query of the rowset.</span></span> <span data-ttu-id="981b8-137">処理を終了する場合、コンシューマーは **Commit** メソッドを呼び出さずに、[IRowsetFastLoad](irowsetfastload-ole-db.md) インターフェイスの参照を解放できます。</span><span class="sxs-lookup"><span data-stu-id="981b8-137">To terminate processing, the consumer can release its reference on the [IRowsetFastLoad](irowsetfastload-ole-db.md) interface without calling the **Commit** method.</span></span> <span data-ttu-id="981b8-138">コンシューマーが行セットに挿入した行にアクセスして値を変更する機能や、そのような行を行セットから個別に削除する機能はありません。</span><span class="sxs-lookup"><span data-stu-id="981b8-138">There are no facilities for accessing a consumer-inserted row in the rowset and changing its values, or removing it individually from the rowset.</span></span>  
  
 <span data-ttu-id="981b8-139">一括コピーされる行は、サーバー上で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用に形式が設定されます。</span><span class="sxs-lookup"><span data-stu-id="981b8-139">Bulk copied rows are formatted on the server for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="981b8-140">行の形式は、ANSI_PADDING など、接続やセッションに設定されたオプションの影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="981b8-140">The row format is affected by any options that may have been set for the connection or session such as ANSI_PADDING.</span></span> <span data-ttu-id="981b8-141">このオプションは、Native Client OLE DB プロバイダーを介して行われるすべての接続に対して既定で設定され [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="981b8-141">This option is set on by default for any connection made through the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="981b8-142">参照</span><span class="sxs-lookup"><span data-stu-id="981b8-142">See Also</span></span>  
 [<span data-ttu-id="981b8-143">IRowsetFastLoad &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="981b8-143">IRowsetFastLoad &#40;OLE DB&#41;</span></span>](irowsetfastload-ole-db.md)  
  
  
