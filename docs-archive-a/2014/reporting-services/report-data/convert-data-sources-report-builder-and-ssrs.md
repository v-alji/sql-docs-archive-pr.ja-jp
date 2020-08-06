---
title: 埋め込みデータソースから共有データソースへの変換 (レポートビルダーおよび SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], embedded
- data sources [Reporting Services], shared
ms.assetid: 0e099c7e-8c03-43eb-9ea3-76e52d9ebbe3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5827bab564b58e7a2b7922f01a33f550a6f523f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632917"
---
# <a name="convert-a-data-source-from-embedded-to-shared-report-builder-and-ssrs"></a><span data-ttu-id="1ed4e-102">埋め込みデータ ソースから共有データ ソースへの変換 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="1ed4e-102">Convert a Data Source from Embedded to Shared (Report Builder and SSRS)</span></span>
  <span data-ttu-id="1ed4e-103">レポート データ ペインの各データ ソースは、レポートに固有のものとして埋め込まれている場合と、共有されている場合とがあります。</span><span class="sxs-lookup"><span data-stu-id="1ed4e-103">Each data source in the Report Data pane is embedded and specific to the report or is shared.</span></span> <span data-ttu-id="1ed4e-104">レポート ビルダーにおける共有データ ソースの参照先は、レポート サーバー上または SharePoint サイト上にパブリッシュされた共有データ ソースです。</span><span class="sxs-lookup"><span data-stu-id="1ed4e-104">In Report Builder, a shared data source points to a published shared data source on a report server or SharePoint site.</span></span> <span data-ttu-id="1ed4e-105">レポート デザイナーにおける共有データ ソースの参照先は、ソリューション エクスプローラーの **[共有データ ソース]** フォルダーに表示される共有データ ソースです。</span><span class="sxs-lookup"><span data-stu-id="1ed4e-105">In Report Designer, a shared data source points to a shared data source in the **Shared Data Sources** folder in Solution Explorer.</span></span>  
  
 <span data-ttu-id="1ed4e-106">埋め込みデータ ソースと共有データ ソースの相違点の詳細については、「[埋め込みおよび共有のデータ接続またはデータ ソース &#40;レポート ビルダーおよび SSRS&#41;](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ed4e-106">For more information about the differences between embedded and shared data sources, see [Embedded and Shared Data Connections or Data Sources &#40;Report Builder and SSRS&#41;](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="1ed4e-107">共有データ ソースの作成方法の詳細については、「[埋め込みデータ ソースまたは共有データ ソースを作成する &#40;SSRS&#41;](../create-an-embedded-or-shared-data-source-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ed4e-107">For more information on how to create a shared data source, see [Create an Embedded or Shared Data Source &#40;SSRS&#41;](../create-an-embedded-or-shared-data-source-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="report-designer"></a><span data-ttu-id="1ed4e-108">レポート デザイナー</span><span class="sxs-lookup"><span data-stu-id="1ed4e-108">Report Designer</span></span>  
  
#### <a name="to-convert-a-data-source-from-embedded-to-shared"></a><span data-ttu-id="1ed4e-109">埋め込みデータ ソースから共有データ ソースに変換するには</span><span class="sxs-lookup"><span data-stu-id="1ed4e-109">To convert a data source from embedded to shared</span></span>  
  
-   <span data-ttu-id="1ed4e-110">レポート データ ペインでデータ ソースを右クリックし、 **[共有データ ソースに変換]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1ed4e-110">In the Report Data pane, right-click the data source, and then click **Convert to Shared Data Source**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1ed4e-111">レポート データ ペインが表示されていない場合は、 **[表示]** メニューの **[レポート データ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1ed4e-111">If the Report Data pane is not visible, on the **View** menu, click **Report Data**.</span></span> <span data-ttu-id="1ed4e-112">ペインがフローティング ウィンドウとして開く場合は、ドッキングすることができます。</span><span class="sxs-lookup"><span data-stu-id="1ed4e-112">If the pane opens as a floating window, you can dock it.</span></span> <span data-ttu-id="1ed4e-113">詳細については、「[レポート デザイナーのレポート データ ペインをドッキングする (SSRS)](../tools/dock-the-report-data-pane-in-report-designer-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ed4e-113">For more information, see [Dock the Report Data Pane in Report Designer &#40;SSRS&#41;](../tools/dock-the-report-data-pane-in-report-designer-ssrs.md).</span></span>  
  
     <span data-ttu-id="1ed4e-114">レポート データ ペインでデータ ソース アイコンが共有データ ソースのアイコンに変わります。</span><span class="sxs-lookup"><span data-stu-id="1ed4e-114">In the Report Data pane, the data source icon changes to the shared data source icon.</span></span> <span data-ttu-id="1ed4e-115">ソリューション エクスプローラーでは、同じ名前の共有データ ソースが **[共有データ ソース]** フォルダーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="1ed4e-115">In Solution Explorer, a shared data source with the same name appears under the **Shared Data Source** folder.</span></span>  
  
### <a name="to-convert-a-data-source-from-shared-to-embedded"></a><span data-ttu-id="1ed4e-116">共有データ ソースを埋め込みデータ ソースに変換するには</span><span class="sxs-lookup"><span data-stu-id="1ed4e-116">To convert a data source from shared to embedded</span></span>  
  
-   <span data-ttu-id="1ed4e-117">レポート データ ペインでデータ ソースを右クリックし、 **[データ ソースのプロパティ]** ダイアログ ボックスを開いて、 **[埋め込み接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1ed4e-117">In the Report Data pane, right-click the data source, open the **Data Source Properties** dialog box, and then click **Embedded Connection**.</span></span> <span data-ttu-id="1ed4e-118">必要な情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="1ed4e-118">Enter the required information.</span></span>  
  
     <span data-ttu-id="1ed4e-119">レポート データ ペインでデータ ソース アイコンが共有データ ソースのアイコンに変わります。</span><span class="sxs-lookup"><span data-stu-id="1ed4e-119">In the Report Data pane, the data source icon changes to the shared data source icon.</span></span>  
  
## <a name="report-builder"></a><span data-ttu-id="1ed4e-120">レポート ビルダー</span><span class="sxs-lookup"><span data-stu-id="1ed4e-120">Report Builder</span></span>  
  
#### <a name="to-convert-a-data-source-from-embedded-to-shared"></a><span data-ttu-id="1ed4e-121">埋め込みデータ ソースから共有データ ソースに変換するには</span><span class="sxs-lookup"><span data-stu-id="1ed4e-121">To convert a data source from embedded to shared</span></span>  
  
-   <span data-ttu-id="1ed4e-122">レポート データ ペインでデータ ソースを右クリックし、 **[データ ソースのプロパティ]** ダイアログ ボックスを開いて、 **[埋め込み接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1ed4e-122">In the Report Data pane, right-click the data source to open the **Data Source Properties** dialog box, and then click **Embedded Connection**.</span></span> <span data-ttu-id="1ed4e-123">必要な情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="1ed4e-123">Enter the required information.</span></span>  
  
     <span data-ttu-id="1ed4e-124">レポート データ ペインでデータ ソース アイコンが共有データ ソースのアイコンに変わります。</span><span class="sxs-lookup"><span data-stu-id="1ed4e-124">In the Report Data pane, the data source icon changes to the shared data source icon.</span></span>  
  
#### <a name="to-convert-a-data-source-from-shared-to-embedded"></a><span data-ttu-id="1ed4e-125">共有データ ソースを埋め込みデータ ソースに変換するには</span><span class="sxs-lookup"><span data-stu-id="1ed4e-125">To convert a data source from shared to embedded</span></span>  
  
-   <span data-ttu-id="1ed4e-126">レポート データ ペインでデータ ソースを右クリックし、 **[データ ソースのプロパティ]** ダイアログ ボックスを開いて、 **[埋め込み接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1ed4e-126">In the Report Data pane, right-click the data source, open the **Data Source Properties** dialog box, and then click **Embedded Connection**.</span></span> <span data-ttu-id="1ed4e-127">必要な情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="1ed4e-127">Enter the required information.</span></span>  
  
     <span data-ttu-id="1ed4e-128">レポート データ ペインでデータ ソース アイコンが共有データ ソースのアイコンに変わります。</span><span class="sxs-lookup"><span data-stu-id="1ed4e-128">In the Report Data pane, the data source icon changes to the shared data source icon.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ed4e-129">参照</span><span class="sxs-lookup"><span data-stu-id="1ed4e-129">See Also</span></span>  
 <span data-ttu-id="1ed4e-130">[レポート データ ソースを管理する](manage-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="1ed4e-130">[Manage Report Data Sources](manage-report-data-sources.md) </span></span>  
 [<span data-ttu-id="1ed4e-131">Reporting Services でのデータ接続、データ ソース、および接続文字列</span><span class="sxs-lookup"><span data-stu-id="1ed4e-131">Data Connections, Data Sources, and Connection Strings in Reporting Services</span></span>](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
