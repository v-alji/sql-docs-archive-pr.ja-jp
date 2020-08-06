---
title: キャッシュ接続マネージャーエディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.cacheconnection.f1
ms.assetid: 0d8f9324-0c35-4eea-b06d-da3cc2426d2c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 38a858217925496d8dd937d684368bdb2e061b14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644595"
---
# <a name="cache-connection-manager-editor"></a><span data-ttu-id="825ae-102">[キャッシュ接続マネージャー エディター]</span><span class="sxs-lookup"><span data-stu-id="825ae-102">Cache Connection Manager Editor</span></span>
  <span data-ttu-id="825ae-103">キャッシュ接続マネージャーでは、キャッシュ変換またはキャッシュ ファイル (.caw) から参照データセットを読み取り、そのデータをキャッシュ ファイルに保存できます。</span><span class="sxs-lookup"><span data-stu-id="825ae-103">The Cache connection manager reads a reference dataset from the Cache transform or from a cache file (.caw), and can save the data to a cache file.</span></span> <span data-ttu-id="825ae-104">データは常にメモリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="825ae-104">The data is always stored in memory.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="825ae-105">キャッシュ接続マネージャーでは、バイナリ ラージ オブジェクト (BLOB) データ型 DT_TEXT、DT_NTEXT、および DT_IMAGE はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="825ae-105">The Cache connection manager does not support the Binary Large Object (BLOB) data types DT_TEXT, DT_NTEXT, and DT_IMAGE.</span></span> <span data-ttu-id="825ae-106">参照データセットに BLOB データ型が含まれている場合、パッケージを実行するとコンポーネントは失敗します。</span><span class="sxs-lookup"><span data-stu-id="825ae-106">If the reference dataset contains a BLOB data type, the component will fail when you run the package.</span></span> <span data-ttu-id="825ae-107">**[キャッシュ接続マネージャー エディター]** を使用して、列のデータ型を変更できます。</span><span class="sxs-lookup"><span data-stu-id="825ae-107">You can use the **Cache Connection Manager Editor** to modify column data types.</span></span>  
  
 <span data-ttu-id="825ae-108">参照変換は、参照データセットで参照を実行します。</span><span class="sxs-lookup"><span data-stu-id="825ae-108">The Lookup transformation performs lookups on the reference dataset.</span></span>  
  
 <span data-ttu-id="825ae-109">**[キャッシュ接続マネージャー エディター]** ダイアログ ボックスには、次のタブがあります。</span><span class="sxs-lookup"><span data-stu-id="825ae-109">The **Cache Connection ManagerEditor** dialog box includes the following tabs:</span></span>  
  
