---
title: 参照変換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptrans.f1
helpviewer_keywords:
- Lookup transformation
- joining columns [Integration Services]
- cache [Integration Services]
- match exactly [Integration Services]
- lookups [Integration Services]
- exact matches [Integration Services]
ms.assetid: de1cc8de-e7af-4727-b5a5-a1f0a739aa09
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 567c5d95c2ee7c15ea5c541f7fe2010d46ba36f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644057"
---
# <a name="lookup-transformation"></a><span data-ttu-id="6da8c-102">参照変換</span><span class="sxs-lookup"><span data-stu-id="6da8c-102">Lookup Transformation</span></span>
  <span data-ttu-id="6da8c-103">参照変換は、入力列のデータを参照データセットの列と結合することにより参照を実行します。</span><span class="sxs-lookup"><span data-stu-id="6da8c-103">The Lookup transformation performs lookups by joining data in input columns with columns in a reference dataset.</span></span> <span data-ttu-id="6da8c-104">参照を使用すると、共通の列の値に基づいている関連テーブル内の追加情報にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-104">You use the lookup to access additional information in a related table that is based on values in common columns.</span></span>  
  
 <span data-ttu-id="6da8c-105">参照データセットは、キャッシュ ファイル、既存のテーブル、既存のビュー、新しいテーブル、または SQL クエリの結果のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="6da8c-105">The reference dataset can be a cache file, an existing table or view, a new table, or the result of an SQL query.</span></span> <span data-ttu-id="6da8c-106">参照変換では、OLE DB 接続マネージャーまたはキャッシュ接続マネージャーを使用して、参照データセットに接続します。</span><span class="sxs-lookup"><span data-stu-id="6da8c-106">The Lookup transformation uses either an OLE DB connection manager or a Cache connection manager to connect to the reference dataset.</span></span> <span data-ttu-id="6da8c-107">詳細については、「 [OLE DB 接続マネージャー](../../connection-manager/ole-db-connection-manager.md) 」および「 [キャッシュ接続マネージャー](../../connection-manager/cache-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6da8c-107">For more information, see [OLE DB Connection Manager](../../connection-manager/ole-db-connection-manager.md) and [Cache Connection Manager](../../connection-manager/cache-connection-manager.md)</span></span>  
  
 <span data-ttu-id="6da8c-108">参照変換は、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-108">You can configure the Lookup transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="6da8c-109">使用する接続マネージャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="6da8c-109">Select the connection manager that you want to use.</span></span> <span data-ttu-id="6da8c-110">データベースに接続する場合は、OLE DB 接続マネージャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="6da8c-110">If you want to connect to a database, select an OLE DB connection manager.</span></span> <span data-ttu-id="6da8c-111">キャッシュ ファイルに接続する場合は、キャッシュ接続マネージャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="6da8c-111">If you want to connect to a cache file, select a Cache connection manager.</span></span>  
  
-   <span data-ttu-id="6da8c-112">参照データセットを含むテーブルまたはビューを指定します。</span><span class="sxs-lookup"><span data-stu-id="6da8c-112">Specify the table or view that contains the reference dataset.</span></span>  
  
-   <span data-ttu-id="6da8c-113">SQL ステートメントを指定して、参照データセットを生成します。</span><span class="sxs-lookup"><span data-stu-id="6da8c-113">Generate a reference dataset by specifying an SQL statement.</span></span>  
  
-   <span data-ttu-id="6da8c-114">入力と参照データセット間の結合を指定します。</span><span class="sxs-lookup"><span data-stu-id="6da8c-114">Specify joins between the input and the reference dataset.</span></span>  
  
-   <span data-ttu-id="6da8c-115">参照データセットの列を参照変換の出力に追加します。</span><span class="sxs-lookup"><span data-stu-id="6da8c-115">Add columns from the reference dataset to the Lookup transformation output.</span></span>  
  
-   <span data-ttu-id="6da8c-116">キャッシュ オプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="6da8c-116">Configure the caching options.</span></span>  
  
 <span data-ttu-id="6da8c-117">参照変換では、OLE DB 接続マネージャー用に次のデータベース プロバイダーをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="6da8c-117">The Lookup transformation supports the following database providers for the OLE DB connection manager:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
-   <span data-ttu-id="6da8c-118">Oracle</span><span class="sxs-lookup"><span data-stu-id="6da8c-118">Oracle</span></span>  
  
-   <span data-ttu-id="6da8c-119">DB2</span><span class="sxs-lookup"><span data-stu-id="6da8c-119">DB2</span></span>  
  
 <span data-ttu-id="6da8c-120">参照変換は、変換入力の値と参照データセットの値の間で等結合を実行しようとします。</span><span class="sxs-lookup"><span data-stu-id="6da8c-120">The Lookup transformation tries to perform an equi-join between values in the transformation input and values in the reference dataset.</span></span> <span data-ttu-id="6da8c-121">等結合の場合、変換入力の各行は、参照データセットの少なくとも 1 行と一致する必要があります。等結合を行うことができない場合、参照変換で次のいずれかの処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-121">(An equi-join means that each row in the transformation input must match at least one row from the reference dataset.) If an equi-join is not possible, the Lookup transformation takes one of the following actions:</span></span>  
  
-   <span data-ttu-id="6da8c-122">参照データセット内に一致するエントリがない場合、結合は行われません。</span><span class="sxs-lookup"><span data-stu-id="6da8c-122">If there is no matching entry in the reference dataset, no join occurs.</span></span> <span data-ttu-id="6da8c-123">既定では、参照変換で一致するエントリがない行は、エラーとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-123">By default, the Lookup transformation treats rows without matching entries as errors.</span></span> <span data-ttu-id="6da8c-124">ただし、それらの行を不一致出力にリダイレクトするように参照変換を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-124">However, you can configure the Lookup transformation to redirect such rows to a no match output.</span></span> <span data-ttu-id="6da8c-125">詳細については、「[[参照変換エディター] &#40;[全般] ページ&#41;](../../lookup-transformation-editor-general-page.md)」および「[[参照変換エディター] &#40;[エラー出力] ページ&#41;](../../lookup-transformation-editor-error-output-page.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6da8c-125">For more information, see [Lookup Transformation Editor &#40;General Page&#41;](../../lookup-transformation-editor-general-page.md) and [Lookup Transformation Editor &#40;Error Output Page&#41;](../../lookup-transformation-editor-error-output-page.md).</span></span>  
  
-   <span data-ttu-id="6da8c-126">参照テーブル内の複数のエントリが一致する場合、参照クエリから最初に返されたエントリのみが返されます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-126">If there are multiple matches in the reference table, the Lookup transformation returns only the first match returned by the lookup query.</span></span> <span data-ttu-id="6da8c-127">複数のエントリが一致する場合、すべての参照データセットをキャッシュに読み込むように参照変換が構成されているときだけ、エラーまたは警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-127">If multiple matches are found, the Lookup transformation generates an error or warning only when the transformation has been configured to load all the reference dataset into the cache.</span></span> <span data-ttu-id="6da8c-128">この場合、参照変換によってデータセットがキャッシュに読み込まれたときに複数の一致エントリが検出されると、警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-128">In this case, the Lookup transformation generates a warning when the transformation detects multiple matches as the transformation fills the cache.</span></span>  
  
 <span data-ttu-id="6da8c-129">複合結合の場合、変換入力の複数の列を参照データセットの列に結合できます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-129">The join can be a composite join, which means that you can join multiple columns in the transformation input to columns in the reference dataset.</span></span> <span data-ttu-id="6da8c-130">この変換では、DT_R4、DT_R8、DT_TEXT、DT_NTEXT、または DT_IMAGE データ型以外のすべてのデータ型の列を結合できます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-130">The transformation supports join columns with any data type, except for DT_R4, DT_R8, DT_TEXT, DT_NTEXT, or DT_IMAGE.</span></span> <span data-ttu-id="6da8c-131">詳細については、「 [Integration Services Data Types](../integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6da8c-131">For more information, see [Integration Services Data Types](../integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="6da8c-132">通常、参照データセットの値が、変換出力に追加されます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-132">Typically, values from the reference dataset are added to the transformation output.</span></span> <span data-ttu-id="6da8c-133">たとえば、参照変換により、入力列の値を使用してテーブルから製品名を抽出し、製品名を変換出力に追加できます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-133">For example, the Lookup transformation can extract a product name from a table using a value from an input column, and then add the product name to the transformation output.</span></span> <span data-ttu-id="6da8c-134">参照テーブルの値によって列の値を置換したり、値を新しい列に追加できます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-134">The values from the reference table can replace column values or can be added to new columns.</span></span>  
  
 <span data-ttu-id="6da8c-135">参照変換が実行する参照では、大文字と小文字は区別されます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-135">The lookups performed by the Lookup transformation are case sensitive.</span></span> <span data-ttu-id="6da8c-136">データ内の大文字/小文字の相違が原因で参照が失敗するのを回避するために、最初に文字マップ変換を使用して、データを大文字または小文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="6da8c-136">To avoid lookup failures that are caused by case differences in data, first use the Character Map transformation to convert the data to uppercase or lowercase.</span></span> <span data-ttu-id="6da8c-137">次に、参照テーブルを生成する SQL ステートメント内で UPPER 関数または LOWER 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="6da8c-137">Then, include the UPPER or LOWER functions in the SQL statement that generates the reference table.</span></span> <span data-ttu-id="6da8c-138">詳細については、「[Character Map Transformation](character-map-transformation.md)」(文字マップ変換)、「[UPPER &#40;Transact-SQL&#41;](/sql/t-sql/functions/upper-transact-sql)」、および「[LOWER &#40;Transact-SQL&#41;](/sql/t-sql/functions/lower-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6da8c-138">For more information, see [Character Map Transformation](character-map-transformation.md), [UPPER &#40;Transact-SQL&#41;](/sql/t-sql/functions/upper-transact-sql), and [LOWER &#40;Transact-SQL&#41;](/sql/t-sql/functions/lower-transact-sql).</span></span>  
  
 <span data-ttu-id="6da8c-139">参照変換の入力と出力を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6da8c-139">The Lookup transformation has the following inputs and outputs:</span></span>  
  
-   <span data-ttu-id="6da8c-140">入力。</span><span class="sxs-lookup"><span data-stu-id="6da8c-140">Input.</span></span>  
  
-   <span data-ttu-id="6da8c-141">一致出力。</span><span class="sxs-lookup"><span data-stu-id="6da8c-141">Match output.</span></span> <span data-ttu-id="6da8c-142">一致出力は、参照データセット内の 1 つ以上のエントリと一致した変換入力内の行を処理します。</span><span class="sxs-lookup"><span data-stu-id="6da8c-142">The match output handles the rows in the transformation input that match at least one entry in the reference dataset.</span></span>  
  
-   <span data-ttu-id="6da8c-143">不一致出力。</span><span class="sxs-lookup"><span data-stu-id="6da8c-143">No Match output.</span></span> <span data-ttu-id="6da8c-144">不一致出力は、参照データセット内の 1 つ以上のエントリと一致しない入力内の行を処理します。</span><span class="sxs-lookup"><span data-stu-id="6da8c-144">The no match output handles rows in the input that do not match at least one entry in the reference dataset.</span></span> <span data-ttu-id="6da8c-145">一致エントリがない行をエラーとして扱うように参照変換を構成している場合、これらの行はエラー出力にリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-145">If you configure the Lookup transformation to treat the rows without matching entries as errors, the rows are redirected to the error output.</span></span> <span data-ttu-id="6da8c-146">それ以外の場合、これらの行は不一致出力にリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-146">Otherwise, the transformation would redirect those rows to the no match output.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6da8c-147">[!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)] の参照変換の出力は 1 つだけでした。</span><span class="sxs-lookup"><span data-stu-id="6da8c-147">In [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)], the Lookup transformation had only one output.</span></span> <span data-ttu-id="6da8c-148">で作成された参照変換を実行する方法の詳細について [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] は、「参照[変換のアップグレード](../../../sql-server/install/upgrade-lookup-transformations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6da8c-148">For more information about how to run a Lookup transformation that was created in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], see [Upgrade Lookup Transformations](../../../sql-server/install/upgrade-lookup-transformations.md).</span></span>  
  
-   <span data-ttu-id="6da8c-149">エラー出力。</span><span class="sxs-lookup"><span data-stu-id="6da8c-149">Error output.</span></span>  
  
## <a name="caching-the-reference-dataset"></a><span data-ttu-id="6da8c-150">参照データセットのキャッシュ</span><span class="sxs-lookup"><span data-stu-id="6da8c-150">Caching the Reference Dataset</span></span>  
 <span data-ttu-id="6da8c-151">インメモリ キャッシュは、参照データセットを格納し、データのインデックスを作成するハッシュ テーブルを格納します。</span><span class="sxs-lookup"><span data-stu-id="6da8c-151">An in-memory cache stores the reference dataset and stores a hash table that indexes the data.</span></span> <span data-ttu-id="6da8c-152">キャッシュは、パッケージの実行が完了するまでメモリ内に保持されます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-152">The cache remains in memory until the execution of the package is completed.</span></span> <span data-ttu-id="6da8c-153">キャッシュはキャッシュ ファイル (.caw) に永続化できます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-153">You can persist the cache to a cache file (.caw).</span></span>  
  
 <span data-ttu-id="6da8c-154">キャッシュをファイルに永続化すると、システムによるキャッシュの読み込みが高速化されます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-154">When you persist the cache to a file, the system loads the cache faster.</span></span> <span data-ttu-id="6da8c-155">これにより、参照変換とパッケージのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="6da8c-155">This improves the performance of the Lookup transformation and the package.</span></span> <span data-ttu-id="6da8c-156">キャッシュ ファイルを使用する場合は、データベース内にあるデータの最新の状態が反映されていないデータを操作していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6da8c-156">Remember, that when you use a cache file, you are working with data that is not as current as the data in the database.</span></span>  
  
 <span data-ttu-id="6da8c-157">キャッシュをファイルに永続化する他の利点を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6da8c-157">The following are additional benefits of persisting the cache to a file:</span></span>  
  
-   <span data-ttu-id="6da8c-158">***複数のパッケージ間でキャッシュ ファイルを共有できます。詳細については、「***  [キャッシュ接続マネージャーの変換を使用してフル キャッシュ モードの参照変換を実装する](../../connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md)  ***」をご覧ください。***</span><span class="sxs-lookup"><span data-stu-id="6da8c-158">***Share the cache file between multiple packages. For more information, see***  [Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager](../../connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md)  ***.***</span></span>  
  
-   <span data-ttu-id="6da8c-159">キャッシュ ファイルをパッケージと一緒に配置できます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-159">Deploy the cache file with a package.</span></span> <span data-ttu-id="6da8c-160">***これにより、このデータを複数のコンピューター上で使用できます。***</span><span class="sxs-lookup"><span data-stu-id="6da8c-160">***You can then use the data on multiple computers.***</span></span> <span data-ttu-id="6da8c-161">詳細については、「 [参照変換用のキャッシュを作成および配置する](create-and-deploy-a-cache-for-the-lookup-transformation.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6da8c-161">For more information, see [Create and Deploy a Cache for the Lookup Transformation](create-and-deploy-a-cache-for-the-lookup-transformation.md).</span></span>  
  
-   <span data-ttu-id="6da8c-162">RAW ファイル ソースを使用してキャッシュ ファイルからデータを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-162">Use the Raw File source to read data from the cache file.</span></span> <span data-ttu-id="6da8c-163">次に他のデータ フロー コンポーネントを使用してデータを変換または移動できます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-163">You can then use other data flow components to transform or move the data.</span></span> <span data-ttu-id="6da8c-164">詳細については、「 [RAW ファイル ソース](../raw-file-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6da8c-164">For more information, see [Raw File Source](../raw-file-source.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6da8c-165">キャッシュ接続マネージャーは、RAW ファイル変換先を使用して作成または変更されたキャッシュ ファイルをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="6da8c-165">The Cache connection manager does not support cache files that are created or modified by using the Raw File destination.</span></span>  
  
-   <span data-ttu-id="6da8c-166">ファイル システム タスクを使用して、キャッシュ ファイルに対して処理を実行したり属性を設定したりできます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-166">Perform operations and set attributes on the cache file by using the File System task.</span></span> <span data-ttu-id="6da8c-167">詳細については、「 [ファイル システム タスク](../../control-flow/file-system-task.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6da8c-167">For more information, see and [File System Task](../../control-flow/file-system-task.md).</span></span>  
  
 <span data-ttu-id="6da8c-168">キャッシュのオプションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="6da8c-168">The following are the caching options:</span></span>  
  
-   <span data-ttu-id="6da8c-169">参照データセットは、テーブル、ビュー、または SQL クエリを使用して生成され、参照変換が実行される前にキャッシュに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-169">The reference dataset is generated by using a table, view, or SQL query and loaded into cache, before the Lookup transformation runs.</span></span> <span data-ttu-id="6da8c-170">OLE DB 接続マネージャーを使用して、データセットにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="6da8c-170">You use the OLE DB connection manager to access the dataset.</span></span>  
  
     <span data-ttu-id="6da8c-171">このキャッシュ オプションは、 [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)]の参照変換に用意されているフル キャッシュ オプションと互換性があります。</span><span class="sxs-lookup"><span data-stu-id="6da8c-171">This caching option is compatible with the full caching option that is available for the Lookup transformation in [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)].</span></span>  
  
-   <span data-ttu-id="6da8c-172">参照データセットは、データ フロー内の接続されているデータ ソースまたはキャッシュ ファイルから生成され、参照変換の実行前にキャッシュに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-172">The reference dataset is generated from a connected data source in the data flow or from a cache file, and is loaded into cache before the Lookup transformation runs.</span></span> <span data-ttu-id="6da8c-173">キャッシュ接続マネージャー (および必要に応じてキャッシュ変換) を使用して、データセットにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="6da8c-173">You use the Cache connection manager, and, optionally, the Cache transformation, to access the dataset.</span></span> <span data-ttu-id="6da8c-174">詳細については、「 [キャッシュ接続マネージャー](../../connection-manager/cache-connection-manager.md) 」および「 [キャッシュ変換](cache-transform.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6da8c-174">For more information, see [Cache Connection Manager](../../connection-manager/cache-connection-manager.md) and [Cache Transform](cache-transform.md).</span></span>  
  
-   <span data-ttu-id="6da8c-175">参照データセットは、参照変換の実行時に、テーブル、ビュー、または SQL クエリを使用して生成されます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-175">The reference dataset is generated by using a table, view, or SQL query during the execution of the Lookup transformation.</span></span> <span data-ttu-id="6da8c-176">参照データセットに一致するエントリがある行、およびデータセットに一致するエントリがない行がキャッシュに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-176">The rows with matching entries in the reference dataset and the rows without matching entries in the dataset are loaded into cache.</span></span>  
  
     <span data-ttu-id="6da8c-177">キャッシュのメモリ サイズを超えると、使用頻度の最も低い行が、参照変換によって自動的にキャッシュから削除されます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-177">When the memory size of the cache is exceeded, the Lookup transformation automatically removes the least frequently used rows from the cache.</span></span>  
  
     <span data-ttu-id="6da8c-178">このキャッシュ オプションは、 [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)]の参照変換に用意されている部分キャッシュ オプションと互換性があります。</span><span class="sxs-lookup"><span data-stu-id="6da8c-178">This caching option is compatible with the partial caching option that is available for the Lookup transformation in [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)].</span></span>  
  
