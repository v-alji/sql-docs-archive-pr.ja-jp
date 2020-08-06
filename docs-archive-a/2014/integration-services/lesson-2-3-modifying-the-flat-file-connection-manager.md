---
title: '手順 3: フラット ファイル接続マネージャーの変更 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 459e3995-2116-4f15-aaa2-32f26113869c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b897f9412a8f2978ebe4137e3e79bf1d28c97844
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632572"
---
# <a name="step-3-modifying-the-flat-file-connection-manager"></a><span data-ttu-id="0e110-102">手順 3:フラット ファイル接続マネージャーの変更</span><span class="sxs-lookup"><span data-stu-id="0e110-102">Step 3: Modifying the Flat File Connection Manager</span></span>
  <span data-ttu-id="0e110-103">この実習では、レッスン 1 で作成、構成したフラット ファイル接続マネージャーを変更します。</span><span class="sxs-lookup"><span data-stu-id="0e110-103">In this task, you will modify the Flat File connection manager that you created and configured in Lesson 1.</span></span> <span data-ttu-id="0e110-104">フラット ファイル接続マネージャーを作成した当初は、1 つのファイルを静的に読み込むように構成しました。</span><span class="sxs-lookup"><span data-stu-id="0e110-104">When originally created, the Flat File connection manager was configured to statically load a single file.</span></span> <span data-ttu-id="0e110-105">フラット ファイル接続マネージャーで繰り返しファイルを読み込むには、接続マネージャーの ConnectionString プロパティを修正し、ユーザー定義変数 `User:varFileName`を使用できるようにする必要があります。この変数に、実行時に読み込むファイルのパスを定義します。</span><span class="sxs-lookup"><span data-stu-id="0e110-105">To enable the Flat File connection manager to iteratively load files, you must modify the ConnectionString property of the connection manager to accept the user-defined variable `User:varFileName`, which contains the path of the file to be loaded at run time.</span></span>  
  
 <span data-ttu-id="0e110-106">接続マネージャーを修正した後、ユーザー定義変数 `User::varFileName`の値を使用し、接続マネージャーの ConnectionString プロパティを作成します。これにより、接続マネージャーは複数のフラット ファイルに接続できるようになります。</span><span class="sxs-lookup"><span data-stu-id="0e110-106">By modifying the connection manager to use the value of the user-defined variable, `User::varFileName`, to populate the ConnectionString property of the connection manager, the connection manager will be able to connect to different flat files.</span></span> <span data-ttu-id="0e110-107">この接続マネージャーを実行すると、Foreach ループ コンテナーの各反復処理により `User::varFileName` 変数が非常に速いスピードで更新されます。</span><span class="sxs-lookup"><span data-stu-id="0e110-107">At run time, each iteration of the Foreach Loop container will dynamically update the `User::varFileName` variable.</span></span> <span data-ttu-id="0e110-108">変数が更新されると、接続マネージャーが複数のフラット ファイルに接続され、異なるデータセットを処理するデータ フローのタスクが発生します。</span><span class="sxs-lookup"><span data-stu-id="0e110-108">Updating the variable, in turn, causes the connection manager to connect to a different flat file, and the data flow task to process a different set of data.</span></span>  
  
### <a name="to-configure-the-flat-file-connection-manager-to-use-a-variable-for-the-connection-string"></a><span data-ttu-id="0e110-109">接続文字列用の変数を使用するようにフラット ファイル接続マネージャーを構成するには</span><span class="sxs-lookup"><span data-stu-id="0e110-109">To configure the Flat File connection manager to use a variable for the connection string</span></span>  
  
1.  <span data-ttu-id="0e110-110">**接続マネージャー** ペインで、 **[Sample Flat File Source Data]** を右クリックして **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e110-110">In the **Connection Managers** pane, right-click **Sample Flat File Source Data**, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="0e110-111">プロパティウィンドウの [**式**] で、空のセルをクリックし、省略記号ボタン ([. **..])** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e110-111">In the Properties window, for **Expressions**, click in the empty cell, and then click the ellipsis button **(...)**.</span></span>  
  
3.  <span data-ttu-id="0e110-112">[**プロパティ式エディター** ] ダイアログボックスの [**プロパティ**] 列で、「」と入力するか、を選択し `ConnectionString` ます。</span><span class="sxs-lookup"><span data-stu-id="0e110-112">In the **Property Expressions Editor** dialog box, in the **Property** column, type or select `ConnectionString`.</span></span>  
  
4.  <span data-ttu-id="0e110-113">[**式**] 列で、省略記号ボタン **([..** .]) をクリックして [**式ビルダー** ] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="0e110-113">In the **Expression** column, click the ellipsis button **(...)** to open the **Expression Builder** dialog box.</span></span>  
  
5.  <span data-ttu-id="0e110-114">**[式ビルダー]** ダイアログ ボックスで **[変数]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="0e110-114">In the **Expression Builder** dialog box, expand the **Variables** node.</span></span>  
  
6.  <span data-ttu-id="0e110-115">変数**User:: varFileName**を [**式**] ボックスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0e110-115">Drag the variable, **User::varFileName**, into the **Expression** box.</span></span>  
  
7.  <span data-ttu-id="0e110-116">**[OK]** をクリックし、 **[式ビルダー]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0e110-116">Click **OK** to close the **Expression Builder** dialog box.</span></span>  
  
8.  <span data-ttu-id="0e110-117">再度 **[OK]** をクリックし、 **[プロパティ式エディター]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0e110-117">Click **OK** again to close the **Property Expressions Editor** dialog box.</span></span>  
  
## <a name="next-lesson-task"></a><span data-ttu-id="0e110-118">次のレッスンの作業</span><span class="sxs-lookup"><span data-stu-id="0e110-118">Next Lesson Task</span></span>  
 [<span data-ttu-id="0e110-119">手順 4:レッスン 2 のチュートリアル パッケージのテスト</span><span class="sxs-lookup"><span data-stu-id="0e110-119">Step 4: Testing the Lesson 2 Tutorial Package</span></span>](../integration-services/lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
  
