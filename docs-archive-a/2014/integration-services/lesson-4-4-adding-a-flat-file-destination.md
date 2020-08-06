---
title: '手順 4 : フラット ファイル変換先の追加 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f4088de3-16d8-419c-96a1-a2cd005d0a5b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eff65f4a94a412d55af8055e302195f87ae4cdb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720241"
---
# <a name="step-4-adding-a-flat-file-destination"></a><span data-ttu-id="39b13-102">手順 4:フラット ファイル変換先の追加</span><span class="sxs-lookup"><span data-stu-id="39b13-102">Step 4: Adding a Flat File Destination</span></span>
  <span data-ttu-id="39b13-103">Lookup Currency Key 変換のエラー出力では、参照操作に失敗したデータ行がスクリプト変換にリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="39b13-103">The error output of the Lookup Currency Key transformation redirects to the Script transformation any data rows that failed the lookup operation.</span></span> <span data-ttu-id="39b13-104">スクリプト変換ではスクリプトが実行され、発生したエラーに関するさらに詳しい情報を記述したエラーの説明が取得されます。</span><span class="sxs-lookup"><span data-stu-id="39b13-104">To enhance information about the errors that occurred, the Script transformation runs a script that gets the description of errors.</span></span>  
  
 <span data-ttu-id="39b13-105">ここでは、後の処理に向けて、失敗した行に関するすべての情報を区切りファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="39b13-105">In this task, you will save all this information about the failed rows to a delimited file for later processing.</span></span> <span data-ttu-id="39b13-106">失敗した行を保存するには、フラット ファイル接続マネージャーで、フラット ファイル変換先を追加し、エラー データを保存するテキスト ファイルを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b13-106">To save the failed rows, you must add and configure a Flat File connection manager for the text file that will contain the error data and a Flat File destination.</span></span> <span data-ttu-id="39b13-107">フラット ファイル変換先が使用するフラット ファイル接続マネージャーでプロパティを設定することにより、フラット ファイル変換先がテキスト ファイルをフォーマットする方法と書き込む方法を指定できます。</span><span class="sxs-lookup"><span data-stu-id="39b13-107">By setting properties on the Flat File connection manager that the Flat File destination uses, you can specify how the Flat File destination formats and writes the text file.</span></span> <span data-ttu-id="39b13-108">詳細については、「[フラットファイル接続マネージャー](connection-manager/file-connection-manager.md) 」および「[フラットファイル変換先](data-flow/flat-file-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b13-108">For more information, see [Flat File Connection Manager](connection-manager/file-connection-manager.md) and [Flat File Destination](data-flow/flat-file-destination.md).</span></span>  
  
### <a name="to-add-and-configure-a-flat-file-destination"></a><span data-ttu-id="39b13-109">新しいフラット ファイルを追加し、エラー データが読み込まれるように構成するには</span><span class="sxs-lookup"><span data-stu-id="39b13-109">To add and configure a Flat File destination</span></span>  
  
