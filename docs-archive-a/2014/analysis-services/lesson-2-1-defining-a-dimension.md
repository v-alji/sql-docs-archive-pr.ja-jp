---
title: ディメンションの定義 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 112696db-3838-4b50-91bd-d2ce5fa04ee5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2eb7a695ffc2c0588396a4a9ea655983c26cc719
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631290"
---
# <a name="defining-a-dimension"></a><span data-ttu-id="96660-102">ディメンションの定義</span><span class="sxs-lookup"><span data-stu-id="96660-102">Defining a Dimension</span></span>
  <span data-ttu-id="96660-103">この実習では、ディメンション ウィザードを使用して Date ディメンションを構築します。</span><span class="sxs-lookup"><span data-stu-id="96660-103">In the following task, you will use the Dimension Wizard to build a Date dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="96660-104">このレッスンを学習するには、レッスン 1 のすべての手順を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="96660-104">This lesson requires that you have completed all the procedures in Lesson 1.</span></span>  
  
### <a name="to-define-a-dimension"></a><span data-ttu-id="96660-105">ディメンションを定義するには</span><span class="sxs-lookup"><span data-stu-id="96660-105">To define a dimension</span></span>  
  
1.  <span data-ttu-id="96660-106">ソリューション エクスプローラー (Microsoft Visual Studio の右側) で、 **[ディメンション]** を右クリックし、 **[新しいディメンション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96660-106">In Solution Explorer (on the right side of Microsoft Visual Studio), right-click **Dimensions**, and then click **New Dimension**.</span></span> <span data-ttu-id="96660-107">ディメンション ウィザードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="96660-107">The Dimension Wizard appears.</span></span>  
  
2.  <span data-ttu-id="96660-108">**[ディメンション ウィザードへようこそ]** ページで **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96660-108">On the **Welcome to the Dimension Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="96660-109">**[作成方法の選択]** ページで **[既存のテーブルの使用]** オプションが選択されていることを確認し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96660-109">On the **Select Creation Method** page, verify that the **Use an existing table** option is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="96660-110">**[基になる情報の指定]** ページで、 **Adventure Works DW 2012** データ ソース ビューが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="96660-110">On the **Specify Source Information** page, verify that the **Adventure Works DW 2012** data source view is selected.</span></span>  
  
5.  <span data-ttu-id="96660-111">**[メイン テーブル]** ボックスの一覧で、 **[Date]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="96660-111">In the **Main table** list, select **Date**.</span></span>  
  
6.  <span data-ttu-id="96660-112">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96660-112">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="96660-113">**[ディメンション属性の選択]** ページで、次の属性の横にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="96660-113">On the **Select Dimension Attributes** page, select the check boxes next to the following attributes:</span></span>  
  
    -   <span data-ttu-id="96660-114">**Date Key**</span><span class="sxs-lookup"><span data-stu-id="96660-114">**Date Key**</span></span>  
  
    -   <span data-ttu-id="96660-115">**Full Date Alternate Key**</span><span class="sxs-lookup"><span data-stu-id="96660-115">**Full Date Alternate Key**</span></span>  
  
    -   <span data-ttu-id="96660-116">**English Month Name**</span><span class="sxs-lookup"><span data-stu-id="96660-116">**English Month Name**</span></span>  
  
    -   <span data-ttu-id="96660-117">**Calendar Quarter**</span><span class="sxs-lookup"><span data-stu-id="96660-117">**Calendar Quarter**</span></span>  
  
    -   <span data-ttu-id="96660-118">**暦年**</span><span class="sxs-lookup"><span data-stu-id="96660-118">**Calendar Year**</span></span>  
  
    -   <span data-ttu-id="96660-119">**Calendar Semester**</span><span class="sxs-lookup"><span data-stu-id="96660-119">**Calendar Semester**</span></span>  
  
8.  <span data-ttu-id="96660-120">**Full Date Alternate Key** 属性の **[属性の型]** 列の設定を **Regular** から **Date**に変更します。</span><span class="sxs-lookup"><span data-stu-id="96660-120">Change the setting of the **Full Date Alternate Key** attribute's **Attribute Type** column from **Regular** to **Date**.</span></span> <span data-ttu-id="96660-121">これを行うには、 **[属性の型]** 列で **[Regular]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96660-121">To do this, click **Regular** in the **Attribute Type** column.</span></span> <span data-ttu-id="96660-122">次に、矢印をクリックしてオプションを展開し、</span><span class="sxs-lookup"><span data-stu-id="96660-122">Then click the arrow to expand the options.</span></span> <span data-ttu-id="96660-123">次に、 **[カレンダーの日付]** をクリックし  >  **Calendar**  >  **Date**ます。</span><span class="sxs-lookup"><span data-stu-id="96660-123">Next, click **Date** > **Calendar** > **Date**.</span></span> <span data-ttu-id="96660-124">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96660-124">Click **OK**.</span></span> <span data-ttu-id="96660-125">次の属性について同じ手順を繰り返し、属性の型を次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="96660-125">Repeat these steps to change the attribute type of the attributes as follows:</span></span>  
  
    -   <span data-ttu-id="96660-126">**English Month Name** から **Month**</span><span class="sxs-lookup"><span data-stu-id="96660-126">**English Month Name** to **Month**</span></span>  
  
    -   <span data-ttu-id="96660-127">**Calendar Quarter** から **Quarter**</span><span class="sxs-lookup"><span data-stu-id="96660-127">**Calendar Quarter** to **Quarter**</span></span>  
  
    -   <span data-ttu-id="96660-128">**Calendar Year** から **Year**</span><span class="sxs-lookup"><span data-stu-id="96660-128">**Calendar Year** to **Year**</span></span>  
  
    -   <span data-ttu-id="96660-129">**Calendar Semester** から **Half Year**</span><span class="sxs-lookup"><span data-stu-id="96660-129">**Calendar Semester** to **Half Year**</span></span>  
  
9. <span data-ttu-id="96660-130">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96660-130">Click **Next**.</span></span>  
  
10. <span data-ttu-id="96660-131">**[ウィザードの完了]** ページの [プレビュー] ペインで、 **Date** ディメンションとその属性を確認できます。</span><span class="sxs-lookup"><span data-stu-id="96660-131">On the **Completing the Wizard** page, in the Preview pane, you can see the **Date** dimension and its attributes.</span></span>  
  
11. <span data-ttu-id="96660-132">**[完了]** をクリックしてウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="96660-132">Click **Finish** to complete the wizard.</span></span>  
  
     <span data-ttu-id="96660-133">ソリューション エクスプローラーでは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトの **[ディメンション]** フォルダー内に Date ディメンションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="96660-133">In Solution Explorer, in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project, the Date dimension appears in the **Dimensions** folder.</span></span> <span data-ttu-id="96660-134">開発環境の中央では、ディメンション デザイナーに Date ディメンションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="96660-134">In the center of the development environment, Dimension Designer displays the Date dimension.</span></span>  
  
12. <span data-ttu-id="96660-135">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96660-135">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="96660-136">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="96660-136">Next Task in Lesson</span></span>  
 [<span data-ttu-id="96660-137">キューブの定義</span><span class="sxs-lookup"><span data-stu-id="96660-137">Defining a Cube</span></span>](lesson-2-2-defining-a-cube.md)  
  
## <a name="see-also"></a><span data-ttu-id="96660-138">参照</span><span class="sxs-lookup"><span data-stu-id="96660-138">See Also</span></span>  
 <span data-ttu-id="96660-139">[多次元モデル内のディメンション](multidimensional-models/dimensions-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="96660-139">[Dimensions in Multidimensional Models](multidimensional-models/dimensions-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="96660-140">[既存のテーブルを使用してディメンションを作成する](multidimensional-models/create-a-dimension-by-using-an-existing-table.md) </span><span class="sxs-lookup"><span data-stu-id="96660-140">[Create a Dimension by Using an Existing Table](multidimensional-models/create-a-dimension-by-using-an-existing-table.md) </span></span>  
 [<span data-ttu-id="96660-141">ディメンション ウィザードを使用したディメンションの作成</span><span class="sxs-lookup"><span data-stu-id="96660-141">Create a Dimension Using the Dimension Wizard</span></span>](multidimensional-models/create-a-dimension-using-the-dimension-wizard.md)  
  
  
