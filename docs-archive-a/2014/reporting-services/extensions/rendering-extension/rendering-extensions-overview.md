---
title: 表示拡張機能の概要 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- formats [Reporting Services], rendering extensions
- rendering extensions [Reporting Services], about extensions
ms.assetid: 909356a0-4709-43e5-b597-33bd9bb22882
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b97aa44ba014d9444ef1a30d581d4e419ccaf3d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641491"
---
# <a name="rendering-extensions-overview"></a><span data-ttu-id="ecf23-102">表示拡張機能の概要</span><span class="sxs-lookup"><span data-stu-id="ecf23-102">Rendering Extensions Overview</span></span>
  <span data-ttu-id="ecf23-103">表示拡張機能は、レポート サーバーのコンポーネントまたはモジュールで、レポートのデータとレイアウト情報をデバイス固有の形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="ecf23-103">A rendering extension is a component or module of a report server that transforms report data and layout information into a device-specific format.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="ecf23-104">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] には、HTML、Excel、Word、CSV またはテキスト、XML、画像および PDF の 7 つの表示拡張機能があります。</span><span class="sxs-lookup"><span data-stu-id="ecf23-104">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] includes seven rendering extensions: HTML, Excel, Word, CSV or Text, XML, Image, and PDF.</span></span> <span data-ttu-id="ecf23-105">追加の表示拡張機能を作成して、他の形式でレポートを生成できます。</span><span class="sxs-lookup"><span data-stu-id="ecf23-105">You can create additional rendering extensions to generate reports in other formats.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ecf23-106">どの表示拡張機能を利用できるかは、RSReportServer.config ファイルのインストール済み拡張機能の一覧で確認できます。</span><span class="sxs-lookup"><span data-stu-id="ecf23-106">To determine which rendering extensions are available, you can view the list of installed extensions in the RSReportServer.config file.</span></span>  
  
 <span data-ttu-id="ecf23-107">次の表は、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] が備えている表示拡張機能の説明です。</span><span class="sxs-lookup"><span data-stu-id="ecf23-107">The following table describes the rendering extensions that are included with [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="ecf23-108">拡張機能の名前</span><span class="sxs-lookup"><span data-stu-id="ecf23-108">Extension Name</span></span>|<span data-ttu-id="ecf23-109">説明</span><span class="sxs-lookup"><span data-stu-id="ecf23-109">Description</span></span>|  
|--------------------|-----------------|  
|`XML`|<span data-ttu-id="ecf23-110">XML 形式でレポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="ecf23-110">Renders a report in XML.</span></span> <span data-ttu-id="ecf23-111">レポートは任意のブラウザーで開きます。</span><span class="sxs-lookup"><span data-stu-id="ecf23-111">The report opens in a browser.</span></span> <span data-ttu-id="ecf23-112">この XML 出力にさらに手を加えれば、新しい表示拡張機能を開発しなくても、必要な表示拡張機能を効率的に追加することができます。</span><span class="sxs-lookup"><span data-stu-id="ecf23-112">Additional transformations applied to this XML output may be a cost effective way of avoiding developing your own rendering extension.</span></span>|  
|`CSV`|<span data-ttu-id="ecf23-113">コンマ区切り形式でレポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="ecf23-113">Renders a report in comma-delimited format.</span></span> <span data-ttu-id="ecf23-114">レポートは、CSV ファイル形式に関連付けられている表示ツールで開きます。</span><span class="sxs-lookup"><span data-stu-id="ecf23-114">The report opens in a viewing tool associated with CSV file formats.</span></span>|  
|`IMAGE`|<span data-ttu-id="ecf23-115">ページ指向形式でレポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="ecf23-115">Renders a report in a page-oriented format.</span></span> <span data-ttu-id="ecf23-116">この形式は、レポート ツール バーの [エクスポート] ボックスに **[TIFF]** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="ecf23-116">The format is shown as **TIFF** in the Export drop-down of the report toolbar.</span></span>|  
|`PDF`|<span data-ttu-id="ecf23-117">Adobe Acrobat Reader 形式でレポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="ecf23-117">Renders a report in the Adobe Acrobat Reader.</span></span> <span data-ttu-id="ecf23-118">この形式は、レポート ツール バーの [エクスポート] ボックスに **[Acrobat (PDF) ファイル]** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="ecf23-118">The format is shown as **Acrobat (PDF) File** in the Export drop-down of the report toolbar.</span></span>|  
|`EXCEL`|<span data-ttu-id="ecf23-119">[!INCLUDE[ofprexcel](../../../includes/ofprexcel-md.md)] 形式でレポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="ecf23-119">Renders a report in [!INCLUDE[ofprexcel](../../../includes/ofprexcel-md.md)].</span></span>|  
|`WORD`|<span data-ttu-id="ecf23-120">レポートを [!INCLUDE[ofprword](../../../includes/ofprword-md.md)] で表示します。</span><span class="sxs-lookup"><span data-stu-id="ecf23-120">Render a report in [!INCLUDE[ofprword](../../../includes/ofprword-md.md)].</span></span>|  
|<span data-ttu-id="ecf23-121">`HTML 4.0` (HTML 表示拡張機能の一部)</span><span class="sxs-lookup"><span data-stu-id="ecf23-121">`HTML 4.0` (part of the HTML rendering extension)</span></span>|<span data-ttu-id="ecf23-122">HTML は、初期状態でレポートを表示するのに使用される形式です。</span><span class="sxs-lookup"><span data-stu-id="ecf23-122">HTML is the format used to initially render the report.</span></span> <span data-ttu-id="ecf23-123">ブラウザーが HTML4.0 をサポートしている場合は、HTML4.0 形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ecf23-123">If your browser support HTML 4.0, that is the format that is used.</span></span> <span data-ttu-id="ecf23-124">それ以外の場合は、HTML 3.2 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ecf23-124">Otherwise, HTML 3.2 is used.</span></span>|  
|<span data-ttu-id="ecf23-125">`MHTML` (HTML 表示拡張機能の一部)</span><span class="sxs-lookup"><span data-stu-id="ecf23-125">`MHTML` (part of the HTML rendering extension)</span></span>|<span data-ttu-id="ecf23-126">MHTML 形式でレポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="ecf23-126">Renders a report in MHTML.</span></span> <span data-ttu-id="ecf23-127">レポートは、Internet Explorer で開きます。</span><span class="sxs-lookup"><span data-stu-id="ecf23-127">The report opens in Internet Explorer.</span></span> <span data-ttu-id="ecf23-128">この形式は、レポート ツール バーの [エクスポート] ボックスに **[Web アーカイブ]** として表示されます。</span><span class="sxs-lookup"><span data-stu-id="ecf23-128">The format is shown as **Web Archive** in the Export drop-down of the report toolbar.</span></span>|  
|`NULL`|<span data-ttu-id="ecf23-129">レポートを特定の形式で表示しません。</span><span class="sxs-lookup"><span data-stu-id="ecf23-129">Does not render a report to a specific format.</span></span> <span data-ttu-id="ecf23-130">この表示拡張機能はレポートをキャッシュするのに有用です。</span><span class="sxs-lookup"><span data-stu-id="ecf23-130">This rendering extension is useful for placing reports in cache.</span></span> <span data-ttu-id="ecf23-131">Null 表示形式は、スケジュールされた実行または配信と連動して使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ecf23-131">Null rendering should be used in conjunction with a scheduled execution or delivery.</span></span>|  
  
 <span data-ttu-id="ecf23-132">推奨形式とその使い方の詳細については、「[レポートのエクスポート &#40;レポート ビルダーおよび SSRS&#41;](../../report-builder/export-reports-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ecf23-132">For more information on the recommended formats and their uses, see [Exporting Reports &#40;Report Builder and SSRS&#41;](../../report-builder/export-reports-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="ecf23-133">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] によって [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] に実装された表示拡張機能は、すべて共通のインターフェイスを使用します。</span><span class="sxs-lookup"><span data-stu-id="ecf23-133">Each of the rendering extensions implemented by [!INCLUDE[msCoName](../../../includes/msconame-md.md)] and shipped with [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] uses a common set of interfaces.</span></span> <span data-ttu-id="ecf23-134">これにより、すべての拡張機能で同じレベルの機能性が実装され、レポート サーバーのコア部分での表示処理用コードがより単純になります。</span><span class="sxs-lookup"><span data-stu-id="ecf23-134">This ensures that each extension implements comparable functionality and reduces the complexity of the rendering code in the core of the report server.</span></span>  
  
## <a name="rendering-object-model"></a><span data-ttu-id="ecf23-135">表示オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="ecf23-135">Rendering Object Model</span></span>  
 <span data-ttu-id="ecf23-136">レポートが処理されると、その処理結果は、表示オブジェクト モデル (ROM) として知られる、公開オブジェクト モデルになります。</span><span class="sxs-lookup"><span data-stu-id="ecf23-136">When a report is processed, the result is a publicly exposed object model known as the Rendering Object Model (ROM).</span></span> <span data-ttu-id="ecf23-137">この表示オブジェクト モデルは、処理されたレポートの内容、レイアウト、およびデータを定義するクラスのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="ecf23-137">The Rendering Object Model is a collection of classes that define the contents, layout, and data of a report that has been processed.</span></span> <span data-ttu-id="ecf23-138">開発者は、ROM を使用して、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のカスタム表示拡張機能を設計、開発、展開できます。</span><span class="sxs-lookup"><span data-stu-id="ecf23-138">The ROM is available to developers who wish to design, develop, and deploy custom rendering extensions for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="ecf23-139">ROM は、レポートの XML 定義とユーザーにより定義されたレポート データが、レポート サーバーにより処理される際に作成されます。</span><span class="sxs-lookup"><span data-stu-id="ecf23-139">ROM is produced when the report server processes a report's XML definition along with the user-defined report data.</span></span> <span data-ttu-id="ecf23-140">処理が完了すると、表示拡張機能によりこの公開オブジェクト モデルが使用され、レポートの出力が定義されます。</span><span class="sxs-lookup"><span data-stu-id="ecf23-140">When processing is complete, the public object model is used by a rendering extension to define the output of the report.</span></span> <span data-ttu-id="ecf23-141">ROM の利用可能なパブリック クラスは `Microsoft.ReportingServices.OnDemandReportRendering` 名前空間で定義されています。</span><span class="sxs-lookup"><span data-stu-id="ecf23-141">The ROM's available public classes are defined in the `Microsoft.ReportingServices.OnDemandReportRendering` namespace.</span></span>  
  
## <a name="writing-custom-rendering-extensions"></a><span data-ttu-id="ecf23-142">カスタム表示拡張機能の記述</span><span class="sxs-lookup"><span data-stu-id="ecf23-142">Writing Custom Rendering Extensions</span></span>  
 <span data-ttu-id="ecf23-143">カスタム表示拡張機能の作成を決める前に、より簡単な代替手段を評価する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ecf23-143">Before you decide to create a custom rendering extension, you should evaluate simpler alternatives.</span></span> <span data-ttu-id="ecf23-144">次のようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="ecf23-144">You can:</span></span>  
  
-   <span data-ttu-id="ecf23-145">既存の拡張機能のデバイス情報の設定を詳細に指定して、表示される出力をカスタマイズする。</span><span class="sxs-lookup"><span data-stu-id="ecf23-145">Customize rendered output by specifying device information settings for existing extensions.</span></span>  
  
-   <span data-ttu-id="ecf23-146">XML 表現形式の出力に XSL 変換 (XSLT) を組み合わせることで、カスタムの形式と表現機能を追加する。</span><span class="sxs-lookup"><span data-stu-id="ecf23-146">Add custom formatting and presentation features by combining XSL Transformations (XSLT) with the output of the XML rendering format.</span></span>  
  
 <span data-ttu-id="ecf23-147">カスタム表示拡張機能の記述は難しい作業です。</span><span class="sxs-lookup"><span data-stu-id="ecf23-147">Writing a custom rendering extension is difficult.</span></span> <span data-ttu-id="ecf23-148">表示拡張機能は、一般的には、レポートの要素のあらゆる組み合わせをサポートする必要があり、多くのクラス、インターフェイス、メソッド、およびプロパティを実装しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="ecf23-148">A rendering extension must typically support all possible combinations of report elements and requires that you implement hundreds of classes, interfaces, methods, and properties.</span></span> <span data-ttu-id="ecf23-149">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] によりサポートされていない形式でレポートを表示する必要があり、独自に表示拡張機能のコードを記述して実装する場合、開発する表示拡張機能のコードは `Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension` インターフェイスを実装する必要があります。このインターフェイスはレポート サーバーにより必要とされます。</span><span class="sxs-lookup"><span data-stu-id="ecf23-149">If you must render a report in a format that is not included with [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] and decide to write your own managed code implementation of a rendering extension, the rendering extension code must implement the `Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension` interface, which is required by the report server.</span></span>  
  
 <span data-ttu-id="ecf23-150">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] に関する補足資料とホワイト ペーパーについては、[Reporting Services Web サイト](https://go.microsoft.com/fwlink/?LinkId=19951)の最新の技術文書を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ecf23-150">For supplemental documentation and whitepapers on [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], see the latest technical resources at the [Reporting Services Web site](https://go.microsoft.com/fwlink/?LinkId=19951).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecf23-151">参照</span><span class="sxs-lookup"><span data-stu-id="ecf23-151">See Also</span></span>  
 <span data-ttu-id="ecf23-152">[表示拡張機能の実装](implementing-a-rendering-extension.md) </span><span class="sxs-lookup"><span data-stu-id="ecf23-152">[Implementing a Rendering Extension](implementing-a-rendering-extension.md) </span></span>  
 [<span data-ttu-id="ecf23-153">Reporting Services 拡張機能ライブラリ</span><span class="sxs-lookup"><span data-stu-id="ecf23-153">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  