---
title: データソースビューデザイナーでのダイアグラムの操作 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.diagramorganizerpane.f1
- sql12.asvs.dsvdesigner.findtable.f1
- sql12.asvs.dsvdesigner.diagrampane.f1
helpviewer_keywords:
- data source views [Analysis Services], diagrams
- diagrams [Analysis Services]
ms.assetid: 491fdd22-2326-4f27-a0dd-0a02faae3fd8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 40a58ed33ff6cfaebf2a6e7c084500dd3ae072da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641309"
---
# <a name="work-with-diagrams-in-data-source-view-designer-analysis-services"></a><span data-ttu-id="215bc-102">データ ソース ビュー デザイナーでのダイアグラムの操作 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="215bc-102">Work with Diagrams in Data Source View Designer (Analysis Services)</span></span>
  <span data-ttu-id="215bc-103">データ ソース ビュー (DSV) ダイアグラムは、DSV でのオブジェクトの視覚的イメージです。</span><span class="sxs-lookup"><span data-stu-id="215bc-103">A data source view (DSV) diagram is a visual representation of the objects in a DSV.</span></span> <span data-ttu-id="215bc-104">対話的な操作で特定のオブジェクトを追加、非表示、削除、または変更できます。</span><span class="sxs-lookup"><span data-stu-id="215bc-104">You can work with the diagram interactively to add, hide, delete or modify specific objects.</span></span> <span data-ttu-id="215bc-105">また、同じ DSV で複数のダイアグラムを作成して、オブジェクトのサブセットに焦点を絞ることができます。</span><span class="sxs-lookup"><span data-stu-id="215bc-105">You can also create multiple diagrams on the same DSV to focus attention on a subset of the objects.</span></span>  
  
 <span data-ttu-id="215bc-106">ダイアグラム ペインに表示されるダイアグラムの領域を変更するには、ペインの右下隅で 4 方向の矢印をクリックし、選択する領域がダイアグラム ペインに表示されるまで、サムネイル ダイアグラム上で選択ボックスをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="215bc-106">To change the area of the diagram that appears in the diagram pane, click the four-headed arrow in the lower right corner of the pane, and then drag the selection box over the thumbnail diagram until you select the area that is to appear in the diagram pane.</span></span>  
  
 <span data-ttu-id="215bc-107">このトピックのセクションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="215bc-107">This topic includes the following sections:</span></span>  
  
 [<span data-ttu-id="215bc-108">ダイアグラムの追加</span><span class="sxs-lookup"><span data-stu-id="215bc-108">Add a Diagram</span></span>](#bkmk_add)  
  
 [<span data-ttu-id="215bc-109">ダイアグラムを編集または削除します。</span><span class="sxs-lookup"><span data-stu-id="215bc-109">Edit or Delete a Diagram</span></span>](#bkmk_edit)  
  
 [<span data-ttu-id="215bc-110">ダイアグラム内でのテーブルの検索</span><span class="sxs-lookup"><span data-stu-id="215bc-110">Find Tables in a Diagram</span></span>](#bkmk_findtables)  
  
 [<span data-ttu-id="215bc-111">ダイアグラム内のオブジェクトの整列</span><span class="sxs-lookup"><span data-stu-id="215bc-111">Arrange Objects in a Diagram</span></span>](#bkmk_arrangeobjects)  
  
 [<span data-ttu-id="215bc-112">オブジェクト配置の保存</span><span class="sxs-lookup"><span data-stu-id="215bc-112">Preserve object arrangement</span></span>](#bkmk_preserve)  
  
##  <a name="add-a-diagram"></a><a name="bkmk_add"></a> <span data-ttu-id="215bc-113">ダイアグラムの追加</span><span class="sxs-lookup"><span data-stu-id="215bc-113">Add a Diagram</span></span>  
 <span data-ttu-id="215bc-114">DSV ダイアグラムは、DSV を作成すると自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="215bc-114">DSV diagrams are created automatically when you create the DSV.</span></span> <span data-ttu-id="215bc-115">DSV の作成後、追加のダイアグラムの作成と削除を行ったり、または特定のオブジェクトを非表示にしたりして、DSV を管理しやすい表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="215bc-115">After the DSV exists, you can create additional diagrams, remove them, or hide specific objects to create a more manageable representation of the DSV.</span></span>  
  
 <span data-ttu-id="215bc-116">新しいダイアグラムを作成するには、 **[ダイアグラム オーガナイザー]** ペイン内を右クリックし、 **[新しいダイアグラム]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="215bc-116">To create a new diagram, right-click anywhere in the **Diagram Organizer** pane, click **New Diagram**.</span></span>  
  
 <span data-ttu-id="215bc-117">Analysis Services プロジェクトでデータソースビュー (DSV) を最初に定義すると、データソースビューに追加されたすべてのテーブルとビューがダイアグラムに追加され \<All Tables> ます。</span><span class="sxs-lookup"><span data-stu-id="215bc-117">When you initially define a data source view (DSV) in an Analysis Services project, all tables and views added to the data source view are added to the \<All Tables> diagram.</span></span> <span data-ttu-id="215bc-118">このダイアグラムはデータ ソース ビュー デザイナーの [ダイアグラム オーガナイザー] ペインに表示され、このダイアグラム内のテーブルおよびその列とリレーションシップが [テーブル] ペインに一覧表示され、さらにスキーマ ペインにグラフィック表示されます。</span><span class="sxs-lookup"><span data-stu-id="215bc-118">This diagram appears in the Diagram Organizer pane in Data Source View Designer, the tables in this diagram (and their columns and relationships) are listed in the Tables pane, and the tables in this diagram (and their columns and relationships) are displayed graphically in the schema pane.</span></span> <span data-ttu-id="215bc-119">ただし、ダイアグラムにテーブル、ビュー、および名前付きクエリを追加すると、 \<All Tables> このダイアグラム内のオブジェクトの数が多すぎると、特に複数のファクトテーブルがダイアグラムに追加され、ディメンションテーブルが複数のファクトテーブルに関連付けられている場合に、リレーションシップを視覚化することが難しくなります。</span><span class="sxs-lookup"><span data-stu-id="215bc-119">However, as you add tables, views and named queries to the \<All Tables> diagram, the sheer number of objects in this diagram makes it difficult to visualize relationships-particularly as multiple fact tables are added to the diagram, and dimension tables relate to multiple fact tables.</span></span>  
  
 <span data-ttu-id="215bc-120">データ ソース ビューにテーブルのサブセットのみを表示する場合の表示を簡潔化するために、データ ソース ビューのテーブル、ビュー、および名前付きクエリのサブセットで構成されるサブダイアグラム (略してダイアグラムと呼ばれる) を定義できます。</span><span class="sxs-lookup"><span data-stu-id="215bc-120">To reduce the visual clutter when you only want to view a subset of the tables in the data source view, you can define sub-diagrams (simply called diagrams) consisting of selected subsets of the tables, views, and named queries in the data source view.</span></span> <span data-ttu-id="215bc-121">ダイアグラムを使用すると、ビジネスやソリューションのニーズに応じてデータ ソース ビューの項目をグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="215bc-121">You can use diagrams to group items in the data source view according to business or solution needs.</span></span>  
  
 <span data-ttu-id="215bc-122">関連するテーブルや名前付きクエリを業務上の目的に合わせて別々のダイアグラムにグループ化すると、多数のテーブル、ビュー、および名前付きクエリが含まれているデータ ソース ビューが理解しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="215bc-122">You can group related tables and named queries in separate diagrams for business purposes, and to make it easier to understand a data source view that contains many tables, views, and named queries.</span></span> <span data-ttu-id="215bc-123">同じテーブルまたは名前付きクエリを、ダイアグラムを除く複数のダイアグラムに含めることができ \<All Tables> ます。</span><span class="sxs-lookup"><span data-stu-id="215bc-123">The same table or named query can be included in multiple diagrams except for the \<All Tables> diagram.</span></span> <span data-ttu-id="215bc-124">ダイアグラムでは \<All Tables> 、データソースビューに含まれるすべてのオブジェクトが1回だけ表示されます。</span><span class="sxs-lookup"><span data-stu-id="215bc-124">In the \<All Tables> diagram, all objects that are contained in the data source view are shown exactly once.</span></span>  
  
##  <a name="edit-or-delete-a-diagram"></a><a name="bkmk_edit"></a><span data-ttu-id="215bc-125">ダイアグラムを編集または削除する</span><span class="sxs-lookup"><span data-stu-id="215bc-125">Edit or Delete a Diagram</span></span>  
 <span data-ttu-id="215bc-126">ダイアグラムの操作をするときは、オブジェクトの追加と削除に使用するコマンドに十分注意してください。</span><span class="sxs-lookup"><span data-stu-id="215bc-126">When working with a diagram, pay close attention to the commands used for adding and removing objects.</span></span> <span data-ttu-id="215bc-127">たとえば、オブジェクトをダイアグラムから削除すると DSV から削除されます。</span><span class="sxs-lookup"><span data-stu-id="215bc-127">For example, deleting an object from a diagram will delete it from the DSV.</span></span> <span data-ttu-id="215bc-128">オブジェクトをダイアグラムからのみ削除する場合は、 **[テーブルの非表示]** を使用します。</span><span class="sxs-lookup"><span data-stu-id="215bc-128">If you only want to delete it from the diagram, use **Hide Table** instead.</span></span>  
  
 <span data-ttu-id="215bc-129">![ダイアグラム ワークスペース (右クリック メニュー) のスクリーンショット](../media/ssas-olapdsv-diagram.gif "ダイアグラム ワークスペース (右クリック メニュー) のスクリーンショット")</span><span class="sxs-lookup"><span data-stu-id="215bc-129">![Screenshot of diagram workspace, right-click menu](../media/ssas-olapdsv-diagram.gif "Screenshot of diagram workspace, right-click menu")</span></span>  
  
 <span data-ttu-id="215bc-130">オブジェクトを個別に非表示にすることができますが、[関連テーブルの表示] を使用して戻すと、ダイアグラムにすべての関連オブジェクトが返されます。</span><span class="sxs-lookup"><span data-stu-id="215bc-130">Although you can hide objects individually, bringing them back using the Show Related Tables command returns all related objects to the diagram.</span></span> <span data-ttu-id="215bc-131">ワークスペースにどのオブジェクトが返されるかを制御するには、[テーブル] ペインからオブジェクトをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="215bc-131">To control which objects are returned to the workspace, drag them from the Tables pane instead.</span></span>  
  
##  <a name="find-tables-in-a-diagram"></a><a name="bkmk_findtables"></a><span data-ttu-id="215bc-132">ダイアグラム内のテーブルの検索</span><span class="sxs-lookup"><span data-stu-id="215bc-132">Find Tables in a Diagram</span></span>  
 <span data-ttu-id="215bc-133">使用するスキーマが大きい場合、 **[ダイアグラム]** ペインで特定のテーブルにスクロールするのが困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="215bc-133">If your schema is large, scrolling to a particular table in the **Diagram** pane may be difficult.</span></span> <span data-ttu-id="215bc-134">この場合、次のツールを使用すると、ダイアグラム内でテーブルを簡単に見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="215bc-134">However, the following tools make it easy to find a table in a diagram.</span></span>  
  
-   <span data-ttu-id="215bc-135">**[テーブル]** ペインでテーブルの一覧をスクロールします。</span><span class="sxs-lookup"><span data-stu-id="215bc-135">Scroll the list of tables in the **Tables** pane.</span></span>  
  
     <span data-ttu-id="215bc-136">現在表示されているダイアグラムにテーブルを含めるには、 **[テーブル]** ペインからダイアグラム ペインにテーブルをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="215bc-136">To include a table in the currently displayed diagram, drag the table from the **Tables** pane to the diagram pane.</span></span>  
  
     <span data-ttu-id="215bc-137">既にダイアグラムに含まれているテーブルを中心に表示するには、 **[テーブル]** ペインでそのテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="215bc-137">To center the display on a table that is already included in the diagram, select the table in the **Tables** pane.</span></span>  
  
-   <span data-ttu-id="215bc-138">**ダイアグラム**ペインのテーブルロケーター-テーブルロケーターは、**ダイアグラム**ペインの右下隅にある垂直スクロールバーと水平スクロールバーの交差部分にある4方向矢印アイコンです。</span><span class="sxs-lookup"><span data-stu-id="215bc-138">Table locator in **Diagram** pane-The table locator is a 4-way arrow icon located at the intersection of the vertical and horizontal scroll bars in the lower right corner of the **Diagram** pane.</span></span> <span data-ttu-id="215bc-139">その中で、ダイアグラム ペインに表示されている現在のダイアグラムのサムネイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="215bc-139">It opens a thumbnail representation of the current diagram in the Diagram pane.</span></span> <span data-ttu-id="215bc-140">このサムネイルを使用すると、ダイアグラム ペインの表示をダイアグラム上の任意の位置に変更できます。</span><span class="sxs-lookup"><span data-stu-id="215bc-140">You can use this thumbnail to change the view in the Diagram pane to any location on the diagram.</span></span>  
  
-   <span data-ttu-id="215bc-141">[**テーブルの検索**] ダイアログボックスを使用して、ダイアグラムペインの [空いている領域] を右クリックし、[**テーブルの検索**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="215bc-141">Use the **Find Table** dialog box- Right-click on open area in the Diagram pane and click **Find Table**.</span></span> <span data-ttu-id="215bc-142">または、ツール バーか **[データ ソース ビュー]** メニューの **[テーブルの検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="215bc-142">Or, click the **Find Table** command on the toolbar or the **Data Source View** menu.</span></span>  
  
     <span data-ttu-id="215bc-143">[フィルター] ボックスに文字列およびワイルドカード文字を入力すると、ダイアグラム内のテーブルのサブセットを表示できます。</span><span class="sxs-lookup"><span data-stu-id="215bc-143">You can type strings and wildcard characters in the Filter box to view subsets of the tables in the diagram.</span></span>  
  
##  <a name="arrange-objects-in-a-diagram"></a><a name="bkmk_arrangeobjects"></a> <span data-ttu-id="215bc-144">ダイアグラム内のオブジェクトの配置</span><span class="sxs-lookup"><span data-stu-id="215bc-144">Arrange Objects in a Diagram</span></span>  
 <span data-ttu-id="215bc-145">データ ソース ビュー デザイナーでは、複数のダイアグラムを定義して DSV をわかりやすくすることができますが、数十個のテーブルを含んでいるダイアグラムは読み取りにくく、テーブルのレイアウトを手動で再調整するのは面倒な作業です。</span><span class="sxs-lookup"><span data-stu-id="215bc-145">Although Data Source View Designer can define multiple diagrams to make a DSV more understandable, diagrams that contain dozens of tables can be hard to read and manually rearranging table layouts is a tedious process.</span></span> <span data-ttu-id="215bc-146">データ ソース ビュー デザイナーでは、現在のダイアグラムにあるテーブル間のリレーションシップに基づいた四角形レイアウトまたは斜線レイアウトを使用して、現在のダイアグラムにあるテーブルを自動的に再調整できます。</span><span class="sxs-lookup"><span data-stu-id="215bc-146">The Data Source View Designer can automatically rearrange tables in the current diagram using either a rectangular or diagonal layout based on the relationships between tables in the current diagram.</span></span>  
  
-   <span data-ttu-id="215bc-147">四角形レイアウトでは、リレーションシップの線は列間ではなくテーブル間に引かれます。</span><span class="sxs-lookup"><span data-stu-id="215bc-147">In a rectangular layout, the relationship lines are drawn between tables instead of between columns.</span></span> <span data-ttu-id="215bc-148">リレーションシップの線は、テーブル間で横方向および縦方向に表示されます。</span><span class="sxs-lookup"><span data-stu-id="215bc-148">Relationship lines are drawn horizontally and vertically between tables.</span></span>  
  
-   <span data-ttu-id="215bc-149">斜線レイアウトでは、リレーションシップの線はテーブル内の関連する列間で、できるだけ直接的に引かれます。</span><span class="sxs-lookup"><span data-stu-id="215bc-149">In a diagonal layout, relationship lines are drawn as directly as possible between related columns in tables.</span></span> <span data-ttu-id="215bc-150">複数の列へのリレーションシップは、テーブル内の関連する最初の列に接続しています。</span><span class="sxs-lookup"><span data-stu-id="215bc-150">A relationship to multiple columns attaches to the first related column in the table.</span></span> <span data-ttu-id="215bc-151">テーブル内の列が表示されていない場合、線はテーブルの一番上に向かって引かれます。</span><span class="sxs-lookup"><span data-stu-id="215bc-151">If the columns in a table are not visible, the lines are drawn to the top of the table.</span></span>  
  
##  <a name="preserve-object-arrangement"></a><a name="bkmk_preserve"></a><span data-ttu-id="215bc-152">オブジェクトの配置を保持する</span><span class="sxs-lookup"><span data-stu-id="215bc-152">Preserve object arrangement</span></span>  
 <span data-ttu-id="215bc-153">希望の方法に従ってテーブルを手動で配置した後、さらにテーブルをダイアグラムに追加すると、ダイアグラムが更新され、その結果、オブジェクトのレイアウトに対して加えた最近の変更が失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="215bc-153">After manually arranging tables the way you want, adding more tables to the diagram can result in a diagram refresh that removes any recent modifications you made to the object layout.</span></span>  
  
 <span data-ttu-id="215bc-154">この動作が発生する可能性が高いのはテーブルを追加するときであり、ダイアグラム オーガナイザーは新しいテーブルを収容する場所を確保するために、他のテーブルを移動することになります。</span><span class="sxs-lookup"><span data-stu-id="215bc-154">This behavior is more likely to occur when you add a table, causing the Diagram Organizer to move other tables in order to accommodate the new one.</span></span> <span data-ttu-id="215bc-155">その後、すべてのテーブルと接続線が正しく表現されるように、ダイアグラムが再描画されます。</span><span class="sxs-lookup"><span data-stu-id="215bc-155">It then redraws the diagram to ensure all tables and connection lines represented correctly.</span></span> <span data-ttu-id="215bc-156">この時点で、特定のオブジェクトの配置に対するすべての手動調整が失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="215bc-156">At this point, any manual adjustments to the placement of specific objects might be lost.</span></span>  
  
 <span data-ttu-id="215bc-157">この問題を回避するには、最終的な調整を行う前に、最初にすべてのテーブルを追加します。</span><span class="sxs-lookup"><span data-stu-id="215bc-157">To avoid this problem, add all the tables first, before making any final adjustments.</span></span> <span data-ttu-id="215bc-158">この場合は、後でダイアグラムを再度開くときに、オブジェクトは自らの位置を保持しています。</span><span class="sxs-lookup"><span data-stu-id="215bc-158">Objects should now retain their position in the diagram when you open it again later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="215bc-159">参照</span><span class="sxs-lookup"><span data-stu-id="215bc-159">See Also</span></span>  
 <span data-ttu-id="215bc-160">[多次元モデルのデータソースビュー](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="215bc-160">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="215bc-161">データ ソース ビュー デザイナー (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="215bc-161">Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  
