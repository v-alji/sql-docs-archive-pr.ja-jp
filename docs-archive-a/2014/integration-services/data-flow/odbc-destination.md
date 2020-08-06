---
title: ODBC 入力先 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcdest.f1
ms.assetid: bffa63e0-c737-4b54-b4ea-495a400ffcf8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: beb29c511af62ba69ca0b9e2c595f61c57edab6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644086"
---
# <a name="odbc-destination"></a><span data-ttu-id="c5591-102">ODBC 入力先</span><span class="sxs-lookup"><span data-stu-id="c5591-102">ODBC Destination</span></span>
  <span data-ttu-id="c5591-103">ODBC 入力先は、ODBC でサポートされているデータベース テーブルにデータを一括で読み込みます。</span><span class="sxs-lookup"><span data-stu-id="c5591-103">The ODBC destination bulk loads data into ODBC-supported database tables.</span></span> <span data-ttu-id="c5591-104">ODBC 入力先は ODBC 接続マネージャーを使用してデータ ソースに接続します。</span><span class="sxs-lookup"><span data-stu-id="c5591-104">The ODBC destination uses an ODBC connection manager to connect to the data source.</span></span>  
  
 <span data-ttu-id="c5591-105">ODBC 入力先には、入力列と入力先データ ソースの列との間のマッピングが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c5591-105">An ODBC destination includes mappings between input columns and columns in the destination data source.</span></span> <span data-ttu-id="c5591-106">入力列をすべての入力先列にマップする必要はありませんが、入力先列のプロパティによっては、入力先列にマップされる入力列がない場合、エラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="c5591-106">You do not have to map input columns to all destination columns, but depending on the properties of the destination columns, errors may occur if no input columns are mapped to the destination columns.</span></span> <span data-ttu-id="c5591-107">たとえば、入力先列で NULL 値が許容されていない場合は、入力列をその列にマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5591-107">For example, if a destination column does not allow null values, an input column must be mapped to that column.</span></span> <span data-ttu-id="c5591-108">また、さまざまな種類の列をマッピングできますが、入力データと入力先の列の型との間に互換性がない場合は、実行時にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="c5591-108">In addition, columns of different types can be mapped, however if the input data is not compatible for the destination column type, an error occurs at runtime.</span></span> <span data-ttu-id="c5591-109">エラー動作設定に応じて、エラーが無視されるか、エラーが発生するか、エラー出力に行が送信されます。</span><span class="sxs-lookup"><span data-stu-id="c5591-109">Depending on the error behavior setting, the error will be ignored, cause a failure, or the row is sent to the error output.</span></span>  
  
 <span data-ttu-id="c5591-110">ODBC 入力先には、1 つの標準出力と 1 つのエラー出力があります。</span><span class="sxs-lookup"><span data-stu-id="c5591-110">The ODBC destination has one regular output and one error output.</span></span>  
  
##  <a name="load-options"></a><a name="BKMK_odbcdestination_loadoptions"></a> <span data-ttu-id="c5591-111">読み込みオプション</span><span class="sxs-lookup"><span data-stu-id="c5591-111">Load Options</span></span>  
 <span data-ttu-id="c5591-112">ODBC 入力先先は、2 つのアクセス読み込みモジュールのうちどちらかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c5591-112">The ODBC destination can use one of two access load modules.</span></span> <span data-ttu-id="c5591-113">[ODBC ソース エディター &#40;[接続マネージャー] ページ&#41;](../odbc-source-editor-connection-manager-page.md)。</span><span class="sxs-lookup"><span data-stu-id="c5591-113">You set the mode in the [ODBC Source Editor &#40;Connection Manager Page&#41;](../odbc-source-editor-connection-manager-page.md).</span></span> <span data-ttu-id="c5591-114">次の 2 つのモードがあります。</span><span class="sxs-lookup"><span data-stu-id="c5591-114">The two modes are:</span></span>  
  
