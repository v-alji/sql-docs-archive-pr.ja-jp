---
title: '手順 2: フラット ファイル接続マネージャーの追加と構成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9a77dd32-d8c2-4961-ad37-2a971f9d6043
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3ba3adee2422af8b2df027f55ec84366b90ddd7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641108"
---
# <a name="step-2-adding-and-configuring-a-flat-file-connection-manager"></a><span data-ttu-id="46c3f-102">手順 2:フラット ファイル接続マネージャーの追加と構成</span><span class="sxs-lookup"><span data-stu-id="46c3f-102">Step 2: Adding and Configuring a Flat File Connection Manager</span></span>
  <span data-ttu-id="46c3f-103">この実習では、先ほど作成したパッケージにフラット ファイル接続マネージャーを追加します。</span><span class="sxs-lookup"><span data-stu-id="46c3f-103">In this task, you add a Flat File connection manager to the package that you just created.</span></span> <span data-ttu-id="46c3f-104">パッケージにフラット ファイル接続マネージャーを追加すると、フラット ファイルからデータを抽出できるようになります。</span><span class="sxs-lookup"><span data-stu-id="46c3f-104">A Flat File connection manager enables a package to extract data from a flat file.</span></span> <span data-ttu-id="46c3f-105">フラット ファイル接続マネージャーでは、フラット ファイルからデータを抽出するときに適用するファイルの名前と場所、ロケールとコード ページ、およびファイル形式を指定できます。また、列区切り記号も指定できます。</span><span class="sxs-lookup"><span data-stu-id="46c3f-105">Using the Flat File connection manager, you can specify the file name and location, the locale and code page, and the file format, including column delimiters, to apply when the package extracts data from the flat file.</span></span> <span data-ttu-id="46c3f-106">さらに、各列のデータ型を手動で指定できます。 **[列の型の予測]** ダイアログ ボックスを使用して、抽出したデータの列を [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] データ型に自動的にマップすることもできます。</span><span class="sxs-lookup"><span data-stu-id="46c3f-106">In addition, you can manually specify the data type for the individual columns, or use the **Suggest Column Types** dialog box to automatically map the columns of extracted data to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] data types.</span></span>  
  
 <span data-ttu-id="46c3f-107">通常は、操作する各フラット ファイルについて、新しいファイル インポート マネージャーを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46c3f-107">You must create a new Flat File connection manager for each file format that you work with.</span></span> <span data-ttu-id="46c3f-108">ただし、このチュートリアルでは、データ形式がまったく同じである複数のフラット ファイルからデータを抽出するので、フラット ファイル接続マネージャーを 1 つだけパッケージに追加して、構成します。</span><span class="sxs-lookup"><span data-stu-id="46c3f-108">Because this tutorial extracts data from multiple flat files that have exactly the same data format, you will need to add and configure only one Flat File connection manager for your package.</span></span>  
  
 <span data-ttu-id="46c3f-109">このチュートリアルでは、フラット ファイル接続マネージャーで次のプロパティを構成します。</span><span class="sxs-lookup"><span data-stu-id="46c3f-109">For this tutorial, you will configure the following properties in your Flat File connection manager:</span></span>  
  
-   <span data-ttu-id="46c3f-110">**列名:** フラット ファイルには列名がないため、フラット ファイル接続マネージャーによって既定の列名が作成されます。</span><span class="sxs-lookup"><span data-stu-id="46c3f-110">**Column names:** Because the flat file does not have column names, the Flat File connection manager creates default column names.</span></span> <span data-ttu-id="46c3f-111">これらの既定の列名は、各列の内容を明確に表していません。</span><span class="sxs-lookup"><span data-stu-id="46c3f-111">These default names are not useful for identifying what each column represents.</span></span> <span data-ttu-id="46c3f-112">わかりやすい名前にするには、既定の列名を変更し、フラット ファイル データの読み込み先であるファクト テーブルと一致する名前を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="46c3f-112">To make these default names more useful, you need to change the default names to names that match the fact table into which the flat file data is to be loaded.</span></span>  
  
