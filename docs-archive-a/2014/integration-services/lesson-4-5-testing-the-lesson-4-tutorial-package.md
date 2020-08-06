---
title: '手順 5: レッスン 4 のチュートリアル パッケージのテスト | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5f18df92-0248-4858-836b-c8b02f0e0439
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4a897f99bf68805e4e66c3b6bbe818b312077fb4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720234"
---
# <a name="step-5-testing-the-lesson-4-tutorial-package"></a><span data-ttu-id="7aeec-102">手順 5:レッスン 4 のチュートリアル パッケージのテスト</span><span class="sxs-lookup"><span data-stu-id="7aeec-102">Step 5: Testing the Lesson 4 Tutorial Package</span></span>
  <span data-ttu-id="7aeec-103">壊れているファイル Currency_BAD.txt を実行すると、CurrencyKey 参照変換の照合結果の生成に失敗します。</span><span class="sxs-lookup"><span data-stu-id="7aeec-103">At run time, the corrupted file, Currency_BAD.txt, will fail to generate a match within the Currency Key Lookup transformation.</span></span> <span data-ttu-id="7aeec-104">ただし、CurrencyKey 参照変換のエラー出力は、失敗した行を新しい [Failed Rows] 変換先へリダイレクトするように構成されています。したがって、コンポーネント自体は失敗せず、パッケージは正常に実行されます。</span><span class="sxs-lookup"><span data-stu-id="7aeec-104">Because the error output of Currency Key Lookup has now been configured to redirect failed rows to the new Failed Rows destination, the component does not fail, and the package runs successfully.</span></span> <span data-ttu-id="7aeec-105">エラーがある行はすべて、ErrorOutput.txt に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="7aeec-105">All failed error rows are written to ErrorOutput.txt.</span></span>  
  
 <span data-ttu-id="7aeec-106">この実習では、パッケージを実行して、変更したエラー出力構成をテストします。</span><span class="sxs-lookup"><span data-stu-id="7aeec-106">In this task, you will test the revised error output configuration by running the package.</span></span> <span data-ttu-id="7aeec-107">パッケージが正常に実行されたら、ErrorOutput.txt ファイルの内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="7aeec-107">Upon successful package execution, you will then view the contents of the ErrorOutput.txt file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7aeec-108">ErrorOutput.txt ファイルにエラー行が蓄積されないようにする場合は、パッケージ実行の間に手動でファイルの内容を削除してください。</span><span class="sxs-lookup"><span data-stu-id="7aeec-108">If you do not want to accumulate error rows in the ErrorOutput.txt file, you should manually delete the file content between package runs.</span></span>  
  
## <a name="checking-the-package-layout"></a><span data-ttu-id="7aeec-109">パッケージ レイアウトの確認</span><span class="sxs-lookup"><span data-stu-id="7aeec-109">Checking the Package layout</span></span>  
 <span data-ttu-id="7aeec-110">パッケージをテストする前に、次の図に示すオブジェクトがレッスン 4 のパッケージの制御フローとデータ フローに含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7aeec-110">Before you test the package you should verify that the control flow and the data flow in the Lesson 4 package contain the objects shown in the following diagrams.</span></span> <span data-ttu-id="7aeec-111">制御フローはレッスン 2 ～ 4 の制御フローと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="7aeec-111">The control flow should be identical to the control flow in lessons 2 - 4.</span></span>  
  
 <span data-ttu-id="7aeec-112">**制御フロー**</span><span class="sxs-lookup"><span data-stu-id="7aeec-112">**Control Flow**</span></span>  
  
 <span data-ttu-id="7aeec-113">![パッケージ内の制御フロー](../../2014/tutorials/media/task4lesson2control.gif "パッケージ内の制御フロー")</span><span class="sxs-lookup"><span data-stu-id="7aeec-113">![Control flow in package](../../2014/tutorials/media/task4lesson2control.gif "Control flow in package")</span></span>  
  
 <span data-ttu-id="7aeec-114">**データ フロー**</span><span class="sxs-lookup"><span data-stu-id="7aeec-114">**Data Flow**</span></span>  
  
 <span data-ttu-id="7aeec-115">![パッケージ内のデータ フロー](../../2014/tutorials/media/task5lesson5data.gif "パッケージ内のデータ フロー")</span><span class="sxs-lookup"><span data-stu-id="7aeec-115">![Data flow in package](../../2014/tutorials/media/task5lesson5data.gif "Data flow in package")</span></span>  
  
### <a name="to-run-the-lesson-4-tutorial-package"></a><span data-ttu-id="7aeec-116">レッスン 4 のチュートリアル パッケージを実行するには</span><span class="sxs-lookup"><span data-stu-id="7aeec-116">To run the Lesson 4 tutorial package</span></span>  
  
1.  <span data-ttu-id="7aeec-117">**[デバッグ]** メニューの **[デバッグの開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7aeec-117">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
2.  <span data-ttu-id="7aeec-118">パッケージの実行が完了したら、 **[デバッグ]** メニューの **[デバッグの停止]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7aeec-118">After the package has completed running, on the **Debug** menu, click **Stop Debugging**.</span></span>  
  
### <a name="to-verify-the-contents-of-the-erroroutputtxt-file"></a><span data-ttu-id="7aeec-119">ErrorOutput.txt ファイルの内容を確認するには</span><span class="sxs-lookup"><span data-stu-id="7aeec-119">To verify the contents of the ErrorOutput.txt file</span></span>  
  
-   <span data-ttu-id="7aeec-120">メモ帳などのテキスト エディターで ErrorOutput.txt ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="7aeec-120">In Notepad or any other text editor, open the ErrorOutput.txt file.</span></span> <span data-ttu-id="7aeec-121">既定の列の順序は、AverageRate、CurrencyID、CurrencyDate、EndOfDateRate、ErrorCode、ErrorColumn、ErrorDescription です。</span><span class="sxs-lookup"><span data-stu-id="7aeec-121">The default column order is: AverageRate, CurrencyID, CurrencyDate, EndOfDateRate, ErrorCode, ErrorColumn, ErrorDescription.</span></span>  
  
     <span data-ttu-id="7aeec-122">ファイルのすべての行には、一致しない CurrencyID 値 BAD、ErrorCode 値 -1071607778、ErrorColumn 値 0、ErrorDescription 値 "参照中に一致する行が見つかりませんでした" が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7aeec-122">Notice that all the rows in the file contain the unmatched CurrencyID value of BAD, the ErrorCode value of -1071607778, the ErrorColumn value of 0, and the ErrorDescription value "Row yielded no match during lookup".</span></span> <span data-ttu-id="7aeec-123">エラーは列固有ではなく、ErrorColumn の値は 0 になっています。</span><span class="sxs-lookup"><span data-stu-id="7aeec-123">The value of the ErrorColumn is set to 0 because the error is not column specific.</span></span> <span data-ttu-id="7aeec-124">これは失敗した参照操作を表します。</span><span class="sxs-lookup"><span data-stu-id="7aeec-124">It is the lookup operation that failed.</span></span> <span data-ttu-id="7aeec-125">.</span><span class="sxs-lookup"><span data-stu-id="7aeec-125">.</span></span>  
  
  
