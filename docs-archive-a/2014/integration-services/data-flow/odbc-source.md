---
title: ODBC 入力元 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.f1
ms.assetid: abcf34eb-9140-4100-82e6-b85bccd22abe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 792557839d60f34bdf944dab150959d4df7cb8cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633939"
---
# <a name="odbc-source"></a><span data-ttu-id="073b3-102">ODBC 入力元</span><span class="sxs-lookup"><span data-stu-id="073b3-102">ODBC Source</span></span>
  <span data-ttu-id="073b3-103">ODBC 入力元は、データベース テーブル、ビュー、または SQL ステートメントを使用して、ODBC でサポートされているデータベースからデータを抽出します。</span><span class="sxs-lookup"><span data-stu-id="073b3-103">The ODBC source extracts data from ODBC-supported database by using a database table, a view, or an SQL statement.</span></span>  
  
 <span data-ttu-id="073b3-104">ODBC 入力元には、データを抽出するために、次のデータ アクセス モードがあります。</span><span class="sxs-lookup"><span data-stu-id="073b3-104">The ODBC source has the following data access modes for extracting data:</span></span>  
  
-   <span data-ttu-id="073b3-105">テーブルまたはビュー。</span><span class="sxs-lookup"><span data-stu-id="073b3-105">A table or view.</span></span>  
  
-   <span data-ttu-id="073b3-106">SQL ステートメントの結果。</span><span class="sxs-lookup"><span data-stu-id="073b3-106">The results of an SQL statement.</span></span>  
  
 <span data-ttu-id="073b3-107">入力元は、使用するプロバイダーを指定する、ODBC 接続マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="073b3-107">The source uses an ODBC connection manager, which specifies the provider to use.</span></span>  
  
 <span data-ttu-id="073b3-108">ODBC 入力元には、ソース データ出力列があります。</span><span class="sxs-lookup"><span data-stu-id="073b3-108">An ODBC source includes the source data output columns.</span></span> <span data-ttu-id="073b3-109">出力列が ODBC 入力先で入力先列にマッピングされている場合に、入力先列にマッピングされている入力列がないときにはエラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="073b3-109">When output columns are mapped in the ODBC destination to the destination columns, errors may occur if no output columns are mapped to the destination columns.</span></span> <span data-ttu-id="073b3-110">さまざまな種類の列をマッピングできますが、出力列と入力先との間に互換性がない場合は、実行時にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="073b3-110">Columns of different types can be mapped, however if the output data is not compatible for the destination then an error occurs at runtime.</span></span> <span data-ttu-id="073b3-111">エラー動作設定に応じて、エラーが無視されるか、エラーが発生するか、エラー出力に行が送信されます。</span><span class="sxs-lookup"><span data-stu-id="073b3-111">Depending on the error behavior, setting the error will be ignored, cause a failure, or the row is sent to the error output.</span></span>  
  
 <span data-ttu-id="073b3-112">ODBC 入力元には、1 つの標準出力と 1 つのエラー出力があります。</span><span class="sxs-lookup"><span data-stu-id="073b3-112">The ODBC source has one regular output and one error output.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="073b3-113">エラー処理</span><span class="sxs-lookup"><span data-stu-id="073b3-113">Error Handling</span></span>  
 <span data-ttu-id="073b3-114">ODBC 入力元にはエラー出力があります。</span><span class="sxs-lookup"><span data-stu-id="073b3-114">The ODBC source has an error output.</span></span> <span data-ttu-id="073b3-115">コンポーネントのエラー出力には、次の出力列があります。</span><span class="sxs-lookup"><span data-stu-id="073b3-115">The component error output includes the following output columns:</span></span>  
  
