---
title: '作業 15: SSIS プロジェクトをビルドして実行する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 13adf4e0-216a-4992-b13d-b7b1e1629e77
ms.author: lle
author: lrtoyou1223
ms.openlocfilehash: 2a008cd848c95b48e6e22798b6ef903942b4d656
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719023"
---
# <a name="task-15-building-and-running-the-ssis-project"></a><span data-ttu-id="d2aa7-102">タスク 15: SSIS プロジェクトをビルドおよび実行する</span><span class="sxs-lookup"><span data-stu-id="d2aa7-102">Task 15: Building and Running the SSIS Project</span></span>

  <span data-ttu-id="d2aa7-103">ここでは、SSIS プロジェクトをビルドおよび実行します。</span><span class="sxs-lookup"><span data-stu-id="d2aa7-103">In this task, you build and run the SSIS project.</span></span> <span data-ttu-id="d2aa7-104">コンピューターに64ビット版の Excel 2010 がインストールされている場合は、Excel ソースが機能するように**Run64BitRuntime**の値を**False**に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2aa7-104">If you have the 64-bit version of Excel 2010 installed on your computer, you should set the value of **Run64BitRuntime** to **False** for the Excel source to work.</span></span>  
  
1.  <span data-ttu-id="d2aa7-105">**ソリューションエクスプローラー**ウィンドウで、メニューの [**プロジェクト**] をクリックし、[ **CleanseAndCurateSuppliers Properties**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2aa7-105">In the **Solution Explorer** window, click **Project** on the menu, and click **CleanseAndCurateSuppliers Properties**.</span></span>  
  
2.  <span data-ttu-id="d2aa7-106">[**プロパティ**] ダイアログボックスで、左側の [**構成プロパティ**] を展開し、[**デバッグ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2aa7-106">In the **Properties** dialog box, expand **Configuration Properties** on left, and click **Debugging**.</span></span>  
  
3.  <span data-ttu-id="d2aa7-107">**Run64BitRuntime**を**False**に設定します。</span><span class="sxs-lookup"><span data-stu-id="d2aa7-107">Set **Run64BitRuntime** to **False**.</span></span>  
  
     <span data-ttu-id="d2aa7-108">![CleanseAndCurateSuppliers プロジェクトのプロパティ](../../2014/tutorials/media/et-buildingandrunningthessisproject-01.jpg "CleanseAndCurateSuppliers プロジェクトのプロパティ")</span><span class="sxs-lookup"><span data-stu-id="d2aa7-108">![CleanseAndCurateSuppliers Project Properties](../../2014/tutorials/media/et-buildingandrunningthessisproject-01.jpg "CleanseAndCurateSuppliers Project Properties")</span></span>  
  
4.  <span data-ttu-id="d2aa7-109">**[OK]** をクリックして、 **[プロパティ]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="d2aa7-109">Click **OK** to close the **Properties** dialog box.</span></span>  
  
5.  <span data-ttu-id="d2aa7-110">メニューバーの [**ビルド**] をクリックし、[ **CleanseAndCurateSuppliers のビルド**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2aa7-110">Click **Build** on menu bar and click **Build CleanseAndCurateSuppliers**.</span></span> <span data-ttu-id="d2aa7-111">ビルド エラーがないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="d2aa7-111">Make sure that there are no build errors.</span></span>  
  
6.  <span data-ttu-id="d2aa7-112">メニューバーの [**デバッグ**] をクリックし、[**デバッグの開始**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2aa7-112">Click **Debug** on the menu bar and click **Start Debugging**.</span></span>  
  
7.  <span data-ttu-id="d2aa7-113">[**進行状況**] ウィンドウでメッセージを確認し、パッケージが実行されて正常に終了したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="d2aa7-113">Review messages in the **Progress** window and verify that package executed and ended successfully.</span></span>  
  
     <span data-ttu-id="d2aa7-114">![進行状況ウィンドウの結果](../../2014/tutorials/media/et-buildingandrunningthessisproject-02.jpg "進行状況ウィンドウの結果")</span><span class="sxs-lookup"><span data-stu-id="d2aa7-114">![Results from Progress Window](../../2014/tutorials/media/et-buildingandrunningthessisproject-02.jpg "Results from Progress Window")</span></span>  
  
     <span data-ttu-id="d2aa7-115">![進行状況ウィンドウの最終状態](../../2014/tutorials/media/et-buildingandrunningthessisproject-03.jpg "進行状況ウィンドウの最終状態")</span><span class="sxs-lookup"><span data-stu-id="d2aa7-115">![Final Status from Progress Window](../../2014/tutorials/media/et-buildingandrunningthessisproject-03.jpg "Final Status from Progress Window")</span></span>  
  
8.  <span data-ttu-id="d2aa7-116">メニューバーの [**デバッグ**] をクリックし、[**デバッグの停止**] をクリックしてデバッグセッションを停止します。</span><span class="sxs-lookup"><span data-stu-id="d2aa7-116">Click **Debug** on menu bar and click **Stop Debugging** to stop the debugging session.</span></span> <span data-ttu-id="d2aa7-117">パッケージの実行に失敗した場合、データ ビューアーを有効にしてコンポーネント間のデータ フローを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2aa7-117">If the package fails, you should enable data viewers and see how the data flows between components.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="d2aa7-118">次の手順</span><span class="sxs-lookup"><span data-stu-id="d2aa7-118">Next Step</span></span>  
 [<span data-ttu-id="d2aa7-119">タスク 16: マスター データ マネージャーを確認する</span><span class="sxs-lookup"><span data-stu-id="d2aa7-119">Task 16: Verifying with Master Data Manager</span></span>](../../2014/tutorials/task-16-verifying-with-master-data-manager.md)  
  
  
