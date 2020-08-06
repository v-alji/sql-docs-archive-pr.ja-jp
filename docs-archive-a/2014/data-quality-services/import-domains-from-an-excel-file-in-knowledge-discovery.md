---
title: ナレッジ検出でドメインを Excel ファイルからインポートする | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 4d3a3940-6c2a-4dc4-90eb-86f26012c165
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 332045466b95088523acda97a931168b0bb5c1ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642966"
---
# <a name="import-domains-from-an-excel-file-in-knowledge-discovery"></a><span data-ttu-id="ae584-102">ナレッジ検出でドメインを Excel ファイルからインポートする</span><span class="sxs-lookup"><span data-stu-id="ae584-102">Import Domains from an Excel File in Knowledge Discovery</span></span>
  <span data-ttu-id="ae584-103">このトピックでは、 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) ナレッジ検出アクティビティで Excel ファイルから 1 つまたは複数のドメインをインポートする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae584-103">This topic describes how to import one or more domains from an Excel file in the [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) knowledge discovery activity.</span></span> <span data-ttu-id="ae584-104">インポート処理は、ナレッジの生成処理を簡略化し、時間と労力を節約します。</span><span class="sxs-lookup"><span data-stu-id="ae584-104">The import process simplifies the knowledge generation process, saving time and effort.</span></span> <span data-ttu-id="ae584-105">インポートにより、Excel ファイルまたはテキスト ファイルでデータを所有しているユーザーは、そのデータを使用してナレッジ ベースを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ae584-105">It enables people who have data in an Excel file or a text file to create a knowledge base with that data.</span></span> <span data-ttu-id="ae584-106">(既存のナレッジベースのドメインに値をインポートする方法の詳細については、「 [Excel ファイルからドメインへの値のインポート](../../2014/data-quality-services/import-values-from-an-excel-file-into-a-domain.md)」を参照してください)。Excel ファイルへのエクスポートはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="ae584-106">(See [Import Values from an Excel File into a Domain](../../2014/data-quality-services/import-values-from-an-excel-file-into-a-domain.md) for more information about importing values into a domain of an existing knowledge base.) Exporting to an Excel file is not supported.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ae584-107">はじめに</span><span class="sxs-lookup"><span data-stu-id="ae584-107">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="ae584-108">前提条件</span><span class="sxs-lookup"><span data-stu-id="ae584-108">Prerequisites</span></span>  
 <span data-ttu-id="ae584-109">Excel ファイルからドメインをインポートするには、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] がインストールされているコンピューターに Excel がインストールされていること、ドメイン値を含む Excel ファイルが作成されていること (「 [How the import works](#How)」を参照)、およびドメインをインポートするナレッジ ベースが作成されていて開いていることが必要です。</span><span class="sxs-lookup"><span data-stu-id="ae584-109">To import domains from an Excel file, Excel must be installed on the computer that the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] is installed on; you must have created an Excel file with domain values (see [How the import works](#How)); and you must have created and opened a knowledge base to import the domain into.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ae584-110">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="ae584-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ae584-111">Permissions</span><span class="sxs-lookup"><span data-stu-id="ae584-111">Permissions</span></span>  
 <span data-ttu-id="ae584-112">Excel ファイルからドメインをインポートするには、DQS_MAIN データベースの dqs_kb_editor ロールまたは dqs_administrator ロールを所有している必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae584-112">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to import domains from an Excel file.</span></span>  
  
##  <a name="import-domains-from-an-excel-file-into-a-knowledge-base"></a><a name="Import"></a> <span data-ttu-id="ae584-113">ドメインを Excel ファイルからナレッジ ベースへインポートする</span><span class="sxs-lookup"><span data-stu-id="ae584-113">Import domains from an Excel file into a knowledge base</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="ae584-114">[Data Quality Client アプリケーションを実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="ae584-114">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="ae584-115">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="ae584-115">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, do one of the following:</span></span>  
  
    -   <span data-ttu-id="ae584-116">インポート先の新しいナレッジ ベースを作成します。これを行うには、 **[新しいナレッジ ベース]** をクリックしてナレッジ ベースの名前を入力し、 **[次の場所からナレッジ ベースを作成]** で **[なし]** を選択します。次に、 **[ナレッジ検出]** アクティビティを選択して、 **[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae584-116">Create a new knowledge base to import into by clicking **New knowledge base**, entering a name for the knowledge base, selecting **None** for **Create knowledge base from**, selecting the **Knowledge Discovery** activity, and then clicking **Create**.</span></span>  
  
    -   <span data-ttu-id="ae584-117">既存のナレッジ ベースを開きます。これを行うには、 **[ナレッジ ベースを開く]** をクリックしてナレッジ ベースを選択し、 **[ナレッジ検出]** を選択して **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae584-117">Open an existing knowledge base to import into by clicking **Open knowledge base**, selecting the knowledge base, selecting **Knowledge Discovery**, and then clicking **Next**.</span></span>  
  
3.  <span data-ttu-id="ae584-118">**[マップ]** ページの **[データ ソース]** で **[Excel ファイル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ae584-118">In the **Map** page, select **Excel File** for **Data Source**.</span></span>  
  
4.  <span data-ttu-id="ae584-119">**[Excel ファイル]** 行の **[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae584-119">Click **Browse** on the **Excel File** line.</span></span>  
  
5.  <span data-ttu-id="ae584-120">**[Excel ファイルの選択]** ダイアログ ボックスで、インポート元の Excel ファイルが格納されているフォルダーに移動し、Excel ファイルを選択して **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae584-120">In the **Select an Excel File** dialog box, move to the folder that contains the Excel file that you want to import from, select the Excel file, and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="ae584-121">**[ワークシート]** ボックスの一覧で、インポート元の Excel ファイルのワークシートを選択します。</span><span class="sxs-lookup"><span data-stu-id="ae584-121">From the **Worksheet** drop-down list, select the worksheet in the Excel file that you want to import from.</span></span>  
  
7.  <span data-ttu-id="ae584-122">先頭の行をデータ見出しと見なし、先頭の行の値を列名として使用する場合は、 **[先頭の行を見出しとして使用]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="ae584-122">Select **Use First Row as header** if you want the first row to be considered a data header, and if you want the values in the first row to be used as column names.</span></span> <span data-ttu-id="ae584-123">先頭の行をデータ値と見なす場合は、 **[先頭の行を見出しとして使用]** をオフにします。この場合、DQS は Excel の見出し名 (英文字) を列に使用します。</span><span class="sxs-lookup"><span data-stu-id="ae584-123">Deselect **Use First Row as header** if you want the first row to be considered a data value, in which case DQS will use the Excel header names (alphabetical letters) for the column.</span></span>  
  
8.  <span data-ttu-id="ae584-124">列を選択し、既存のドメインを列にマップするか、新しいドメインを作成して列にマップします。新しいドメインを作成するには、 **[ドメインの作成]** アイコンをクリックし、 **[ドメインの作成]** ダイアログ ボックスでドメインを作成します。</span><span class="sxs-lookup"><span data-stu-id="ae584-124">Select a column, and then either map an existing domain to the column, or create a new domain by clicking the **Create a Domain** icon, creating a domain in the **Create a domain** dialog box, and then mapping the domain to the column.</span></span> <span data-ttu-id="ae584-125">ドメインのデータ型は列のデータ型と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae584-125">The data type of the domain must match the data type of the column.</span></span> <span data-ttu-id="ae584-126">スプレッドシートのすべての列について、この手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="ae584-126">Repeat for all columns of the spreadsheet.</span></span>  
  
9. <span data-ttu-id="ae584-127">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae584-127">Click **Next**.</span></span>  
  
10. <span data-ttu-id="ae584-128">**[検出]** ページで、 **[開始]** をクリックして Excel スプレッドシート内のデータを分析します。</span><span class="sxs-lookup"><span data-stu-id="ae584-128">In the **Discover** page, click **Start** to analyze the data in the Excel spreadsheet.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ae584-129">データのアップロードが完了する前にページを閉じた場合は、ファイルのアップロード処理が終了します。</span><span class="sxs-lookup"><span data-stu-id="ae584-129">If you leave the page before the data has been uploaded, the file upload process will be terminated.</span></span>  
  
11. <span data-ttu-id="ae584-130">分析が正常に完了したことを確認して、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae584-130">Verify that the analysis completed successfully, and then click **Next**.</span></span>  
  
12. <span data-ttu-id="ae584-131">**[ドメイン値の管理]** ページで、 **[ドメイン]** ボックスの一覧に正しいドメインが表示されていること、およびドメイン テーブルに値が入力されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ae584-131">In the **Manage Domain Values** page, verify that the correct domains are listed in the **Domains** list and that values are entered in the domain table.</span></span>  
  
13. <span data-ttu-id="ae584-132">**[完了]** をクリックします。次に、ナレッジ ベースを発行する場合は **[発行]** をクリックし、発行しない場合は **[いいえ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae584-132">Click **Finish**, and then click **Publish** to publish the knowledge base, or **No** not to publish.</span></span>  
  
14. <span data-ttu-id="ae584-133">ナレッジ ベースが発行されたことを確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae584-133">Verify that the knowledge base was published, and then click **OK**.</span></span>  
  
##  <a name="follow-up-after-importing-domains-from-an-excel-file"></a><a name="FollowUp"></a><span data-ttu-id="ae584-134">補足情報: Excel ファイルからドメインをインポートした後</span><span class="sxs-lookup"><span data-stu-id="ae584-134">Follow Up: After Importing Domains from an Excel File</span></span>  
 <span data-ttu-id="ae584-135">Excel ファイルからドメインをインポートした後で、ドメインのコンテンツに応じてナレッジをドメインに追加したり、ドメインをクレンジング プロジェクトや照合プロジェクトで使用したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="ae584-135">After you import domains from an Excel file, you can add knowledge to the domains or use the domains in a cleansing or matching project, depending on the contents of the domains.</span></span> <span data-ttu-id="ae584-136">詳しくは、「[ナレッジ検出の実行](../../2014/data-quality-services/perform-knowledge-discovery.md)」、「[ドメインの管理](../../2014/data-quality-services/managing-a-domain.md)」、「[複合ドメインの管理](../../2014/data-quality-services/managing-a-composite-domain.md)」、「[照合ポリシーの作成](../../2014/data-quality-services/create-a-matching-policy.md)」、「[データ クレンジング](../../2014/data-quality-services/data-cleansing.md)」、または「[データ照合](../../2014/data-quality-services/data-matching.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ae584-136">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), [Managing a Composite Domain](../../2014/data-quality-services/managing-a-composite-domain.md), [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md), [Data Cleansing](../../2014/data-quality-services/data-cleansing.md), or [Data Matching](../../2014/data-quality-services/data-matching.md).</span></span>  
  
##  <a name="how-the-import-works"></a><a name="How"></a><span data-ttu-id="ae584-137">インポートのしくみ</span><span class="sxs-lookup"><span data-stu-id="ae584-137">How the import works</span></span>  
 <span data-ttu-id="ae584-138">インポート操作では、DQS は Excel ファイルを次のように解釈します。</span><span class="sxs-lookup"><span data-stu-id="ae584-138">In the import operation, DQS interprets an Excel file as follows:</span></span>  
  
-   <span data-ttu-id="ae584-139">列はドメインを表す</span><span class="sxs-lookup"><span data-stu-id="ae584-139">A column represents a domain</span></span>  
  
-   <span data-ttu-id="ae584-140">行はデータ レコードを表す</span><span class="sxs-lookup"><span data-stu-id="ae584-140">A row represents a data record</span></span>  
  
-   <span data-ttu-id="ae584-141">先頭の行は、 **[先頭の行を見出しとして使用]** チェック ボックスの設定に応じて、ドメインを表すか、最初のデータ値またはレコードになる</span><span class="sxs-lookup"><span data-stu-id="ae584-141">The first row either represents domain names or is the first data value or record, depending upon the setting of the **Use First Row as header** checkbox.</span></span>  
  
 <span data-ttu-id="ae584-142">インポート操作には、次のルールが適用されます。</span><span class="sxs-lookup"><span data-stu-id="ae584-142">The following rules apply to the import operation:</span></span>  
  
-   <span data-ttu-id="ae584-143">この操作では、ドメイン値がナレッジ ベースにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="ae584-143">This operation imports domain values into a knowledge base.</span></span> <span data-ttu-id="ae584-144">ドメイン ルールまたは照合ポリシーはインポートされません。</span><span class="sxs-lookup"><span data-stu-id="ae584-144">It does not import domain rules or a matching policy.</span></span>  
  
-   <span data-ttu-id="ae584-145">Excel ファイルの拡張子は、.xlsx、.xls、または .csv です。</span><span class="sxs-lookup"><span data-stu-id="ae584-145">The Excel file can have the extension .xlsx, .xls, or .csv.</span></span> <span data-ttu-id="ae584-146">ドメイン値または完全なドメインをインポートするには、Microsoft Excel が [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] コンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae584-146">Microsoft Excel must be installed on the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] computer to import domain values or a complete domain.</span></span> <span data-ttu-id="ae584-147">Excel Version 2003 以降がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ae584-147">Excel versions 2003 and later are supported.</span></span> <span data-ttu-id="ae584-148">64 ビット バージョンの Excel を使用する場合は、Excel 2003 ファイルのみがサポートされます。Excel 2007 または 2010 ファイルはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="ae584-148">If the 64-bit version of Excel is used, only Excel 2003 files will be supported; Excel 2007 or 2010 files will not be supported.</span></span>  
  
-   <span data-ttu-id="ae584-149">64 ビットの Excel では、Excel ファイル タイプ .xlsx はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="ae584-149">Excel files of type .xlsx are not supported for an Excel 64-bit installation.</span></span> <span data-ttu-id="ae584-150">64 ビットの Excel を使用している場合は、スプレッドシート ファイルを .xls ファイルとして保存してください。</span><span class="sxs-lookup"><span data-stu-id="ae584-150">If you are using 64-bit Excel, save the spreadsheet file as an .xls file.</span></span>  
  
-   <span data-ttu-id="ae584-151">.xlsx および .xls ファイルでは、列のデータ型は最初の 8 行で最も多く使用されているデータ型によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="ae584-151">In .xlsx and .xls files, the data type of the column is determined by the most prevalent data type in the first eight rows.</span></span> <span data-ttu-id="ae584-152">セルがそのデータ型に従っていない場合、セルの値は null になります。</span><span class="sxs-lookup"><span data-stu-id="ae584-152">If a cell does not conform to that data type, it will be given a null value.</span></span>  
  
-   <span data-ttu-id="ae584-153">.csv ファイルでは、データ型は最初の 8 行で最も多く使用されているデータ型によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="ae584-153">In .csv files, the data type is determined by the most prevalent data type in the first eight rows.</span></span>  
  
-   <span data-ttu-id="ae584-154">ドメイン ルールに従っていない Excel スプレッドシートの値は無効な値としてインポートされます。</span><span class="sxs-lookup"><span data-stu-id="ae584-154">A value in an Excel spreadsheet that does not conform to a domain rule will be imported as an invalid value.</span></span>  
  
-   <span data-ttu-id="ae584-155">Excel ファイルの形式が正しくないか、Excel ファイルが破損している場合は、インポート操作でエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="ae584-155">If the Excel file is not in the right format or is corrupted, the import operation will result in an error.</span></span>  
  
  