-   <span data-ttu-id="073b3-116">**エラー コード**: 現在のエラーに対応する数字です。</span><span class="sxs-lookup"><span data-stu-id="073b3-116">**Error Code**: The number that corresponds to the current error.</span></span> <span data-ttu-id="073b3-117">エラーの一覧については、使用している ODBC でサポートされているデータベースのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="073b3-117">See the documentation for the ODBC-supported database you are using for a list of errors.</span></span> <span data-ttu-id="073b3-118">SSIS エラー コードの一覧については、「SSIS のエラー コードおよびメッセージ リファレンス」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="073b3-118">For a list of SSIS error codes, see the SSIS Error Code and Message Reference.</span></span>  
  
-   <span data-ttu-id="073b3-119">**エラー列**: (変換エラーの) エラーの原因となるソース列。</span><span class="sxs-lookup"><span data-stu-id="073b3-119">**Error Column**: The source column causing the error (for conversion errors).</span></span>  
  
-   <span data-ttu-id="073b3-120">標準出力データ列。</span><span class="sxs-lookup"><span data-stu-id="073b3-120">The standard output data columns.</span></span>  
  
 <span data-ttu-id="073b3-121">ODBC 入力元は、エラー動作の設定に応じて、抽出処理中に発生したエラー (データ変換、切り捨て) をエラー出力に返します。</span><span class="sxs-lookup"><span data-stu-id="073b3-121">Depending on the error behavior setting, the ODBC source supports returning errors (data conversion, truncation) that occur during the extraction process in the error output.</span></span> <span data-ttu-id="073b3-122">詳細については、「[ODBC 変換先エディター &#40;[接続マネージャー] ページ&#41;](../odbc-destination-editor-connection-manager-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="073b3-122">For more information, see [ODBC Destination Editor &#40;Connection Manager Page&#41;](../odbc-destination-editor-connection-manager-page.md).</span></span>  
  
## <a name="data-type-support"></a><span data-ttu-id="073b3-123">データ型のサポート</span><span class="sxs-lookup"><span data-stu-id="073b3-123">Data Type Support</span></span>  
 <span data-ttu-id="073b3-124">ODBC 入力元でサポートされるデータ型については、「Connector for Open Database Connectivity (ODBC) by Attunity」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="073b3-124">For information about the data types supported by the ODBC source, see Connector for Open Database Connectivity (ODBC) by Attunity.</span></span>  
  
## <a name="extract-options"></a><span data-ttu-id="073b3-125">抽出オプション</span><span class="sxs-lookup"><span data-stu-id="073b3-125">Extract Options</span></span>  
 <span data-ttu-id="073b3-126">ODBC 入力元は、 **バッチ** または **行ごと** のどちらかのモードで動作します。</span><span class="sxs-lookup"><span data-stu-id="073b3-126">The ODBC source operates in either **Batch** or **Row-by-Row** mode.</span></span> <span data-ttu-id="073b3-127">使用するモードは、 **FetchMethod** プロパティによって決まります。</span><span class="sxs-lookup"><span data-stu-id="073b3-127">The mode used is determined by the **FetchMethod** property.</span></span> <span data-ttu-id="073b3-128">以下に、モードの説明を示します。</span><span class="sxs-lookup"><span data-stu-id="073b3-128">The following list describes the modes.</span></span>  
  
-   <span data-ttu-id="073b3-129">**バッチ**: コンポーネントは、把握した ODBC プロバイダーの機能に基づいて、最も効率的なフェッチ方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="073b3-129">**Batch**: The component attempts to use the most efficient fetch method based on the perceived ODBC provider capabilities.</span></span> <span data-ttu-id="073b3-130">最新の ODBC プロバイダーの場合、これは配列バインドを使用する SQLFetchScroll です (このとき、配列のサイズは **BatchSize** プロパティによって決定します)。</span><span class="sxs-lookup"><span data-stu-id="073b3-130">For most modern ODBC providers, this is SQLFetchScroll with array binding (where the array size is determined by the **BatchSize** property).</span></span> <span data-ttu-id="073b3-131">**[バッチ]** を選択したが、この方法がプロバイダーでサポートされていない場合、ODBC 入力先は自動的に **[行ごと]** モードに切り替わります。</span><span class="sxs-lookup"><span data-stu-id="073b3-131">If you select **Batch** and the provider does not support this method, the ODBC destination automatically switches to the **Row-by-row** mode.</span></span>  
  
-   <span data-ttu-id="073b3-132">**行ごと**: コンポーネントは SQLFetch を使用して、一度に 1 行ずつ取得します。</span><span class="sxs-lookup"><span data-stu-id="073b3-132">**Row-by Row**: The component uses SQLFetch to retrieve the rows one at a time.</span></span>  
  
 <span data-ttu-id="073b3-133">**FetchMethod** プロパティの詳細については、「 [ODBC 入力元のカスタム プロパティ](odbc-source-custom-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="073b3-133">For more information about the **FetchMethod** property, see [ODBC Source Custom Properties](odbc-source-custom-properties.md).</span></span>  
  
## <a name="parallelism"></a><span data-ttu-id="073b3-134">Parallelism</span><span class="sxs-lookup"><span data-stu-id="073b3-134">Parallelism</span></span>  
 <span data-ttu-id="073b3-135">並列実行できる ODBC 入力元コンポーネントの数に制限はありません。これは、同一テーブル上にある場合または異なるテーブル上にある場合、同一コンピューター上で実行する場合または異なるコンピューター上で実行する場合のいずれにも該当します (ただし、通常のグローバルなセッション制限を除きます)。</span><span class="sxs-lookup"><span data-stu-id="073b3-135">There is no limitation on the number of ODBC source components that can run in parallel against the same table or different tables, on the same machine or on different machines (other than normal global session limits).</span></span>  
  
 <span data-ttu-id="073b3-136">ただし、使用する ODBC プロバイダーの制限によって、プロバイダーを介するコンカレント接続数が制限される場合があります。</span><span class="sxs-lookup"><span data-stu-id="073b3-136">However, limitations of the ODBC provider being used may restrict the number of concurrent connections through the provider.</span></span> <span data-ttu-id="073b3-137">これらの制限によって、ODBC 入力元で使用できる並列インスタンス数のサポートが制限されます。</span><span class="sxs-lookup"><span data-stu-id="073b3-137">These limitations limit the number of supported parallel instances possible for the ODBC source.</span></span> <span data-ttu-id="073b3-138">SSIS プロバイダーは、使用される ODBC プロバイダーの制限を把握し、SSIS パッケージを作成する際に考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="073b3-138">The SSIS developer must be aware of the limitations of any ODBC provider being used and take them into consideration when building SSIS packages.</span></span>  
  
## <a name="troubleshooting-the-odbc-source"></a><span data-ttu-id="073b3-139">ODBC 入力元のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="073b3-139">Troubleshooting the ODBC Source</span></span>  
 <span data-ttu-id="073b3-140">ODBC 入力元による外部データ プロバイダーの呼び出しをログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="073b3-140">You can log the calls that the ODBC source makes to external data providers.</span></span> <span data-ttu-id="073b3-141">このログ機能を使用すると、ODBC 入力元による外部データ ソースからのデータ読み込みに関するトラブルシューティングを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="073b3-141">You can use this logging capability to troubleshoot the loading of data from external data sources that the ODBC source performs.</span></span> <span data-ttu-id="073b3-142">ODBC 入力元による外部データ プロバイダーの呼び出しをログに記録するには、ODBC ドライバー マネージャーによるトレースを有効にします。</span><span class="sxs-lookup"><span data-stu-id="073b3-142">To log the calls that the ODBC source makes to external data providers, enable the ODBC driver manager trace.</span></span> <span data-ttu-id="073b3-143">詳細については、「 *ODBC で ODBC トレースを生成する方法 (データ ソース管理者向け)* 」の Microsoft のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="073b3-143">For more information, see the Microsoft documentation on *How To Generate an ODBC Trace with ODBC the Data Source Administrator.*</span></span>  
  
## <a name="configuring-the-odbc-source"></a><span data-ttu-id="073b3-144">ODBC 入力元の構成</span><span class="sxs-lookup"><span data-stu-id="073b3-144">Configuring the ODBC Source</span></span>  
 <span data-ttu-id="073b3-145">ODBC 入力元は、プログラムによって、または SSIS デザイナーを使用して構成できます。</span><span class="sxs-lookup"><span data-stu-id="073b3-145">You can configure the ODBC source programmatically or through the SSIS Designer.</span></span>  
  
 <span data-ttu-id="073b3-146">詳細については、次のいずれかのトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="073b3-146">For more information, see one of the following topics:</span></span>  
  
-   <span data-ttu-id="073b3-147">[ODBC ソース エディター ([接続マネージャー] ページ)](../odbc-source-editor-connection-manager-page.md)</span><span class="sxs-lookup"><span data-stu-id="073b3-147">[ODBC Source Editor &#40;Connection Manager Page&#41;](../odbc-source-editor-connection-manager-page.md)</span></span>  
  
-   <span data-ttu-id="073b3-148">[[ODBC ソース エディター] &#40;[列] ページ&#41;](../odbc-source-editor-columns-page.md)</span><span class="sxs-lookup"><span data-stu-id="073b3-148">[ODBC Source Editor &#40;Columns Page&#41;](../odbc-source-editor-columns-page.md)</span></span>  
  
-   <span data-ttu-id="073b3-149">[[ODBC ソース エディター] &#40;[エラー出力] ページ&#41;](../odbc-source-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="073b3-149">[ODBC Source Editor &#40;Error Output Page&#41;](../odbc-source-editor-error-output-page.md)</span></span>  
  
 <span data-ttu-id="073b3-150">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="073b3-150">The **Advanced Editor** dialog box contains the properties that can be set programmatically.</span></span>  
  
 <span data-ttu-id="073b3-151">**[詳細エディター]** ダイアログ ボックスを開くには、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="073b3-151">To open the **Advanced Editor** dialog box:</span></span>  
  
-   <span data-ttu-id="073b3-152">**プロジェクトの** [データ フロー] [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 画面で、ODBC 入力元を右クリックし、 **[詳細エディターの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="073b3-152">In the **Data Flow** screen of your [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project, right click the ODBC source and select **Show Advanced Editor**.</span></span>  
  
 <span data-ttu-id="073b3-153">[詳細エディター] ダイアログ ボックスで設定できるプロパティの詳細については、「 [ODBC 入力元のカスタム プロパティ](odbc-source-custom-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="073b3-153">For more information about the properties that you can set in the Advanced Editor dialog box, see [ODBC Source Custom Properties](odbc-source-custom-properties.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="073b3-154">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="073b3-154">In This Section</span></span>  
  
-   <span data-ttu-id="073b3-155">[[ODBC ソース エディター] &#40;[エラー出力] ページ&#41;](../odbc-source-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="073b3-155">[ODBC Source Editor &#40;Error Output Page&#41;](../odbc-source-editor-error-output-page.md)</span></span>  
  
-   <span data-ttu-id="073b3-156">[[ODBC ソース エディター] &#40;[列] ページ&#41;](../odbc-source-editor-columns-page.md)</span><span class="sxs-lookup"><span data-stu-id="073b3-156">[ODBC Source Editor &#40;Columns Page&#41;](../odbc-source-editor-columns-page.md)</span></span>  
  
-   <span data-ttu-id="073b3-157">[ODBC ソース エディター ([接続マネージャー] ページ)](../odbc-source-editor-connection-manager-page.md)</span><span class="sxs-lookup"><span data-stu-id="073b3-157">[ODBC Source Editor &#40;Connection Manager Page&#41;](../odbc-source-editor-connection-manager-page.md)</span></span>  
  
-   [<span data-ttu-id="073b3-158">ODBC 入力元を使用したデータ抽出</span><span class="sxs-lookup"><span data-stu-id="073b3-158">Extract Data by Using the ODBC Source</span></span>](odbc-source.md)  
  
-   [<span data-ttu-id="073b3-159">ODBC 入力元のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="073b3-159">ODBC Source Custom Properties</span></span>](odbc-source-custom-properties.md)  
  
  