-   <span data-ttu-id="c5591-115">**バッチ**: このモードでは、ODBC 入力先は、把握した ODBC プロバイダーの機能に基づいて、最も効率的な挿入方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="c5591-115">**Batch**: In this mode the ODBC destination attempts to use the most efficient insertion method based on the perceived ODBC provider capabilities.</span></span> <span data-ttu-id="c5591-116">最新の ODBC プロバイダーの場合、これは、パラメーターを設定した INSERT ステートメントを準備し、行方向の配列パラメーター バインドを使用する方法です (このとき、配列のサイズは **BatchSize** プロパティによって制御します)。</span><span class="sxs-lookup"><span data-stu-id="c5591-116">For most modern ODBC providers, this would mean preparing an INSERT statement with parameters and then using a row-wise array parameter binding (where the array size is controlled by the **BatchSize** property).</span></span> <span data-ttu-id="c5591-117">**[バッチ]** を選択したが、この方法がプロバイダーでサポートされていない場合、ODBC 入力先は自動的に **[行ごと]** モードに切り替わります。</span><span class="sxs-lookup"><span data-stu-id="c5591-117">If you select **Batch** and the provider does not support this method, the ODBC destination automatically switches to the **Row-by-row** mode.</span></span>  
  
-   <span data-ttu-id="c5591-118">**行ごと**: このモードでは、ODBC 入力先はパラメーターを設定した INSERT ステートメントを準備し、 **SQL の Execute** を使用して一度に 1 行ずつ行を挿入します。</span><span class="sxs-lookup"><span data-stu-id="c5591-118">**Row-by-row**: In this mode, the ODBC destination prepares an INSERT statement with parameters and uses **SQL Execute** to insert rows one at a time.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="c5591-119">エラー処理</span><span class="sxs-lookup"><span data-stu-id="c5591-119">Error Handling</span></span>  
 <span data-ttu-id="c5591-120">ODBC 入力先にはエラー出力があります。</span><span class="sxs-lookup"><span data-stu-id="c5591-120">The ODBC destination has an error output.</span></span> <span data-ttu-id="c5591-121">コンポーネントのエラー出力には、次の出力列があります。</span><span class="sxs-lookup"><span data-stu-id="c5591-121">The component error output includes the following output columns:</span></span>  
  
-   <span data-ttu-id="c5591-122">**エラー コード**: 現在のエラーに対応する数字です。</span><span class="sxs-lookup"><span data-stu-id="c5591-122">**Error Code**: The number that corresponds to the current error.</span></span> <span data-ttu-id="c5591-123">エラーの一覧については、ソース データベースのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5591-123">See the documentation for your source database for a list of errors.</span></span> <span data-ttu-id="c5591-124">SSIS エラー コードの一覧については、「SSIS のエラー コードおよびメッセージ リファレンス」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5591-124">For a list of SSIS error codes, see the SSIS Error Code and Message Reference.</span></span>  
  
-   <span data-ttu-id="c5591-125">**エラー列**: (変換エラーの) エラーの原因となるソース列。</span><span class="sxs-lookup"><span data-stu-id="c5591-125">**Error Column**: The source column causing the error (for conversion errors).</span></span>  
  