-   <span data-ttu-id="6da8c-179">参照データセットは、参照変換の実行時に、テーブル、ビュー、または SQL クエリを使用して生成されます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-179">The reference dataset is generated by using a table, view, or SQL query during the execution of the Lookup transformation.</span></span> <span data-ttu-id="6da8c-180">データはキャッシュされません。</span><span class="sxs-lookup"><span data-stu-id="6da8c-180">No data is cached.</span></span>  
  
     <span data-ttu-id="6da8c-181">このキャッシュ オプションは、 [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)]の参照変換に用意されているキャッシュなしオプションと互換性があります。</span><span class="sxs-lookup"><span data-stu-id="6da8c-181">This caching option is compatible with the no caching option that is available for the Lookup transformation in [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)].</span></span>  
  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="6da8c-182">と [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、文字列の比較方法が異なります。</span><span class="sxs-lookup"><span data-stu-id="6da8c-182">and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] differ in the way they compare strings.</span></span> <span data-ttu-id="6da8c-183">実行前に参照データセットをキャッシュに読み込むように参照変換が構成されている場合、 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] によりキャッシュ内で参照比較が行われます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-183">If the Lookup transformation is configured to load the reference dataset into cache before the Lookup transformation runs, [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] does the lookup comparison in the cache.</span></span> <span data-ttu-id="6da8c-184">それ以外の場合、参照操作でパラメーター化 SQL ステートメントが使用され、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] により参照比較が行われます。</span><span class="sxs-lookup"><span data-stu-id="6da8c-184">Otherwise, the lookup operation uses a parameterized SQL statement and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does the lookup comparison.</span></span> <span data-ttu-id="6da8c-185">つまり、キャッシュの種類に応じて、参照変換が、同じ参照テーブルから異なる数の一致結果を返す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6da8c-185">This means that the Lookup transformation might return a different number of matches from the same lookup table depending on the cache type.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="6da8c-186">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="6da8c-186">Related Tasks</span></span>  
 <span data-ttu-id="6da8c-187">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="6da8c-187">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span> <span data-ttu-id="6da8c-188">詳細については、以下のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6da8c-188">For more details, see the following topics.</span></span>  
  
