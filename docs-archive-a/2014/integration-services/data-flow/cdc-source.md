---
title: CDC ソース | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsource.f1
ms.assetid: 99775608-e177-44ed-bb44-aaccb0f4f327
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 064c25b129364dfcd813d71a462586303dd4ff60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644585"
---
# <a name="cdc-source"></a><span data-ttu-id="f057c-102">CDC ソース</span><span class="sxs-lookup"><span data-stu-id="f057c-102">CDC Source</span></span>
  <span data-ttu-id="f057c-103">CDC ソースは [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 変更テーブルから変更データの範囲を読み取り、変更内容を下流の他の SSIS コンポーネントに伝えます。</span><span class="sxs-lookup"><span data-stu-id="f057c-103">The CDC source reads a range of change data from [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] change tables and delivers the changes downstream to other SSIS components.</span></span>  
  
 <span data-ttu-id="f057c-104">CDC ソースによって読み取られた変更データの範囲は "CDC 処理範囲" と呼ばれ、現在のデータ フローの開始前に実行される CDC 制御タスクによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="f057c-104">The range of change data read by the CDC source is called the CDC Processing Range and is determine by the CDC Control task that is executed before the current data flow starts.</span></span> <span data-ttu-id="f057c-105">CDC 処理範囲は、テーブル グループの CDC 処理の状態を保持するパッケージ変数の値から導き出されます。</span><span class="sxs-lookup"><span data-stu-id="f057c-105">The CDC Processing Range is derived from the value of a package variable that maintains the state of the CDC processing for a group of tables.</span></span>  
  
 <span data-ttu-id="f057c-106">CDC ソースは、データベース テーブル、ビュー、または SQL ステートメントを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースからデータを抽出します。</span><span class="sxs-lookup"><span data-stu-id="f057c-106">The CDC source extracts data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database by using a database table, a view, or an SQL statement.</span></span>  
  
 <span data-ttu-id="f057c-107">CDC ソースは、次の構成を使用します。</span><span class="sxs-lookup"><span data-stu-id="f057c-107">The CDC source uses the following configurations:</span></span>  
  
-   <span data-ttu-id="f057c-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC データベースにアクセスするための、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ADO.NET 接続マネージャー。</span><span class="sxs-lookup"><span data-stu-id="f057c-108">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ADO.NET connection manager to access the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC database.</span></span> <span data-ttu-id="f057c-109">CDC ソース接続を構成する方法の詳細については、「 [[CDC ソース エディター] &#40;[接続マネージャー] ページ&#41;](../cdc-source-editor-connection-manager-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f057c-109">For more information about configuring the CDC source connection, see [CDC Source Editor &#40;Connection Manager Page&#41;](../cdc-source-editor-connection-manager-page.md).</span></span>  
  
-   <span data-ttu-id="f057c-110">CDC のために有効にされたテーブル。</span><span class="sxs-lookup"><span data-stu-id="f057c-110">A table enabled for CDC.</span></span>  
  
-   <span data-ttu-id="f057c-111">選択したテーブルのキャプチャ インスタンスの名前 (複数存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="f057c-111">The name of the capture instance of the selected table (if more-than-one exists).</span></span>  
  
-   <span data-ttu-id="f057c-112">変更処理モード。</span><span class="sxs-lookup"><span data-stu-id="f057c-112">The change processing mode.</span></span>  
  
-   <span data-ttu-id="f057c-113">CDC 処理範囲が決定される基になる、CDC 状態パッケージ変数の名前。</span><span class="sxs-lookup"><span data-stu-id="f057c-113">The name of the CDC state package variable based on which the CDC Processing range is determined.</span></span> <span data-ttu-id="f057c-114">CDC ソースによって、その変数が変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="f057c-114">The CDC source does not modify that variable.</span></span>  
  
 <span data-ttu-id="f057c-115">CDC ソースによって返されるデータは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC 関数の **cdc.fn_cdc_get_all_changes_\<capture-instance-name>** または **cdc.fn_cdc_get_net_changes_\<capture-instance-name>** (使用できる場合) によって返されるデータと同じです。</span><span class="sxs-lookup"><span data-stu-id="f057c-115">The data returned by the CDC Source is the same as that returned by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC functions **cdc.fn_cdc_get_all_changes_\<capture-instance-name>** or **cdc.fn_cdc_get_net_changes_\<capture-instance-name>** (when available).</span></span> <span data-ttu-id="f057c-116">唯一、必要に応じて追加できる列として **__$initial_processing** があります。この列は、現在の処理範囲がテーブルの初期読み込みの範囲と重複できるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="f057c-116">The only optional addition is the column, **__$initial_processing** that indicates whether the current processing range can overlap with an initial load of the table.</span></span> <span data-ttu-id="f057c-117">初期処理の詳細については、「 [CDC 制御タスク](../control-flow/cdc-control-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f057c-117">For more information about initial processing, see [CDC Control Task](../control-flow/cdc-control-task.md).</span></span>  
  
 <span data-ttu-id="f057c-118">CDC ソースには、1 つの標準出力と 1 つのエラー出力があります。</span><span class="sxs-lookup"><span data-stu-id="f057c-118">The CDC source has one regular output and one error output.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="f057c-119">エラー処理</span><span class="sxs-lookup"><span data-stu-id="f057c-119">Error Handling</span></span>  
 <span data-ttu-id="f057c-120">CDC ソースにはエラー出力があります。</span><span class="sxs-lookup"><span data-stu-id="f057c-120">The CDC source has an error output.</span></span> <span data-ttu-id="f057c-121">コンポーネントのエラー出力には、次の出力列があります。</span><span class="sxs-lookup"><span data-stu-id="f057c-121">The component error output includes the following output columns:</span></span>  
  
-   <span data-ttu-id="f057c-122">**エラー コード**: 値は常に -1 です。</span><span class="sxs-lookup"><span data-stu-id="f057c-122">**Error Code**: The value is always -1.</span></span>  
  
-   <span data-ttu-id="f057c-123">**エラー列**: (変換エラーの) エラーの原因となるソース列。</span><span class="sxs-lookup"><span data-stu-id="f057c-123">**Error Column**: The source column causing the error (for conversion errors).</span></span>  
  
-   <span data-ttu-id="f057c-124">**エラー行の列**: エラーの原因となったレコード データ。</span><span class="sxs-lookup"><span data-stu-id="f057c-124">**Error Row Columns**: The record data that causes the error.</span></span>  
  
 <span data-ttu-id="f057c-125">CDC ソースは、エラー動作の設定に応じて、抽出処理中に発生したエラー (データ変換、切り捨て) をエラー出力に返します。</span><span class="sxs-lookup"><span data-stu-id="f057c-125">Depending on the error behavior setting, the CDC source supports returning errors (data conversion, truncation) that occur during the extraction process in the error output.</span></span> <span data-ttu-id="f057c-126">詳細については、「 [[CDC ソース エディター] &#40;[エラー出力] ページ&#41;](../cdc-source-editor-error-output-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f057c-126">For more information, see [CDC Source Editor &#40;Error Output Page&#41;](../cdc-source-editor-error-output-page.md).</span></span>  
  
## <a name="data-type-support"></a><span data-ttu-id="f057c-127">データ型のサポート</span><span class="sxs-lookup"><span data-stu-id="f057c-127">Data Type Support</span></span>  
 <span data-ttu-id="f057c-128">Microsoft の CDC ソース コンポーネントはすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型をサポートし、SSIS データ型に正確にマッピングします。</span><span class="sxs-lookup"><span data-stu-id="f057c-128">The CDC source component for Microsoft supports all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, which are mapped to the correct SSIS data types.</span></span>  
  
## <a name="troubleshooting-the-cdc-source"></a><span data-ttu-id="f057c-129">CDC ソースのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="f057c-129">Troubleshooting the CDC Source</span></span>  
 <span data-ttu-id="f057c-130">以下に、CDC ソースのトラブルシューティング情報を示します。</span><span class="sxs-lookup"><span data-stu-id="f057c-130">The following contains information on troubleshooting the CDC source.</span></span>  
  
### <a name="use-this-script-to-isolate-problems-and-reproduce-them-in-sql-server-management-studio"></a><span data-ttu-id="f057c-131">このスクリプトを使用して問題を特定し、SQL Server Management Studio で再現する</span><span class="sxs-lookup"><span data-stu-id="f057c-131">Use this script to isolate problems and reproduce them in SQL Server Management Studio</span></span>  
 <span data-ttu-id="f057c-132">CDC ソース操作は、CDC ソースを呼び出す前に実行される CDC 制御タスク操作によって管理されます。</span><span class="sxs-lookup"><span data-stu-id="f057c-132">The CDC source operation is governed by the operation of the CDC Control task executed before invoking the CDC source.</span></span> <span data-ttu-id="f057c-133">CDC 制御タスクは、開始 LSN と終了 LSN が保存されている CDC 状態パッケージ変数の値を比較します。</span><span class="sxs-lookup"><span data-stu-id="f057c-133">The CDC Control task prepares the value of the CDC state package variable to contain the start and end LSNs.</span></span> <span data-ttu-id="f057c-134">CDC 制御タスクは、次のスクリプトに相当する関数を実行します。</span><span class="sxs-lookup"><span data-stu-id="f057c-134">It performs function equivalent to the following script:</span></span>  
  
```  
use <cdc-enabled-database-name>  
               declare @start_lsn binary(10), @end_lsn binary(10)  
               set @start_lsn = sys.fn_cdc_increment_lsn(  
                       convert(binary(10),'0x' + '<value-from-state-cs>', 1))  
               set @end_lsn =   
                       convert(binary(10),'0x' + '<value-from-state-ce>', 1)  
               select * from cdc.fn_cdc_get_net_changes_dbo_Table1(@start_lsn,  
@end_lsn, '<mode>')  
```  
  
 <span data-ttu-id="f057c-135">各値の説明:</span><span class="sxs-lookup"><span data-stu-id="f057c-135">where:</span></span>  
  
-   <span data-ttu-id="f057c-136">\<cdc-enabled-database-name> は、変更テーブルが含まれる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースの名前です。</span><span class="sxs-lookup"><span data-stu-id="f057c-136">\<cdc-enabled-database-name> is the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database containing the change tables.</span></span>  
  
-   <span data-ttu-id="f057c-137">\<value-from-state-cs> は、CDC 状態変数に、CS/\<value-from-state-cs>/ として示される値です (CS は Current-processing-range-Start (現在の処理範囲の開始) の略語です)。</span><span class="sxs-lookup"><span data-stu-id="f057c-137">\<value-from-state-cs> is the value that appears in the CDC state variable as CS/\<value-from-state-cs>/ (CS stands for Current-processing-range-Start).</span></span>  
  
-   <span data-ttu-id="f057c-138">\<value-from-state-ce> は、CDC 状態変数に、CE/\<value-from-state-cs>/ として示される値です (CE は Current-processing-range-End (現在の処理範囲の開始) の略語です)。</span><span class="sxs-lookup"><span data-stu-id="f057c-138">\<value-from-state-ce> is the value that appears in the CDC state variable as CE/\<value-from-state-cs>/ (CE stands for Current-processing-range-End).</span></span>  
  
-   <span data-ttu-id="f057c-139">\<mode> は、CDC の処理モードです。</span><span class="sxs-lookup"><span data-stu-id="f057c-139">\<mode> are the CDC processing modes.</span></span> <span data-ttu-id="f057c-140">この処理モードは、 **[すべて]** 、 **[古い値を含むすべて]** 、 **[差分]** 、 **[更新マスクを含む差分]** 、 **[結合を含む差分]** のいずれかの値です。</span><span class="sxs-lookup"><span data-stu-id="f057c-140">The processing modes have one of the following values **All**, **All with Old Values**, **Net**, **Net with Update Mask**, **Net with Merge**.</span></span>  
  
 <span data-ttu-id="f057c-141">このスクリプトを実行すると、エラーの再現と特定を簡単に行うことができる [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で問題を再現することによって、問題を特定できます。</span><span class="sxs-lookup"><span data-stu-id="f057c-141">This script helps isolate problems by reproducing them in the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], where it is easy to reproduce and identify errors.</span></span>  
  
#### <a name="sql-server-error-message"></a><span data-ttu-id="f057c-142">SQL Server エラー メッセージ</span><span class="sxs-lookup"><span data-stu-id="f057c-142">SQL Server Error Message</span></span>  
 <span data-ttu-id="f057c-143">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]によって、次のメッセージが返されることがあります。</span><span class="sxs-lookup"><span data-stu-id="f057c-143">The following message may be returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
 <span data-ttu-id="f057c-144">**プロシージャまたは関数 cdc.fn_cdc_get_net_changes_\<..> に指定された引数が不足しています。**</span><span class="sxs-lookup"><span data-stu-id="f057c-144">**An insufficient number of arguments were supplied for the procedure or function cdc.fn_cdc_get_net_changes_\<..>.**</span></span>  
  
 <span data-ttu-id="f057c-145">このエラーは、引数が不足していることを示すものではありません。</span><span class="sxs-lookup"><span data-stu-id="f057c-145">This error does not indicate that an argument is missing.</span></span> <span data-ttu-id="f057c-146">CDC 状態変数の開始または終了 LSN 値が無効であることを示します。</span><span class="sxs-lookup"><span data-stu-id="f057c-146">It means that the start or end LSN values in the CDC state variable are invalid.</span></span>  
  
## <a name="configuring-the-cdc-source"></a><span data-ttu-id="f057c-147">CDC ソースの構成</span><span class="sxs-lookup"><span data-stu-id="f057c-147">Configuring the CDC Source</span></span>  
 <span data-ttu-id="f057c-148">CDC ソースは、プログラムによって、または SSIS デザイナーを使用して構成できます。</span><span class="sxs-lookup"><span data-stu-id="f057c-148">You can configure the CDC source programmatically or through the SSIS Designer.</span></span>  
  
 <span data-ttu-id="f057c-149">詳細については、次のいずれかのトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f057c-149">For more information, see one of the following topics:</span></span>  
  
-   <span data-ttu-id="f057c-150">[[CDC ソース エディター] &#40;[接続マネージャー] ページ&#41;](../cdc-source-editor-connection-manager-page.md)</span><span class="sxs-lookup"><span data-stu-id="f057c-150">[CDC Source Editor &#40;Connection Manager Page&#41;](../cdc-source-editor-connection-manager-page.md)</span></span>  
  
-   <span data-ttu-id="f057c-151">[[CDC ソース エディター] &#40;[列] ページ&#41;](../cdc-source-editor-columns-page.md)</span><span class="sxs-lookup"><span data-stu-id="f057c-151">[CDC Source Editor &#40;Columns Page&#41;](../cdc-source-editor-columns-page.md)</span></span>  
  
-   <span data-ttu-id="f057c-152">[CDC ソース エディター &#40;[エラー出力] ページ&#41;](../cdc-source-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="f057c-152">[CDC Source Editor &#40;Error Output Page&#41;](../cdc-source-editor-error-output-page.md)</span></span>  
  
 <span data-ttu-id="f057c-153">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f057c-153">The **Advanced Editor** dialog box contains the properties that can be set programmatically.</span></span>  
  
 <span data-ttu-id="f057c-154">**[詳細エディター]** ダイアログ ボックスを開くには、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="f057c-154">To open the **Advanced Editor** dialog box:</span></span>  
  
-   <span data-ttu-id="f057c-155">**プロジェクトの** [データ フロー] [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 画面で、CDC ソースを右クリックし、 **[詳細エディターの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f057c-155">In the **Data Flow** screen of your [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project, right click the CDC source and select **Show Advanced Editor**.</span></span>  
  
 <span data-ttu-id="f057c-156">**[詳細エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、「 [CDC ソースのカスタム プロパティ](cdc-source-custom-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f057c-156">For more information about the properties that you can set in the **Advanced Editor** dialog box, see [CDC Source Custom Properties](cdc-source-custom-properties.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f057c-157">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f057c-157">In This Section</span></span>  
  
-   <span data-ttu-id="f057c-158">[[CDC ソース エディター] &#40;[接続マネージャー] ページ&#41;](../cdc-source-editor-connection-manager-page.md)</span><span class="sxs-lookup"><span data-stu-id="f057c-158">[CDC Source Editor &#40;Connection Manager Page&#41;](../cdc-source-editor-connection-manager-page.md)</span></span>  
  
-   <span data-ttu-id="f057c-159">[[CDC ソース エディター] &#40;[列] ページ&#41;](../cdc-source-editor-columns-page.md)</span><span class="sxs-lookup"><span data-stu-id="f057c-159">[CDC Source Editor &#40;Columns Page&#41;](../cdc-source-editor-columns-page.md)</span></span>  
  
-   <span data-ttu-id="f057c-160">[CDC ソース エディター &#40;[エラー出力] ページ&#41;](../cdc-source-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="f057c-160">[CDC Source Editor &#40;Error Output Page&#41;](../cdc-source-editor-error-output-page.md)</span></span>  
  
-   [<span data-ttu-id="f057c-161">CDC ソースのカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="f057c-161">CDC Source Custom Properties</span></span>](cdc-source-custom-properties.md)  
  
-   [<span data-ttu-id="f057c-162">CDC ソースを使用した変更データ抽出</span><span class="sxs-lookup"><span data-stu-id="f057c-162">Extract Change Data Using the CDC Source</span></span>](cdc-source.md)  
  
## <a name="related-content"></a><span data-ttu-id="f057c-163">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="f057c-163">Related Content</span></span>  
  
-   <span data-ttu-id="f057c-164">mattmasson.com のブログ「 [CDC ソースの処理モード](https://www.mattmasson.com/2012/01/processing-modes-for-the-cdc-source/)」</span><span class="sxs-lookup"><span data-stu-id="f057c-164">Blog entry, [Processing Modes for the CDC Source](https://www.mattmasson.com/2012/01/processing-modes-for-the-cdc-source/), on mattmasson.com.</span></span>  
  
  