-   <span data-ttu-id="46c3f-113">**データのマッピング:** フラット ファイル接続マネージャーのデータ型マッピングを指定します。このマッピングは、その接続マネージャーを参照するすべてのフラット ファイル データ ソース コンポーネントで使用されます。</span><span class="sxs-lookup"><span data-stu-id="46c3f-113">**Data mappings:** The data type mappings that you specify for the Flat File connection manager will be used by all flat file data source components that reference the connection manager.</span></span> <span data-ttu-id="46c3f-114">フラット ファイル接続マネージャーでは、データ型を手動でマップできます。また、 **[列の型の予測]** ダイアログ ボックスを使用してマップすることもできます。</span><span class="sxs-lookup"><span data-stu-id="46c3f-114">You can either manually map the data types by using the Flat File connection manager, or you can use the **Suggest Column Types** dialog box.</span></span> <span data-ttu-id="46c3f-115">このチュートリアルでは、 **[列の型の予測]** ダイアログ ボックスで予測されたマッピングを表示し、 **[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスで必要なマッピングを手動で行います。</span><span class="sxs-lookup"><span data-stu-id="46c3f-115">In this tutorial, you will view the mappings suggested in the **Suggest Column Types** dialog box and then manually make the necessary mappings in the **Flat File Connection Manager Editor** dialog box.</span></span>  
  
 <span data-ttu-id="46c3f-116">フラット ファイル接続マネージャーでは、データ ファイルに関するロケール情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="46c3f-116">The Flat File connection manager provides locale information about the data file.</span></span> <span data-ttu-id="46c3f-117">コンピューターが、地域オプション [英語 (米国) を使用するように構成されていない場合は、[**フラットファイル接続マネージャーエディター** ] ダイアログボックスで追加のプロパティを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46c3f-117">If your computer is not configured to use the regional option English (United States), you must set additional properties in the **Flat File Connection Manager Editor** dialog box.</span></span>  
  
### <a name="to-add-a-flat-file-connection-manager-to-the-ssis-package"></a><span data-ttu-id="46c3f-118">SSIS パッケージにフラット ファイル接続マネージャーを追加するには</span><span class="sxs-lookup"><span data-stu-id="46c3f-118">To add a Flat File connection manager to the SSIS package</span></span>  
  
1.  <span data-ttu-id="46c3f-119">**[接続マネージャー]** 領域内を右クリックし、 **[新しいフラット ファイル接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46c3f-119">Right-click anywhere in the **Connection Managers** area, and then click **New Flat File Connection**.</span></span>  
  
2.  <span data-ttu-id="46c3f-120">**[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスで、 **[接続マネージャー名]** に「 **Sample Flat File Source Data**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="46c3f-120">In the **Flat File Connection Manager Editor** dialog box, for **Connection manager name**, type **Sample Flat File Source Data**.</span></span>  
  
3.  <span data-ttu-id="46c3f-121">**[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46c3f-121">Click **Browse**.</span></span>  
  
4.  <span data-ttu-id="46c3f-122">**[ファイルを開く]** ダイアログ ボックスで、コンピューター上の SampleCurrencyData.txt ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="46c3f-122">In the **Open** dialog box, locate the SampleCurrencyData.txt file on your machine.</span></span>  
  
     <span data-ttu-id="46c3f-123">このサンプル データは、 [!INCLUDE[ssIS](../includes/ssis-md.md)] のレッスン パッケージに含まれています。</span><span class="sxs-lookup"><span data-stu-id="46c3f-123">The sample data is included with the [!INCLUDE[ssIS](../includes/ssis-md.md)] lesson packages.</span></span> <span data-ttu-id="46c3f-124">サンプル データとレッスン パッケージをダウンロードするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="46c3f-124">To download the sample data and the lesson packages, do the following.</span></span>  
  
    1.  <span data-ttu-id="46c3f-125">「 [Integration Services 製品サンプル](https://go.microsoft.com/fwlink/?LinkId=275027)」に移動します。</span><span class="sxs-lookup"><span data-stu-id="46c3f-125">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="46c3f-126">[**ダウンロード**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="46c3f-126">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="46c3f-127">SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip ファイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="46c3f-127">Click the  SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
5.  <span data-ttu-id="46c3f-128">[先頭データ行を列名として使用する] チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="46c3f-128">Clear the Column names in the first data row checkbox.</span></span>  
  
### <a name="to-set-locale-sensitive-properties"></a><span data-ttu-id="46c3f-129">ロケール依存型のプロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="46c3f-129">To set locale sensitive properties</span></span>  
  
1.  <span data-ttu-id="46c3f-130">**[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスで、 **[全般]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46c3f-130">In the **Flat File Connection Manager Editor** dialog box, click **General**.</span></span>  
  
2.  <span data-ttu-id="46c3f-131">**ロケール**を英語 (米国) に設定し、**コードページ**を1252に設定します。</span><span class="sxs-lookup"><span data-stu-id="46c3f-131">Set **Locale** to English (United States) and **Code page** to 1252.</span></span>  
  
### <a name="to-rename-columns-in-the-flat-file-connection-manager"></a><span data-ttu-id="46c3f-132">フラット ファイル接続マネージャーで列名を変更するには</span><span class="sxs-lookup"><span data-stu-id="46c3f-132">To rename columns in the Flat File connection manager</span></span>  
  
1.  <span data-ttu-id="46c3f-133">**[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスで、 **[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46c3f-133">In the **Flat File Connection Manager Editor** dialog box, click **Advanced**.</span></span>  
  
2.  <span data-ttu-id="46c3f-134">プロパティ ペインで、次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="46c3f-134">In the property pane, make the following changes:</span></span>  
  
    -   <span data-ttu-id="46c3f-135">**列 0**の name プロパティをに変更し `AverageRate` ます。</span><span class="sxs-lookup"><span data-stu-id="46c3f-135">Change the **Column 0** name property to `AverageRate`.</span></span>  
  
    -   <span data-ttu-id="46c3f-136">**列 1**の name プロパティをに変更 `CurrencyID` します。</span><span class="sxs-lookup"><span data-stu-id="46c3f-136">Change the **Column 1** name property to `CurrencyID`.</span></span>  
  
    -   <span data-ttu-id="46c3f-137">**列 2**の name プロパティをに変更 `CurrencyDate` します。</span><span class="sxs-lookup"><span data-stu-id="46c3f-137">Change the **Column 2** name property to `CurrencyDate`.</span></span>  
  
    -   <span data-ttu-id="46c3f-138">**列 3**の name プロパティをに変更 `EndOfDayRate` します。</span><span class="sxs-lookup"><span data-stu-id="46c3f-138">Change the **Column 3** name property to `EndOfDayRate`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="46c3f-139">既定では、4 つのすべての列が文字列データ型 [DT_STR] に設定され、`OutputColumnWidth` は 50 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="46c3f-139">By default, all four of the columns are initially set to a string data type [DT_STR] with an `OutputColumnWidth` of 50.</span></span>  
  
### <a name="to-remap-column-data-types"></a><span data-ttu-id="46c3f-140">列のデータ型を再マップするには</span><span class="sxs-lookup"><span data-stu-id="46c3f-140">To remap column data types</span></span>  
  
1.  <span data-ttu-id="46c3f-141">**[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスで、 **[型の推測]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46c3f-141">In the **Flat File Connection Manager Editor** dialog box, click **Suggest Types**.</span></span>  
  
     [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="46c3f-142">は、最初の 200 行分のデータに基づいて最適なデータ型を自動的に予測します。</span><span class="sxs-lookup"><span data-stu-id="46c3f-142">automatically suggests the most appropriate data types based on the first 200 rows of data.</span></span> <span data-ttu-id="46c3f-143">この推測オプションを変更して、サンプルの行数を変更したり、整数またはブール データの既定のデータ型を指定したり、文字列の列の余白としてスペースを挿入することもできます。</span><span class="sxs-lookup"><span data-stu-id="46c3f-143">You can also change these suggestion options to sample more or less data, to specify the default data type for integer or Boolean data, or to add spaces as padding to string columns.</span></span>  
  
     <span data-ttu-id="46c3f-144">ここでは **[列の型の予測]** ダイアログ ボックスのオプションを変更せずに、 **[OK]** をクリックして [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] に列のデータ型を予測させます。</span><span class="sxs-lookup"><span data-stu-id="46c3f-144">For now, make no changes to the options in the **Suggest Column Types** dialog box, and click **OK** to have [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] suggest data types for columns.</span></span> <span data-ttu-id="46c3f-145">これにより、 **[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスの **[詳細設定]** ペインに戻ります。このペインでは、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]によって予測された列のデータ型を確認できます</span><span class="sxs-lookup"><span data-stu-id="46c3f-145">This returns you to the **Advanced** pane of the **Flat File Connection Manager Editor** dialog box, where you can view the column data types suggested by [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="46c3f-146">( **[キャンセル]** をクリックすると、列のメタデータの予測は行われず、既定の文字列データ型 (DT_STR) が使用されます)。</span><span class="sxs-lookup"><span data-stu-id="46c3f-146">(If you click **Cancel**, no suggestions are made to column metadata and the default string (DT_STR) data type is used.)</span></span>  
  
     <span data-ttu-id="46c3f-147">このチュートリアルでは、SampleCurrencyData.txt ファイルのデータに対応するデータ型を [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] が推測します。推測されたデータ型は、下表の 2 列目に示されています。</span><span class="sxs-lookup"><span data-stu-id="46c3f-147">In this tutorial, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] suggests the data types shown in the second column of the following table for the data from the SampleCurrencyData.txt file.</span></span> <span data-ttu-id="46c3f-148">一方、変換先の列に必要なデータ型 (以降の手順で定義します) は、下表の 4 列目に示されています。</span><span class="sxs-lookup"><span data-stu-id="46c3f-148">However, the data types that are required for the columns in the destination, which will be defined in a later step, are shown in the last column of the following table.</span></span>  
  
    |<span data-ttu-id="46c3f-149">フラット ファイルの列</span><span class="sxs-lookup"><span data-stu-id="46c3f-149">Flat File Column</span></span>|<span data-ttu-id="46c3f-150">推測されたデータ型</span><span class="sxs-lookup"><span data-stu-id="46c3f-150">Suggested Type</span></span>|<span data-ttu-id="46c3f-151">変換先列</span><span class="sxs-lookup"><span data-stu-id="46c3f-151">Destination Column</span></span>|<span data-ttu-id="46c3f-152">変換先の型</span><span class="sxs-lookup"><span data-stu-id="46c3f-152">Destination Type</span></span>|  
    |----------------------|--------------------|------------------------|----------------------|  
    |<span data-ttu-id="46c3f-153">AverageRate</span><span class="sxs-lookup"><span data-stu-id="46c3f-153">AverageRate</span></span>|<span data-ttu-id="46c3f-154">float [DT_R4]</span><span class="sxs-lookup"><span data-stu-id="46c3f-154">float [DT_R4]</span></span>|<span data-ttu-id="46c3f-155">FactCurrency.AverageRate</span><span class="sxs-lookup"><span data-stu-id="46c3f-155">FactCurrency.AverageRate</span></span>|<span data-ttu-id="46c3f-156">float</span><span class="sxs-lookup"><span data-stu-id="46c3f-156">float</span></span>|  
    |<span data-ttu-id="46c3f-157">CurrencyID</span><span class="sxs-lookup"><span data-stu-id="46c3f-157">CurrencyID</span></span>|<span data-ttu-id="46c3f-158">string [DT_STR]</span><span class="sxs-lookup"><span data-stu-id="46c3f-158">string [DT_STR]</span></span>|<span data-ttu-id="46c3f-159">DimCurrency,CurrencyAlternateKey</span><span class="sxs-lookup"><span data-stu-id="46c3f-159">DimCurrency.CurrencyAlternateKey</span></span>|<span data-ttu-id="46c3f-160">nchar(3)</span><span class="sxs-lookup"><span data-stu-id="46c3f-160">nchar(3)</span></span>|  
    |<span data-ttu-id="46c3f-161">CurrencyDate</span><span class="sxs-lookup"><span data-stu-id="46c3f-161">CurrencyDate</span></span>|<span data-ttu-id="46c3f-162">date [DT_DATE]</span><span class="sxs-lookup"><span data-stu-id="46c3f-162">date [DT_DATE]</span></span>|<span data-ttu-id="46c3f-163">DimDate.FullDateAlternateKey</span><span class="sxs-lookup"><span data-stu-id="46c3f-163">DimDate.FullDateAlternateKey</span></span>|<span data-ttu-id="46c3f-164">date</span><span class="sxs-lookup"><span data-stu-id="46c3f-164">date</span></span>|  
    |<span data-ttu-id="46c3f-165">EndOfDayRate</span><span class="sxs-lookup"><span data-stu-id="46c3f-165">EndOfDayRate</span></span>|<span data-ttu-id="46c3f-166">float [DT_R4]</span><span class="sxs-lookup"><span data-stu-id="46c3f-166">float [DT_R4]</span></span>|<span data-ttu-id="46c3f-167">FactCurrency.EndOfDayRate</span><span class="sxs-lookup"><span data-stu-id="46c3f-167">FactCurrency.EndOfDayRate</span></span>|<span data-ttu-id="46c3f-168">float</span><span class="sxs-lookup"><span data-stu-id="46c3f-168">float</span></span>|  
  
     <span data-ttu-id="46c3f-169">列に対して提案されたデータ型 `CurrencyID` は、変換先テーブルのフィールドのデータ型と互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="46c3f-169">The data type suggested for the `CurrencyID` column is incompatible with the data type of the field in the destination table.</span></span> <span data-ttu-id="46c3f-170">のデータ型 `DimCurrency.CurrencyAlternateKey` は nchar (3) であるため、を `CurrencyID` 文字列 [DT_STR] から文字列 [DT_WSTR] に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46c3f-170">Because the data type of `DimCurrency.CurrencyAlternateKey` is nchar (3), `CurrencyID` must be changed from string [DT_STR] to string [DT_WSTR].</span></span> <span data-ttu-id="46c3f-171">また、フィールド `DimDate.FullDateAlternateKey` は date データ型として定義されているため、を `CurrencyDate` date [DT_Date] からデータベース日付 [DT_DBDATE] に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46c3f-171">Additionally, the field `DimDate.FullDateAlternateKey` is defined as a date data type; therefore, `CurrencyDate` needs to be changed from date [DT_Date] to database date [DT_DBDATE].</span></span>  
  
2.  <span data-ttu-id="46c3f-172">一覧で、CurrencyID 列を選択し、プロパティペインで、列のデータ型を `CurrencyID` 文字列 [DT_STR] から Unicode 文字列 [DT_WSTR] に変更します。</span><span class="sxs-lookup"><span data-stu-id="46c3f-172">In the list, select the CurrencyID column and in the property pane, change the Data Type of column `CurrencyID` from string [DT_STR] to Unicode string [DT_WSTR].</span></span>  
  
3.  <span data-ttu-id="46c3f-173">プロパティペインで、 `CurrencyDate` date [DT_DATE] のデータ型を [データベースの日付 [DT_DBDATE] に変更します。</span><span class="sxs-lookup"><span data-stu-id="46c3f-173">In the property pane, change the data type of column `CurrencyDate` from date [DT_DATE] to database date [DT_DBDATE].</span></span>  
  
4.  <span data-ttu-id="46c3f-174">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46c3f-174">Click **OK**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="46c3f-175">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="46c3f-175">Next Task in Lesson</span></span>  
 [<span data-ttu-id="46c3f-176">手順 3:OLE DB 接続マネージャーの追加と構成</span><span class="sxs-lookup"><span data-stu-id="46c3f-176">Step 3: Adding and Configuring an OLE DB Connection Manager</span></span>](lesson-1-3-adding-and-configuring-an-ole-db-connection-manager.md)  
  
## <a name="see-also"></a><span data-ttu-id="46c3f-177">参照</span><span class="sxs-lookup"><span data-stu-id="46c3f-177">See Also</span></span>  
 <span data-ttu-id="46c3f-178">[フラットファイル接続マネージャー](connection-manager/file-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="46c3f-178">[Flat File Connection Manager](connection-manager/file-connection-manager.md) </span></span>  
 [<span data-ttu-id="46c3f-179">Integration Services のデータ型</span><span class="sxs-lookup"><span data-stu-id="46c3f-179">Integration Services Data Types</span></span>](data-flow/integration-services-data-types.md)  
  
  
