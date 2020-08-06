---
title: IRowsetFastLoad::Commit (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IRowsetFastLoad::Commit (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Commit method
ms.assetid: 19de9128-b91a-4626-847f-af721edaa24e
author: rothja
ms.author: jroth
ms.openlocfilehash: cfdf355919f65fd2cedacd09249e2aae59321390
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644450"
---
# <a name="irowsetfastloadcommit-ole-db"></a><span data-ttu-id="9e5b3-102">IRowsetFastLoad::Commit (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="9e5b3-102">IRowsetFastLoad::Commit (OLE DB)</span></span>
  <span data-ttu-id="9e5b3-103">挿入される行のバッチの終わりをマークし、挿入された行を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のテーブルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="9e5b3-103">Marks the end of a batch of inserted rows and writes the rows to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="9e5b3-104">サンプルについては、「[IRowsetFastLoad を使用したデータの一括コピー (OLE DB)](irowsetfastload-ole-db.md)」と「[IROWSETFASTLOAD と ISEQUENTIALSTREAM を使用した SQL SERVER への BLOB データの送信 (OLE DB)](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e5b3-104">For samples, see [Bulk Copy Data Using IRowsetFastLoad &#40;OLE DB&#41;](irowsetfastload-ole-db.md) and [Send BLOB Data to SQL SERVER Using IROWSETFASTLOAD and ISEQUENTIALSTREAM &#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e5b3-105">構文</span><span class="sxs-lookup"><span data-stu-id="9e5b3-105">Syntax</span></span>  
  
```  
  
HRESULT Commit(  
BOOL   
fDone  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="9e5b3-106">引数</span><span class="sxs-lookup"><span data-stu-id="9e5b3-106">Arguments</span></span>  
 <span data-ttu-id="9e5b3-107">*fDone*[in]</span><span class="sxs-lookup"><span data-stu-id="9e5b3-107">*fDone*[in]</span></span>  
 <span data-ttu-id="9e5b3-108">FALSE の場合、行セットは有効なまま保持され、コンシューマーはこの行セットを使用してさらに行を挿入できます。</span><span class="sxs-lookup"><span data-stu-id="9e5b3-108">If FALSE, the rowset maintains validity and can be used by the consumer for additional row insertion.</span></span> <span data-ttu-id="9e5b3-109">TRUE の場合、行セットは無効になり、コンシューマーはこれ以上行を挿入できません。</span><span class="sxs-lookup"><span data-stu-id="9e5b3-109">If TRUE, the rowset loses validity and no further insertion can be done by the consumer.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="9e5b3-110">リターン コードの値</span><span class="sxs-lookup"><span data-stu-id="9e5b3-110">Return Code Values</span></span>  
 <span data-ttu-id="9e5b3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9e5b3-111">S_OK</span></span>  
 <span data-ttu-id="9e5b3-112">メソッドが成功し、挿入されたすべてのデータが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに書き込まれました。</span><span class="sxs-lookup"><span data-stu-id="9e5b3-112">The method succeeded and all inserted data has been written to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="9e5b3-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9e5b3-113">E_FAIL</span></span>  
 <span data-ttu-id="9e5b3-114">プロバイダー固有のエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9e5b3-114">A provider-specific error occurred.</span></span> <span data-ttu-id="9e5b3-115">特定のエラー テキストのエラー情報をプロバイダーから取得してください。</span><span class="sxs-lookup"><span data-stu-id="9e5b3-115">Retrieve error information for the specific error text from the provider.</span></span>  
  
 <span data-ttu-id="9e5b3-116">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="9e5b3-116">E_UNEXPECTED</span></span>  
 <span data-ttu-id="9e5b3-117">既に **IRowsetFastLoad::Commit** メソッドによって無効になっている一括コピー行セットに対して呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="9e5b3-117">The method was called on a bulk copy rowset previously invalidated by the **IRowsetFastLoad::Commit** method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e5b3-118">解説</span><span class="sxs-lookup"><span data-stu-id="9e5b3-118">Remarks</span></span>  
 <span data-ttu-id="9e5b3-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーの一括コピー行セットは、遅延更新モードの行セットとして動作します。</span><span class="sxs-lookup"><span data-stu-id="9e5b3-119">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider bulk copy rowset behaves as a delayed-update mode rowset.</span></span> <span data-ttu-id="9e5b3-120">ユーザーが行セットを使用して行データを挿入すると、挿入された行は、**IRowsetUpdate** をサポートする行セットでの保留中の挿入と同様の形式で扱われます。</span><span class="sxs-lookup"><span data-stu-id="9e5b3-120">As the user inserts row data through the rowset, inserted rows are treated in the same fashion as pending inserts on a rowset supporting **IRowsetUpdate**.</span></span>  
  
 <span data-ttu-id="9e5b3-121">コンシューマーは、**IRowsetUpdate::Update** メソッドを使用して保留中の行を SQL Server のインスタンスに送信するのと同様に、一括コピー行セットに対して **Commit** メソッドを呼び出して、挿入された行を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに書き込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e5b3-121">The consumer must call the **Commit** method on the bulk copy rowset to write inserted rows to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table in the same way as the **IRowsetUpdate::Update** method is used to submit pending rows to an instance of SQL Server.</span></span>  
  
 <span data-ttu-id="9e5b3-122">コンシューマーが **Commit** メソッドを呼び出さないで一括コピー行セットの参照を解放すると、挿入されてもそれ以前に書き込まれていない行はすべて失われます。</span><span class="sxs-lookup"><span data-stu-id="9e5b3-122">If the consumer releases its reference on the bulk copy rowset without calling the **Commit** method, all inserted rows not previously written are lost.</span></span>  
  
 <span data-ttu-id="9e5b3-123">コンシューマーは、*fDone* 引数を FALSE に設定して **Commit** メソッドを呼び出すことにより、挿入される行をバッチ処理できます。</span><span class="sxs-lookup"><span data-stu-id="9e5b3-123">The consumer can batch inserted rows by calling the **Commit** method with the *fDone* argument set to FALSE.</span></span> <span data-ttu-id="9e5b3-124">*fDone* を TRUE に設定すると、その行セットは無効になります。</span><span class="sxs-lookup"><span data-stu-id="9e5b3-124">When *fDone*is set to TRUE, the rowset becomes invalid.</span></span> <span data-ttu-id="9e5b3-125">無効な一括コピー行セットでは、**ISupportErrorInfo** インターフェイスと **IRowsetFastLoad::Release** メソッドのみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="9e5b3-125">An invalid bulk copy rowset supports only the **ISupportErrorInfo** interface and **IRowsetFastLoad::Release** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e5b3-126">参照</span><span class="sxs-lookup"><span data-stu-id="9e5b3-126">See Also</span></span>  
 [<span data-ttu-id="9e5b3-127">IRowsetFastLoad &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="9e5b3-127">IRowsetFastLoad &#40;OLE DB&#41;</span></span>](irowsetfastload-ole-db.md)  
  
  