-   <span data-ttu-id="c5591-126">標準出力データ列。</span><span class="sxs-lookup"><span data-stu-id="c5591-126">The standard output data columns.</span></span>  
  
 <span data-ttu-id="c5591-127">ODBC 入力先は、エラー動作の設定に応じて、抽出処理中に発生したエラー (データ変換、切り捨て) をエラー出力に返します。</span><span class="sxs-lookup"><span data-stu-id="c5591-127">Depending on the error behavior setting, the ODBC destination supports returning errors (data conversion, truncation) that occur during the extraction process in the error output.</span></span> <span data-ttu-id="c5591-128">詳細については、「[CDC ソース エディター &#40;[エラー出力] ページ&#41;](../odbc-source-editor-error-output-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5591-128">For more information, see [ODBC Source Editor &#40;Error Output Page&#41;](../odbc-source-editor-error-output-page.md).</span></span>  
  
## <a name="parallelism"></a><span data-ttu-id="c5591-129">Parallelism</span><span class="sxs-lookup"><span data-stu-id="c5591-129">Parallelism</span></span>  
 <span data-ttu-id="c5591-130">並列実行できる ODBC 入力先コンポーネントの数に制限はありません。これは、同一テーブル上にある場合または異なるテーブル上にある場合、同一コンピューター上で実行する場合または異なるコンピューター上で実行する場合のいずれにも該当します (ただし、通常のグローバルなセッション制限を除きます)。</span><span class="sxs-lookup"><span data-stu-id="c5591-130">There is no limitation on the number of ODBC destination components that can run in parallel against the same table or different tables, on the same machine or on different machines (other than normal global session limits).</span></span>  
  
 <span data-ttu-id="c5591-131">ただし、使用する ODBC プロバイダーの制限によって、プロバイダーを介するコンカレント接続数が制限される場合があります。</span><span class="sxs-lookup"><span data-stu-id="c5591-131">However, limitations of the ODBC provider being used may restrict the number of concurrent connections through the provider.</span></span> <span data-ttu-id="c5591-132">これらの制限によって、ODBC 入力先で使用できる並列インスタンス数のサポートが制限されます。</span><span class="sxs-lookup"><span data-stu-id="c5591-132">These limitations limit the number of supported parallel instances possible for the ODBC destination.</span></span> <span data-ttu-id="c5591-133">SSIS プロバイダーは、使用される ODBC プロバイダーの制限を把握し、SSIS パッケージを作成する際に考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5591-133">The SSIS developer must be aware of the limitations of any ODBC provider being used and take them into consideration when building SSIS packages.</span></span>  
  
 <span data-ttu-id="c5591-134">また、同一テーブルへの同時読み込みの場合、標準のレコード ロックのためにパフォーマンスが低下することがある点についても理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5591-134">You must also be aware that concurrently loading into the same table may reduce performance because of standard record locking.</span></span> <span data-ttu-id="c5591-135">これは、読み込まれているデータとテーブルの編成によって異なります。</span><span class="sxs-lookup"><span data-stu-id="c5591-135">This depends on the data being loaded and on the table organization.</span></span>  
  
## <a name="troubleshooting-the-odbc-destination"></a><span data-ttu-id="c5591-136">ODBC 入力先のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="c5591-136">Troubleshooting the ODBC Destination</span></span>  
 <span data-ttu-id="c5591-137">ODBC 入力元による外部データ プロバイダーの呼び出しをログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="c5591-137">You can log the calls that the ODBC source makes to external data providers.</span></span> <span data-ttu-id="c5591-138">このログ機能を使用すると、ODBC 入力先による外部データ ソースへのデータ保存に関するトラブルシューティングを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c5591-138">You can use this logging capability to troubleshoot the saving of data to external data sources that the ODBC destination performs.</span></span> <span data-ttu-id="c5591-139">ODBC 入力先による外部データ プロバイダーの呼び出しをログに記録するには、ODBC ドライバー マネージャーによるトレースを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c5591-139">To log the calls that the ODBC destination makes to external data providers, enable the ODBC driver manager trace.</span></span> <span data-ttu-id="c5591-140">詳細については、「 *ODBC で ODBC トレースを生成する方法 (データ ソース管理者向け)* 」 の Microsoft のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5591-140">For more information, see the Microsoft documentation on *How To Generate an ODBC Trace with ODBC the Data Source Administrator*.</span></span>  
  
## <a name="configuring-the-odbc-destination"></a><span data-ttu-id="c5591-141">ODBC 入力先の構成</span><span class="sxs-lookup"><span data-stu-id="c5591-141">Configuring the ODBC Destination</span></span>  
 <span data-ttu-id="c5591-142">ODBC 入力先は、プログラムによって、または SSIS デザイナーを使用して構成できます。</span><span class="sxs-lookup"><span data-stu-id="c5591-142">You can configure the ODBC destination programatically or through the SSIS Designer</span></span>  
  
 <span data-ttu-id="c5591-143">詳細については、次のいずれかのトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5591-143">For more information, see one of the following topics:</span></span>  
  
-   <span data-ttu-id="c5591-144">[ODBC 変換先エディター &#40;[接続マネージャー] ページ&#41;](../odbc-destination-editor-connection-manager-page.md)</span><span class="sxs-lookup"><span data-stu-id="c5591-144">[ODBC Destination Editor &#40;Connection Manager Page&#41;](../odbc-destination-editor-connection-manager-page.md)</span></span>  
  
-   <span data-ttu-id="c5591-145">[ODBC 変換先エディター &#40;[マッピング] ページ&#41;](../odbc-destination-editor-mappings-page.md)</span><span class="sxs-lookup"><span data-stu-id="c5591-145">[ODBC Destination Editor &#40;Mappings Page&#41;](../odbc-destination-editor-mappings-page.md)</span></span>  
  
-   <span data-ttu-id="c5591-146">[ODBC 変換先エディター &#40;[エラー出力] ページ&#41;](../odbc-destination-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="c5591-146">[ODBC Destination Editor &#40;Error Output Page&#41;](../odbc-destination-editor-error-output-page.md)</span></span>  
  
 <span data-ttu-id="c5591-147">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c5591-147">The **Advanced Editor** dialog box contains the properties that can be set programmatically.</span></span>  
  
 <span data-ttu-id="c5591-148">**[詳細エディター]** ダイアログ ボックスを開くには、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="c5591-148">To open the **Advanced Editor** dialog box:</span></span>  
  
-   <span data-ttu-id="c5591-149">**プロジェクトの** [データ フロー] [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 画面で、ODBC 入力先を右クリックし、 **[詳細エディターの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5591-149">In the **Data Flow** screen of your [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project, right click the ODBC destination and select **Show Advanced Editor**.</span></span>  
  
 <span data-ttu-id="c5591-150">[詳細エディター] ダイアログ ボックスで設定できるプロパティの詳細については、「 [ODBC 入力先のカスタム プロパティ](odbc-destination-custom-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5591-150">For more information about the properties that you can set in the Advanced Editor dialog box, see [ODBC Destination Custom Properties](odbc-destination-custom-properties.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c5591-151">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c5591-151">In This Section</span></span>  
  
-   <span data-ttu-id="c5591-152">[ODBC 変換先エディター &#40;[エラー出力] ページ&#41;](../odbc-destination-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="c5591-152">[ODBC Destination Editor &#40;Error Output Page&#41;](../odbc-destination-editor-error-output-page.md)</span></span>  
  
-   <span data-ttu-id="c5591-153">[ODBC 変換先エディター &#40;[マッピング] ページ&#41;](../odbc-destination-editor-mappings-page.md)</span><span class="sxs-lookup"><span data-stu-id="c5591-153">[ODBC Destination Editor &#40;Mappings Page&#41;](../odbc-destination-editor-mappings-page.md)</span></span>  
  
-   <span data-ttu-id="c5591-154">[ODBC 変換先エディター &#40;[接続マネージャー] ページ&#41;](../odbc-destination-editor-connection-manager-page.md)</span><span class="sxs-lookup"><span data-stu-id="c5591-154">[ODBC Destination Editor &#40;Connection Manager Page&#41;](../odbc-destination-editor-connection-manager-page.md)</span></span>  
  
-   [<span data-ttu-id="c5591-155">ODBC 変換先を使用したデータ読み込み</span><span class="sxs-lookup"><span data-stu-id="c5591-155">Load Data by Using the ODBC Destination</span></span>](odbc-destination.md)  
  
-   [<span data-ttu-id="c5591-156">ODBC 変換先のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="c5591-156">ODBC Destination Custom Properties</span></span>](odbc-destination-custom-properties.md)  
  
  
