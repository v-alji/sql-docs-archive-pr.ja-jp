---
title: '手順 4: レッスン 5 のチュートリアル パッケージのテスト | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5215b77d-c2ec-4b25-a3de-ca49ea197d74
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 76e4692de4daa9ddd6ed0e418bed5cda74ec7650
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633892"
---
# <a name="step-4-testing-the-lesson-5-tutorial-package"></a><span data-ttu-id="43ba3-102">手順 4:レッスン 5 のチュートリアル パッケージのテスト</span><span class="sxs-lookup"><span data-stu-id="43ba3-102">Step 4: Testing the Lesson 5 Tutorial Package</span></span>
  <span data-ttu-id="43ba3-103">パッケージを実行すると、そのときに更新される変数から `Directory` の値が取得されます。パッケージの作成時に指定した元の名前は使用されません。</span><span class="sxs-lookup"><span data-stu-id="43ba3-103">At run time, your package will obtain the value for the `Directory` property from a variable updated at run time, rather than using the original directory name that you specified when you created the package.</span></span> <span data-ttu-id="43ba3-104">この変数の値は、SSISTutorial.dtsConfig ファイルにより生成されます。</span><span class="sxs-lookup"><span data-stu-id="43ba3-104">The value of the variable is populated by the SSISTutorial.dtsConfig file.</span></span>  
  
 <span data-ttu-id="43ba3-105">パッケージの実行時に、Directory プロパティが新しい値に更新されているかどうかを確認するには、パッケージを実行してみます。</span><span class="sxs-lookup"><span data-stu-id="43ba3-105">To verify that the package updates the Directory property with the new value during run time, simply execute the package.</span></span> <span data-ttu-id="43ba3-106">3 つのサンプル データ ファイルのみが新しいディレクトリにコピーされるため、データ フローは 3 回だけ実行されます。元のフォルダーの 14 ファイルには反復処理は実行されません。</span><span class="sxs-lookup"><span data-stu-id="43ba3-106">Because only three sample data files were copied to the new directory, the data flow will run only three times, rather than iterate through the 14 files in the original folder.</span></span>  
  
## <a name="checking-the-package-layout"></a><span data-ttu-id="43ba3-107">パッケージ レイアウトの確認</span><span class="sxs-lookup"><span data-stu-id="43ba3-107">Checking the Package Layout</span></span>  
 <span data-ttu-id="43ba3-108">パッケージをテストする前に、次の図に示すオブジェクトがレッスン 5 のパッケージの制御フローとデータ フローに含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="43ba3-108">Before you test the package you should verify that the control and data flows in the Lesson 5 package contains the objects shown in the following diagrams.</span></span> <span data-ttu-id="43ba3-109">制御フローはレッスン 4 の制御フローと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="43ba3-109">The control flow should be identical to the control flow in lesson 4.</span></span> <span data-ttu-id="43ba3-110">データ フローはレッスン 4 のデータ フローと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="43ba3-110">The data flow should be identical to the data flow in lessons 4.</span></span>  
  
 <span data-ttu-id="43ba3-111">**制御フロー**</span><span class="sxs-lookup"><span data-stu-id="43ba3-111">**Control Flow**</span></span>  
  
 <span data-ttu-id="43ba3-112">![パッケージ内の制御フロー](../../2014/tutorials/media/task4lesson2control.gif "パッケージ内の制御フロー")</span><span class="sxs-lookup"><span data-stu-id="43ba3-112">![Control flow in package](../../2014/tutorials/media/task4lesson2control.gif "Control flow in package")</span></span>  
  
 <span data-ttu-id="43ba3-113">**データ フロー**</span><span class="sxs-lookup"><span data-stu-id="43ba3-113">**Data Flow**</span></span>  
  
 <span data-ttu-id="43ba3-114">![パッケージ内のデータ フロー](../../2014/tutorials/media/task9lesson1data.gif "パッケージ内のデータ フロー")</span><span class="sxs-lookup"><span data-stu-id="43ba3-114">![Data flow in package](../../2014/tutorials/media/task9lesson1data.gif "Data flow in package")</span></span>  
  
### <a name="to-test-the-lesson-5-tutorial-package"></a><span data-ttu-id="43ba3-115">レッスン 5 で作成したチュートリアル パッケージをテストするには</span><span class="sxs-lookup"><span data-stu-id="43ba3-115">To test the Lesson 5 tutorial package</span></span>  
  
1.  <span data-ttu-id="43ba3-116">**[デバッグ]** メニューの **[デバッグの開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43ba3-116">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
2.  <span data-ttu-id="43ba3-117">パッケージの実行が完了したら、 **[デバッグ]** メニューの **[デバッグの停止]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43ba3-117">After the package has completed running, on the **Debug** menu, and then click **Stop Debugging**.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="43ba3-118">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="43ba3-118">Next Lesson</span></span>  
 [<span data-ttu-id="43ba3-119">レッスン 6: プロジェクト配置モデルを持つパラメーターを使用する</span><span class="sxs-lookup"><span data-stu-id="43ba3-119">Lesson 6: Using Parameters with the Project Deployment Model</span></span>](../integration-services/lesson-6-using-parameters-with-the-project-deployment-model-in-ssis.md)  
  
  
