---
title: 新規または既存のレポートをレポート プロジェクトに追加する (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], creating
ms.assetid: 8bc0bb53-ad8a-464d-bb6a-7fea5fa62c5c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b66bf8ef0181b549900d984d20b1279f9b5005c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737920"
---
# <a name="add-a-new-or-existing-report-to-a-report-project-ssrs"></a><span data-ttu-id="37a82-102">新規または既存のレポートをレポート プロジェクトに追加する (SSRS)</span><span class="sxs-lookup"><span data-stu-id="37a82-102">Add a New or Existing Report to a Report Project (SSRS)</span></span>
  <span data-ttu-id="37a82-103">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] では、レポート ウィザードを使用するか、新しい空のレポートをプロジェクトに追加することによって、新しいレポートを追加できます。</span><span class="sxs-lookup"><span data-stu-id="37a82-103">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you can add a new report by using the Report Wizard or by adding a new blank report to your project.</span></span> <span data-ttu-id="37a82-104">既存のレポートを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="37a82-104">You can also add an existing report.</span></span> <span data-ttu-id="37a82-105">レポートを追加すると、そのレポートの名前が、プロジェクトの **[レポート]** フォルダーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="37a82-105">After you add a report, you can see the report name listed under the **Reports** folder in your project.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="37a82-106">既存のデータ ソースを使ったレポートをプレビューするには、レポート作成クライアントから、そのデータ ソースにアクセスするための権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="37a82-106">To preview a report with existing data sources, you must have permissions to the data source from your report authoring client.</span></span> <span data-ttu-id="37a82-107">詳細については、「 [SSRS&#41;&#40;の埋め込みデータソースまたは共有データソースの作成](../create-an-embedded-or-shared-data-source-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37a82-107">For more information, see [Create an Embedded or Shared Data Source &#40;SSRS&#41;](../create-an-embedded-or-shared-data-source-ssrs.md).</span></span>  
  
 <span data-ttu-id="37a82-108">レポートを追加した後、データ ソースやデータセットを定義したり、レポート レイアウトをデザインしたりできます。</span><span class="sxs-lookup"><span data-stu-id="37a82-108">After you add a report, you can define data sources, datasets, and design a report layout.</span></span> <span data-ttu-id="37a82-109">開始するには、「[基本的なテーブル レポートの作成 &#40;SSRS チュートリアル&#41;](../create-a-basic-table-report-ssrs-tutorial.md)」または「[テーブル &#40;レポート ビルダーおよび SSRS&#41;](../report-design/tables-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37a82-109">To get started, see [Create a Basic Table Report &#40;SSRS Tutorial&#41;](../create-a-basic-table-report-ssrs-tutorial.md) or [Tables &#40;Report Builder  and SSRS&#41;](../report-design/tables-report-builder-and-ssrs.md).</span></span>  
  
### <a name="to-add-a-new-report-using-the-report-wizard"></a><span data-ttu-id="37a82-110">レポート ウィザードを使って新しいレポートを追加するには</span><span class="sxs-lookup"><span data-stu-id="37a82-110">To add a new report using the Report Wizard</span></span>  
  
1.  <span data-ttu-id="37a82-111">ソリューション エクスプローラーで [レポート] フォルダーを右クリックし、 **[新しいレポートの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="37a82-111">In Solution Explorer, right-click the Reports folder, and then click **Add New Report**.</span></span> <span data-ttu-id="37a82-112">**[レポート ウィザード]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="37a82-112">The **Report Wizard** dialog box opens.</span></span>  
  
     <span data-ttu-id="37a82-113">ウィザードの手順に従うことにより、データ ソースの作成、クエリを使ったデータセットの作成、グループの定義、レイアウトの指定、スタイル (色やフォントなど) の選択、レポートの作成などの作業を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="37a82-113">The wizard steps you through creating a data source, creating a dataset with a query, defining groups, specifying a layout, choosing a style that includes color and font, and creating the report.</span></span> <span data-ttu-id="37a82-114">これには次の手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="37a82-114">The steps include:</span></span>  
  
    -   <span data-ttu-id="37a82-115">**データ ソースの選択**</span><span class="sxs-lookup"><span data-stu-id="37a82-115">**Select a Data Source.**</span></span> <span data-ttu-id="37a82-116">レポート作成の最初の手順は、データ ソースを定義することです。</span><span class="sxs-lookup"><span data-stu-id="37a82-116">The first step in creating a report is to define a data source.</span></span> <span data-ttu-id="37a82-117">レポート ウィザードにより、レポート プロジェクト内のすべての共有データ ソースが表示されます。同時に、新しいデータ ソースを作成するオプションも表示されます。</span><span class="sxs-lookup"><span data-stu-id="37a82-117">Report Wizard provides a list of all shared data sources in the report project, in addition to an option to create a new data source.</span></span>  
  
    -   <span data-ttu-id="37a82-118">**クエリのデザイン**</span><span class="sxs-lookup"><span data-stu-id="37a82-118">**Design a Query.**</span></span> <span data-ttu-id="37a82-119">次の手順は、クエリを設計することです。</span><span class="sxs-lookup"><span data-stu-id="37a82-119">The next step is to design a query.</span></span> <span data-ttu-id="37a82-120">クエリの作成方法としては、クエリ文字列を入力する以外にも、クエリ デザイナーを使用する方法や、別のレポートからクエリをインポートする方法もあります。</span><span class="sxs-lookup"><span data-stu-id="37a82-120">You can type the query string, build it using Query Designer, or import a query from another report.</span></span> <span data-ttu-id="37a82-121">クエリ デザイナーの詳細については、「 [Reporting Services クエリ デザイナー](../reporting-services-query-designers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37a82-121">For information about Query Designers, see [Reporting Services Query Designers](../reporting-services-query-designers.md).</span></span>  
  
    -   <span data-ttu-id="37a82-122">**レポートの種類の選択**</span><span class="sxs-lookup"><span data-stu-id="37a82-122">**Choose a Report Type.**</span></span> <span data-ttu-id="37a82-123">次の手順は、作成するレポートの種類を選択することです。</span><span class="sxs-lookup"><span data-stu-id="37a82-123">The next step is to select the type of report you want.</span></span> <span data-ttu-id="37a82-124">表形式のレポートか、マトリックス形式のレポートを選択することができます。</span><span class="sxs-lookup"><span data-stu-id="37a82-124">You can choose a tabular or matrix report.</span></span> <span data-ttu-id="37a82-125">表形式のレポートは、列数が固定されます。</span><span class="sxs-lookup"><span data-stu-id="37a82-125">A tabular report has a fixed number of columns.</span></span> <span data-ttu-id="37a82-126">マトリックス形式のレポート (クロス集計レポート) は、クエリの結果により列数が変化します。</span><span class="sxs-lookup"><span data-stu-id="37a82-126">A matrix, or crosstab, report has a variable number of columns based on the results of the query.</span></span> <span data-ttu-id="37a82-127">マップ レポートには、地理的背景に対する分析が表示されます。</span><span class="sxs-lookup"><span data-stu-id="37a82-127">A map report displays analytical against a geographic background.</span></span>  
  
    -   <span data-ttu-id="37a82-128">**スタイルの選択**</span><span class="sxs-lookup"><span data-stu-id="37a82-128">**Choose a Style.**</span></span> <span data-ttu-id="37a82-129">次の手順は、スタイル テンプレートを使用してスタイルをレポートに適用することです。</span><span class="sxs-lookup"><span data-stu-id="37a82-129">The next step is to apply a style to the report using a style template.</span></span> <span data-ttu-id="37a82-130">テンプレートを選択して、フォントや色、罫線のスタイルなどのスタイルをレポートに適用します。</span><span class="sxs-lookup"><span data-stu-id="37a82-130">Select a template to apply styles such as font, color, and border style to the report.</span></span> <span data-ttu-id="37a82-131">レポート デザイナーには、[スレート]、[フォレスト]、[フォーマル]、[太字]、[オーシャン]、[汎用] の 6 つのスタイル テンプレートが用意されています。</span><span class="sxs-lookup"><span data-stu-id="37a82-131">Report Designer provides six style templates: Slate, Forest, Corporate, Bold, Ocean, and Generic.</span></span> <span data-ttu-id="37a82-132">また、新しいスタイル テンプレートを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="37a82-132">You can also add additional style templates.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="37a82-133">既存のテンプレートを変更したり、新しいテンプレートを追加したりできます。そのためには、Common7\IDE\PrivateAssemblies\Business<lang フォルダーの StyleTemplates.xml ファイルを編集し \\ \> ます。ここで、 \<lang> は使用している言語です (たとえば、の英語バージョンのを使用している場合、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] フォルダー名は "EN" になります)。</span><span class="sxs-lookup"><span data-stu-id="37a82-133">You can alter existing templates or add new ones by editing the StyleTemplates.xml file in the \Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\Business Intelligence Wizards\Reports\Styles\\<lang\> folder, where \<lang> is the language you are using (for example, if you are using the English language version of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], the folder name is "EN").</span></span> <span data-ttu-id="37a82-134">このフォルダーは、レポート デザイナーがインストールされているコンピューターにあります。</span><span class="sxs-lookup"><span data-stu-id="37a82-134">This folder is located on the computer on which Report Designer is installed.</span></span> <span data-ttu-id="37a82-135">StyleTemplates.xml ファイルは 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="37a82-135">There are two copies of the StyleTemplates.xml file.</span></span> <span data-ttu-id="37a82-136">レポート ウィザードを使って適用されたスタイルを修正するには、使用言語に対応するフォルダー内のファイルを編集します。</span><span class="sxs-lookup"><span data-stu-id="37a82-136">To modify the styles that are applied through the Report Wizard, edit the file that is in the folder created for the language you are using.</span></span>  
  
    -   <span data-ttu-id="37a82-137">**レポートの名前付け**</span><span class="sxs-lookup"><span data-stu-id="37a82-137">**Name the Report.**</span></span>  <span data-ttu-id="37a82-138">最後の手順は、レポートに名前を付け、レポートに含まれるフィールドを確認することです。</span><span class="sxs-lookup"><span data-stu-id="37a82-138">The final step is to name the report and verify the fields that will be included in the report.</span></span> <span data-ttu-id="37a82-139">すべての手順が完了したら、レポート デザイナーはレポートを作成し、それをレポート サーバー プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="37a82-139">When all steps are completed, Report Designer creates the report and adds it to the report server project.</span></span>  
  
### <a name="to-add-a-new-blank-report"></a><span data-ttu-id="37a82-140">新しい空のレポートを追加するには</span><span class="sxs-lookup"><span data-stu-id="37a82-140">To add a new blank report</span></span>  
  
1.  <span data-ttu-id="37a82-141">**[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="37a82-141">From the **Project** menu, click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="37a82-142">**[テンプレート]** の **[レポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="37a82-142">In **Templates**, click **Report**.</span></span>  
  
3.  <span data-ttu-id="37a82-143">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="37a82-143">Click **Add**.</span></span>  
  
     <span data-ttu-id="37a82-144">新しい空のレポートがプロジェクトに追加され、デザイン画面に表示されます。</span><span class="sxs-lookup"><span data-stu-id="37a82-144">A new blank report is added to the project and displayed on the design surface.</span></span>  
  
### <a name="to-add-an-existing-report"></a><span data-ttu-id="37a82-145">既存のレポートを追加するには</span><span class="sxs-lookup"><span data-stu-id="37a82-145">To add an existing report</span></span>  
  
1.  <span data-ttu-id="37a82-146">[**プロジェクト**] メニューの [**追加**] をクリックし、[**既存の項目**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="37a82-146">From the **Project** menu, click **Add**, and then **Existing Item**.</span></span>  
  
2.  <span data-ttu-id="37a82-147">.rdl ファイルがある場所に移動して、ファイルを選択し、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="37a82-147">Navigate to the location of the .rdl file, select it, and then click **Add**.</span></span>  
  
     <span data-ttu-id="37a82-148">レポートがプロジェクトの **[レポート]** フォルダーに追加されます。</span><span class="sxs-lookup"><span data-stu-id="37a82-148">The report is added to the project under the **Reports** folder.</span></span> <span data-ttu-id="37a82-149">プロジェクトを閉じてから開き直すと、一連のレポートがアルファベット順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="37a82-149">When you close and re-open the project, reports are sorted alphabetically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37a82-150">参照</span><span class="sxs-lookup"><span data-stu-id="37a82-150">See Also</span></span>  
 [<span data-ttu-id="37a82-151">Reporting Services チュートリアル &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="37a82-151">Reporting Services Tutorials &#40;SSRS&#41;</span></span>](../reporting-services-tutorials-ssrs.md)  
  
  