-   [<span data-ttu-id="6da8c-189">キャッシュなしモードまたは部分キャッシュ モードの参照を実装する</span><span class="sxs-lookup"><span data-stu-id="6da8c-189">Implement a Lookup in No Cache or Partial Cache Mode</span></span>](implement-a-lookup-in-no-cache-or-partial-cache-mode.md)  
  
-   [<span data-ttu-id="6da8c-190">キャッシュ接続マネージャーの変換を使用してフル キャッシュ モードの参照変換を実装する</span><span class="sxs-lookup"><span data-stu-id="6da8c-190">Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager</span></span>](../../connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md)  
  
-   [<span data-ttu-id="6da8c-191">OLE DB 接続マネージャーを使用してフル キャッシュ モードの参照変換を実装する</span><span class="sxs-lookup"><span data-stu-id="6da8c-191">Implement a Lookup Transformation in Full Cache Mode Using the OLE DB Connection Manager</span></span>](../../connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md)  
  
-   [<span data-ttu-id="6da8c-192">データ フロー コンポーネントのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="6da8c-192">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a><span data-ttu-id="6da8c-193">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="6da8c-193">Related Content</span></span>  
  
-   <span data-ttu-id="6da8c-194">msdn.microsoft.com のビデオ「 [フル キャッシュ モードで参照変換を実装する方法](https://go.microsoft.com/fwlink/?LinkId=131031)」</span><span class="sxs-lookup"><span data-stu-id="6da8c-194">Video, [How to: Implement a Lookup Transformation in Full Cache Mode](https://go.microsoft.com/fwlink/?LinkId=131031), on msdn.microsoft.com</span></span>  
  
-   <span data-ttu-id="6da8c-195">blogs.msdn.com のブログ「 [参照変換のキャッシュ モードを使用する際の推奨事項](https://go.microsoft.com/fwlink/?LinkId=146623)」</span><span class="sxs-lookup"><span data-stu-id="6da8c-195">Blog entry, [Best Practices for Using the Lookup Transformation Cache Modes](https://go.microsoft.com/fwlink/?LinkId=146623), on blogs.msdn.com</span></span>  
  
-   <span data-ttu-id="6da8c-196">blogs.msdn.com のブログ「 [参照パターン : 大文字と小文字を区別しない](https://go.microsoft.com/fwlink/?LinkId=157782)」</span><span class="sxs-lookup"><span data-stu-id="6da8c-196">Blog entry, [Lookup Pattern: Case Insensitive](https://go.microsoft.com/fwlink/?LinkId=157782), on blogs.msdn.com</span></span>  
  
-   <span data-ttu-id="6da8c-197">msftisprodsamples.codeplex.com のサンプル「 [参照変換](https://go.microsoft.com/fwlink/?LinkId=267528)」</span><span class="sxs-lookup"><span data-stu-id="6da8c-197">Sample, [Lookup Transformation](https://go.microsoft.com/fwlink/?LinkId=267528), on msftisprodsamples.codeplex.com.</span></span>  
  
     <span data-ttu-id="6da8c-198">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 製品サンプルとサンプル データベースのインストールの詳細については、「 [SQL Server Integration Services 製品サンプル](https://go.microsoft.com/fwlink/?LinkId=267527)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6da8c-198">For information on installing [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] product samples and sample databases, see [SQL Server Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=267527).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6da8c-199">参照</span><span class="sxs-lookup"><span data-stu-id="6da8c-199">See Also</span></span>  
 <span data-ttu-id="6da8c-200">[あいまい参照変換](fuzzy-lookup-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="6da8c-200">[Fuzzy Lookup Transformation](fuzzy-lookup-transformation.md) </span></span>  
 <span data-ttu-id="6da8c-201">[用語参照変換](term-lookup-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="6da8c-201">[Term Lookup Transformation](term-lookup-transformation.md) </span></span>  
 <span data-ttu-id="6da8c-202">[データ フロー](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="6da8c-202">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="6da8c-203">Integration Services の変換</span><span class="sxs-lookup"><span data-stu-id="6da8c-203">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