-   <span data-ttu-id="825ae-110">[[全般] タブ](#generaltab)</span><span class="sxs-lookup"><span data-stu-id="825ae-110">[General tab](#generaltab)</span></span>  
  
-   <span data-ttu-id="825ae-111">[[列] タブ](#columnstab)</span><span class="sxs-lookup"><span data-stu-id="825ae-111">[Columns tab](#columnstab)</span></span>  
  
 <span data-ttu-id="825ae-112">キャッシュ接続マネージャーの詳細については、「 [Cache Connection Manager](connection-manager/cache-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="825ae-112">To learn more about the Cache Connection Manager, see [Cache Connection Manager](connection-manager/cache-connection-manager.md).</span></span>  
  
##  <a name="general-tab"></a><a name="generaltab"></a><span data-ttu-id="825ae-113">[全般] タブ</span><span class="sxs-lookup"><span data-stu-id="825ae-113">General Tab</span></span>  
 <span data-ttu-id="825ae-114">**[キャッシュ接続マネージャー エディター]** ダイアログ ボックスの **[全般]** タブを使用すると、ファイルからキャッシュを読み取るか、キャッシュをファイルに保存するかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="825ae-114">Use the **General** tab of the **Cache Connection ManagerEditor** dialog box to indicate whether to read the cache from a file or save the cache to a file.</span></span>  
  
### <a name="options"></a><span data-ttu-id="825ae-115">Options</span><span class="sxs-lookup"><span data-stu-id="825ae-115">Options</span></span>  
 <span data-ttu-id="825ae-116">**接続マネージャー名**</span><span class="sxs-lookup"><span data-stu-id="825ae-116">**Connection manager name**</span></span>  
 <span data-ttu-id="825ae-117">ワークフローにおけるキャッシュ接続マネージャーの一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="825ae-117">Provide a unique name for the cache connection in the workflow.</span></span> <span data-ttu-id="825ae-118">指定された名前は、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="825ae-118">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="825ae-119">**説明**</span><span class="sxs-lookup"><span data-stu-id="825ae-119">**Description**</span></span>  
 <span data-ttu-id="825ae-120">接続の説明を記述します。</span><span class="sxs-lookup"><span data-stu-id="825ae-120">Describe the connection.</span></span> <span data-ttu-id="825ae-121">パッケージを自己文書化して目的を明確にし、保守が容易になるように、接続の目的に従って記述することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="825ae-121">As a best practice, describe the connection according to its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="825ae-122">**[ファイル キャッシュを使用する]**</span><span class="sxs-lookup"><span data-stu-id="825ae-122">**Use file cache**</span></span>  
 <span data-ttu-id="825ae-123">キャッシュ ファイルを使用するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="825ae-123">Indicate whether to use a cache file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="825ae-124">パッケージの保護レベルは、キャッシュ ファイルに適用されません。</span><span class="sxs-lookup"><span data-stu-id="825ae-124">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="825ae-125">キャッシュ ファイルに機密情報が含まれている場合は、アクセス制御リスト (ACL) を使用して、ファイルを格納している場所またはフォルダーへのアクセスを制限します。</span><span class="sxs-lookup"><span data-stu-id="825ae-125">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="825ae-126">特定のアカウントに対してのみアクセスを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="825ae-126">You should enable access only to certain accounts.</span></span> <span data-ttu-id="825ae-127">詳細については、「 [パッケージで使用されるファイルへのアクセス](../../2014/integration-services/access-to-files-used-by-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="825ae-127">For more information, see [Access to Files Used by Packages](../../2014/integration-services/access-to-files-used-by-packages.md).</span></span>  
  
 <span data-ttu-id="825ae-128">キャッシュ ファイルを使用するようにキャッシュ接続マネージャーを構成すると、接続マネージャーは、次のいずれかの処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="825ae-128">If you configure the cache connection manager to use a cache file, the connection manager will do one of the following actions:</span></span>  
  
-   <span data-ttu-id="825ae-129">データ フロー内のデータ ソースからキャッシュ接続マネージャーにデータが書き込まれるようにキャッシュ変換が構成されている場合は、データをファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="825ae-129">Save data to the file when a Cache Transform transformation is configured to write data from a data source in the data flow to the Cache connection manager.</span></span> <span data-ttu-id="825ae-130">詳しくは、「 [Cache Transform](data-flow/transformations/cache-transform.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="825ae-130">For more information, see [Cache Transform](data-flow/transformations/cache-transform.md).</span></span>  
  
-   <span data-ttu-id="825ae-131">キャッシュ ファイルからデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="825ae-131">Read data from the cache file.</span></span>  
  
 <span data-ttu-id="825ae-132">**[ファイル名]**</span><span class="sxs-lookup"><span data-stu-id="825ae-132">**File name**</span></span>  
 <span data-ttu-id="825ae-133">キャッシュ ファイルのパスと名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="825ae-133">Type the path and file name of the cache file.</span></span>  
  
 <span data-ttu-id="825ae-134">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="825ae-134">**Browse**</span></span>  
 <span data-ttu-id="825ae-135">キャッシュ ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="825ae-135">Locate the cache file.</span></span>  
  
 <span data-ttu-id="825ae-136">**[メタデータの更新]**</span><span class="sxs-lookup"><span data-stu-id="825ae-136">**Refresh Metadata**</span></span>  
 <span data-ttu-id="825ae-137">キャッシュ接続マネージャーで列のメタデータを削除し、選択したキャッシュ ファイルの列のメタデータでキャッシュ接続マネージャーを再設定します。</span><span class="sxs-lookup"><span data-stu-id="825ae-137">Delete the column metadata in the Cache connection manager and repopulate the Cache connection manager with column metadata from a selected cache file.</span></span>  
  
##  <a name="columns-tab"></a><a name="columnstab"></a><span data-ttu-id="825ae-138">[列] タブ</span><span class="sxs-lookup"><span data-stu-id="825ae-138">Columns Tab</span></span>  
 <span data-ttu-id="825ae-139">**[キャッシュ接続マネージャー エディター]** ダイアログ ボックスの **[列]** タブを使用すると、キャッシュ内の各列のプロパティを構成できます。</span><span class="sxs-lookup"><span data-stu-id="825ae-139">Use the **Columns** tab of the **Cache Connection Manager Editor** dialog box to configure the properties of each column in the cache.</span></span>  
  
### <a name="options"></a><span data-ttu-id="825ae-140">Options</span><span class="sxs-lookup"><span data-stu-id="825ae-140">Options</span></span>  
 <span data-ttu-id="825ae-141">**列**</span><span class="sxs-lookup"><span data-stu-id="825ae-141">**Column**</span></span>  
 <span data-ttu-id="825ae-142">列名を指定します。</span><span class="sxs-lookup"><span data-stu-id="825ae-142">Specify the column name.</span></span>  
  
 <span data-ttu-id="825ae-143">**[インデックス位置]**</span><span class="sxs-lookup"><span data-stu-id="825ae-143">**Index Position**</span></span>  
 <span data-ttu-id="825ae-144">各列のインデックス位置を指定して、インデックス列として使用する列を指定します。</span><span class="sxs-lookup"><span data-stu-id="825ae-144">Specify which columns are index columns by specifying the index position of each column.</span></span> <span data-ttu-id="825ae-145">インデックスは 1 つまたは複数の列のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="825ae-145">The index is a collection of one or more columns.</span></span>  
  
 <span data-ttu-id="825ae-146">インデックス以外の列の場合、インデックス位置は 0 です。</span><span class="sxs-lookup"><span data-stu-id="825ae-146">For non-index columns, the index position is 0.</span></span>  
  
 <span data-ttu-id="825ae-147">インデックス列の場合、インデックスの位置は連続した正の数になります。</span><span class="sxs-lookup"><span data-stu-id="825ae-147">For index columns, the index position is a sequential, positive number.</span></span> <span data-ttu-id="825ae-148">この数は、参照変換が参照データセットの行と入力データ ソースの行を比較する順序を示します。</span><span class="sxs-lookup"><span data-stu-id="825ae-148">This number indicates the order in which the Lookup transformation compares rows in the reference dataset to rows in the input data source.</span></span> <span data-ttu-id="825ae-149">最も固有な値を含む列に、最も小さいインデックス位置を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="825ae-149">The column with the most unique values should have the lowest index position.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="825ae-150">参照変換がキャッシュ接続マネージャーを使用するように構成されている場合、参照データセット内のインデックス列のみ入力列にマップできます。</span><span class="sxs-lookup"><span data-stu-id="825ae-150">When the Lookup transformation is configured to use a Cache connection manager, only index columns in the reference dataset can be mapped to input columns.</span></span> <span data-ttu-id="825ae-151">また、すべてのインデックス列をマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="825ae-151">Also, all index columns must be mapped.</span></span>  
  
 <span data-ttu-id="825ae-152">**Type**</span><span class="sxs-lookup"><span data-stu-id="825ae-152">**Type**</span></span>  
 <span data-ttu-id="825ae-153">列のデータ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="825ae-153">Specify the data type of the column.</span></span>  
  
 `Length`  
 <span data-ttu-id="825ae-154">列のデータ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="825ae-154">Specifies the column data type.</span></span> <span data-ttu-id="825ae-155">`Length` は、そのデータ型で使用できる範囲内であれば更新できます。</span><span class="sxs-lookup"><span data-stu-id="825ae-155">If applicable to the data type, you can update `Length`.</span></span>  
  
 `Precision`  
 <span data-ttu-id="825ae-156">特定の列のデータ型の有効桁数を指定します。</span><span class="sxs-lookup"><span data-stu-id="825ae-156">Specifies the precision for certain column data types.</span></span> <span data-ttu-id="825ae-157">precision は、数値全体の桁数です。</span><span class="sxs-lookup"><span data-stu-id="825ae-157">Precision is the number of digits in a number.</span></span> <span data-ttu-id="825ae-158">`Precision` は、そのデータ型で使用できる範囲内であれば更新できます。</span><span class="sxs-lookup"><span data-stu-id="825ae-158">If applicable to the data type, you can update `Precision`.</span></span>  
  
 `Scale`  
 <span data-ttu-id="825ae-159">特定の列のデータ型の小数点以下桁数を指定します。</span><span class="sxs-lookup"><span data-stu-id="825ae-159">Specifies the scale for certain column data types.</span></span> <span data-ttu-id="825ae-160">scale は、数値の中で小数点より右側の桁数です。</span><span class="sxs-lookup"><span data-stu-id="825ae-160">Scale is the number of digits to the right of the decimal point in a number.</span></span> <span data-ttu-id="825ae-161">`Scale` は、そのデータ型で使用できる範囲内であれば更新できます。</span><span class="sxs-lookup"><span data-stu-id="825ae-161">If applicable to the data type, you can update `Scale`.</span></span>  
  
 `Code Page`  
 <span data-ttu-id="825ae-162">列の型のコード ページを指定します。</span><span class="sxs-lookup"><span data-stu-id="825ae-162">Specifies the code page for the column type.</span></span> <span data-ttu-id="825ae-163">`Code Page` は、そのデータ型で使用できる範囲内であれば更新できます。</span><span class="sxs-lookup"><span data-stu-id="825ae-163">If applicable to the data type, you can update `Code Page`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="825ae-164">参照</span><span class="sxs-lookup"><span data-stu-id="825ae-164">See Also</span></span>  
 [<span data-ttu-id="825ae-165">参照変換</span><span class="sxs-lookup"><span data-stu-id="825ae-165">Lookup Transformation</span></span>](data-flow/transformations/lookup-transformation.md)  
  
  
