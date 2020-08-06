---
title: '手順 4: レッスン 2 のチュートリアル パッケージのテスト | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0e8c0a25-8f79-41df-8ed2-f82a74b129cd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c055f80cbe9e6748b82569204e3a2d82e2f437e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632567"
---
# <a name="step-4-testing-the-lesson-2-tutorial-package"></a><span data-ttu-id="c561a-102">手順 4:レッスン 2 のチュートリアル パッケージのテスト</span><span class="sxs-lookup"><span data-stu-id="c561a-102">Step 4: Testing the Lesson 2 Tutorial Package</span></span>
  <span data-ttu-id="c561a-103">Foreach ループ コンテナーとフラット ファイル接続マネージャーを構成したので、Lesson 2 のパッケージは、Sample Data フォルダー内の 14 個のフラット ファイルに対して反復処理を実行できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="c561a-103">With the Foreach Loop container and the Flat File connection manager now configured, the Lesson 2 package can iterate through the collection of 14 flat files in the Sample Data folder.</span></span> <span data-ttu-id="c561a-104">指定した条件を満たすファイル名が見つかるたびに、Foreach ループ コンテナーは、ユーザー定義変数にそのファイル名を取り込みます。</span><span class="sxs-lookup"><span data-stu-id="c561a-104">Each time a file name is found that matches the specified file name criteria, the Foreach Loop container populates the user-defined variable with the file name.</span></span> <span data-ttu-id="c561a-105">次に、この変数に基づいて、フラット ファイル接続マネージャーの ConnectionString プロパティを更新し、新しいフラット ファイルへの接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="c561a-105">This variable, in turn, updates the ConnectionString property of the Flat File connection manager, and a connection to the new flat file is made.</span></span> <span data-ttu-id="c561a-106">さらに、新しいフラット ファイル内のデータに対して未変更のデータ フロー タスクを実行してから、フォルダー内の次のファイルに接続します。</span><span class="sxs-lookup"><span data-stu-id="c561a-106">The Foreach Loop container then runs the unmodified data flow task against the data in the new flat file before connecting to the next file in the folder.</span></span>  
  
 <span data-ttu-id="c561a-107">次の手順を実行して、パッケージに追加した新しいループ機能をテストします。</span><span class="sxs-lookup"><span data-stu-id="c561a-107">Use the following procedure to test the new looping functionality that you have added to your package.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c561a-108">レッスン 1 で作成したパッケージを実行した場合、このレッスンでパッケージを実行する前に、AdventureWorksDW2012 の dbo.FactCurrency からレコードを削除する必要があります。そうしないと、主キー制約違反を示すエラーが発生してパッケージが失敗します。</span><span class="sxs-lookup"><span data-stu-id="c561a-108">If you ran the package from Lesson 1, you will need to delete the records from dbo.FactCurrency in AdventureWorksDW2012 before you run the package from this lesson or the package will fail with errors indicating a Violation of Primary Key constraint.</span></span> <span data-ttu-id="c561a-109">[デバッグ] メニューの [デバッグの開始] をクリックして (または F5 キーを押して) パッケージを実行すると、レッスン 1 とレッスン 2 の両方が実行されるため、同じエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="c561a-109">You will receive the same errors if you run the package by selecting Debug/Start Debugging (or press F5) because both Lesson 1 and Lesson 2 will run.</span></span> <span data-ttu-id="c561a-110">レッスン 2 では、レッスン 1 で既に挿入されたレコードを挿入しようとします。</span><span class="sxs-lookup"><span data-stu-id="c561a-110">Lesson 2 will attempt to insert records already inserted in Lesson 1.</span></span>  
  
## <a name="checking-the-package-layout"></a><span data-ttu-id="c561a-111">パッケージ レイアウトの確認</span><span class="sxs-lookup"><span data-stu-id="c561a-111">Checking the Package Layout</span></span>  
 <span data-ttu-id="c561a-112">パッケージをテストする前に、次の図に示すオブジェクトがレッスン 2 のパッケージの制御フローとデータ フローに含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c561a-112">Before you test the package you should verify that the control and data flows in the Lesson 2 package contains the objects shown in the following diagrams.</span></span> <span data-ttu-id="c561a-113">データ フローはレッスン 1 のデータ フローと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="c561a-113">The data flow should be identical to the data flow in lesson 1.</span></span>  
  
 <span data-ttu-id="c561a-114">**制御フロー**</span><span class="sxs-lookup"><span data-stu-id="c561a-114">**Control Flow**</span></span>  
  
 <span data-ttu-id="c561a-115">![パッケージ内の制御フロー](../../2014/tutorials/media/task4lesson2control.gif "パッケージ内の制御フロー")</span><span class="sxs-lookup"><span data-stu-id="c561a-115">![Control flow in package](../../2014/tutorials/media/task4lesson2control.gif "Control flow in package")</span></span>  
  
 <span data-ttu-id="c561a-116">**データ フロー**</span><span class="sxs-lookup"><span data-stu-id="c561a-116">**Data Flow**</span></span>  
  
 <span data-ttu-id="c561a-117">![パッケージ内のデータ フロー](../../2014/tutorials/media/task9lesson1data.gif "パッケージ内のデータ フロー")</span><span class="sxs-lookup"><span data-stu-id="c561a-117">![Data flow in package](../../2014/tutorials/media/task9lesson1data.gif "Data flow in package")</span></span>  
  
### <a name="to-test-the-lesson-2-tutorial-package"></a><span data-ttu-id="c561a-118">レッスン 2 で作成したチュートリアル パッケージをテストするには</span><span class="sxs-lookup"><span data-stu-id="c561a-118">To test the Lesson 2 tutorial package</span></span>  
  
1.  <span data-ttu-id="c561a-119">**ソリューション エクスプローラー**で **Lesson 2.dtsx** を右クリックし、 **[パッケージの実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c561a-119">In **Solution Explorer**, right-click **Lesson 2.dtsx** and click **Execute Package**.</span></span>  
  
     <span data-ttu-id="c561a-120">パッケージが実行されます。</span><span class="sxs-lookup"><span data-stu-id="c561a-120">The package will run.</span></span> <span data-ttu-id="c561a-121">各ループの状態は [出力] ウィンドウで確認できます。または、[**進行状況**] タブをクリックして確認することもできます。たとえば、ファイル Currency_VEB.txt からコピー先のテーブルに1097行が追加されたことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="c561a-121">You can verify the status of each loop in the Output window, or by clicking on the **Progress** tab. For example, you can see that 1097 lines were added to the destination table from the file Currency_VEB.txt.</span></span>  
  
2.  <span data-ttu-id="c561a-122">パッケージの実行が完了したら、 **[デバッグ]** メニューの **[デバッグの停止]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c561a-122">After the package has completed running, on the **Debug** menu, click **Stop Debugging**.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="c561a-123">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="c561a-123">Next Lesson</span></span>  
 [<span data-ttu-id="c561a-124">レッスン 5: パッケージ配置モデルのパッケージ構成の追加</span><span class="sxs-lookup"><span data-stu-id="c561a-124">Lesson 5: Adding Package Configurations for the Package Deployment Model</span></span>](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="c561a-125">参照</span><span class="sxs-lookup"><span data-stu-id="c561a-125">See Also</span></span>  
 [<span data-ttu-id="c561a-126">プロジェクトとパッケージの実行</span><span class="sxs-lookup"><span data-stu-id="c561a-126">Execution of Projects and Packages</span></span>](packages/run-integration-services-ssis-packages.md)  
  
  
