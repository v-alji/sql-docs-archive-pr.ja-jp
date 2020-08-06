---
title: キャッシュ変換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.cachetrans.f1
helpviewer_keywords:
- Cache transform
ms.assetid: a5683fc8-9c32-4634-819e-e9815627e4f1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 34be3252a3caf344c95e13ae45cc485a8c4ffdc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642209"
---
# <a name="cache-transform"></a><span data-ttu-id="5c290-102">キャッシュ変換</span><span class="sxs-lookup"><span data-stu-id="5c290-102">Cache Transform</span></span>
  <span data-ttu-id="5c290-103">キャッシュ変換は、データ フロー内の接続されているデータ ソースのデータをキャッシュ接続マネージャーに書き込んで、参照変換用の参照データセットを生成します。</span><span class="sxs-lookup"><span data-stu-id="5c290-103">The Cache Transform transformation generates a reference dataset for the Lookup Transformation by writing data from a connected data source in the data flow to a Cache connection manager.</span></span> <span data-ttu-id="5c290-104">参照変換は、接続されているデータ ソースの入力列のデータを参照データベースの列と結合することにより参照を実行します。</span><span class="sxs-lookup"><span data-stu-id="5c290-104">The Lookup transformation performs lookups by joining data in input columns from a connected data source with columns in the reference database.</span></span>  
  
 <span data-ttu-id="5c290-105">参照変換をフル キャッシュ モードで実行するように構成する場合は、キャッシュ接続マネージャーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5c290-105">You can use the Cache connection manager when you want to configure the Lookup Transformation to run in the full cache mode.</span></span> <span data-ttu-id="5c290-106">このモードでは、参照変換の実行前に参照データセットがキャッシュに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="5c290-106">In this mode, the reference dataset is loaded into cache before the Lookup Transformation runs.</span></span>  
  
 <span data-ttu-id="5c290-107">キャッシュ接続マネージャーおよびキャッシュ変換でフル キャッシュ モードの参照変換を構成する手順については、「 [Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager](../../connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md)」(キャッシュ接続マネージャーを使用してフル キャッシュ モードの参照変換を実装する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c290-107">For instructions on how to configure the Lookup transformation in full cache mode with the Cache connection manager and Cache Transform transformation, see [Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager](../../connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="5c290-108">参照データセットのキャッシュの詳細については、「 [Lookup Transformation](lookup-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c290-108">For more information on caching the reference dataset, see [Lookup Transformation](lookup-transformation.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5c290-109">キャッシュ変換では一意の行だけがキャッシュ接続マネージャーに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="5c290-109">The Cache Transform writes only unique rows to the Cache connection manager.</span></span>  
  
 <span data-ttu-id="5c290-110">単一のパッケージ内で同じキャッシュ接続マネージャーにデータを書き込むことができるのは 1 つのキャッシュ変換だけです。</span><span class="sxs-lookup"><span data-stu-id="5c290-110">In a single package, only one Cache Transform can write data to the same Cache connection manager.</span></span> <span data-ttu-id="5c290-111">パッケージに複数のキャッシュ変換が含まれている場合、パッケージが実行されたときに最初に呼び出されたキャッシュ変換が接続マネージャーにデータを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="5c290-111">If the package contains multiple Cache Transforms, the first Cache Transform that is called when the package runs, writes the data to the connection manager.</span></span> <span data-ttu-id="5c290-112">それ以降のキャッシュ変換による書き込み操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="5c290-112">The write operations of subsequent Cache Transforms fail.</span></span>  
  
 <span data-ttu-id="5c290-113">詳細については、「 [Cache Connection Manager](../../connection-manager/cache-connection-manager.md) 」および「 [Cache Connection Manager Editor](../../cache-connection-manager-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c290-113">For more information, see [Cache Connection Manager](../../connection-manager/cache-connection-manager.md) and [Cache Connection Manager Editor](../../cache-connection-manager-editor.md).</span></span>  
  
## <a name="configuration-of-the-cache-transform"></a><span data-ttu-id="5c290-114">キャッシュ変換の構成</span><span class="sxs-lookup"><span data-stu-id="5c290-114">Configuration of the Cache Transform</span></span>  
 <span data-ttu-id="5c290-115">データをキャッシュ ファイル (.caw) に保存するようにキャッシュ接続マネージャーを構成できます。</span><span class="sxs-lookup"><span data-stu-id="5c290-115">You can configure the Cache connection manager to save the data to a cache file (.caw).</span></span>  
  
 <span data-ttu-id="5c290-116">キャッシュ変換は、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="5c290-116">You can configure the Cache Transform in the following ways:</span></span>  
  
-   <span data-ttu-id="5c290-117">キャッシュ接続マネージャーを指定します。</span><span class="sxs-lookup"><span data-stu-id="5c290-117">Specify the Cache connection manager.</span></span>  
  
-   <span data-ttu-id="5c290-118">キャッシュ変換の入力列をキャッシュ接続マネージャーの変換先列にマップします。</span><span class="sxs-lookup"><span data-stu-id="5c290-118">Map the input columns in the Cache Transform to destination columns in the Cache connection manager.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5c290-119">各入力列を変換先列にマップする必要があります。このとき、列のデータ型が一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="5c290-119">Each input column must be mapped to a destination column, and the column data types must match.</span></span> <span data-ttu-id="5c290-120">それ以外の場合、 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] デザイナーによりエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5c290-120">Otherwise, [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] Designer displays an error message.</span></span>  
  
     <span data-ttu-id="5c290-121">**[キャッシュ接続マネージャー エディター]** を使用して、列のデータ型、名前、およびその他の列プロパティを変更できます。</span><span class="sxs-lookup"><span data-stu-id="5c290-121">You can use the **Cache Connection Manager Editor** to modify column data types, names, and other column properties.</span></span>  
  
 <span data-ttu-id="5c290-122">プロパティは、 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] デザイナーから設定できます。</span><span class="sxs-lookup"><span data-stu-id="5c290-122">You can set properties through [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] Designer.</span></span> <span data-ttu-id="5c290-123">**[詳細エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、「 [Transformation Custom Properties](transformation-custom-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c290-123">For more information about the properties that you can set in the **Advanced Editor** dialog box, see [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="5c290-124">プロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](../set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c290-124">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c290-125">参照</span><span class="sxs-lookup"><span data-stu-id="5c290-125">See Also</span></span>  
 <span data-ttu-id="5c290-126">[Integration Services の変換](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="5c290-126">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 [<span data-ttu-id="5c290-127">データ フロー</span><span class="sxs-lookup"><span data-stu-id="5c290-127">Data Flow</span></span>](../data-flow.md)  
  
  
