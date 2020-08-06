---
title: データ ソース オブジェクト (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], data source objects
- SQL Server Native Client, data source objects
- SQLNCLI, data source objects
- SQL Server Native Client OLE DB provider, data source objects
- OLE DB data source objects [SQL Server Native Client]
- data source objects [OLE DB]
- CLSID
ms.assetid: c1d4ed20-ad3b-4e33-a26b-38d7517237b7
author: rothja
ms.author: jroth
ms.openlocfilehash: 9cf3f0b0308d655b50149c174547c19966f550ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711909"
---
# <a name="data-source-objects-ole-db"></a><span data-ttu-id="da3d0-102">データ ソース オブジェクト (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="da3d0-102">Data Source Objects (OLE DB)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="da3d0-103">Native Client では、などのデータストアへのリンクを確立するために使用される一連の OLE DB インターフェイスに対して、データソースという用語を使用し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="da3d0-103">Native Client uses the term data source for the set of OLE DB interfaces used to establish a link to a data store, such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="da3d0-104">プロバイダーのデータソースオブジェクトのインスタンスを作成することは、ネイティブクライアントコンシューマーの最初のタスクです [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="da3d0-104">Creating an instance of the data source object of the provider is the first task of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client consumer.</span></span>  
  
 <span data-ttu-id="da3d0-105">すべての OLE DB プロバイダーは、そのプロバイダー自体のクラス ID (CLSID) を宣言します。</span><span class="sxs-lookup"><span data-stu-id="da3d0-105">Every OLE DB provider declares a class identifier (CLSID) for itself.</span></span> <span data-ttu-id="da3d0-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーの CLSID は、C/c + + GUID CLSID_SQLNCLI10 です (シンボル SQLNCLI_CLSID は、参照する SQLNCLI ファイルの正しい progid に解決されます)。</span><span class="sxs-lookup"><span data-stu-id="da3d0-106">The CLSID for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider is the C/C++ GUID CLSID_SQLNCLI10 (the symbol SQLNCLI_CLSID will resolve to the correct progid in the sqlncli.h file that you reference).</span></span> <span data-ttu-id="da3d0-107">コンシューマーは、CLSID を指定して OLE **CoCreateInstance** 関数を使用し、データ ソース オブジェクトのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="da3d0-107">With the CLSID, the consumer uses the OLE **CoCreateInstance** function to manufacture an instance of the data source object.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="da3d0-108">Native Client は、インプロセスサーバーです。</span><span class="sxs-lookup"><span data-stu-id="da3d0-108">Native Client is an in-process server.</span></span> <span data-ttu-id="da3d0-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーオブジェクトのインスタンスは、実行可能なコンテキストを示すために、CLSCTX_INPROC_SERVER マクロを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="da3d0-109">Instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider objects are created using the CLSCTX_INPROC_SERVER macro to indicate the executable context.</span></span>  
  
 <span data-ttu-id="da3d0-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーのデータソースオブジェクトは、コンシューマーが既存のデータベースに接続できるようにする OLE DB 初期化インターフェイスを公開し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="da3d0-110">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider data source object exposes the OLE DB initialization interfaces that allow the consumer to connect to existing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
 <span data-ttu-id="da3d0-111">Native Client OLE DB プロバイダーを介して行われるすべての接続で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、次のオプションが自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="da3d0-111">Every connection made through the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider sets these options automatically:</span></span>  
  
-   <span data-ttu-id="da3d0-112">SET ANSI_WARNINGS ON</span><span class="sxs-lookup"><span data-stu-id="da3d0-112">SET ANSI_WARNINGS ON</span></span>  
  
-   <span data-ttu-id="da3d0-113">SET ANSI_NULLS ON</span><span class="sxs-lookup"><span data-stu-id="da3d0-113">SET ANSI_NULLS ON</span></span>  
  
-   <span data-ttu-id="da3d0-114">SET ANSI_PADDING ON</span><span class="sxs-lookup"><span data-stu-id="da3d0-114">SET ANSI_PADDING ON</span></span>  
  
-   <span data-ttu-id="da3d0-115">SET ANSI_NULL_DFLT_ON ON</span><span class="sxs-lookup"><span data-stu-id="da3d0-115">SET ANSI_NULL_DFLT_ON ON</span></span>  
  
