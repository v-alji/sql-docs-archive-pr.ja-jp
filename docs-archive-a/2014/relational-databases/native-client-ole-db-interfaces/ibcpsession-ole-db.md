---
title: IBCPSession (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- IBCPSession interface
ms.assetid: 00d0311f-8b71-4ad6-824d-0e89119347a3
author: rothja
ms.author: jroth
ms.openlocfilehash: 0d32da9c06a200d5924dbae18d6b7513f46c88ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739810"
---
# <a name="ibcpsession-ole-db"></a><span data-ttu-id="e942c-102">IBCPSession (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="e942c-102">IBCPSession (OLE DB)</span></span>
  <span data-ttu-id="e942c-103">**IBCPSession** インターフェイスでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のファイルベースの一括コピー操作のサポートが公開されます。</span><span class="sxs-lookup"><span data-stu-id="e942c-103">The **IBCPSession** interface exposes support for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] file-based bulk copy operations.</span></span> <span data-ttu-id="e942c-104">**Ibcpsession**インターフェイスは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ネイティブクライアント OLE DB プロバイダーのセッションと同じレベルで公開されます。</span><span class="sxs-lookup"><span data-stu-id="e942c-104">The **IBCPSession** interface is exposed in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider under the same level as Sessions.</span></span> <span data-ttu-id="e942c-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーでは、データソースオブジェクトはセッションオブジェクトのファクトリであり、SSPROP_ENABLEBULKCOPY の接続プロパティには一括コピー操作が指定されています。</span><span class="sxs-lookup"><span data-stu-id="e942c-105">In the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, data source objects are factories for Session objects, and bulk copy operations are specified in the connection property SSPROP_ENABLEBULKCOPY.</span></span> <span data-ttu-id="e942c-106">また、SSPROP_ENABLEFASTLOAD プロパティは true に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e942c-106">In addition, the SSPROP_ENABLEFASTLOAD property should be set to true.</span></span>  
  
 <span data-ttu-id="e942c-107">**IDBCreateSession::CreateSession** メソッドを呼び出すと、**BulkCopySession** オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e942c-107">Calling the **IDBCreateSession::CreateSession** method will then result in the creation of a **BulkCopySession** object.</span></span> <span data-ttu-id="e942c-108">その後、作成された **IBCPSession** オブジェクトの **IBCPSession** インターフェイスとほぼ同じシグネチャを使用して、**IBCPSession** オブジェクト経由で公開されるファイルベースのすべての一括コピー メソッドを呼び出せるようになります。</span><span class="sxs-lookup"><span data-stu-id="e942c-108">All the file-based bulk copy methods exposed through the **IBCPSession** object are then callable with nearly similar signatures on this **IBCPSession** object's **IBCPSession** interface.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e942c-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、 [IRowsetFastLoad](irowsetfastload-ole-db.md)インターフェイスを使用して、メモリベースの一括コピー操作をサポートします。</span><span class="sxs-lookup"><span data-stu-id="e942c-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports memory-based bulk copy operations through the [IRowsetFastLoad](irowsetfastload-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="e942c-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブクライアント OLE DB プロバイダーを使用した一括コピー操作の詳細については、「[一括コピー操作の実行](../native-client/features/performing-bulk-copy-operations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e942c-110">For more information about using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider for bulk copy operations, see [Performing Bulk Copy Operations](../native-client/features/performing-bulk-copy-operations.md).</span></span>  
  
 <span data-ttu-id="e942c-111">**IBCPSession** インターフェイスの使用方法を示したサンプルについては、「[IBCPSession::BCPDone &#40;OLE DB&#41;](ibcpsession-bcpdone-ole-db.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e942c-111">For a sample showing how to use the **IBCPSession** interface, see [IBCPSession::BCPDone &#40;OLE DB&#41;](ibcpsession-bcpdone-ole-db.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e942c-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e942c-112">In This Section</span></span>  
  
|<span data-ttu-id="e942c-113">方法</span><span class="sxs-lookup"><span data-stu-id="e942c-113">Method</span></span>|<span data-ttu-id="e942c-114">説明</span><span class="sxs-lookup"><span data-stu-id="e942c-114">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e942c-115">IBCPSession::BCPColFmt &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="e942c-115">IBCPSession::BCPColFmt &#40;OLE DB&#41;</span></span>](ibcpsession-bcpcolfmt-ole-db.md)|<span data-ttu-id="e942c-116">プログラム変数と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列のバインドを作成します。</span><span class="sxs-lookup"><span data-stu-id="e942c-116">Creates a binding between program variables and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] columns.</span></span>|  
|[<span data-ttu-id="e942c-117">IBCPSession::BCPColumns &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="e942c-117">IBCPSession::BCPColumns &#40;OLE DB&#41;</span></span>](ibcpsession-bcpcolumns-ole-db.md)|<span data-ttu-id="e942c-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブル内の列にバインドされるフィールド数を設定します。</span><span class="sxs-lookup"><span data-stu-id="e942c-118">Sets the number of fields that are to be bound to the columns in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>|  
|[<span data-ttu-id="e942c-119">IBCPSession::BCPControl &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="e942c-119">IBCPSession::BCPControl &#40;OLE DB&#41;</span></span>](ibcpsession-bcpcontrol-ole-db.md)|<span data-ttu-id="e942c-120">一括コピー操作のオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="e942c-120">Sets the options for a bulk copy operation.</span></span>|  
|[<span data-ttu-id="e942c-121">IBCPSession::BCPDone &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="e942c-121">IBCPSession::BCPDone &#40;OLE DB&#41;</span></span>](ibcpsession-bcpdone-ole-db.md)|<span data-ttu-id="e942c-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に送信される残りの行をコミットします。</span><span class="sxs-lookup"><span data-stu-id="e942c-122">Commits the remaining rows to be sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="e942c-123">IBCPSession::BCPExec &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="e942c-123">IBCPSession::BCPExec &#40;OLE DB&#41;</span></span>](ibcpsession-bcpexec-ole-db.md)|<span data-ttu-id="e942c-124">一括コピー操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="e942c-124">Performs the bulk copy operation.</span></span>|  
|[<span data-ttu-id="e942c-125">IBCPSession::BCPInit &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="e942c-125">IBCPSession::BCPInit &#40;OLE DB&#41;</span></span>](ibcpsession-bcpinit-ole-db.md)|<span data-ttu-id="e942c-126">一括コピー構造を初期化し、エラー チェックを実行して、データ ファイルとフォーマット ファイルの名前が正しいことを確認します。その後、それらのファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="e942c-126">Initializes the bulk copy structure, performs some error checking, verifies that the data and format file names are correct, and then opens them.</span></span>|  
|[<span data-ttu-id="e942c-127">IBCPSession::BCPReadFmt &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="e942c-127">IBCPSession::BCPReadFmt &#40;OLE DB&#41;</span></span>](ibcpsession-bcpreadfmt-ole-db.md)|<span data-ttu-id="e942c-128">フォーマット ファイルから列ごとにフォーマット情報を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="e942c-128">Reads format information for each column from the format file.</span></span>|  
|[<span data-ttu-id="e942c-129">IBCPSession::BCPWriteFmt &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="e942c-129">IBCPSession::BCPWriteFmt &#40;OLE DB&#41;</span></span>](ibcpsession-bcpwritefmt-ole-db.md)|<span data-ttu-id="e942c-130">フォーマット ファイルに列ごとのフォーマット情報を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="e942c-130">Writes format information for each column to the format file.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e942c-131">参照</span><span class="sxs-lookup"><span data-stu-id="e942c-131">See Also</span></span>  
 [<span data-ttu-id="e942c-132">インターフェイス &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="e942c-132">Interfaces &#40;OLE DB&#41;</span></span>](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
