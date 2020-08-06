---
title: BLOB と OLE オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- BLOBs
- storage object [OLE DB]
- SQL Server Native Client OLE DB provider, BLOBs
- large data, OLE objects
ms.assetid: 767fa2f6-9cd2-436f-add5-e760bed29a58
author: rothja
ms.author: jroth
ms.openlocfilehash: 15f8b4915ba9b05a5be19854a2e27a2e8ff3a346
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741925"
---
# <a name="blobs-and-ole-objects"></a><span data-ttu-id="b45ed-102">BLOB と OLE オブジェクト</span><span class="sxs-lookup"><span data-stu-id="b45ed-102">BLOBs and OLE Objects</span></span>
  <span data-ttu-id="b45ed-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、 **ISequentialStream**インターフェイスを公開して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ntext**、 **text**、 **image**、 **varchar (max)**、 **nvarchar (max**)、 **varbinary (max)**、および xml データ型へのコンシューマーアクセスをバイナリラージオブジェクト (blob) としてサポートします。</span><span class="sxs-lookup"><span data-stu-id="b45ed-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **ISequentialStream** interface to support consumer access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ntext**, **text**, **image**, **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, and xml data types as binary large objects (BLOBs).</span></span> <span data-ttu-id="b45ed-104">**ISequentialStream** の **Read** メソッドを使用すると、扱いやすい単位で大量のデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="b45ed-104">The **Read** method on **ISequentialStream** lets the consumer retrieve much data in manageable chunks.</span></span>  
  
 <span data-ttu-id="b45ed-105">この機能を示すサンプルについては、「[大きなデータの設定 (OLE DB)](../native-client-ole-db-how-to/set-large-data-ole-db.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b45ed-105">For a sample demonstrating this feature, see [Set Large Data &#40;OLE DB&#41;](../native-client-ole-db-how-to/set-large-data-ole-db.md).</span></span>  
  
 <span data-ttu-id="b45ed-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、コンシューマーがデータ変更のためにバインドされたアクセサーにインターフェイスポインターを提供するときに、コンシューマーが実装した**IStorage**インターフェイスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b45ed-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider can use a consumer-implemented **IStorage** interface when the consumer provides the interface pointer in an accessor bound for data modification.</span></span>  
  
 <span data-ttu-id="b45ed-107">大きな値のデータ型の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、 **IROWSET**および DDL インターフェイスの型サイズの想定を確認します。</span><span class="sxs-lookup"><span data-stu-id="b45ed-107">For large value data types, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider checks for type size assumptions in **IRowset** and DDL interfaces.</span></span> <span data-ttu-id="b45ed-108">最大サイズが無制限に設定された**varchar**、 **nvarchar**、および**varbinary**データ型の列は、スキーマ行セットと列データ型を返すインターフェイスによって islong として表されます。</span><span class="sxs-lookup"><span data-stu-id="b45ed-108">Columns with **varchar**, **nvarchar**, and **varbinary** data types with max size set to unlimited will be represented as ISLONG through the schema rowsets and interfaces returning column data types.</span></span>  
  
 <span data-ttu-id="b45ed-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、 **varchar (max)**、 **varbinary (max)** 、 **nvarchar (max)** 型をそれぞれ DBTYPE_STR、DBTYPE_BYTES および DBTYPE_WSTR として公開します。</span><span class="sxs-lookup"><span data-stu-id="b45ed-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **varchar(max)**, **varbinary(max)** and **nvarchar(max)** types as DBTYPE_STR, DBTYPE_BYTES and DBTYPE_WSTR respectively.</span></span>  
  
 <span data-ttu-id="b45ed-110">これらの型を使用するには、アプリケーションに次のオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="b45ed-110">To work with these types an application has the following options:</span></span>  
  
-   <span data-ttu-id="b45ed-111">データ型 DBTYPE_STR、DBTYPE_BYTES、または DBTYPE_WSTR としてバインドします。</span><span class="sxs-lookup"><span data-stu-id="b45ed-111">Bind as the type (DBTYPE_STR, DBTYPE_BYTES, DBTYPE_WSTR).</span></span> <span data-ttu-id="b45ed-112">バッファーのサイズが十分でない場合、これらのデータ型は以前のリリースでの動作と同様に (以前よりも大きな値を格納できるようになりましたが)、切り捨てが行われます。</span><span class="sxs-lookup"><span data-stu-id="b45ed-112">If the buffer is not big enough truncation will occur, exactly as for these types in previous releases (although larger values are now available).</span></span>  
  
-   <span data-ttu-id="b45ed-113">データ型としてバインドし、DBTYPE_BYREF も指定します。</span><span class="sxs-lookup"><span data-stu-id="b45ed-113">Bind as the type and also specify DBTYPE_BYREF.</span></span>  
  
-   <span data-ttu-id="b45ed-114">DBTYPE_IUNKNOWN としてバインドし、ストリーミングを使用します。</span><span class="sxs-lookup"><span data-stu-id="b45ed-114">Bind as DBTYPE_IUNKNOWN and use streaming.</span></span>  
  
 <span data-ttu-id="b45ed-115">DBTYPE_IUNKNOWN にバインドすると、ISequentialStream ストリーム機能が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b45ed-115">If bound to DBTYPE_IUNKNOWN, ISequentialStream stream functionality is used.</span></span> <span data-ttu-id="b45ed-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、大きな値のデータ型の DBTYPE_IUNKNOWN として出力パラメーターをバインドすることをサポートしています。これは、ストアドプロシージャがこれらのデータ型を戻り値として返し、クライアントに DBTYPE_IUNKNOWN として公開されるシナリオを容易にします。</span><span class="sxs-lookup"><span data-stu-id="b45ed-116">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports binding output parameters as DBTYPE_IUNKNOWN for large value data types to facilitate scenarios where a stored procedure returns these data types as return values which will be exposed as DBTYPE_IUNKNOWN to the client.</span></span>  
  
## <a name="storage-object-limitations"></a><span data-ttu-id="b45ed-117">ストレージ オブジェクトの制限事項</span><span class="sxs-lookup"><span data-stu-id="b45ed-117">Storage Object Limitations</span></span>  
  
-   <span data-ttu-id="b45ed-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、開いているストレージオブジェクトを1つだけサポートできます。</span><span class="sxs-lookup"><span data-stu-id="b45ed-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider can support only a single open storage object.</span></span> <span data-ttu-id="b45ed-119">複数の **ISequentialStream** インターフェイス ポインターへの参照を取得するために、複数のストレージ オブジェクトを開こうとすると、DBSTATUS_E_CANTCREATE が返されます。</span><span class="sxs-lookup"><span data-stu-id="b45ed-119">Attempts to open more than one storage object (to get a reference on more than one **ISequentialStream** interface pointer) return DBSTATUS_E_CANTCREATE.</span></span>  
  
-   <span data-ttu-id="b45ed-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーでは、DBPROP_BLOCKINGSTORAGEOBJECTS 読み取り専用プロパティの既定値は VARIANT_TRUE です。</span><span class="sxs-lookup"><span data-stu-id="b45ed-120">In the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, the default value of the DBPROP_BLOCKINGSTORAGEOBJECTS read-only property is VARIANT_TRUE.</span></span> <span data-ttu-id="b45ed-121">この値は、ストレージ オブジェクトがアクティブである場合に、(ストレージ オブジェクト以外の) 一部のメソッドが失敗して E_UNEXPECTED が返されることを示します。</span><span class="sxs-lookup"><span data-stu-id="b45ed-121">This indicates that if a storage object is active, some methods (other than those on the storage objects) will fail with E_UNEXPECTED.</span></span>  
  
-   <span data-ttu-id="b45ed-122">コンシューマーが実装したストレージオブジェクトによって示されるデータの長さは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ストレージオブジェクトを参照する行アクセサーが作成されるときに、Native Client OLE DB プロバイダーに認識される必要があります。</span><span class="sxs-lookup"><span data-stu-id="b45ed-122">The length of data presented by a consumer-implemented storage object must be made known to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider when the row accessor that references the storage object is created.</span></span> <span data-ttu-id="b45ed-123">コンシューマー側では、アクセサーの作成に使用する DBBINDING 構造体に長さのインジケーターをバインドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b45ed-123">The consumer must bind a length indicator in the DBBINDING structure used for accessor creation.</span></span>  
  
-   <span data-ttu-id="b45ed-124">行に1つ以上の大きなデータ値が含まれていて DBPROP_ACCESSORDER が DBPROPVAL_AO_RANDOM ない場合、コンシューマーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 他の行の値を取得する前に、Native Client OLE DB プロバイダーカーソルによってサポートされる行セットを使用して行データを取得するか、すべての大きなデータ値を処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b45ed-124">If a row contains more than a single large data value and DBPROP_ACCESSORDER is not DBPROPVAL_AO_RANDOM, the consumer must either use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider cursor-supported rowset to retrieve row data or process all large data values before retrieving other row values.</span></span> <span data-ttu-id="b45ed-125">DBPROP_ACCESSORDER が DBPROPVAL_AO_RANDOM 場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーはすべての xml データ型をバイナリラージオブジェクト (blob) としてキャッシュし、任意の順序でアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="b45ed-125">If DBPROP_ACCESSORDER is DBPROPVAL_AO_RANDOM, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider caches all the xml data types as binary large objects (BLOBs) so that it can be accessed in any order.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b45ed-126">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b45ed-126">In This Section</span></span>  
  
-   [<span data-ttu-id="b45ed-127">大きなデータの取得</span><span class="sxs-lookup"><span data-stu-id="b45ed-127">Getting Large Data</span></span>](getting-large-data.md)  
  
-   [<span data-ttu-id="b45ed-128">大きなデータの設定</span><span class="sxs-lookup"><span data-stu-id="b45ed-128">Setting Large Data</span></span>](setting-large-data.md)  
  
-   [<span data-ttu-id="b45ed-129">BLOB 出力パラメーターのストリーミング サポート</span><span class="sxs-lookup"><span data-stu-id="b45ed-129">Streaming Support for BLOB Output Parameters</span></span>](streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a><span data-ttu-id="b45ed-130">参照</span><span class="sxs-lookup"><span data-stu-id="b45ed-130">See Also</span></span>  
 <span data-ttu-id="b45ed-131">[SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="b45ed-131">[SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md) </span></span>  
 [<span data-ttu-id="b45ed-132">大きな値をとるデータ型の使用</span><span class="sxs-lookup"><span data-stu-id="b45ed-132">Using Large Value Types</span></span>](../native-client/features/using-large-value-types.md)  
  
  
