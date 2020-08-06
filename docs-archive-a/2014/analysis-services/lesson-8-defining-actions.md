---
title: 'レッスン 8: アクションの定義 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 15459396-83c9-48a0-b10a-99ae38768c79
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4d4daaed3f1992478b309529fc15e2e903a27920
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737165"
---
# <a name="lesson-8-defining-actions"></a><span data-ttu-id="78a9a-102">レッスン 8: アクションの定義</span><span class="sxs-lookup"><span data-stu-id="78a9a-102">Lesson 8: Defining Actions</span></span>
  <span data-ttu-id="78a9a-103">このレッスンでは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトでアクションを定義する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="78a9a-103">In this lesson, you will learn to define actions in your [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="78a9a-104">アクションは [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] に格納される多次元式 (MDX) ステートメントです。アクションはクライアント アプリケーションに統合することができ、ユーザーによって開始可能です。</span><span class="sxs-lookup"><span data-stu-id="78a9a-104">An action is just a Multidimensional Expressions (MDX) statement that is stored in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and which can be incorporated into client applications and started by a user.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="78a9a-105">このチュートリアルの各レッスンの操作内容が反映されたプロジェクトを、オンラインで入手できます。</span><span class="sxs-lookup"><span data-stu-id="78a9a-105">Completed projects for all of the lessons in this tutorial are available online.</span></span> <span data-ttu-id="78a9a-106">途中のレッスンから開始する場合は、前のレッスンの操作内容が反映されたプロジェクトを作業の開始点として使用できます。</span><span class="sxs-lookup"><span data-stu-id="78a9a-106">You can jump ahead to any lesson by using the completed project from the previous lesson as a starting point.</span></span> <span data-ttu-id="78a9a-107">このチュートリアルのサンプル プロジェクトをダウンロードするには、[ここ](https://go.microsoft.com/fwlink/?LinkID=221866) をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="78a9a-107">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to download the sample projects that go with this tutorial.</span></span>  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="78a9a-108">は、次の表に示されている種類のアクションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="78a9a-108">supports the types of actions that are described in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="78a9a-109">CommandLine</span><span class="sxs-lookup"><span data-stu-id="78a9a-109">CommandLine</span></span>|<span data-ttu-id="78a9a-110">コマンド プロンプトでコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="78a9a-110">Executes a command at the command prompt</span></span>|  
|<span data-ttu-id="78a9a-111">データセット</span><span class="sxs-lookup"><span data-stu-id="78a9a-111">Dataset</span></span>|<span data-ttu-id="78a9a-112">データセットをクライアント アプリケーションに返します。</span><span class="sxs-lookup"><span data-stu-id="78a9a-112">Returns a dataset to a client application.</span></span>|  
|<span data-ttu-id="78a9a-113">ドリルスルー</span><span class="sxs-lookup"><span data-stu-id="78a9a-113">Drillthrough</span></span>|<span data-ttu-id="78a9a-114">ドリルスルー ステートメントを式として返します。この式は、行セットを返すときにクライアントによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="78a9a-114">Returns a drillthrough statement as an expression, which the client executes to return a rowset</span></span>|  
|<span data-ttu-id="78a9a-115">Html</span><span class="sxs-lookup"><span data-stu-id="78a9a-115">Html</span></span>|<span data-ttu-id="78a9a-116">インターネット ブラウザーで HTML スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="78a9a-116">Executes an HTML script in an Internet browser</span></span>|  
|<span data-ttu-id="78a9a-117">[専用]</span><span class="sxs-lookup"><span data-stu-id="78a9a-117">Proprietary</span></span>|<span data-ttu-id="78a9a-118">この一覧に表示されていないインターフェイスを使用して操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="78a9a-118">Performs an operation by using an interface other than those listed in this table.</span></span>|  
|<span data-ttu-id="78a9a-119">レポート</span><span class="sxs-lookup"><span data-stu-id="78a9a-119">Report</span></span>|<span data-ttu-id="78a9a-120">パラメーター化された URL ベースの要求をレポート サーバーに送信して、レポートをクライアント アプリケーションに返します。</span><span class="sxs-lookup"><span data-stu-id="78a9a-120">Submits a parameterized URL-based request to a report server and returns a report to a client application.</span></span>|  
|<span data-ttu-id="78a9a-121">[行セット]</span><span class="sxs-lookup"><span data-stu-id="78a9a-121">Rowset</span></span>|<span data-ttu-id="78a9a-122">行セットをクライアント アプリケーションに返します。</span><span class="sxs-lookup"><span data-stu-id="78a9a-122">Returns a rowset to a client application.</span></span>|  
|<span data-ttu-id="78a9a-123">ステートメント</span><span class="sxs-lookup"><span data-stu-id="78a9a-123">Statement</span></span>|<span data-ttu-id="78a9a-124">OLE DB コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="78a9a-124">Runs an OLE DB command.</span></span>|  
|<span data-ttu-id="78a9a-125">URL</span><span class="sxs-lookup"><span data-stu-id="78a9a-125">URL</span></span>|<span data-ttu-id="78a9a-126">インターネット ブラウザーで動的 Web ページを表示します。</span><span class="sxs-lookup"><span data-stu-id="78a9a-126">Displays a dynamic Web page in an Internet browser.</span></span>|  
  
 <span data-ttu-id="78a9a-127">アクションを使用すると、アプリケーションを起動したり、選択したアイテムのコンテキスト内で他のステップを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="78a9a-127">Actions let users start an application or perform other steps within the context of a selected item.</span></span> <span data-ttu-id="78a9a-128">詳細については、 [アクション &#40;Analysis Services - 多次元データ&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md)および [「多次元モデルのアクション」](multidimensional-models/actions-in-multidimensional-models.md)</span><span class="sxs-lookup"><span data-stu-id="78a9a-128">For more information, see [Actions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md), [Actions in Multidimensional Models](multidimensional-models/actions-in-multidimensional-models.md)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="78a9a-129">アクション例については、[計算ツール] ペインの [テンプレート] タブか、 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW サンプル データ ウェアハウスのアクション例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78a9a-129">For examples of actions, see the action examples on the Templates tab in the Calculation Tools pane or in the examples in the [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW sample data warehouse.</span></span> <span data-ttu-id="78a9a-130">このデータベースのインストールの詳細については、「 [Analysis Services 多次元モデリング チュートリアル用のサンプル データおよびプロジェクトのインストール](install-sample-data-and-projects.md)」 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78a9a-130">For more information about installing this database, see [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](install-sample-data-and-projects.md).</span></span>  
  
 <span data-ttu-id="78a9a-131">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="78a9a-131">This lesson includes the following task:</span></span>  
  
 [<span data-ttu-id="78a9a-132">ドリルスルー アクションの定義と使用</span><span class="sxs-lookup"><span data-stu-id="78a9a-132">Defining and Using a Drillthrough Action</span></span>](lesson-8-1-defining-and-using-a-drillthrough-action.md)  
 <span data-ttu-id="78a9a-133">この作業では、このチュートリアルで以前に定義したファクト ディメンションのリレーションシップによって、ドリルスルー アクションの定義、使用、変更を行います。</span><span class="sxs-lookup"><span data-stu-id="78a9a-133">In this task, you define, use, and then modify a drillthrough action through the fact dimension relationship that you defined earlier in this tutorial.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="78a9a-134">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="78a9a-134">Next Lesson</span></span>  
 [<span data-ttu-id="78a9a-135">レッスン 9: パースペクティブと翻訳の定義</span><span class="sxs-lookup"><span data-stu-id="78a9a-135">Lesson 9: Defining Perspectives and Translations</span></span>](lesson-9-defining-perspectives-and-translations.md)  
  
## <a name="see-also"></a><span data-ttu-id="78a9a-136">参照</span><span class="sxs-lookup"><span data-stu-id="78a9a-136">See Also</span></span>  
 <span data-ttu-id="78a9a-137">[Analysis Services チュートリアルのシナリオ](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="78a9a-137">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 <span data-ttu-id="78a9a-138">[Adventure Works チュートリアル &#40;の多次元モデリング&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="78a9a-138">[Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span></span>  
 <span data-ttu-id="78a9a-139">[アクション &#40;Analysis Services-多次元データ&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="78a9a-139">[Actions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="78a9a-140">多次元モデルのアクション</span><span class="sxs-lookup"><span data-stu-id="78a9a-140">Actions in Multidimensional Models</span></span>](multidimensional-models/actions-in-multidimensional-models.md)  
  
  
