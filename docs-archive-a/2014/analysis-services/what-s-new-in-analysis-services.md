---
title: Analysis Services とビジネスインテリジェンスの新機能 |&#39;Microsoft Docs
ms.custom: ''
ms.date: 06/07/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: aa69c299-b8f4-4969-86d8-b3292fe13f08
author: minewiskan
ms.author: owend
ms.openlocfilehash: 18863a565b63ccc1a9bd2eb0e7619d4d133c5d33
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633343"
---
# <a name="what39s-new-in-sql-server-2014-analysis-services"></a><span data-ttu-id="8df9f-102">SQL Server 2014 Analysis Services の&#39;の新機能</span><span class="sxs-lookup"><span data-stu-id="8df9f-102">What&#39;s New in SQL Server 2014 Analysis Services</span></span>
  <span data-ttu-id="8df9f-103">多次元モデルに対して Power View レポートをサポートする機能を追加する例外で [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は、以前のリリースから変更されていません。</span><span class="sxs-lookup"><span data-stu-id="8df9f-103">With exception to added functionality supporting Power View Reports against Multidimensional Models, [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] is unchanged from the previous release.</span></span>

 <span data-ttu-id="8df9f-104">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]このリリースで異なる他の製品およびテクノロジについては、「 [SQL Server 2014 の新機能](../sql-server/what-s-new-in-sql-server-2016.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8df9f-104">For information about other [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] products and technologies that are different in this release, see [What's New in SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).</span></span>

## <a name="updates-to-design-tool-installation"></a><span data-ttu-id="8df9f-105">デザイン ツールのインストールに対する更新</span><span class="sxs-lookup"><span data-stu-id="8df9f-105">Updates to Design Tool installation</span></span>
 <span data-ttu-id="8df9f-106">以前は Business Intelligence Development Studio (BIDS) と呼ばれていた、ビジネス インテリジェンス用 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] (SSDT-BI) を使用して、Analysis Services モデル、Reporting Services レポート、および Integration Services パッケージを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8df9f-106">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] for Business Intelligence (SSDT-BI), previously known as Business Intelligence Development Studio (BIDS), is used to create Analysis Services models, Reporting Services reports, and Integration Services packages.</span></span> <span data-ttu-id="8df9f-107">次の場所から SSDT-BI をダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="8df9f-107">You can download SSDT-BI from the following locations:</span></span>

-   [<span data-ttu-id="8df9f-108">SSDT-BI for Visual Studio 2013 のダウンロード</span><span class="sxs-lookup"><span data-stu-id="8df9f-108">Download SSDT-BI for Visual Studio 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396526)

-   [<span data-ttu-id="8df9f-109">SSDT-BI for Visual Studio 2012 のダウンロード</span><span class="sxs-lookup"><span data-stu-id="8df9f-109">Download SSDT-BI for Visual Studio 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=273673)

 <span data-ttu-id="8df9f-110">SSDT-BI または BIDS の以前のバージョンをコンピューターにインストールしていた場合は、新しいバージョンが以前のバージョンと共にサイド バイ サイドでインストールされます。</span><span class="sxs-lookup"><span data-stu-id="8df9f-110">If you have a prior version of SSDT-BI or BIDS installed on your computer, the newer version is installed side-by-side the previous version.</span></span> <span data-ttu-id="8df9f-111">サーバーの特定のバージョンに関連付けられているプロジェクトとソリューションを変更できるように、1 台のワークステーションでデザイン ツールの新しいバージョンと以前のバージョンを実行することは一般的です。</span><span class="sxs-lookup"><span data-stu-id="8df9f-111">It's common to run newer and older versions of the design tools on a single workstation so that you can modify projects and solutions tied to specific versions of the server.</span></span>