-   <span data-ttu-id="da3d0-116">SET QUOTED_IDENTIFIER ON</span><span class="sxs-lookup"><span data-stu-id="da3d0-116">SET QUOTED_IDENTIFIER ON</span></span>  
  
-   <span data-ttu-id="da3d0-117">SET CONCAT_OF_NULL_YIELDS_NULL ON</span><span class="sxs-lookup"><span data-stu-id="da3d0-117">SET CONCAT_OF_NULL_YIELDS_NULL ON</span></span>  
  
 <span data-ttu-id="da3d0-118">この例では、クラス識別子マクロを使用し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] て、Native Client OLE DB プロバイダーのデータソースオブジェクトを作成し、 **IDBInitialize**インターフェイスへの参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="da3d0-118">This example uses the class identifier macro to create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider data source object and get a reference to its **IDBInitialize** interface.</span></span>  
  
```  
IDBInitialize*   pIDBInitialize;  
HRESULT          hr;  
  
hr = CoCreateInstance(CLSID_SQLNCLI10, NULL, CLSCTX_INPROC_SERVER,  
    IID_IDBInitialize, (void**) &pIDBInitialize);  
  
if (SUCCEEDED(hr))  
{  
    //  Perform necessary processing with the interface.  
    pIDBInitialize->Uninitialize();  
    pIDBInitialize->Release();  
}  
else  
{  
    // Display error from CoCreateInstance.  
}  
```  
  
 <span data-ttu-id="da3d0-119">Native Client OLE DB プロバイダーのデータソースオブジェクトのインスタンスを正常に作成すると [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、データソースを初期化し、セッションを作成することによって、コンシューマーアプリケーションを続行できます。</span><span class="sxs-lookup"><span data-stu-id="da3d0-119">With successful creation of an instance of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider data source object, the consumer application can continue by initializing the data source and creating sessions.</span></span> <span data-ttu-id="da3d0-120">OLE DB セッションは、データへのアクセスや操作を可能にするインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="da3d0-120">OLE DB sessions present the interfaces that allow data access and manipulation.</span></span>  
  
 <span data-ttu-id="da3d0-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データソースの初期化の一環として、の指定されたインスタンスへの最初の接続を行います。</span><span class="sxs-lookup"><span data-stu-id="da3d0-121">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider makes its first connection to a specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as part of a successful data source initialization.</span></span> <span data-ttu-id="da3d0-122">いずれかのデータ ソース初期化インターフェイスで参照が保持されている間、または **IDBInitialize::Uninitialize** メソッドが呼び出されるまで、その最初の接続が維持されます。</span><span class="sxs-lookup"><span data-stu-id="da3d0-122">The connection is maintained as long as a reference is maintained on any data source initialization interface, or until the **IDBInitialize::Uninitialize** method is called.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="da3d0-123">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="da3d0-123">In This Section</span></span>  
  
-   [<span data-ttu-id="da3d0-124">データ ソースのプロパティ &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="da3d0-124">Data Source Properties &#40;OLE DB&#41;</span></span>](data-source-properties-ole-db.md)  
  
-   [<span data-ttu-id="da3d0-125">データ ソース情報のプロパティ</span><span class="sxs-lookup"><span data-stu-id="da3d0-125">Data Source Information Properties</span></span>](data-source-information-properties.md)  
  
-   [<span data-ttu-id="da3d0-126">初期化プロパティと承認プロパティ</span><span class="sxs-lookup"><span data-stu-id="da3d0-126">Initialization and Authorization Properties</span></span>](initialization-and-authorization-properties.md)  
  
-   [<span data-ttu-id="da3d0-127">セッション</span><span class="sxs-lookup"><span data-stu-id="da3d0-127">Sessions</span></span>](sessions.md)  
  
-   [<span data-ttu-id="da3d0-128">セッション プロパティ</span><span class="sxs-lookup"><span data-stu-id="da3d0-128">Session Properties</span></span>](session-properties-sql-server-native-client-ole-db-provider.md)  
  
-   [<span data-ttu-id="da3d0-129">保存されるデータ ソース オブジェクト</span><span class="sxs-lookup"><span data-stu-id="da3d0-129">Persisted Data Source Objects</span></span>](persisted-data-source-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="da3d0-130">参照</span><span class="sxs-lookup"><span data-stu-id="da3d0-130">See Also</span></span>  
 [<span data-ttu-id="da3d0-131">SQL Server Native Client &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="da3d0-131">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
