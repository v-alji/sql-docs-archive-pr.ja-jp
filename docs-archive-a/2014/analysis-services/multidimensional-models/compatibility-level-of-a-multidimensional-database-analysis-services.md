---
title: 多次元データベースの互換性レベルの設定 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 978279e6-a581-4184-af9d-8701b9826a89
author: minewiskan
ms.author: owend
ms.openlocfilehash: eea3d522abc5133e759cf476f3b169fd570b196f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737122"
---
# <a name="set-the-compatibility-level-of-a-multidimensional-database-analysis-services"></a><span data-ttu-id="adf01-102">多次元データベースの互換性レベルの設定 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="adf01-102">Set the Compatibility Level of a Multidimensional Database (Analysis Services)</span></span>
  <span data-ttu-id="adf01-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]では、データベース互換性レベル プロパティによって、データベースの機能レベルが決定されます。</span><span class="sxs-lookup"><span data-stu-id="adf01-103">In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the database compatibility level property determines the functional level of a database.</span></span> <span data-ttu-id="adf01-104">互換性レベルは、各モデルの種類に固有です。</span><span class="sxs-lookup"><span data-stu-id="adf01-104">Compatibility levels are unique to each model type.</span></span> <span data-ttu-id="adf01-105">たとえば、の互換性レベルは、 `1100` データベースが多次元か表形式かによって異なる意味を持ちます。</span><span class="sxs-lookup"><span data-stu-id="adf01-105">For example, a compatibility level of `1100` has a different meaning depending on whether the database is multidimensional or tabular.</span></span>  
  
 <span data-ttu-id="adf01-106">このトピックでは、多次元データベースの互換性レベルについてのみ説明します。</span><span class="sxs-lookup"><span data-stu-id="adf01-106">This topic describes compatibility level for multidimensional databases only.</span></span> <span data-ttu-id="adf01-107">表形式ソリューションの詳細については、「[互換性レベル &#40;SSAS 表形式 SP1&#41;](../tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="adf01-107">For more information about tabular solutions, see [Compatibility Level &#40;SSAS Tabular SP1&#41;](../tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="adf01-108">表形式モデルには、多次元モデルに適用できないデータベース互換性レベルが存在します。</span><span class="sxs-lookup"><span data-stu-id="adf01-108">Tabular models have additional database compatibility levels that are not applicable to multidimensional models.</span></span> <span data-ttu-id="adf01-109">互換性レベル `1103` は、多次元モデルには存在しません。</span><span class="sxs-lookup"><span data-stu-id="adf01-109">Compatibility level `1103` does not exist for multidimensional models.</span></span> <span data-ttu-id="adf01-110">表形式ソリューションの詳細について[は、SQL Server 2012 SP1 および互換性レベルの表形式モデルの新機能](https://go.microsoft.com/fwlink/?LinkId=301727)を参照してください `1103` 。</span><span class="sxs-lookup"><span data-stu-id="adf01-110">See [What is new for the Tabular model in SQL Server 2012 SP1 and compatibility level](https://go.microsoft.com/fwlink/?LinkId=301727) for more information about `1103` for tabular solutions.</span></span>  
  
 <span data-ttu-id="adf01-111">**多次元データベースの互換性レベル**</span><span class="sxs-lookup"><span data-stu-id="adf01-111">**Compatibility Levels for multidimensional databases**</span></span>  
  
 <span data-ttu-id="adf01-112">現在、機能レベルによって異なる多次元データベースの動作は、文字列ストレージ アーキテクチャのみです。</span><span class="sxs-lookup"><span data-stu-id="adf01-112">Currently, the only multidimensional database behavior that varies by functional level is string storage architecture.</span></span> <span data-ttu-id="adf01-113">データベースの互換性レベルを高くすることで、メジャーとディメンションの文字列ストレージの上限である 4 GB をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="adf01-113">By raising the database compatibility level, you can override the 4 gigabyte maximum limit for string storage of measures and dimensions.</span></span>  
  
 <span data-ttu-id="adf01-114">多次元データベースの `CompatibilityLevel` プロパティの有効値を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="adf01-114">For a multidimensional database, valid values for the `CompatibilityLevel` property include the following:</span></span>  
  
|<span data-ttu-id="adf01-115">設定</span><span class="sxs-lookup"><span data-stu-id="adf01-115">Setting</span></span>|<span data-ttu-id="adf01-116">説明</span><span class="sxs-lookup"><span data-stu-id="adf01-116">Description</span></span>|  
|-------------|-----------------|  
|`1050`|<span data-ttu-id="adf01-117">この値はスクリプトやツールには表示されませんが、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、または [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]で作成されたデータベースを表します。</span><span class="sxs-lookup"><span data-stu-id="adf01-117">This value is not visible in script or tools, but it corresponds to databases created in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], or [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="adf01-118">`CompatibilityLevel` が明示的に設定されていないデータベースはすべて、暗黙的に `1050` レベルで実行されます。</span><span class="sxs-lookup"><span data-stu-id="adf01-118">Any database that does not have `CompatibilityLevel` explicitly set is implicitly running at the `1050` level.</span></span>|  
|`1100`|<span data-ttu-id="adf01-119">これは、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]で作成した新しいデータベースの既定値です。</span><span class="sxs-lookup"><span data-stu-id="adf01-119">This is the default value for new databases that you create in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] or [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="adf01-120">また、この値を以前のバージョンの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で作成されたデータベースに指定すると、この互換性レベルでのみサポートされている機能 (つまり、文字列データを含むディメンション属性や個別のカウント メジャーの大きくなった文字列ストレージ) を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="adf01-120">You can also specify it for databases created in earlier versions of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to enable the use of features that are supported only at this compatibility level (namely, increased string storage for dimension attributes or distinct count measures that contain string data).</span></span><br /><br /> <span data-ttu-id="adf01-121">データベースには、 `CompatibilityLevel` 追加のプロパティが設定されてい `1100` `StringStoresCompatibilityLevel` ます。これにより、パーティションおよびディメンションの代替文字列ストレージを選択できます。</span><span class="sxs-lookup"><span data-stu-id="adf01-121">Databases that have a `CompatibilityLevel` set to `1100` get an additional property, `StringStoresCompatibilityLevel`, that lets you choose alternative string storage for partitions and dimensions.</span></span>|  
  
> [!WARNING]  
>  <span data-ttu-id="adf01-122">高いレベルに設定したデータベース互換性は元に戻せません。</span><span class="sxs-lookup"><span data-stu-id="adf01-122">Setting the database compatibility to a higher level is irreversible.</span></span> <span data-ttu-id="adf01-123">互換性レベルをに上げた後は `1100` 、データベースを新しいサーバーで実行し続ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="adf01-123">After you increase the compatibility level to `1100`, you must continue to run the database on newer servers.</span></span> <span data-ttu-id="adf01-124">にロールバックすることはできません `1050` 。</span><span class="sxs-lookup"><span data-stu-id="adf01-124">You cannot rollback to `1050`.</span></span> <span data-ttu-id="adf01-125">`1100`またはより前のサーバーのバージョンでは、データベースをアタッチまたは復元することはできません [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="adf01-125">You cannot attach or restore an `1100` database on a server version that is earlier than [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] or [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="adf01-126">前提条件</span><span class="sxs-lookup"><span data-stu-id="adf01-126">Prerequisites</span></span>  
 <span data-ttu-id="adf01-127">データベース互換性レベルは、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]で導入されました。</span><span class="sxs-lookup"><span data-stu-id="adf01-127">Database compatibility levels are introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span> <span data-ttu-id="adf01-128">データベース互換性レベルを表示または設定するには、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="adf01-128">You must have [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] or higher to view or set the database compatibility level.</span></span>  
  
 <span data-ttu-id="adf01-129">データベースをローカル キューブにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="adf01-129">The database cannot be a local cube.</span></span> <span data-ttu-id="adf01-130">ローカル キューブでは、`CompatibilityLevel` プロパティがサポートされません。</span><span class="sxs-lookup"><span data-stu-id="adf01-130">Local cubes do not support the `CompatibilityLevel` property.</span></span>  
  
 <span data-ttu-id="adf01-131">データベースは、以前のリリース (SQL Server 2008 R2 以前) で作成され、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 以降のサーバーにアタッチまたは復元されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="adf01-131">The database must have been created in a previous release (SQL Server 2008 R2 or earlier) and then attached or restored to a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] or higher server.</span></span> <span data-ttu-id="adf01-132">SQL Server 2012 に配置されたデータベースは既に `1100` であり、ダウングレードして低いレベルで実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="adf01-132">Databases deployed to SQL Server 2012 are already at `1100` and cannot be downgraded to run at a lower level.</span></span>  
  
## <a name="determine-the-existing-database-compatibility-level-for-a-multidimensional-database"></a><span data-ttu-id="adf01-133">多次元データベースの既存のデータベース互換性レベルの確認</span><span class="sxs-lookup"><span data-stu-id="adf01-133">Determine the existing database compatibility level for a multidimensional database</span></span>  
 <span data-ttu-id="adf01-134">データベース互換性レベルを表示または変更するには、XMLA を使用するしかありません。</span><span class="sxs-lookup"><span data-stu-id="adf01-134">The only way to view or modify the database compatibility level is through XMLA.</span></span> <span data-ttu-id="adf01-135">データベースを指定する XMLA スクリプトは、SQL Server Management Studio で表示または変更できます。</span><span class="sxs-lookup"><span data-stu-id="adf01-135">You can view or modify the XMLA script that specifies your database in SQL Server Management Studio.</span></span>  
  
 <span data-ttu-id="adf01-136">データベースの XMLA 定義で `CompatibilityLevel` プロパティを検索し、それが存在しなかった場合、データベースが `1050` レベルになっている可能性が高いと考えられます。</span><span class="sxs-lookup"><span data-stu-id="adf01-136">If you search the XMLA definition of a database for the property `CompatibilityLevel` and it does not exist, you most likely have a database at the `1050` level.</span></span>  
  
 <span data-ttu-id="adf01-137">XMLA スクリプトの表示と変更の方法については、次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="adf01-137">Instructions for viewing and modifying the XMLA script are provided in the next section.</span></span>  
  
## <a name="set-the-database-compatibility-level-in-sql-server-management-studio"></a><span data-ttu-id="adf01-138">SQL Server Management Studio でのデータベース互換性レベルの設定</span><span class="sxs-lookup"><span data-stu-id="adf01-138">Set the database compatibility level in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="adf01-139">互換性レベルを上げる前に、変更を元に戻すことができるように、データベースをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="adf01-139">Before raising the compatibility level, backup the database in case you want to reverse your changes later.</span></span>  
  
2.  <span data-ttu-id="adf01-140">SQL Server Management Studio を使用して、データベースをホストする [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="adf01-140">Using SQL Server Management Studio, connect to the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server that hosts the database.</span></span>  
  
3.  <span data-ttu-id="adf01-141">データベース名を右クリックし、 **[データベースをスクリプト化]** をポイントして **[ALTER]** をポイントします。次に、 **[新しいクエリ エディター ウィンドウ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="adf01-141">Right-click the database name, point to **Script Database as**, point to **ALTER to**, and then select **New Query Editor Window**.</span></span> <span data-ttu-id="adf01-142">データベースの XMLA 表現が新しいウィンドウで開きます。</span><span class="sxs-lookup"><span data-stu-id="adf01-142">An XMLA representation of the database will open in a new window.</span></span>  
  
4.  <span data-ttu-id="adf01-143">次の XML 要素をコピーします。</span><span class="sxs-lookup"><span data-stu-id="adf01-143">Copy the following XML element:</span></span>  
  
    ```  
    <ddl200:CompatibilityLevel>1100</ddl200:CompatibilityLevel>  
    ```  
  
5.  <span data-ttu-id="adf01-144">それを、 `</Annotations>` 終了要素の後、 `<Language>` 要素の前に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="adf01-144">Paste it after the `</Annotations>` closing element and before the `<Language>` element.</span></span> <span data-ttu-id="adf01-145">XML は次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="adf01-145">The XML should look similar to the following example:</span></span>  
  
    ```  
    </Annotations>  
    <ddl200:CompatibilityLevel>1100</ddl200:CompatibilityLevel>  
    <Language>1033</Language>  
    ```  
  
6.  <span data-ttu-id="adf01-146">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="adf01-146">Save the file.</span></span>  
  
7.  <span data-ttu-id="adf01-147">スクリプトを実行するには、[クエリ] メニューの **[実行]** をクリックするか、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="adf01-147">To run the script, click **Execute** on the Query menu or press F5.</span></span>  
  
## <a name="supported-operations-that-require-the-same-compatibility-level"></a><span data-ttu-id="adf01-148">同じ互換性レベルが必要なサポートされる操作</span><span class="sxs-lookup"><span data-stu-id="adf01-148">Supported Operations that Require the Same Compatibility Level</span></span>  
 <span data-ttu-id="adf01-149">次の操作では、ソース データベースで同じ互換性レベルを共有している必要があります。</span><span class="sxs-lookup"><span data-stu-id="adf01-149">The following operations require that the source databases share the same compatibility level.</span></span>  
  
1.  <span data-ttu-id="adf01-150">異なるデータベースのパーティションのマージは、両方のデータベースで同じ互換性レベルを共有している場合にのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="adf01-150">Merging partitions from different databases is supported only if both databases share the same compatibility level.</span></span>  
  
2.  <span data-ttu-id="adf01-151">別のデータベースのリンク ディメンションを使用するには、同じ互換性レベルが必要です。</span><span class="sxs-lookup"><span data-stu-id="adf01-151">Using linked dimensions from another database requires the same compatibility level.</span></span> <span data-ttu-id="adf01-152">たとえば、データベースのデータベースからリンクディメンションを使用する場合は、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] データベースを [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] サーバーに移植 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] し、互換性レベルをに設定する必要があり `1100` ます。</span><span class="sxs-lookup"><span data-stu-id="adf01-152">For example, if you want to use a linked dimension from a [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] database in a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] database, you must port the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] database to a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] server and set the compatibility level to `1100`.</span></span>  
  