> [!NOTE]
>  <span data-ttu-id="8df9f-112">SSDT の Visual Studio 2012 バージョンと Visual Studio 2013 バージョンを入手できるダウンロード サイトは複数存在します。</span><span class="sxs-lookup"><span data-stu-id="8df9f-112">There are several download sites for the Visual Studio 2012 and Visual Studio 2013 versions of SSDT.</span></span> <span data-ttu-id="8df9f-113">ほとんどのダウンロードには、BI プロジェクト テンプレートが含まれていません。</span><span class="sxs-lookup"><span data-stu-id="8df9f-113">Most do not include the BI project templates.</span></span> <span data-ttu-id="8df9f-114">上記のリンクを使用すると、適切なバージョンを取得できます。</span><span class="sxs-lookup"><span data-stu-id="8df9f-114">Using the links above will get you the correct version.</span></span> <span data-ttu-id="8df9f-115">[ビジネスインテリジェンスプロジェクトテンプレート] フォルダーが表示されている場合は、SSDT の正しいバージョンがあることがわかります。</span><span class="sxs-lookup"><span data-stu-id="8df9f-115">You'll know that you have the correct version of SSDT-BI if you see the Business Intelligence project templates folder.</span></span> <span data-ttu-id="8df9f-116">このフォルダーには、Analysis Services、Reporting Services、および Integration Services 用のプロジェクト テンプレートが格納されています。</span><span class="sxs-lookup"><span data-stu-id="8df9f-116">This folder contains the project templates for Analysis Services, Reporting Services and Integration Services.</span></span> <span data-ttu-id="8df9f-117">SSDT-BI をインストールした方法によっては、SQL Server データベース用の追加のプロジェクト テンプレートも表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="8df9f-117">Depending on how you installed SSDT-BI, you might also see an additional project template for SQL Server databases.</span></span>

 <span data-ttu-id="8df9f-118">![SSDT の新しいプロジェクト テンプレート](media/ssdt-biprojects.png "SSDT の新しいプロジェクト テンプレート")</span><span class="sxs-lookup"><span data-stu-id="8df9f-118">![New Project templates in SSDT](media/ssdt-biprojects.png "New Project templates in SSDT")</span></span>

## <a name="features-recently-added-power-view-for-multidimensional-models"></a><span data-ttu-id="8df9f-119">最近追加された機能: 多次元モデルの Power View</span><span class="sxs-lookup"><span data-stu-id="8df9f-119">Features recently added: Power View for Multidimensional Models</span></span>
 <span data-ttu-id="8df9f-120">多次元モデルに対応する Power View レポートを作成する機能は、[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 1 Cumulative Update 4 で最初に導入されました。</span><span class="sxs-lookup"><span data-stu-id="8df9f-120">The ability to create Power View reports against multidimensional models was first introduced in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 1 Cumulative Update 4.</span></span> <span data-ttu-id="8df9f-121">多次元モデルの Power View 機能は、現在では製品の一部として [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] に含まれています。</span><span class="sxs-lookup"><span data-stu-id="8df9f-121">Power View for Multidimensional Models functionality is now included as part of [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span>

 <span data-ttu-id="8df9f-122">**多次元モデルの Power View レポート**</span><span class="sxs-lookup"><span data-stu-id="8df9f-122">**Power View Report for a Multidimensional Model**</span></span>

 <span data-ttu-id="8df9f-123">![Power View レポート](media/powerviewreport-wn.gif "Power View レポート")</span><span class="sxs-lookup"><span data-stu-id="8df9f-123">![Power View Report](media/powerviewreport-wn.gif "Power View Report")</span></span>

 <span data-ttu-id="8df9f-124">この機能は、多次元モデル (OLAP キューブとも呼びます) を最新のレポート クライアント ツールで使用できるようにするため、組織が BI への既存の投資を最大限に活用するうえで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8df9f-124">This functionality helps organizations maximize existing BI investments by enabling multidimensional models (also known as OLAP cubes) to be used with the latest client reporting tools.</span></span> <span data-ttu-id="8df9f-125">多次元モデル内のデータの種類に応じて、テーブルやマトリックスから、バブル チャートや地理的マップまで、さまざまな動的視覚エフェクトを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="8df9f-125">Depending on the types of data in the multidimensional model, users can easily create a variety of dynamic visualizations from tables and matrices, to bubble charts and geographical maps.</span></span> <span data-ttu-id="8df9f-126">また、多次元モデルは、Data Analysis Expressions (DAX) を使用するクエリをサポートするようになりました。</span><span class="sxs-lookup"><span data-stu-id="8df9f-126">Multidimensional models now also support queries using Data Analysis Expressions (DAX).</span></span>

 <span data-ttu-id="8df9f-127">多次元モデルの Power View には、 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SharePoint モードの) の組み込みの Power View レポート機能が必要です。</span><span class="sxs-lookup"><span data-stu-id="8df9f-127">Power View for Multidimensional Models requires the built-in Power View reporting capability in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (in SharePoint mode).</span></span> <span data-ttu-id="8df9f-128">Power View の他のバージョン、特に Excel 2013 の Power View アドインは、多次元モデルをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="8df9f-128">Other versions of Power View, specifically the Power View Add-in in Excel 2013, do not support multidimensional models.</span></span>

 <span data-ttu-id="8df9f-129">詳細については、「[多次元モデルの Power View](https://msdn.microsoft.com/library/dn140246.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8df9f-129">To learn more, see [Power View for Multidimensional Models](https://msdn.microsoft.com/library/dn140246.aspx).</span></span>


