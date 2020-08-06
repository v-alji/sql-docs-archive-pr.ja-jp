---
title: '手順 3: レッスン 6 のパッケージのテスト | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c184c92d-948f-4037-a502-5fabd909c84c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3c7ab82e9b04fe0752252102374f745e311d830d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736559"
---
# <a name="step-3-testing-the-lesson-6-package"></a><span data-ttu-id="a8fc7-102">手順 3:レッスン 6 のパッケージのコピー</span><span class="sxs-lookup"><span data-stu-id="a8fc7-102">Step 3: Testing the Lesson 6 Package</span></span>
  <span data-ttu-id="a8fc7-103">パッケージを実行すると、VarFolderName パラメーターから Directory プロパティの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="a8fc7-103">At run time, your package will obtain the value for the Directory property from the VarFolderName parameter.</span></span>  
  
 <span data-ttu-id="a8fc7-104">パッケージの実行時に、Directory プロパティが新しい値に更新されているかどうかを確認するには、パッケージを実行してみます。</span><span class="sxs-lookup"><span data-stu-id="a8fc7-104">To verify that the package updates the Directory property with the new value during run time, simply execute the package.</span></span> <span data-ttu-id="a8fc7-105">3 つのサンプル データ ファイルのみが新しいディレクトリにコピーされるため、データ フローは 3 回だけ実行されます。元のフォルダーの 14 ファイルには反復処理は実行されません。</span><span class="sxs-lookup"><span data-stu-id="a8fc7-105">Because only three sample data files were copied to the new directory, the data flow will run only three times, rather than iterate through the 14 files in the original folder.</span></span>  
  
## <a name="checking-the-package-layout"></a><span data-ttu-id="a8fc7-106">パッケージ レイアウトの確認</span><span class="sxs-lookup"><span data-stu-id="a8fc7-106">Checking the Package Layout</span></span>  
 <span data-ttu-id="a8fc7-107">パッケージをテストする前に、次の図に示すオブジェクトがレッスン 6 のパッケージの制御フローとデータ フローに含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a8fc7-107">Before you test the package you should verify that the control and data flows in the Lesson 6 package contains the objects shown in the following diagrams.</span></span> <span data-ttu-id="a8fc7-108">制御フローはレッスン 5 の制御フローと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8fc7-108">The control flow should be identical to the control flow in lesson 5.</span></span> <span data-ttu-id="a8fc7-109">データ フローはレッスン 5 のデータ フローと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8fc7-109">The data flow should be identical to the data flow in lesson 5.</span></span>  
  
 <span data-ttu-id="a8fc7-110">**制御フロー**</span><span class="sxs-lookup"><span data-stu-id="a8fc7-110">**Control Flow**</span></span>  
  
 <span data-ttu-id="a8fc7-111">![制御フロー](../../2014/tutorials/media/task3lesson6control.jpg "制御フロー")</span><span class="sxs-lookup"><span data-stu-id="a8fc7-111">![Control Flow](../../2014/tutorials/media/task3lesson6control.jpg "Control Flow")</span></span>  
  
 <span data-ttu-id="a8fc7-112">**データ フロー**</span><span class="sxs-lookup"><span data-stu-id="a8fc7-112">**Data Flow**</span></span>  
  
 <span data-ttu-id="a8fc7-113">![データ フロー](../../2014/tutorials/media/task3lesson6data.jpg "Data Flow")</span><span class="sxs-lookup"><span data-stu-id="a8fc7-113">![Data Flow](../../2014/tutorials/media/task3lesson6data.jpg "Data Flow")</span></span>  
  
### <a name="to-test-the-lesson-6-tutorial-package"></a><span data-ttu-id="a8fc7-114">レッスン 6 のチュートリアル パッケージをテストするには</span><span class="sxs-lookup"><span data-stu-id="a8fc7-114">TO test the Lesson 6 tutorial package</span></span>  
  
1.  <span data-ttu-id="a8fc7-115">[デバッグ] メニューの [デバッグの開始] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8fc7-115">On the Debug menu, click Start Debugging.</span></span>  
  
2.  <span data-ttu-id="a8fc7-116">パッケージの実行が完了したら、[デバッグ] メニューの [デバッグの停止] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8fc7-116">After the package has completed running, on the Debug menu, and then click Stop Debugging.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="a8fc7-117">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="a8fc7-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="a8fc7-118">手順 4:レッスン 6 のパッケージの展開</span><span class="sxs-lookup"><span data-stu-id="a8fc7-118">Step 4: Deploying the Lesson 6 Package</span></span>](../integration-services/lesson-6-4-deploying-the-lesson-6-package.md)  
  
  