3.  <span data-ttu-id="adf01-153">サーバーの同期は、サーバーで同じバージョンとデータベース互換性レベルを共有している場合にのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="adf01-153">Synchronizing servers is only supported for servers that share the same version and database compatibility level.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="adf01-154">次の手順</span><span class="sxs-lookup"><span data-stu-id="adf01-154">Next Steps</span></span>  
 <span data-ttu-id="adf01-155">データベース互換性レベルを上げると、[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] で `StringStoresCompatibilityLevel` プロパティを設定できるようになります。</span><span class="sxs-lookup"><span data-stu-id="adf01-155">After you increase the database compatibility level, you can set the `StringStoresCompatibilityLevel` property in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="adf01-156">これにより、メジャーとディメンションの文字列ストレージが大きくなります。</span><span class="sxs-lookup"><span data-stu-id="adf01-156">This increases string storage for measures and dimensions.</span></span> <span data-ttu-id="adf01-157">この機能の詳細については、「 [ディメンションおよびパーティションの文字列ストレージの構成](configure-string-storage-for-dimensions-and-partitions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="adf01-157">For more information about this feature, see [Configure String Storage for Dimensions and Partitions](configure-string-storage-for-dimensions-and-partitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adf01-158">参照</span><span class="sxs-lookup"><span data-stu-id="adf01-158">See Also</span></span>  
 [<span data-ttu-id="adf01-159">データベースのバックアップ、復元、および同期 &#40;XMLA&#41;</span><span class="sxs-lookup"><span data-stu-id="adf01-159">Backing Up, Restoring, and Synchronizing Databases &#40;XMLA&#41;</span></span>](../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
