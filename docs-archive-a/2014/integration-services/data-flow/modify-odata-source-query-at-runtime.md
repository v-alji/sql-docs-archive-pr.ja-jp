---
title: 実行時の OData ソースクエリの変更 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: bcbba7f4-6e5d-46e6-a73a-3f17d3ff376a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b3dbc4d27f2d11537a9d66980ef6ca59b80811b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741145"
---
# <a name="modify-odata-source-query-at-runtime"></a><span data-ttu-id="b0a4f-102">実行時の OData ソース クエリの変更</span><span class="sxs-lookup"><span data-stu-id="b0a4f-102">Modify OData Source Query at Runtime</span></span>
  <span data-ttu-id="b0a4f-103">データ フロー タスクの [OData ソース].[クエリ] プロパティに**式**を追加すると、OData ソースのクエリを実行時に変更できます。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-103">You can modify the OData Source query at runtime by adding an expression to the **[OData Source].[Query]** property of the Data Flow task.</span></span>  
  
 <span data-ttu-id="b0a4f-104">列が、デザイン時に使用したのと同じ状態にとどまっている必要があることに注意してください。それ以外の場合は、パッケージの実行時にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-104">Note that the columns must remain the same as what was used at design time; otherwise you will get an error when the package is executed.</span></span> <span data-ttu-id="b0a4f-105">$select クエリ オプションを使用する場合は、同じ列を (同じ順序で) 指定してください。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-105">Be sure to specify the same columns (in the same order) when using the $select query option.</span></span> <span data-ttu-id="b0a4f-106">$select オプションを使用するより安全な代替手段は、ソース コンポーネント UI で、直接使用することを希望しない列を選択解除することです。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-106">A safer alternative to using the $select option is to deselect the columns you don't want directly from the Source Component UI.</span></span>  
  
 <span data-ttu-id="b0a4f-107">クエリの値を実行時に動的に設定するいくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-107">There are a few different ways of dynamically setting the query value at runtime.</span></span> <span data-ttu-id="b0a4f-108">次に、いくつかの一般的な方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-108">Below are some of the more common methods.</span></span>  
  
## <a name="exposing-the-query-as-a-parameter"></a><span data-ttu-id="b0a4f-109">クエリをパラメーターとして公開</span><span class="sxs-lookup"><span data-stu-id="b0a4f-109">Exposing the Query as a Parameter</span></span>  
 <span data-ttu-id="b0a4f-110">次の手順には、OData ソース コンポーネントによって使用されるクエリを、パッケージに対するパラメーターとして公開する手順が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-110">The following procedure has steps to expose query used by an OData Source component as a parameter to the package.</span></span>  
  
1.  <span data-ttu-id="b0a4f-111">**[データ フロー タスク]** を右クリックし、 **[パラメーター化]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-111">Right click on the **Data Flow task** and select the **Parameterize...** option.</span></span>  
  
2.  <span data-ttu-id="b0a4f-112">**[パラメーター化]** ダイアログで、 **[プロパティ]** に対して **[\<Name of the OData Source Component>].[Query]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-112">In the **Parameterize** dialog, select **[\<Name of the OData Source Component>].[Query]** for **Property**.</span></span>  
  
3.  <span data-ttu-id="b0a4f-113">**[新しいパラメーターの作成]** または **[既存のパラメーターを使用する]** のどちらかを選択します。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-113">Choose whether to **create new parameter** or **use an existing parameter**.</span></span>  
  
4.  <span data-ttu-id="b0a4f-114">**[新しいパラメーターを作成する]** を選択した場合は、次の作業を実行します。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-114">If you select **Create new parameter**, do the following:</span></span>  
  
    1.  <span data-ttu-id="b0a4f-115">パラメーターの **[名前]** と **[説明]** を入力します。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-115">Enter **name** and **description** for the parameter.</span></span>  
  
    2.  <span data-ttu-id="b0a4f-116">パラメーターの既定の **[値]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-116">Specify default **value** for the parameter.</span></span>  
  
    3.  <span data-ttu-id="b0a4f-117">パラメーターに対応する **[スコープ]** ( **[パッケージ]** または **[プロジェクト]** ) を指定します。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-117">Specify the **scope** (**package** or **project**) for the parameter.</span></span>  
  
    4.  <span data-ttu-id="b0a4f-118">パラメーターが **[必須]** であるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-118">Specify whether the parameter is **required** or not</span></span>  
  
5.  <span data-ttu-id="b0a4f-119">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-119">Click **OK** to close the dialog box.</span></span>  
  
## <a name="using-an-expression"></a><span data-ttu-id="b0a4f-120">式の使用</span><span class="sxs-lookup"><span data-stu-id="b0a4f-120">Using an Expression</span></span>  
 <span data-ttu-id="b0a4f-121">この方法は、クエリ文字列を実行時に動的に構築する場合役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-121">This method is useful when you want to dynamically construct query string at runtime.</span></span> <span data-ttu-id="b0a4f-122">この例では、他の手段 (スクリプト、パラメーターなど) を使用して MaxRows 変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-122">In this example, MaxRows variable will be set through other means (script, parameter, etc).</span></span>  
  
1.  <span data-ttu-id="b0a4f-123">使用中の **[OData ソース]** を含む **[データ フロー タスク]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-123">Select the **Data Flow Task** which contains your **OData Source**.</span></span>  
  
2.  <span data-ttu-id="b0a4f-124">**[プロパティ]** ウィンドウで、 **[Expressions]** プロパティを強調表示します。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-124">In the **Properties** window, highlight the **Expressions** property.</span></span>  
  
3.  <span data-ttu-id="b0a4f-125">[...](省略記号) ボタンをクリックして、[**プロパティ式エディター**] を表示します。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-125">Click the ... (ellipses) button to bring up the **Property Expressions Editor**.</span></span>  
  
4.  <span data-ttu-id="b0a4f-126">**[OData ソース].[クエリ]** プロパティを選択します。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-126">Select the **[OData Source].[Query]** property.</span></span>  
  
5.  <span data-ttu-id="b0a4f-127">[...][**式**] の (省略記号) ボタン。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-127">Click the ... (ellipses) button for **Expression**.</span></span>  
  
6.  <span data-ttu-id="b0a4f-128">**[式]** を入力します。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-128">Enter the **expression**.</span></span>  
  
7.  <span data-ttu-id="b0a4f-129">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-129">Click **OK**.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="b0a4f-130">この方法を使用する場合、値が、正しくエンコードされた URL であることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-130">Note that when using this approach you need to ensure that the values set are properly URL encoded.</span></span> <span data-ttu-id="b0a4f-131">ユーザー入力から値を受け取る (たとえば、パラメーターに基づいて個々のクエリ オプションの値を設定する) 場合は、SQL インジェクション型の攻撃の可能性を防止するために、値を検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0a4f-131">When receiving values from user input (for example, setting individual query option values from a parameter), you must ensure that the values are validated to avoid potential SQL injection-type attacks.</span></span>  
  
  
