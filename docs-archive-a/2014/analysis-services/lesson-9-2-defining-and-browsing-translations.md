---
title: 翻訳の定義と参照 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0e60be99-3768-499c-a22c-a4ec37e61887
author: minewiskan
ms.author: owend
ms.openlocfilehash: 351960375ce60825dfceccaa83856545c6b9208f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718830"
---
# <a name="defining-and-browsing-translations"></a><span data-ttu-id="50b42-102">翻訳の定義と表示</span><span class="sxs-lookup"><span data-stu-id="50b42-102">Defining and Browsing Translations</span></span>
  <span data-ttu-id="50b42-103">翻訳とは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のオブジェクトの名前を特定の言語で表現することです。</span><span class="sxs-lookup"><span data-stu-id="50b42-103">A translation is a representation of the names of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects in a specific language.</span></span> <span data-ttu-id="50b42-104">オブジェクトには、メジャー グループ、メジャー、ディメンション、属性、階層、KPI、アクション、計算されるメンバーなどがあります。</span><span class="sxs-lookup"><span data-stu-id="50b42-104">Objects include measure groups, measures, dimensions, attributes, hierarchies, KPIs, actions, and calculated members.</span></span> <span data-ttu-id="50b42-105">翻訳によって、複数言語を使用するクライアント アプリケーションをサーバーがサポートできるようになります。</span><span class="sxs-lookup"><span data-stu-id="50b42-105">Translations provide server support for client applications that can support multiple languages.</span></span> <span data-ttu-id="50b42-106">この場合、クライアントは、ロケール識別子 (LCID) を [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のインスタンスに渡します。 のインスタンスはこの LCID に基づいて、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトにメタデータを提供する際に使用する翻訳セットを判別します。</span><span class="sxs-lookup"><span data-stu-id="50b42-106">By using such a client, the client passes the locale identifier (LCID) to the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], which uses the LCID to determine which set of translations to use when it provides metadata for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects.</span></span> <span data-ttu-id="50b42-107">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトにその言語の翻訳が含まれていない場合、または特定のオブジェクトの翻訳が含まれていない場合は、オブジェクトのメタデータがクライアントに送り返される際に既定の言語が使用されます。</span><span class="sxs-lookup"><span data-stu-id="50b42-107">If an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object does not contain a translation for that language, or does not contain a translation for a specified object, the default language is used in returning the object metadata back to the client.</span></span> <span data-ttu-id="50b42-108">たとえば、フランスのビジネス ユーザーが、フランス語にロケール設定されたワークステーションからキューブにアクセスした場合、該当する項目がフランス語に翻訳されているのであれば、メンバー キャプションとメンバー プロパティ値がフランス語で表示されます。</span><span class="sxs-lookup"><span data-stu-id="50b42-108">For example, if a business user in France accesses a cube from a workstation that has a French locale setting, the business user will see the member captions and member property values in French if a French translation exists.</span></span> <span data-ttu-id="50b42-109">一方、ドイツのビジネス ユーザーが、ドイツ語にロケール設定されたワークステーションから同じキューブにアクセスすると、メンバー キャプションとメンバー プロパティ値はドイツ語で表示されます。</span><span class="sxs-lookup"><span data-stu-id="50b42-109">However, if a business user in Germany accesses the same cube from a workstation that has a German locale setting, the business user will see the captions names and member property values in German.</span></span> <span data-ttu-id="50b42-110">詳細については、「[ディメンションの翻訳](multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)」、「[キューブの翻訳](multidimensional-models-olap-logical-cube-objects/cube-translations.md)」、「[翻訳 &#40;Analysis Services&#41;](translations-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50b42-110">For more information, see [Dimension Translations](multidimensional-models-olap-logical-dimension-objects/dimension-translations.md), [Cube Translations](multidimensional-models-olap-logical-cube-objects/cube-translations.md), [Translations &#40;Analysis Services&#41;](translations-analysis-services.md).</span></span>  
  
 <span data-ttu-id="50b42-111">このトピックの作業では、Date ディメンションのディメンション オブジェクトと [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ オブジェクトの限定されたセットに関するメタデータ翻訳を定義します。</span><span class="sxs-lookup"><span data-stu-id="50b42-111">In the tasks in this topic, you define metadata translations for a limited set of dimension objects in the Date dimension and cube objects in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span> <span data-ttu-id="50b42-112">それから、これらのディメンションとキューブ オブジェクトを表示して、メタデータ翻訳を確認します。</span><span class="sxs-lookup"><span data-stu-id="50b42-112">You will then browse these dimension and cube objects to examine the metadata translations.</span></span>  
  
## <a name="specifying-translations-for-the-date-dimension-metadata"></a><span data-ttu-id="50b42-113">Date ディメンションのメタデータの翻訳の指定</span><span class="sxs-lookup"><span data-stu-id="50b42-113">Specifying Translations for the Date Dimension Metadata</span></span>  
  
1.  <span data-ttu-id="50b42-114">**Date** ディメンションのディメンション デザイナーを開き、 **[翻訳]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="50b42-114">Open Dimension Designer for the **Date** dimension, and then click the **Translations** tab.</span></span>  
  
     <span data-ttu-id="50b42-115">各ディメンション オブジェクトの既定の言語でメタデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="50b42-115">The metadata in the default language for each dimension object appears.</span></span> <span data-ttu-id="50b42-116">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブの既定の言語は英語です。</span><span class="sxs-lookup"><span data-stu-id="50b42-116">The default language in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube is English.</span></span>  
  
2.  <span data-ttu-id="50b42-117">**[翻訳]** タブのツール バーで **[新しい翻訳]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="50b42-117">On the toolbar of the **Translations** tab, click the **New Translation** button.</span></span>  
  
     <span data-ttu-id="50b42-118">**[言語の選択]** ダイアログ ボックスに言語の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="50b42-118">A list of languages appears in the **Select Language** dialog box.</span></span>  
  
3.  <span data-ttu-id="50b42-119">**[スペイン語 (スペイン)]** をクリックして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50b42-119">Click **Spanish (Spain)**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="50b42-120">新しい列が表示されるので、翻訳対象のメタデータ オブジェクトのスペイン語の翻訳をその列で定義します。</span><span class="sxs-lookup"><span data-stu-id="50b42-120">A new column appears in which you will define the Spanish translations for the metadata objects you want to translate.</span></span> <span data-ttu-id="50b42-121">このチュートリアルでは、プロセスを示すために少数のオブジェクトだけを翻訳します。</span><span class="sxs-lookup"><span data-stu-id="50b42-121">In this tutorial, we will only translate a few objects just to illustrate the process.</span></span>  
  
4.  <span data-ttu-id="50b42-122">**[翻訳]** タブのツール バーで **[新しい翻訳]** ボタンをクリックします。 **[言語の選択]** ダイアログ ボックスで **[フランス語 (フランス)]** をクリックして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50b42-122">On the toolbar of the **Translations** tab, click the **New Translation** button, click **French (France)** in the **Select Language** dialog box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="50b42-123">新しい言語列が表示されるので、フランス語の翻訳をその列で定義します。</span><span class="sxs-lookup"><span data-stu-id="50b42-123">Another language column appears in which you will define French translations.</span></span>  
  
5.  <span data-ttu-id="50b42-124">**Date**ディメンションの**キャプション**オブジェクトの行で、[ `Fecha` **スペイン語 (スペイン)** ] 翻訳列と [ `Temps` **フランス語 (フランス)** ] 翻訳列に「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="50b42-124">In the row for the **Caption** object for the **Date** dimension, type `Fecha` in the **Spanish (Spain)** translation column and `Temps` in the **French (France)** translation column.</span></span>  
  
6.  <span data-ttu-id="50b42-125">**Month Name**属性の**Caption**オブジェクトの行で、 `Mes del Año` **スペイン語 (スペイン)** 翻訳列を入力し、[ `Mois d'Année` **フランス語 (フランス)** ] 翻訳列に「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="50b42-125">In the row for the **Caption** object for the **Month Name** attribute, type `Mes del Año` in the **Spanish (Spain)** translation column and `Mois d'Année` in the **French (France)** translation column.</span></span>  
  
     <span data-ttu-id="50b42-126">これらの翻訳を入力すると、省略記号 (**..**.) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="50b42-126">Notice that when you enter these translations, an ellipsis (**...**) appears.</span></span> <span data-ttu-id="50b42-127">この参照ボタンをクリックすると、属性階層の各メンバーの翻訳を入力する基になるテーブルの列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="50b42-127">Clicking this ellipsis will enable you to specify a column in the underlying table that provides translations for each member of the attribute hierarchy.</span></span>  
  
7.  <span data-ttu-id="50b42-128">**Month Name**属性の [**スペイン語 (スペイン)** ] 翻訳の省略記号 (**...**) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50b42-128">Click the ellipsis (**...**) for the **Spanish (Spain)** translation for the **Month Name** attribute.</span></span>  
  
     <span data-ttu-id="50b42-129">**[属性データの翻訳]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="50b42-129">The **Attribute Data Translation** dialog box appears.</span></span>  
  
8.  <span data-ttu-id="50b42-130">次の図のように、 **[翻訳列]** ボックスの一覧で **[SpanishMonthName]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50b42-130">In the **Translation columns** list, select **SpanishMonthName**, as shown in the following image.</span></span>  
  
     <span data-ttu-id="50b42-131">![[属性データの翻訳] ダイアログボックス](../../2014/tutorials/media/l9-translations-4.gif "[属性データの翻訳] ダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="50b42-131">![Attribute Data Translation dialog box](../../2014/tutorials/media/l9-translations-4.gif "Attribute Data Translation dialog box")</span></span>  
  
9. <span data-ttu-id="50b42-132">[ **OK**] をクリックし、 **Month Name**属性の [**フランス語 (フランス)** ] 翻訳の省略記号ボタン ([**...**]) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50b42-132">Click **OK**, and then click the ellipsis (**...**) for the **French (France)** translation for the **Month Name** attribute.</span></span>  
  
10. <span data-ttu-id="50b42-133">**[翻訳列]** ボックスの一覧で **[FrenchMonthName]** をクリックして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50b42-133">In the **Translation columns** list, select **FrenchMonthName**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="50b42-134">この手順は、ディメンション オブジェクトおよびメンバーのメタデータ翻訳を定義するプロセスを示しています。</span><span class="sxs-lookup"><span data-stu-id="50b42-134">The steps in this procedure illustrate the process of defining metadata translations for dimension objects and members.</span></span>  
  
## <a name="specifying-translations-for-the-analysis-services-tutorial-cube-metadata"></a><span data-ttu-id="50b42-135">Analysis Services Tutorial キューブのメタデータの翻訳の指定</span><span class="sxs-lookup"><span data-stu-id="50b42-135">Specifying Translations for the Analysis Services Tutorial Cube Metadata</span></span>  
  
1.  <span data-ttu-id="50b42-136">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ デザイナーを開いて、 **[翻訳]** タブに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="50b42-136">Switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then switch to the **Translations** tab.</span></span>  
  
     <span data-ttu-id="50b42-137">次の図のように、各キューブ オブジェクトの既定の言語でメタデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="50b42-137">The metadata in the default language for each cube object appears, as shown in the following image.</span></span> <span data-ttu-id="50b42-138">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブの既定の言語は英語です。</span><span class="sxs-lookup"><span data-stu-id="50b42-138">The default language in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube is English.</span></span>  
  
     <span data-ttu-id="50b42-139">![[翻訳] タブの既定の言語](../../2014/tutorials/media/l9-translations-5.gif "[翻訳] タブの既定の言語")</span><span class="sxs-lookup"><span data-stu-id="50b42-139">![Default language in Translations tab](../../2014/tutorials/media/l9-translations-5.gif "Default language in Translations tab")</span></span>  
  
2.  <span data-ttu-id="50b42-140">**[翻訳]** タブのツール バーで **[新しい翻訳]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="50b42-140">On the toolbar of the **Translations** tab, click the **New Translation** button.</span></span>  
  
     <span data-ttu-id="50b42-141">**[言語の選択]** ダイアログ ボックスに言語の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="50b42-141">A list of languages appears in the **Select Language** dialog box.</span></span>  
  
3.  <span data-ttu-id="50b42-142">**[スペイン語 (スペイン)]** を選択して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50b42-142">Select **Spanish (Spain)**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="50b42-143">新しい列が表示されるので、翻訳対象のメタデータ オブジェクトのスペイン語の翻訳をその列で定義します。</span><span class="sxs-lookup"><span data-stu-id="50b42-143">A new column appears in which you will define the Spanish translations for the metadata objects you want to translate.</span></span> <span data-ttu-id="50b42-144">このチュートリアルでは、プロセスを示すために少数のオブジェクトだけを翻訳します。</span><span class="sxs-lookup"><span data-stu-id="50b42-144">In this tutorial, we will only translate a few objects just to illustrate the process.</span></span>  
  
4.  <span data-ttu-id="50b42-145">**[翻訳]** タブのツール バーで **[新しい翻訳]** ボタンをクリックします。 **[言語の選択]** ダイアログ ボックスで **[フランス語 (フランス)]** をクリックして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50b42-145">On the toolbar of the **Translations** tab, click the **New Translation** button, select **French (France)** in the **Select Language** dialog box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="50b42-146">新しい言語列が表示されるので、フランス語の翻訳をその列で定義します。</span><span class="sxs-lookup"><span data-stu-id="50b42-146">Another language column appears in which you will define French translations.</span></span>  
  
5.  <span data-ttu-id="50b42-147">**Date**ディメンションの**キャプション**オブジェクトの行で、[ `Fecha` **スペイン語 (スペイン)** ] 翻訳列と [ `Temps` **フランス語 (フランス)** ] 翻訳列に「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="50b42-147">In the row for the **Caption** object for the **Date** dimension, type `Fecha` in the **Spanish (Spain)** translation column and `Temps` in the **French (France)** translation column.</span></span>  
  
6.  <span data-ttu-id="50b42-148">**Internet Sales**メジャーグループの**キャプション**オブジェクトの行で、[ `Ventas del lnternet` **スペイン語 (スペイン)** ] 翻訳列と [ `Ventes D'Internet` **フランス語 (フランス)** ] 翻訳列に「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="50b42-148">In the row for the **Caption** object for the **Internet Sales** measure group, type `Ventas del lnternet` in the **Spanish (Spain)** translation column and `Ventes D'Internet` in the **French (France)** translation column.</span></span>  
  
7.  <span data-ttu-id="50b42-149">Internet Sales sales Amount メジャーの**キャプション**オブジェクトの行で、[ `Cantidad de las Ventas del Internet` **スペイン語 (スペイン)** ] 翻訳列と [ `Quantité de Ventes d'Internet` **フランス語 (フランス)** ] 翻訳列に「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="50b42-149">In the row for the **Caption** object for the Internet Sales-Sales Amount measure, type `Cantidad de las Ventas del Internet` in the **Spanish (Spain)** translation column and `Quantité de Ventes d'Internet` in the **French (France)** translation column.</span></span>  
  
     <span data-ttu-id="50b42-150">この手順は、キューブ オブジェクトのメタデータ翻訳を定義するプロセスを示しています。</span><span class="sxs-lookup"><span data-stu-id="50b42-150">The steps in this procedure illustrate the process of defining metadata translations for cube objects.</span></span>  
  
## <a name="browsing-the-cube-by-using-translations"></a><span data-ttu-id="50b42-151">翻訳を使用したキューブの表示</span><span class="sxs-lookup"><span data-stu-id="50b42-151">Browsing the Cube By Using Translations</span></span>  
  
1.  <span data-ttu-id="50b42-152">**[ビルド]** メニューの **[Analysis Services Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50b42-152">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="50b42-153">配置が正常に完了したら、 **[ブラウザー]** タブに切り替えて、 **[再接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50b42-153">When deployment has successfully completed, switch to the **Browser** tab, and then click **Reconnect**.</span></span>  
  
3.  <span data-ttu-id="50b42-154">**データ** ペインからすべての階層とメジャーを削除して、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [パースペクティブ] **ボックスの一覧で [** Tutorial] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50b42-154">Remove all hierarchies and measures from the **Data** pane and select [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial in the **Perspectives** list.</span></span>  
  
4.  <span data-ttu-id="50b42-155">メタデータ ペインで、 **[Measures]** 、 **[Internet Sales]** の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="50b42-155">In the metadata pane, expand **Measures** and then expand **Internet Sales**.</span></span>  
  
     <span data-ttu-id="50b42-156">このメジャー グループに **Internet Sales-Sales Amount** メジャー (英語) があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="50b42-156">Notice that the **Internet Sales-Sales Amount** measure appears in English in this measure group.</span></span>  
  
5.  <span data-ttu-id="50b42-157">ツール バーの **[言語]** ボックスの一覧で **[スペイン語 (スペイン)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50b42-157">On the toolbar, select **Spanish (Spain)** in the **Language** list.</span></span>  
  
     <span data-ttu-id="50b42-158">メタデータ ペインのアイテムが再設定されます。</span><span class="sxs-lookup"><span data-stu-id="50b42-158">Notice that the items in the metadata pane are repopulated.</span></span> <span data-ttu-id="50b42-159">メタデータ ペインのアイテムが再設定されると、Internet Sales-Sales Amount メジャーが [Internet Sales] 表示フォルダーに表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="50b42-159">After the items in the metadata pane are repopulated, notice that the Internet Sales-Sales Amount measure no longer appears in the Internet Sales display folder.</span></span> <span data-ttu-id="50b42-160">代わりに、 `Ventas del lnternet` 次の図に示すように、スペイン語ではという名前の新しい表示フォルダーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="50b42-160">Instead, it appears in Spanish in a new display folder named `Ventas del lnternet`, as shown in the following image.</span></span>  
  
     <span data-ttu-id="50b42-161">![再読み込みメタデータペイン](../../2014/tutorials/media/l9-translations-6.gif "再読み込みメタデータペイン")</span><span class="sxs-lookup"><span data-stu-id="50b42-161">![Repopulated metadata pane](../../2014/tutorials/media/l9-translations-6.gif "Repopulated metadata pane")</span></span>  
  
6.  <span data-ttu-id="50b42-162">メタデータペインでを右クリックし、[ `Cantidad de las Ventas del Internet` **クエリに追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="50b42-162">In the metadata pane, right-click `Cantidad de las Ventas del Internet` and then select **Add to Query**.</span></span>  
  
7.  <span data-ttu-id="50b42-163">[メタデータ] ペインで、[] を展開し、[ `Fecha` ] を展開**します。** **[** カレンダーの日付] を右クリックし、[**フィルターに追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="50b42-163">In the metadata pane, expand `Fecha`, expand **Fecha.Calendar Date**, right-click **Fecha.Calendar Date**, and then select **Add to Filter**.</span></span>  
  
8.  <span data-ttu-id="50b42-164">**フィルター** ペインで、フィルター式として **[CY 2007]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="50b42-164">In the **Filter** pane, select **CY 2007** as the filter expression.</span></span>  
  
9. <span data-ttu-id="50b42-165">メタデータ ペインで **[Mes del Ano]** を右クリックし、 **[クエリに追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50b42-165">In the metadata pane, right-click **Mes del Ano** and select **Add to Query**.</span></span>  
  
     <span data-ttu-id="50b42-166">次の図のように、月の名前がスペイン語で表示されます。</span><span class="sxs-lookup"><span data-stu-id="50b42-166">Notice that the month names appear in Spanish, as shown in the following image.</span></span>  
  
     <span data-ttu-id="50b42-167">![データ ペインに表示されたスペイン語での月の名前](../../2014/tutorials/media/l9-translations-7.gif "データ ペインに表示されたスペイン語での月の名前")</span><span class="sxs-lookup"><span data-stu-id="50b42-167">![Month names in Spanish in data pane](../../2014/tutorials/media/l9-translations-7.gif "Month names in Spanish in data pane")</span></span>  
  
10. <span data-ttu-id="50b42-168">ツール バーの **[言語]** ボックスの一覧で **[フランス語 (フランス)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50b42-168">On the toolbar, select **French (France)** in the **Language** list.</span></span>  
  
     <span data-ttu-id="50b42-169">月の名前がフランス語で表示され、メジャー名もフランス語で表示されます。</span><span class="sxs-lookup"><span data-stu-id="50b42-169">Notice that the month names now appear in French and that the measure name now also appears in French.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="50b42-170">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="50b42-170">Next Lesson</span></span>  
 [<span data-ttu-id="50b42-171">レッスン 10: 管理ロールの定義</span><span class="sxs-lookup"><span data-stu-id="50b42-171">Lesson 10: Defining Administrative Roles</span></span>](lesson-10-defining-administrative-roles.md)  
  
## <a name="see-also"></a><span data-ttu-id="50b42-172">参照</span><span class="sxs-lookup"><span data-stu-id="50b42-172">See Also</span></span>  
 <span data-ttu-id="50b42-173">[ディメンションの翻訳](multidimensional-models-olap-logical-dimension-objects/dimension-translations.md) </span><span class="sxs-lookup"><span data-stu-id="50b42-173">[Dimension Translations](multidimensional-models-olap-logical-dimension-objects/dimension-translations.md) </span></span>  
 <span data-ttu-id="50b42-174">[キューブの翻訳](multidimensional-models-olap-logical-cube-objects/cube-translations.md) </span><span class="sxs-lookup"><span data-stu-id="50b42-174">[Cube Translations](multidimensional-models-olap-logical-cube-objects/cube-translations.md) </span></span>  
 [<span data-ttu-id="50b42-175">翻訳 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="50b42-175">Translations &#40;Analysis Services&#41;</span></span>](translations-analysis-services.md)  
  
  
