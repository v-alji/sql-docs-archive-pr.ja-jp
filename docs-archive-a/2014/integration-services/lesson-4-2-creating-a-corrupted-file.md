---
title: '手順 2: 破損ファイルの作成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: cd0b18dc-66c3-4d88-86ef-8e40cb660fae
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0dd5fbe942774192881489e9ea430672f9da5083
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640138"
---
# <a name="step-2-creating-a-corrupted-file"></a><span data-ttu-id="8fd12-102">手順 2:破損ファイルの作成</span><span class="sxs-lookup"><span data-stu-id="8fd12-102">Step 2: Creating a Corrupted File</span></span>
  <span data-ttu-id="8fd12-103">変換エラーの構成と処理を体験するために、コンポーネントの処理が失敗するサンプル フラット ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="8fd12-103">In order to demonstrate the configuration and handling of transformation errors, you will have to create a sample flat file that when processed causes a component to fail.</span></span>  
  
 <span data-ttu-id="8fd12-104">この実習では、既存のサンプル フラット ファイルのコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="8fd12-104">In this task, you will create a copy of an existing sample flat file.</span></span> <span data-ttu-id="8fd12-105">その後、このファイルをメモ帳などで開き、 **CurrencyID** 列を編集して、参照変換中に照合が失敗するようにします。</span><span class="sxs-lookup"><span data-stu-id="8fd12-105">You will then open the file in Notepad and edit the **CurrencyID** column to ensure that it will fail to produce a match during the transformations lookup.</span></span> <span data-ttu-id="8fd12-106">新しいファイルの処理時、参照が失敗すると Lookup Currency Key 変換は失敗し、それ以降のパッケージも失敗します。</span><span class="sxs-lookup"><span data-stu-id="8fd12-106">When the new file is processed, the lookup failure will cause the Currency Key Lookup transformation to fail and therefore fail the rest of the package.</span></span> <span data-ttu-id="8fd12-107">破損しているサンプル ファイルを作成したら、パッケージを実行して、パッケージのエラーを確認します。</span><span class="sxs-lookup"><span data-stu-id="8fd12-107">After you have created the corrupted sample file, you will run the package to view the package failure.</span></span>  
  
### <a name="to-create-a-corrupted-sample-flat-file"></a><span data-ttu-id="8fd12-108">破損しているサンプル フラット ファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="8fd12-108">To create a corrupted sample flat file</span></span>  
  
1.  <span data-ttu-id="8fd12-109">メモ帳などのテキスト エディターで Currency_VEB.txt ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="8fd12-109">In Notepad or any other text editor, open the Currency_VEB.txt file.</span></span>  
  
     <span data-ttu-id="8fd12-110">このサンプル データは、SSIS のレッスン パッケージに含まれています。</span><span class="sxs-lookup"><span data-stu-id="8fd12-110">The sample data is included with the SSIS Lesson packages.</span></span> <span data-ttu-id="8fd12-111">サンプル データとレッスン パッケージをダウンロードするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="8fd12-111">To download the sample data and the lesson packages, do the following.</span></span>  
  
    1.  <span data-ttu-id="8fd12-112">[Integration Services 製品サンプル](https://go.microsoft.com/fwlink/?LinkID=267527)に移動します。</span><span class="sxs-lookup"><span data-stu-id="8fd12-112">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkID=267527).</span></span>  
  
    2.  <span data-ttu-id="8fd12-113">[**ダウンロード**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8fd12-113">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="8fd12-114">SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip ファイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8fd12-114">Click the SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
2.  <span data-ttu-id="8fd12-115">テキストエディターの検索と置換機能を使用して、のすべてのインスタンスを検索 `VEB` し、それらをに置き換え `BAD` ます。</span><span class="sxs-lookup"><span data-stu-id="8fd12-115">Use the text editor's find and replace feature to find all instances of `VEB` and replace them with `BAD`.</span></span>  
  
3.  <span data-ttu-id="8fd12-116">他のサンプルデータファイルと同じフォルダーで、変更したファイルをとして保存し `Currency_BAD.txt` ます。</span><span class="sxs-lookup"><span data-stu-id="8fd12-116">In the same folder as the other sample data files, save the modified file as `Currency_BAD.txt`.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="8fd12-117">`Currency_BAD.txt`が他のサンプルデータファイルと同じフォルダーに保存されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8fd12-117">Make sure that `Currency_BAD.txt` is saved the same folder as the other sample data files.</span></span>  
  
4.  <span data-ttu-id="8fd12-118">テキスト エディターを閉じます。</span><span class="sxs-lookup"><span data-stu-id="8fd12-118">Close your text editor.</span></span>  
  
### <a name="to-verify-that-an-error-will-occur-during-run-time"></a><span data-ttu-id="8fd12-119">実行時にエラーが発生することを確認するには</span><span class="sxs-lookup"><span data-stu-id="8fd12-119">To verify that an error will occur during run time</span></span>  
  
1.  <span data-ttu-id="8fd12-120">**[デバッグ]** メニューの **[デバッグの開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8fd12-120">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="8fd12-121">データ フローの 3 つ目の反復処理で、Lookup Currency Key 変換が Currency_BAD.txt ファイルを処理しようとし、変換が失敗します。</span><span class="sxs-lookup"><span data-stu-id="8fd12-121">On the third iteration of the data flow, the Lookup Currency Key transformation tries to process the Currency_BAD.txt file, and the transformation will fail.</span></span> <span data-ttu-id="8fd12-122">この変換エラーにより、パッケージ全体が失敗します。</span><span class="sxs-lookup"><span data-stu-id="8fd12-122">The failure of the transformation will cause the whole package to fail.</span></span>  
  
2.  <span data-ttu-id="8fd12-123">**[デバッグ]** メニューの **[デバッグの停止]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8fd12-123">On the **Debug** menu, click **Stop Debugging**.</span></span>  
  
3.  <span data-ttu-id="8fd12-124">デザイン画面で、 **[実行結果]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8fd12-124">On the design surface, click the **Execution Results** tab.</span></span>  
  
4.  <span data-ttu-id="8fd12-125">ログの内容を参照し、次の処理不能エラーが発生していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8fd12-125">Browse through the log and verify that the following unhandled error occurred:</span></span>  
  
     `[Lookup Currency Key[27]] Error: Row yielded no match during lookup.`  
  
    > [!NOTE]  
    >  <span data-ttu-id="8fd12-126">数値 27 はコンポーネントの ID です。</span><span class="sxs-lookup"><span data-stu-id="8fd12-126">The number 27 is the ID of the component.</span></span> <span data-ttu-id="8fd12-127">この値はデータ フローを構築したときに割り当てられるもので、パッケージの値とは異なることがあります。</span><span class="sxs-lookup"><span data-stu-id="8fd12-127">This value is assigned when you build the data flow, and the value in your package may be different.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8fd12-128">次の手順</span><span class="sxs-lookup"><span data-stu-id="8fd12-128">Next Steps</span></span>  
 [<span data-ttu-id="8fd12-129">手順 3:エラー フロー リダイレクトの追加</span><span class="sxs-lookup"><span data-stu-id="8fd12-129">Step 3: Adding Error Flow Redirection</span></span>](lesson-4-3-adding-error-flow-redirection.md)  
  
  