1.  <span data-ttu-id="39b13-110">**[データ フロー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="39b13-110">Click the **Data Flow** tab.</span></span>  
  
2.  <span data-ttu-id="39b13-111">**[SSIS ツールボックス]** で **[その他]** を展開し、 **[フラット ファイル変換先]** をデータ フロー デザイン画面上にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="39b13-111">In the **SSIS Toolbox**, expand **Other**, and drag **Flat File Destination** onto the data flow design surface.</span></span> <span data-ttu-id="39b13-112">**[フラット ファイル変換先]** を **[Get Error Description]** 変換のすぐ下にドロップします。</span><span class="sxs-lookup"><span data-stu-id="39b13-112">Put the **Flat File Destination** directly underneath the **Get Error Description** transformation.</span></span>  
  
3.  <span data-ttu-id="39b13-113">**[Get Error Description]** 変換をクリックし、緑の矢印を新しい **[フラット ファイル変換先]** までドラッグします。</span><span class="sxs-lookup"><span data-stu-id="39b13-113">Click the **Get Error Description** transformation, and then drag the green arrow onto the new **Flat File Destination**.</span></span>  
  
4.  <span data-ttu-id="39b13-114">**[データ フロー]** デザイン画面で、新しく追加した **[フラット ファイル変換先]** 変換の **[フラット ファイル変換先]** をクリックし、名前を **Failed Rows**に変更します。</span><span class="sxs-lookup"><span data-stu-id="39b13-114">On the **Data Flow** design surface, click **Flat File Destination** in the newly added **Flat File Destination** transformation, and change the name to **Failed Rows**.</span></span>  
  
5.  <span data-ttu-id="39b13-115">この **Failed Rows** 変換を右クリックし、 **[編集]** をクリックします。次に、 **[フラット ファイル変換先エディター]** の **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39b13-115">Right-click the **Failed Rows** transformation, click **Edit**, and then in the **Flat File Destination Editor**, click **New**.</span></span>  
  
6.  <span data-ttu-id="39b13-116">**[フラット ファイル形式]** ダイアログ ボックスで、 **[区切り記号]** が選択されていることを確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39b13-116">In the **Flat File Format** dialog box, verify that **Delimited** is selected, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="39b13-117">[**フラットファイル接続マネージャーエディター**] の [**接続マネージャー名**] ボックスに、「」と入力 `Error Data` します。</span><span class="sxs-lookup"><span data-stu-id="39b13-117">In the **Flat File Connection Manager Editor**, in the **Connection Manager Name** box type `Error Data`.</span></span>  
  
8.  <span data-ttu-id="39b13-118">**[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスで、 **[参照]** をクリックし、ファイルの保存先のフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="39b13-118">In the **Flat File Connection Manager Editor** dialog box, click **Browse**, and locate the folder in which to store the file.</span></span>  
  
9. <span data-ttu-id="39b13-119">[**開く**] ダイアログボックスの [**ファイル名**] に「」と入力し、 `ErrorOutput.txt` [**開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39b13-119">In the **Open** dialog box, for **File name**, type `ErrorOutput.txt`, and then click **Open**.</span></span>  
  
10. <span data-ttu-id="39b13-120">**[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスで、 **[ロケール]** ボックスに [英語 (米国)]、 **[コード ページ]** に [1252 (ANSI - ラテン I)] が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="39b13-120">In the **Flat File Connection Manager Editor** dialog box, verify that the **Locale** box contains English (United States) and **Code page** contains 1252 (ANSI -Latin I).</span></span>  
  
11. <span data-ttu-id="39b13-121">[オプション] ペインで、 **[列]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39b13-121">In the options pane, click **Columns**.</span></span>  
  
     <span data-ttu-id="39b13-122">変換元データ ファイルの列に加え、新しい 3 つの列 (ErrorCode、ErrorColumn、および ErrorDescription) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="39b13-122">Notice that, in addition to the columns from the source data file, three new columns are present: ErrorCode, ErrorColumn, and ErrorDescription.</span></span> <span data-ttu-id="39b13-123">これらの列は、Lookup Currency Key 変換のエラー出力と Get Error Description 変換のスクリプトによって生成されたものです。これらの列は、失敗した行の問題を解決するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="39b13-123">These columns are generated by the error output of the Lookup Currency Key transformation and by the script in the Get Error Description transformation, and can be used to troubleshoot the cause of the failed row.</span></span>  
  
12. <span data-ttu-id="39b13-124">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39b13-124">Click **OK**.</span></span>  
  
13. <span data-ttu-id="39b13-125">**[フラット ファイル変換先エディター]** で、 **[ファイル内のデータを上書きする]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="39b13-125">In the **Flat File Destination Editor**, clear the **Overwrite data in the file** check box.</span></span>  
  
     <span data-ttu-id="39b13-126">このチェック ボックスをオフにすると、複数のパッケージ実行でエラーが継続します。</span><span class="sxs-lookup"><span data-stu-id="39b13-126">Clearing this check box persists the errors over multiple package executions.</span></span>  
  
14. <span data-ttu-id="39b13-127">**[フラット ファイル変換先エディター]** の **[マッピング]** をクリックし、すべての列が正しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="39b13-127">In the **Flat File Destination Editor**, click **Mappings** to verify that all the columns are correct.</span></span> <span data-ttu-id="39b13-128">必要に応じて、変換先の列の名前を変更できます。</span><span class="sxs-lookup"><span data-stu-id="39b13-128">Optionally, you can rename the columns in the destination.</span></span>  
  
15. <span data-ttu-id="39b13-129">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39b13-129">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="39b13-130">次の手順</span><span class="sxs-lookup"><span data-stu-id="39b13-130">Next Steps</span></span>  
 [<span data-ttu-id="39b13-131">手順 5:レッスン 4 のチュートリアル パッケージのテスト</span><span class="sxs-lookup"><span data-stu-id="39b13-131">Step 5: Testing the Lesson 4 Tutorial Package</span></span>](../integration-services/lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
  
