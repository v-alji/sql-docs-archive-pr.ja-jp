---
title: '手順 9: レッスン 1 のチュートリアル パッケージのテスト | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9aee7acf-797b-46f2-830d-80ab64a9f0b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dff1132489c1683430b1003e88f5037664b11983
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641082"
---
# <a name="step-9-testing-the-lesson-1-tutorial-package"></a><span data-ttu-id="4d4ce-102">手順 9:レッスン 1 のチュートリアル パッケージのテスト</span><span class="sxs-lookup"><span data-stu-id="4d4ce-102">Step 9: Testing the Lesson 1 Tutorial Package</span></span>
  <span data-ttu-id="4d4ce-103">このレッスンでは次の作業を行いました。</span><span class="sxs-lookup"><span data-stu-id="4d4ce-103">In this lesson, you have done the following tasks:</span></span>  
  
-   <span data-ttu-id="4d4ce-104">新しい [!INCLUDE[ssIS](../includes/ssis-md.md)] プロジェクトを作成しました。</span><span class="sxs-lookup"><span data-stu-id="4d4ce-104">Created a new [!INCLUDE[ssIS](../includes/ssis-md.md)] project.</span></span>  
  
-   <span data-ttu-id="4d4ce-105">ソース データおよび変換先データに接続するための接続マネージャーをパッケージに追加し、構成しました。</span><span class="sxs-lookup"><span data-stu-id="4d4ce-105">Configured the connection managers that the package needs to connect to the source and destination data.</span></span>  
  
-   <span data-ttu-id="4d4ce-106">フラット ファイル ソースからデータを取得し、そのデータに対して必要な参照変換を実行した後、変換先に合わせてデータを構成するためのデータ フローを追加しました。</span><span class="sxs-lookup"><span data-stu-id="4d4ce-106">Added a data flow that takes the data from a flat file source, performs the necessary Lookup transformations on the data, and configures the data for the destination.</span></span>  
  
 <span data-ttu-id="4d4ce-107">これでパッケージは完成です。</span><span class="sxs-lookup"><span data-stu-id="4d4ce-107">Your package is now complete!</span></span> <span data-ttu-id="4d4ce-108">次に、パッケージをテストします。</span><span class="sxs-lookup"><span data-stu-id="4d4ce-108">It is time to test your package.</span></span>  
  
## <a name="checking-the-package-layout"></a><span data-ttu-id="4d4ce-109">パッケージ レイアウトの確認</span><span class="sxs-lookup"><span data-stu-id="4d4ce-109">Checking the Package Layout</span></span>  
 <span data-ttu-id="4d4ce-110">パッケージをテストする前に、次の図に示すオブジェクトがレッスン 1 のパッケージの制御フローとデータ フローに含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4d4ce-110">Before you test the package you should verify that the control and data flows in the Lesson 1 package contain the objects shown in the following diagrams.</span></span>  
  
 <span data-ttu-id="4d4ce-111">**制御フロー**</span><span class="sxs-lookup"><span data-stu-id="4d4ce-111">**Control Flow**</span></span>  
  
 <span data-ttu-id="4d4ce-112">![パッケージ内の制御フロー](../../2014/tutorials/media/task9lesson1control.gif "パッケージ内の制御フロー")</span><span class="sxs-lookup"><span data-stu-id="4d4ce-112">![Control flow in package](../../2014/tutorials/media/task9lesson1control.gif "Control flow in package")</span></span>  
  
 <span data-ttu-id="4d4ce-113">**データ フロー**</span><span class="sxs-lookup"><span data-stu-id="4d4ce-113">**Data Flow**</span></span>  
  
 <span data-ttu-id="4d4ce-114">![パッケージ内のデータ フロー](../../2014/tutorials/media/task9lesson1data.gif "パッケージ内のデータ フロー")</span><span class="sxs-lookup"><span data-stu-id="4d4ce-114">![Data flow in package](../../2014/tutorials/media/task9lesson1data.gif "Data flow in package")</span></span>  
  
### <a name="to-run-the-lesson-1-tutorial-package"></a><span data-ttu-id="4d4ce-115">レッスン 1 のチュートリアル パッケージを実行するには</span><span class="sxs-lookup"><span data-stu-id="4d4ce-115">To run the Lesson 1 tutorial package</span></span>  
  
1.  <span data-ttu-id="4d4ce-116">**[デバッグ]** メニューの **[デバッグの開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d4ce-116">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="4d4ce-117">パッケージが実行されます。その結果、 **AdventureWorksDW2012** の **FactCurrency**ファクト テーブルに 1,097 個の行が追加されます。</span><span class="sxs-lookup"><span data-stu-id="4d4ce-117">The package will run, resulting in 1097 rows successfully added into the **FactCurrency** fact table in **AdventureWorksDW2012**.</span></span>  
  
2.  <span data-ttu-id="4d4ce-118">パッケージの実行が完了したら、 **[デバッグ]** メニューの **[デバッグの停止]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d4ce-118">After the package has completed running, on the **Debug** menu, click **Stop Debugging**.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="4d4ce-119">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="4d4ce-119">Next Lesson</span></span>  
 [<span data-ttu-id="4d4ce-120">レッスン 2: ループの追加</span><span class="sxs-lookup"><span data-stu-id="4d4ce-120">Lesson 2: Adding Looping</span></span>](../integration-services/lesson-2-adding-looping-with-ssis.md)  
  
## <a name="see-also"></a><span data-ttu-id="4d4ce-121">参照</span><span class="sxs-lookup"><span data-stu-id="4d4ce-121">See Also</span></span>  
 [<span data-ttu-id="4d4ce-122">プロジェクトとパッケージの実行</span><span class="sxs-lookup"><span data-stu-id="4d4ce-122">Execution of Projects and Packages</span></span>](packages/run-integration-services-ssis-packages.md)  
  
  
