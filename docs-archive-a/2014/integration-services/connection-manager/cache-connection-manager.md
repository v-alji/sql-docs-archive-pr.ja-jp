---
title: キャッシュ接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Cache connection manager
ms.assetid: bdc92038-3720-4795-8a5c-79b963f2c952
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b8a7cc8bbe9e93c385fca6257e0be2e79bd3148a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641178"
---
# <a name="cache-connection-manager"></a><span data-ttu-id="2b930-102">キャッシュ接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="2b930-102">Cache Connection Manager</span></span>
  <span data-ttu-id="2b930-103">キャッシュ接続マネージャーでは、キャッシュ変換またはキャッシュ ファイル (.caw) からデータを読み取り、そのデータをキャッシュ ファイルに保存できます。</span><span class="sxs-lookup"><span data-stu-id="2b930-103">The Cache connection manager reads data from the Cache transform or from a cache file (.caw), and can save the data to a cache file.</span></span> <span data-ttu-id="2b930-104">キャッシュ ファイルを使用するようにキャッシュ接続マネージャーを構成したかどうかに関係なく、データは常にメモリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="2b930-104">Whether you configure the Cache connection manager to use a cache file, the data is always stored in memory.</span></span>  
  
 <span data-ttu-id="2b930-105">キャッシュ変換を使用して、データ フロー内の接続されているデータ ソースのデータをキャッシュ接続マネージャーに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="2b930-105">The Cache Transform transformation writes data from a connected data source in the data flow to a Cache connection manager.</span></span> <span data-ttu-id="2b930-106">パッケージ内の参照変換は、データに対する参照を実行します。</span><span class="sxs-lookup"><span data-stu-id="2b930-106">The Lookup transformation in a package performs lookups on the data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2b930-107">キャッシュ接続マネージャーでは、バイナリ ラージ オブジェクト (BLOB) データ型 DT_TEXT、DT_NTEXT、および DT_IMAGE はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="2b930-107">The Cache connection manager does not support the Binary Large Object (BLOB) data types DT_TEXT, DT_NTEXT, and DT_IMAGE.</span></span> <span data-ttu-id="2b930-108">参照データセットに BLOB データ型が含まれている場合、パッケージを実行するとコンポーネントは失敗します。</span><span class="sxs-lookup"><span data-stu-id="2b930-108">If the reference dataset contains a BLOB data type, the component will fail when you run the package.</span></span> <span data-ttu-id="2b930-109">**[キャッシュ接続マネージャー エディター]** を使用して、列のデータ型を変更できます。</span><span class="sxs-lookup"><span data-stu-id="2b930-109">You can use the **Cache Connection Manager Editor** to modify column data types.</span></span> <span data-ttu-id="2b930-110">詳細については、「 [キャッシュ接続マネージャー エディター](../cache-connection-manager-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b930-110">For more information, see [Cache Connection Manager Editor](../cache-connection-manager-editor.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2b930-111">パッケージの保護レベルは、キャッシュ ファイルに適用されません。</span><span class="sxs-lookup"><span data-stu-id="2b930-111">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="2b930-112">キャッシュ ファイルに機密情報が含まれている場合は、アクセス制御リスト (ACL) を使用して、ファイルを格納している場所またはフォルダーへのアクセスを制限します。</span><span class="sxs-lookup"><span data-stu-id="2b930-112">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="2b930-113">特定のアカウントに対してのみアクセスを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b930-113">You should enable access only to certain accounts.</span></span> <span data-ttu-id="2b930-114">詳細については、「 [パッケージで使用されるファイルへのアクセス](../access-to-files-used-by-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b930-114">For more information, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
## <a name="configuration-of-the-cache-connection-manager"></a><span data-ttu-id="2b930-115">キャッシュ接続マネージャーの構成</span><span class="sxs-lookup"><span data-stu-id="2b930-115">Configuration of the Cache Connection Manager</span></span>  
 <span data-ttu-id="2b930-116">キャッシュ接続マネージャーは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="2b930-116">You can configure the Cache connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="2b930-117">キャッシュ ファイルを使用するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="2b930-117">Indicate whether to use a cache file.</span></span>  
  
     <span data-ttu-id="2b930-118">キャッシュ ファイルを使用するようにキャッシュ接続マネージャーを構成すると、接続マネージャーは、次のいずれかの処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="2b930-118">If you configure the cache connection manager to use a cache file, the connection manager will do one of the following actions:</span></span>  
  
    -   <span data-ttu-id="2b930-119">データ フロー内のデータ ソースからキャッシュ接続マネージャーにデータが書き込まれるようにキャッシュ変換が構成されている場合は、データをファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="2b930-119">Save data to the file when a Cache Transform transformation is configured to write data from a data source in the data flow to the Cache connection manager.</span></span>  
  
    -   <span data-ttu-id="2b930-120">キャッシュ ファイルからデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="2b930-120">Read data from the cache file.</span></span>  
  
     <span data-ttu-id="2b930-121">詳しくは、「 [Cache Transform](../data-flow/transformations/cache-transform.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2b930-121">For more information, see [Cache Transform](../data-flow/transformations/cache-transform.md).</span></span>  
  
-   <span data-ttu-id="2b930-122">キャッシュに格納されている列のメタデータを変更します。</span><span class="sxs-lookup"><span data-stu-id="2b930-122">Change metadata for the columns stored in the cache.</span></span>  
  
-   <span data-ttu-id="2b930-123">式を使用して ConnectionString プロパティを設定し、実行時にキャッシュ ファイル名を更新します。</span><span class="sxs-lookup"><span data-stu-id="2b930-123">Update the cache file name at runtime by using an expression to set the ConnectionString property.</span></span> <span data-ttu-id="2b930-124">詳細については、「 [パッケージでプロパティ式を使用する](../expressions/use-property-expressions-in-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b930-124">For more information, see [Use Property Expressions in Packages](../expressions/use-property-expressions-in-packages.md).</span></span>  
  
 <span data-ttu-id="2b930-125">プロパティを設定するには [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="2b930-125">You can set properties through [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="2b930-126">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] デザイナーで設定できるプロパティの詳細については、「 [[キャッシュ接続マネージャー エディター] ダイアログ ボックス](../cache-connection-manager-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b930-126">For more information about the properties that you can set in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Designer, see [Cache Connection Manager Editor](../cache-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="2b930-127">プログラムによる接続マネージャーの構成方法については、「<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>」および「[プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b930-127">For information about how to configure a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="2b930-128">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="2b930-128">Related Tasks</span></span>  
 [<span data-ttu-id="2b930-129">キャッシュ接続マネージャーの変換を使用してフル キャッシュ モードの参照変換を実装する</span><span class="sxs-lookup"><span data-stu-id="2b930-129">Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager</span></span>](lookup-transformation-full-cache-mode-ole-db-connection-manager.md)  
  
  
