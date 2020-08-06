---
title: テーブルモデルデザイナー (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- SQL12.ASVS.BIDTOOLSET.TOPLEVSEMMODUIENTRY.F1
ms.assetid: 45735c57-2a95-4e45-8994-7242df6c9c5f
author: minewiskan
ms.author: owend
ms.openlocfilehash: ac63826d3e8a93f341c181faeef44714afd92353
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634702"
---
# <a name="tabular-model-designer-ssas-tabular"></a><span data-ttu-id="d1725-102">テーブル モデル デザイナー (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="d1725-102">Tabular Model Designer (SSAS Tabular)</span></span>
  <span data-ttu-id="d1725-103">テーブルモデルデザイナーは、Microsoft 2010 以降と統合されたの一部であり、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロフェッショナルなテーブルモデルソリューションの開発専用のプロジェクトの種類のテンプレートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="d1725-103">The tabular model designer is part of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], integrated with Microsoft [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 2010 or later, with additional project type templates specifically for developing professional tabular model solutions.</span></span>  
  
 <span data-ttu-id="d1725-104">このトピックのセクション:</span><span class="sxs-lookup"><span data-stu-id="d1725-104">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="d1725-105">メリット</span><span class="sxs-lookup"><span data-stu-id="d1725-105">Benefits</span></span>](#bkmk_benefits)  
  
-   [<span data-ttu-id="d1725-106">プロジェクト テンプレート</span><span class="sxs-lookup"><span data-stu-id="d1725-106">Project Templates</span></span>](#bkmk_proj_temp)  
  
-   [<span data-ttu-id="d1725-107">ウィンドウおよびメニュー</span><span class="sxs-lookup"><span data-stu-id="d1725-107">Windows and Menus</span></span>](#bkmk_wind_men)  
  
-   [<span data-ttu-id="d1725-108">Visual Studio の統合</span><span class="sxs-lookup"><span data-stu-id="d1725-108">Visual Studio Integration</span></span>](#bkmk_vsint)  
  
##  <a name="benefits"></a><a name="bkmk_benefits"></a> <span data-ttu-id="d1725-109">利点</span><span class="sxs-lookup"><span data-stu-id="d1725-109">Benefits</span></span>  
 <span data-ttu-id="d1725-110">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]をインストールすると、テーブル モデルを作成するための新しいプロジェクト テンプレートが、使用可能なプロジェクトの種類に追加されます。</span><span class="sxs-lookup"><span data-stu-id="d1725-110">When you install [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], new project templates for creating tabular models are added to the available project types.</span></span> <span data-ttu-id="d1725-111">いずれかのテンプレートを使用して新しいテーブル モデル プロジェクトを作成した後は、テーブル モデル デザイナー ツール、およびウィザードを使用して、モデル作成を開始できます。</span><span class="sxs-lookup"><span data-stu-id="d1725-111">After creating a new tabular model project by using one of the templates, you can begin model authoring by using the tabular model designer tools and wizards.</span></span>  
  
 <span data-ttu-id="d1725-112">プロフェッショナルな多次元のテーブル モデル ソリューション作成のための新しいテンプレートとツールのほかに、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 環境には、組織のために最も強力な BI ソリューションを作成するための、デバッグ、およびプロジェクトのライフ サイクルに関する機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="d1725-112">In addition to new templates and tools for authoring professional multidimensional and tabular model solutions, the [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] environment provides debugging and project lifecycle capabilities that ensure you create the most powerful BI solutions for your organization.</span></span> <span data-ttu-id="d1725-113">[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]の詳細については、「 [Visual Studio の概要](https://go.microsoft.com/fwlink/?LinkId=206389)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1725-113">For more information about [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], see [Getting Started with Visual Studio](https://go.microsoft.com/fwlink/?LinkId=206389).</span></span>  
  
##  <a name="project-templates"></a><a name="bkmk_proj_temp"></a> <span data-ttu-id="d1725-114">プロジェクト テンプレート</span><span class="sxs-lookup"><span data-stu-id="d1725-114">Project Templates</span></span>  
 <span data-ttu-id="d1725-115">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]をインストールすると、以下のテーブル モデル プロジェクト テンプレートがビジネス インテリジェンス プロジェクトの種類に追加されます。</span><span class="sxs-lookup"><span data-stu-id="d1725-115">When you install [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the following tabular model project templates are added to the Business Intelligence project types:</span></span>  
  
 <span data-ttu-id="d1725-116">**Analysis Services のテーブル プロジェクト**</span><span class="sxs-lookup"><span data-stu-id="d1725-116">**Analysis Services Tabular Project**</span></span>  
 <span data-ttu-id="d1725-117">このテンプレートを使用すると、新しい、空白のテーブル モデル プロジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d1725-117">This template can be used to create a new, blank tabular model project.</span></span>  
  
 <span data-ttu-id="d1725-118">**サーバー (表形式) からのインポート**</span><span class="sxs-lookup"><span data-stu-id="d1725-118">**Import from Server (Tabular)**</span></span>  
 <span data-ttu-id="d1725-119">このテンプレートを使用すると、Analysis Services 内の既存のテーブル モデルからメタデータを抽出して、新しいテーブル モデル プロジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d1725-119">This template can be used to create a new tabular model project by extracting the metadata from an existing tabular model in Analysis Services.</span></span>  
  
 <span data-ttu-id="d1725-120">**PowerPivot からのインポート**</span><span class="sxs-lookup"><span data-stu-id="d1725-120">**Import from PowerPivot**</span></span>  
 <span data-ttu-id="d1725-121">このテンプレートを使用すると、 [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] ファイルからメタデータとデータを抽出して、新しいテーブル モデル プロジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d1725-121">This template is used for creating a new tabular model project by extracting the metadata and data from a [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d1725-122">テーブル モデル プロジェクトでは、テーブル モードの Analysis Services サーバー インスタンスがローカルまたはネットワーク上で実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1725-122">Tabular model projects require an Analysis Services server instance in tabular mode be running locally or on the network.</span></span>  
  
##  <a name="windows-and-menus"></a><a name="bkmk_wind_men"></a><span data-ttu-id="d1725-123">ウィンドウとメニュー</span><span class="sxs-lookup"><span data-stu-id="d1725-123">Windows and Menus</span></span>  
 <span data-ttu-id="d1725-124">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] のテーブル モデルの作成環境には、次が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d1725-124">The [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] tabular model authoring environment includes the following:</span></span>  
  
### <a name="designer-window"></a><span data-ttu-id="d1725-125">デザイナー ウィンドウ</span><span class="sxs-lookup"><span data-stu-id="d1725-125">Designer Window</span></span>  
 <span data-ttu-id="d1725-126">デザイナー ウィンドウは、モデルを視覚的に表現し、テーブル モデルの作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d1725-126">The designer window is used to author tabular models by providing a visual representation of the model.</span></span> <span data-ttu-id="d1725-127">Model.bim ファイルを開くと、デザイナー ウィンドウにそのモデルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1725-127">When you open the Model.bim file, the model opens in the designer window.</span></span> <span data-ttu-id="d1725-128">デザイナー ウィンドウでは、2 つの異なる表示モードを使用してモデルを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="d1725-128">You can author a model in the designer window by using two different view modes:</span></span>  
  
 <span data-ttu-id="d1725-129">**[Data View] (データ ビュー)**</span><span class="sxs-lookup"><span data-stu-id="d1725-129">**Data View**</span></span>  
 <span data-ttu-id="d1725-130">データ ビューではテーブルが表形式のグリッド形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1725-130">The data view displays tables in a tabular, grid format.</span></span> <span data-ttu-id="d1725-131">また、メジャー グリッドを使用してメジャーを定義することもできます。メジャー グリッドはテーブルごとにデータ ビューのみで表示することができます。</span><span class="sxs-lookup"><span data-stu-id="d1725-131">You can also define measures by using the measure grid, which can be shown for each table in Data View only.</span></span>  
  
 <span data-ttu-id="d1725-132">**ダイアグラムビュー**</span><span class="sxs-lookup"><span data-stu-id="d1725-132">**Diagram View**</span></span>  
 <span data-ttu-id="d1725-133">ダイアグラム ビューでは、テーブル間のリレーションシップと共にグラフィカルな形式でテーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1725-133">The diagram view displays tables, with relationships between them, in a graphical format.</span></span> <span data-ttu-id="d1725-134">列、メジャー、階層、および KPI はフィルター選択することも、定義済みのパースペクティブを使用してモデルを表示することを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="d1725-134">Columns, measures, hierarchies, and KPIs can be filtered, and you can choose to view the model by using a defined perspective.</span></span>  
  
 <span data-ttu-id="d1725-135">どちらのビューでもほとんどのモデル作成タスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="d1725-135">Most model authoring tasks can be performed in either view.</span></span>  
  
### <a name="solution-explorer"></a><span data-ttu-id="d1725-136">ソリューション エクスプローラー</span><span class="sxs-lookup"><span data-stu-id="d1725-136">Solution Explorer</span></span>  
 <span data-ttu-id="d1725-137">ソリューション エクスプローラー ウィンドウには、テーブル モデル プロジェクトの論理的コンテナーとしての作業対象のソリューションと、その関連付けられたアイテムが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1725-137">The Solution Explorer window presents the active solution as a logical container for a tabular model project and its associated items.</span></span> <span data-ttu-id="d1725-138">モデル プロジェクト (.smproj) には、References オブジェクト (空) と Model.bim ファイルのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d1725-138">The model project (.smproj) contains only a References object (empty) and the Model.bim file.</span></span> <span data-ttu-id="d1725-139">このビューからプロジェクト アイテムを開いて、変更やその他の管理作業を直接実行することができます。</span><span class="sxs-lookup"><span data-stu-id="d1725-139">You can open project items for modification and perform other management tasks directly from this view.</span></span>  
  
 <span data-ttu-id="d1725-140">テーブル モデル ソリューションには、通常、1 つのプロジェクトしか含まれませんが、ソリューションには、Integration Services プロジェクトや Reporting Services プロジェクトなど、その他のプロジェクトも含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d1725-140">Tabular model solutions typically contain only one project; however, a solution can contain other projects too, for example, Integration Services or Reporting services project.</span></span> <span data-ttu-id="d1725-141">テーブル モデル プロジェクト ファイルと異なる種類で、ビルド アクション プロパティが [なし] に設定されているか、出力ディレクトリにコピー プロパティが [コピーしない] に設定されている場合は、任意数のファイルを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="d1725-141">You can add any number of files provided they are not of the same type as tabular model project files and their Build Action property is set to None, or Copy to Output property is set to Do Not Copy.</span></span>  
  
 <span data-ttu-id="d1725-142">ソリューション エクスプローラーを表示するには、 **[表示]** メニューの **[ソリューション エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1725-142">To view Solution Explorer, click the **View** menu, and then click **Solution Explorer**.</span></span>  
  
### <a name="properties-window"></a><span data-ttu-id="d1725-143">[プロパティ] ウィンドウ</span><span class="sxs-lookup"><span data-stu-id="d1725-143">Properties Window</span></span>  
 <span data-ttu-id="d1725-144">プロパティ ウィンドウには、選択したオブジェクトのプロパティが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1725-144">The Properties window lists the properties of the selected object.</span></span> <span data-ttu-id="d1725-145">次のオブジェクトには、プロパティ ウィンドウで表示および編集できるプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="d1725-145">The following objects have properties that can be viewed and edited in the Properties window:</span></span>  
  
-   <span data-ttu-id="d1725-146">Model.bim</span><span class="sxs-lookup"><span data-stu-id="d1725-146">Model.bim</span></span>  
  
-   <span data-ttu-id="d1725-147">テーブル</span><span class="sxs-lookup"><span data-stu-id="d1725-147">Table</span></span>  
  
-   <span data-ttu-id="d1725-148">列</span><span class="sxs-lookup"><span data-stu-id="d1725-148">Column</span></span>  
  
-   <span data-ttu-id="d1725-149">Measure</span><span class="sxs-lookup"><span data-stu-id="d1725-149">Measure</span></span>  
  
 <span data-ttu-id="d1725-150">プロジェクト ウィンドウには、プロジェクト プロパティによりプロジェクト名とプロジェクト フォルダーのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1725-150">Project Properties display only the project name and project folder in the Properties window.</span></span> <span data-ttu-id="d1725-151">プロジェクトには、モーダル プロパティ ダイアログ ボックスを使用して設定できる配置オプションと配置サーバーの追加の設定もあります。</span><span class="sxs-lookup"><span data-stu-id="d1725-151">Projects also have additional deployment Options and deployment server settings that you can set using a modal properties dialog box.</span></span> <span data-ttu-id="d1725-152">これらのプロパティを表示するには、 **ソリューション エクスプローラー**で、プロジェクトを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1725-152">To view these properties, in **Solution Explorer**, right click the project, and then click **Properties**.</span></span>  
  
 <span data-ttu-id="d1725-153">プロパティ ウィンドウのフィールドには、クリックすると開くコントロールが埋め込まれています。</span><span class="sxs-lookup"><span data-stu-id="d1725-153">Fields in the Properties window have embedded controls that open when you click them.</span></span> <span data-ttu-id="d1725-154">編集コントロールの種類は、プロパティごとに異なります。</span><span class="sxs-lookup"><span data-stu-id="d1725-154">The type of edit control depends on the particular property.</span></span> <span data-ttu-id="d1725-155">コントロールには、エディット ボックス、ドロップダウン リスト、およびカスタム ダイアログ ボックスへのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d1725-155">Controls include edit boxes, dropdown lists, and links to custom dialog boxes.</span></span> <span data-ttu-id="d1725-156">淡色表示のプロパティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="d1725-156">Properties that are shown as dimmed are read-only.</span></span>  
  
 <span data-ttu-id="d1725-157">**プロパティ** ウィンドウを開くには、 **[表示]** メニューをクリックしてから **[プロパティ ウィンドウ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1725-157">To view the **Properties** window, click the **View** menu, and then click **Properties Window**.</span></span>  
  
### <a name="error-list"></a><span data-ttu-id="d1725-158">エラー一覧</span><span class="sxs-lookup"><span data-stu-id="d1725-158">Error List</span></span>  
 <span data-ttu-id="d1725-159">エラー一覧ウィンドウには、次のようなモデルの状態に関するメッセージが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d1725-159">The Error List window contains messages about the model state:</span></span>  
  
-   <span data-ttu-id="d1725-160">セキュリティのベスト プラクティスについての通知。</span><span class="sxs-lookup"><span data-stu-id="d1725-160">Notifications about security best practices.</span></span>  
  
-   <span data-ttu-id="d1725-161">データ処理の要件。</span><span class="sxs-lookup"><span data-stu-id="d1725-161">Requirements for data processing.</span></span>  
  
-   <span data-ttu-id="d1725-162">計算列、メジャー、およびロールの行フィルターのセマンティック エラー情報。</span><span class="sxs-lookup"><span data-stu-id="d1725-162">Semantic error information for calculated columns, measures, and row filters for roles.</span></span> <span data-ttu-id="d1725-163">計算列では、エラー メッセージをダブルクリックすると、エラーのソースに移動できます。</span><span class="sxs-lookup"><span data-stu-id="d1725-163">For calculated columns, you can double-click the error message to navigate to the source of the error.</span></span>  
  
-   <span data-ttu-id="d1725-164">DirectQuery 検証エラー。</span><span class="sxs-lookup"><span data-stu-id="d1725-164">DirectQuery validation errors.</span></span>  
  
 <span data-ttu-id="d1725-165">既定では、 **エラー一覧** は、エラーが返されない限り表示されません。</span><span class="sxs-lookup"><span data-stu-id="d1725-165">By default, the **Error List** does not appear unless an error is returned.</span></span> <span data-ttu-id="d1725-166">ただし、 **エラー一覧** ウィンドウはいつでも表示できます。</span><span class="sxs-lookup"><span data-stu-id="d1725-166">You can, however, view the **Error List** window at any time.</span></span> <span data-ttu-id="d1725-167">**エラー一覧** ウィンドウを表示するには、 **[表示]** メニューをクリックしてから **[エラー一覧]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1725-167">To view the **Error List** window, click the **View** menu, and then click **Error List**.</span></span>  
  
### <a name="output"></a><span data-ttu-id="d1725-168">出力</span><span class="sxs-lookup"><span data-stu-id="d1725-168">Output</span></span>  
 <span data-ttu-id="d1725-169">ビルドと配置の情報が、(進捗状況のモーダル ダイアログに加えて) **出力** ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1725-169">Build and deployment information is displayed in the **Output** Window (in addition to the modal progress dialog).</span></span> <span data-ttu-id="d1725-170">**出力** ウィンドウを表示するには、 **[表示]** をクリックしてから [出力] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1725-170">To view the **Output** window, click the **View** menu, and then click Output.</span></span>  
  
### <a name="menu-items"></a><span data-ttu-id="d1725-171">メニュー項目</span><span class="sxs-lookup"><span data-stu-id="d1725-171">Menu Items</span></span>  
 <span data-ttu-id="d1725-172">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]をインストールすると、テーブル モデルの作成のために特化したメニュー項目が Visual Studio のメニュー バーに追加されます。</span><span class="sxs-lookup"><span data-stu-id="d1725-172">When you install [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], additional menu items specifically for authoring tabular models are added to the Visual Studio menu bar.</span></span> <span data-ttu-id="d1725-173">**[モデル]** メニューを使用して、データ インポート ウィザードを起動したり、既存の接続を表示したり、ワークスペース データを処理したりできるほか、 [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel でモデル ワークスペースを参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="d1725-173">The **Model** menu can be used to launch the Data Import Wizard, view existing connections, process workspace data, and browse the model workspace in [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel.</span></span> <span data-ttu-id="d1725-174">**[テーブル]** メニューは、テーブル間のリレーションシップの作成と管理、メジャーの作成と管理のほか、データ テーブルの設定や計算オプションなど、各種のテーブル プロパティを指定する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="d1725-174">The **Table** menu is used to create and manage relationships between tables, create and manage measures, specify data table settings, specify calculation options, and specify other table properties.</span></span> <span data-ttu-id="d1725-175">**[列]** メニューでは、テーブル内の列の追加と削除、列の表示と非表示のほか、列のプロパティ (データ型、フィルターなど) を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="d1725-175">With the **Column** menu, you can add and delete columns in a table, hide and unhide columns, and specify other column properties such as data types and filters.</span></span> <span data-ttu-id="d1725-176">テーブル モデル ソリューションは、 **[ビルド]** メニューからビルドおよび配置できます。</span><span class="sxs-lookup"><span data-stu-id="d1725-176">You can build and deploy tabular model solutions on the **Build** menu.</span></span> <span data-ttu-id="d1725-177">コピーと貼り付けの機能は、 **[編集]** メニューに含まれています。</span><span class="sxs-lookup"><span data-stu-id="d1725-177">Copy/Paste functions are included on the **Edit** menu.</span></span>  
  
 <span data-ttu-id="d1725-178">これらのメニュー項目に加えて、Analysis Services のオプションに別途設定が追加されます。追加された設定には、[ツール] のメニュー項目からアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="d1725-178">In addition to these menu items, additional settings are added to the Analysis Services options on the Tools menu items.</span></span>  
  
### <a name="toolbar"></a><span data-ttu-id="d1725-179">ツール バー</span><span class="sxs-lookup"><span data-stu-id="d1725-179">Toolbar</span></span>  
 <span data-ttu-id="d1725-180">Analysis Services ツール バーを使用すると、最もよく使用されるモデル作成コマンドにすばやく簡単にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="d1725-180">The Analysis Services toolbar provides quick and easy access to the most frequently used model authoring commands.</span></span>  
  
##  <a name="visual-studio-integration"></a><a name="bkmk_vsint"></a> <span data-ttu-id="d1725-181">Visual Studio との統合</span><span class="sxs-lookup"><span data-stu-id="d1725-181">Visual Studio Integration</span></span>  
 <span data-ttu-id="d1725-182">**ソース管理**</span><span class="sxs-lookup"><span data-stu-id="d1725-182">**Source Control**</span></span>  
 <span data-ttu-id="d1725-183">Analysis Services プロジェクトは、選択したソース管理プラグインと統合されます。</span><span class="sxs-lookup"><span data-stu-id="d1725-183">Analysis Services projects integrate with the selected source control plug-in.</span></span> <span data-ttu-id="d1725-184">ソース コントロールを使用するように Visual Studio を構成した場合は、ソリューション エクスプローラーからチェックインとチェックアウトを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d1725-184">If you have configured Visual Studio to use source control, you can use check in/check out from Solution Explorer.</span></span> <span data-ttu-id="d1725-185">Team Foundation Server を使用するように構成するには、「 [Team Foundation バージョン管理を使用する Visual Studio の構成](https://msdn.microsoft.com/library/ms253064.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1725-185">To configure to use Team Foundation Server, see [Configure Visual Studio with Team Foundation Version Control](https://msdn.microsoft.com/library/ms253064.aspx).</span></span> <span data-ttu-id="d1725-186">多くのサード パーティ製ソース管理プラグインもサポートされます。</span><span class="sxs-lookup"><span data-stu-id="d1725-186">Many third-party source control plug-ins are supported as well.</span></span>  
  
 <span data-ttu-id="d1725-187">**フォント**</span><span class="sxs-lookup"><span data-stu-id="d1725-187">**Fonts**</span></span>  
 <span data-ttu-id="d1725-188">テーブル モデルでは [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 環境フォントを使用して表示フォントを制御します。</span><span class="sxs-lookup"><span data-stu-id="d1725-188">Tabular models use the [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] environment font to control the fonts in the display.</span></span> <span data-ttu-id="d1725-189">既定の [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] フォントに、対象の言語で必要なすべての Unicode 文字がない場合は、このフォントの変更が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="d1725-189">It can be necessary to change this font if the default [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] font does not have all of the Unicode characters you need for your language.</span></span> <span data-ttu-id="d1725-190">フォントを変更するには、 **[ツール]** メニューをクリックし、 **[オプション]**、 **[フォントおよび色]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1725-190">To change fonts, click the **Tools** menu, then click **Options**, and then click **Fonts and Colors**.</span></span>  
  
 <span data-ttu-id="d1725-191">**キーボード ショートカット**</span><span class="sxs-lookup"><span data-stu-id="d1725-191">**Keyboard Shortcuts**</span></span>  
 <span data-ttu-id="d1725-192">Analysis Services のキーボード ショートカットは、[ツール]  > [オプション] > [キーボード] ダイアログで構成/再マップできます。</span><span class="sxs-lookup"><span data-stu-id="d1725-192">The Analysis Services keyboard shortcuts can be configured/remapped through the Tools->Options->Keyboard dialog.</span></span> <span data-ttu-id="d1725-193">テーブル モデル デザイナーのコンテキストでは、ビルド、保存、デバッグ、新しいプロジェクトなど、一部のグローバル [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ショートカットがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d1725-193">Some global [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] shortcuts, such as build, save, debug, new project, etc. are supported in the tabular model designer context.</span></span> <span data-ttu-id="d1725-194">その他のテーブル モデル デザイナーに固有のショートカットは Analysis Services コンテキストです。</span><span class="sxs-lookup"><span data-stu-id="d1725-194">Other tabular model designer specific shortcuts are in the Analysis Services context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1725-195">参照</span><span class="sxs-lookup"><span data-stu-id="d1725-195">See Also</span></span>  
 <span data-ttu-id="d1725-196">[SSAS 表形式&#41;&#40;テーブルモデルプロジェクト](tabular-models/tabular-model-projects-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="d1725-196">[Tabular Model Projects &#40;SSAS Tabular&#41;](tabular-models/tabular-model-projects-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="d1725-197">プロパティ (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="d1725-197">Properties &#40;SSAS Tabular&#41;</span></span>](tabular-models/properties-ssas-tabular.md)  
  
  
