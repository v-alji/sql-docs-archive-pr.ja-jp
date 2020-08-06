---
title: 高度なデータマイニングクエリエディター |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 27e7fc46-689d-43a4-9647-1c27d182bdd6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2aadf4df75b1ccf6001ad8e97d589ce5666f56ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633697"
---
# <a name="advanced-data-mining-query-editor"></a><span data-ttu-id="c7059-102">詳細データ マイニング クエリ エディター</span><span class="sxs-lookup"><span data-stu-id="c7059-102">Advanced Data Mining Query Editor</span></span>
  <span data-ttu-id="c7059-103">**データマイニングクエリ詳細エディター**は、カスタムモデルとクエリを作成するためのツールです。</span><span class="sxs-lookup"><span data-stu-id="c7059-103">The **Data Mining Query Advanced Editor** is a tool to help you build custom models and queries.</span></span>  
  
 <span data-ttu-id="c7059-104">エディターには、一連のテンプレートとクリック可能なリンクが用意されています。</span><span class="sxs-lookup"><span data-stu-id="c7059-104">The editor provides a set of templates with clickable links.</span></span> <span data-ttu-id="c7059-105">各リンクをクリックするだけで、ダイアログ ボックスを使用してオブジェクトや値を選択し、複雑なデータ マイニング拡張機能 (DMX) ステートメントを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="c7059-105">Just click each link, and use the dialog boxes to select objects or values and build complex Data Mining Extensions (DMX) statements.</span></span> <span data-ttu-id="c7059-106">テキスト編集モデルにビューを切り替えて、DMX ステートメントを手動で変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="c7059-106">You can switch the view to text editing model to modify the DMX statement manually.</span></span>  
  
 <span data-ttu-id="c7059-107">**詳細エディターデータマイニングクエリ**にアクセスするには、[**クエリ**] をクリックし、[**詳細設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c7059-107">To get to the **Data Mining Query Advanced Editor**, click **Query** and then click **Advanced**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="c7059-108">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="c7059-108">UI element list</span></span>  
 <span data-ttu-id="c7059-109">**DMX クエリ ペイン**</span><span class="sxs-lookup"><span data-stu-id="c7059-109">**DMX Query pane**</span></span>  
 <span data-ttu-id="c7059-110">ここで、現在の DMX ステートメントを確認できます。</span><span class="sxs-lookup"><span data-stu-id="c7059-110">Here you can see the current DMX statement.</span></span>  
  
 <span data-ttu-id="c7059-111">現在の DMX ステートメントをコピーするには、このペインを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="c7059-111">Right-click in the pane to copy the current DMX statement.</span></span>  
  
 <span data-ttu-id="c7059-112">ステートメントの強調表示された部分をクリックすると、その句に固有のオプションを選択できます。</span><span class="sxs-lookup"><span data-stu-id="c7059-112">You can click any highlighted part of the statement to get options specific to that clause.</span></span> <span data-ttu-id="c7059-113">たとえば、出力を削除、追加、または編集するには、リンクを右クリックし **\<Output>** ます。</span><span class="sxs-lookup"><span data-stu-id="c7059-113">For example, to delete, add, or edit an output, right-click the **\<Output>** link.</span></span>  
  
 <span data-ttu-id="c7059-114">**[クエリの編集]/[クエリ ビルダー]**</span><span class="sxs-lookup"><span data-stu-id="c7059-114">**Edit Query/Query Builder**</span></span>  
 <span data-ttu-id="c7059-115">このボタンを使用すると、テキストエディター間でエディターを切り替えることができます。ここでは、DMX ステートメントを直接記述できます。および**クエリビルダー**。 DMX ステートメントの作成に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c7059-115">Use this button to switch the editor between a text editor, where you can write DMX statements directly; and the **Query Builder**, which helps you build a DMX statement.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c7059-116">**警告:** クエリが実行される前にビューを切り替えると、一部の変更が失われる可能性があることを示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c7059-116">**Warning:** If you switch views before the query has been run, a message appears stating that you might lose some changes.</span></span> <span data-ttu-id="c7059-117">DMX ステートメントが有効な場合、多くの場合、**クエリビルダー**によってこれらの変更が正常に変換される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c7059-117">If the DMX statement is valid, in many cases the **Query Builder** might successfully convert these changes.</span></span> <span data-ttu-id="c7059-118">ただし、特に複雑な DMX ステートメントを作成した場合は、ビューを切り替える前に作業内容を必ず保存してください。</span><span class="sxs-lookup"><span data-stu-id="c7059-118">However, if you have built a particularly complex DMX statement, you should definitely save your work before switching views.</span></span>  
  
 <span data-ttu-id="c7059-119">**[DMX テンプレート]**</span><span class="sxs-lookup"><span data-stu-id="c7059-119">**DMX Templates**</span></span>  
 <span data-ttu-id="c7059-120">DMX の例を含むテンプレートの一覧からテンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="c7059-120">Click and select from a list of templates that contain DMX examples.</span></span> <span data-ttu-id="c7059-121">このテンプレートには、入れ子になったテーブルを使用するクエリ、モデルを管理する DMX ステートメントなど、必要になるほぼすべての種類のモデルや予測クエリが用意されています。</span><span class="sxs-lookup"><span data-stu-id="c7059-121">The templates provide just about every type of model or prediction query that you might need, including queries that use nested tables, and DMX statements to manage models.</span></span> <span data-ttu-id="c7059-122">DMX を把握している場合でも、テンプレートを使用すると、構文を正しく使用できるので時間を節約できます。</span><span class="sxs-lookup"><span data-stu-id="c7059-122">Even if you know some DMX, the templates can save you time by getting the syntax right.</span></span>  
  
 <span data-ttu-id="c7059-123">**モデルの選択**</span><span class="sxs-lookup"><span data-stu-id="c7059-123">**Choose Model**</span></span>  
 <span data-ttu-id="c7059-124">現在の接続で使用できるデータ マイニング モデルの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="c7059-124">Click to view a list of data mining models available on the current connection.</span></span>  
  
 <span data-ttu-id="c7059-125">**Dmx クエリ**ペインで dmx ステートメントのモデル名をクリックして、使用可能なモデルの一覧を表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="c7059-125">You can also display a list of available models by clicking on the model name in the DMX statement in the **DMX Query** pane.</span></span> <span data-ttu-id="c7059-126">通常、モデル名は赤色で強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="c7059-126">The model name is typically highlighted in red.</span></span>  
  
 <span data-ttu-id="c7059-127">**入力の選択**</span><span class="sxs-lookup"><span data-stu-id="c7059-127">**Select Input**</span></span>  
 <span data-ttu-id="c7059-128">マイニング モデルへの入力として使用するデータを選択できます。</span><span class="sxs-lookup"><span data-stu-id="c7059-128">Click to choose the data to use as input to the mining model.</span></span> <span data-ttu-id="c7059-129">データソースが指定されていない場合は、 **\<Input>** **DMX クエリ**ペインで赤色で強調表示されているリンクをクリックすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c7059-129">If no data source has been specified, you can also click the **\<Input>** link, which is highlighted in red in the **DMX Query** pane.</span></span>  
  
 <span data-ttu-id="c7059-130">ドロップダウンリストから [ \*\* \@ inputrowset\*\* ] を選択すると、[ **inputrowset の置換**] ダイアログボックスが開き、既存の入力を変更できます。</span><span class="sxs-lookup"><span data-stu-id="c7059-130">Select **\@InputRowset** from the dropdown list to open the **Replace InputRowset** dialog box and modify an existing input.</span></span>  
  
 <span data-ttu-id="c7059-131">[**入力の追加**] を選択して [**入力の追加**] ダイアログボックスを開き、新しいデータソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="c7059-131">Select **Add Input** to open the **Add Input** dialog box and specify a new data source.</span></span>  
  
 <span data-ttu-id="c7059-132">また、[DMX クエリ] ペインで強調表示されている [ \*\* \@ inputrowset\*\* ] リンクをクリックして、既存の入力を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="c7059-132">You can also modify an existing input by clicking the **\@InputRowset** link, which is highlighted in red in the DMX Query pane.</span></span>  
  
 <span data-ttu-id="c7059-133">**マップ列**</span><span class="sxs-lookup"><span data-stu-id="c7059-133">**Map Columns**</span></span>  
 <span data-ttu-id="c7059-134">マイニング モデルの列を選択し、これらの列を外部データ ソースの列にマップします。</span><span class="sxs-lookup"><span data-stu-id="c7059-134">Select columns from the mining model and then map them to columns in the external data source.</span></span>  
  
 <span data-ttu-id="c7059-135">DMX クエリペインで、強調表示されたリンクをクリックすることもでき **\<Mapping>** ます。</span><span class="sxs-lookup"><span data-stu-id="c7059-135">You can also click the highlighted **\<Mapping>** link in the DMX Query pane.</span></span>  
  
 <span data-ttu-id="c7059-136">**[出力の追加]**</span><span class="sxs-lookup"><span data-stu-id="c7059-136">**Add Output**</span></span>  
 <span data-ttu-id="c7059-137">予測クエリの一部として出力とする列を選択します。</span><span class="sxs-lookup"><span data-stu-id="c7059-137">Click to choose the columns that should be output as part of a prediction query.</span></span>  
  
 <span data-ttu-id="c7059-138">DMX クエリペインで、強調表示されたリンクをクリックすることもでき **\<Add Output>** ます。</span><span class="sxs-lookup"><span data-stu-id="c7059-138">You can also click the highlighted **\<Add Output>** link in the DMX Query pane.</span></span>  
  
 <span data-ttu-id="c7059-139">**[モデル列]**</span><span class="sxs-lookup"><span data-stu-id="c7059-139">**Model Columns**</span></span>  
 <span data-ttu-id="c7059-140">選択したマイニング モデル内の列を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="c7059-140">Lists the columns in the selected mining model.</span></span> <span data-ttu-id="c7059-141">列名の横に表示されるひし形のマークは、その列が予測可能列であることを表します。</span><span class="sxs-lookup"><span data-stu-id="c7059-141">A diamond mark next to the column name indicates that the column is a predictable column.</span></span>  
  
 <span data-ttu-id="c7059-142">**[入力列]**</span><span class="sxs-lookup"><span data-stu-id="c7059-142">**Input Columns**</span></span>  
 <span data-ttu-id="c7059-143">入力として追加された外部データ ソースの列を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="c7059-143">Lists the columns from the external data source that have been added as inputs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7059-144">参照</span><span class="sxs-lookup"><span data-stu-id="c7059-144">See Also</span></span>  
 [<span data-ttu-id="c7059-145">クエリ &#40;SQL Server データマイニングアドイン&#41;</span><span class="sxs-lookup"><span data-stu-id="c7059-145">Query &#40;SQL Server Data Mining Add-ins&#41;</span></span>](query-sql-server-data-mining-add-ins.md)  
  
  
