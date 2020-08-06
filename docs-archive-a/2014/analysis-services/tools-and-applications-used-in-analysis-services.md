---
title: Analysis Services | で使用されるツールとアプリケーションMicrosoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0ddb3b7a-7464-4d04-8659-11cb2e4cf3c3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 36bbcbca4323a9ce327b5fa89398dfb20da319c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632742"
---
# <a name="tools-and-applications-used-in-analysis-services"></a><span data-ttu-id="1416f-102">Analysis Services で使用するツールとアプリケーション</span><span class="sxs-lookup"><span data-stu-id="1416f-102">Tools and applications used in Analysis Services</span></span>
  <span data-ttu-id="1416f-103">Analysis Services モデルの構築および Analysis Services インスタンス上で関連付けられているデータベースの管理に必要なツールやアプリケーションを検索します。</span><span class="sxs-lookup"><span data-stu-id="1416f-103">Find the tools and applications you'll need for building Analysis Services models, and managing the associated databases on an Analysis Services instance.</span></span>

## <a name="analysis-services-model-designers"></a><span data-ttu-id="1416f-104">Analysis Services モデルのデザイナー</span><span class="sxs-lookup"><span data-stu-id="1416f-104">Analysis Services Model Designers</span></span>
 <span data-ttu-id="1416f-105">テーブル モデルおよび多次元モデルは、Visual Studio シェル内で構築されたソリューションのプロジェクト テンプレートから作成されます。</span><span class="sxs-lookup"><span data-stu-id="1416f-105">Tabular and multidimensional models are created from project templates in a solution built inside the Visual Studio shell.</span></span> <span data-ttu-id="1416f-106">このプロジェクト テンプレートには、Analysis Services ソリューションを構成するモデル、キューブ、ディメンション、ロールを作成するためのデザイナーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="1416f-106">The project template provides the designers for creating models, cubes, dimensions, and roles that comprise an Analysis Services solution.</span></span>

### <a name="download-sql-server-data-tools-for-business-intelligence-ssdt-bi"></a><span data-ttu-id="1416f-107">SQL Server Data Tools for Business Intelligence (SSDT-BI) のダウンロード</span><span class="sxs-lookup"><span data-stu-id="1416f-107">Download SQL Server Data Tools for Business Intelligence (SSDT-BI)</span></span>
 <span data-ttu-id="1416f-108">以前は Business Intelligence Development Studio (BIDS) と呼ばれていた、ビジネス インテリジェンス用 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] (SSDT-BI) を使用して、Analysis Services モデル、Reporting Services レポート、および Integration Services パッケージを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1416f-108">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] for Business Intelligence (SSDT-BI), previously known as Business Intelligence Development Studio (BIDS), is used to create Analysis Services models, Reporting Services reports, and Integration Services packages.</span></span> <span data-ttu-id="1416f-109">次の場所から SSDT-BI をダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="1416f-109">You can download SSDT-BI from the following locations:</span></span>

-   [<span data-ttu-id="1416f-110">SSDT-BI for Visual Studio 2013 のダウンロード</span><span class="sxs-lookup"><span data-stu-id="1416f-110">Download SSDT-BI for Visual Studio 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396526)

-   [<span data-ttu-id="1416f-111">SSDT-BI for Visual Studio 2012 のダウンロード</span><span class="sxs-lookup"><span data-stu-id="1416f-111">Download SSDT-BI for Visual Studio 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=273673)

 <span data-ttu-id="1416f-112">SSDT-BI または BIDS の以前のバージョンをコンピューターにインストールしていた場合は、新しいバージョンが以前のバージョンと共にサイド バイ サイドでインストールされます。</span><span class="sxs-lookup"><span data-stu-id="1416f-112">If you have a prior version of SSDT-BI or BIDS installed on your computer, the newer version is installed side-by-side the previous version.</span></span> <span data-ttu-id="1416f-113">サーバーの特定のバージョンに関連付けられているプロジェクトとソリューションを変更できるように、1 台のワークステーションでデザイン ツールの新しいバージョンと以前のバージョンを実行することは一般的です。</span><span class="sxs-lookup"><span data-stu-id="1416f-113">It's common to run newer and older versions of the design tools on a single workstation so that you can modify projects and solutions tied to specific versions of the server.</span></span>

> [!NOTE]
>  <span data-ttu-id="1416f-114">SSDT の Visual Studio 2012 バージョンと Visual Studio 2013 バージョンを入手できるダウンロード サイトは複数存在します。</span><span class="sxs-lookup"><span data-stu-id="1416f-114">There are several download sites for the Visual Studio 2012 and Visual Studio 2013 versions of SSDT.</span></span> <span data-ttu-id="1416f-115">ほとんどのダウンロードには、BI プロジェクト テンプレートが含まれていません。</span><span class="sxs-lookup"><span data-stu-id="1416f-115">Most do not include the BI project templates.</span></span> <span data-ttu-id="1416f-116">上記のリンクを使用すると、適切なバージョンを取得できます。</span><span class="sxs-lookup"><span data-stu-id="1416f-116">Using the links above will get you the correct version.</span></span> <span data-ttu-id="1416f-117">[ビジネスインテリジェンスプロジェクトテンプレート] フォルダーが表示されている場合は、SSDT の正しいバージョンがあることがわかります。</span><span class="sxs-lookup"><span data-stu-id="1416f-117">You'll know that you have the correct version of SSDT-BI if you see the Business Intelligence project templates folder.</span></span> <span data-ttu-id="1416f-118">このフォルダーには、Analysis Services、Reporting Services、および Integration Services 用のプロジェクト テンプレートが格納されています。</span><span class="sxs-lookup"><span data-stu-id="1416f-118">This folder contains the project templates for Analysis Services, Reporting Services and Integration Services.</span></span> <span data-ttu-id="1416f-119">SSDT-BI をインストールした方法によっては、SQL Server データベース用の追加のプロジェクト テンプレートも表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="1416f-119">Depending on how you installed SSDT-BI, you might also see an additional project template for SQL Server databases.</span></span>

 <span data-ttu-id="1416f-120">![SSDT の新しいプロジェクト テンプレート](media/ssdt-biprojects.png "SSDT の新しいプロジェクト テンプレート")</span><span class="sxs-lookup"><span data-stu-id="1416f-120">![New Project templates in SSDT](media/ssdt-biprojects.png "New Project templates in SSDT")</span></span>

## <a name="administrative-tools"></a><span data-ttu-id="1416f-121">管理ツール</span><span class="sxs-lookup"><span data-stu-id="1416f-121">Administrative tools</span></span>

### <a name="sql-server-management-studio"></a><span data-ttu-id="1416f-122">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1416f-122">SQL Server Management Studio</span></span>
 <span data-ttu-id="1416f-123">Management Studio は、Analysis Services を含むすべての SQL Server 機能用の主要な管理ツールです。</span><span class="sxs-lookup"><span data-stu-id="1416f-123">Management Studio is the primary administration tool for all SQL Server features, including Analysis Services.</span></span> <span data-ttu-id="1416f-124">SQL Server Management Studio はオプションのコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="1416f-124">SQL Server Management Studio is an optional component.</span></span> <span data-ttu-id="1416f-125">SQL Server Management Studio が他の SQL Server アプリケーションと一緒に Windows Server 2012 のアプリ ページに表示されない場合は、SQL Server セットアップを実行してインストールに追加します。</span><span class="sxs-lookup"><span data-stu-id="1416f-125">If you don't see it with other SQL Server applications on the Apps page in Windows Server 2012, run SQL Server Setup to add it to your installation.</span></span>

### <a name="sql-server-profiler"></a><span data-ttu-id="1416f-126">SQL Server プロファイラー</span><span class="sxs-lookup"><span data-stu-id="1416f-126">SQL Server Profiler</span></span>
 <span data-ttu-id="1416f-127">正式に非推奨とされていても、SQL Server Profiler は接続、MDX クエリの実行、および他のサーバー操作を簡単に監視する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="1416f-127">Although it's officially deprecated, SQL Server Profiler provides an easy way to monitor connections, MDX query execution, and other server operations.</span></span> <span data-ttu-id="1416f-128">SQL Server Profiler は既定でインストールされます。</span><span class="sxs-lookup"><span data-stu-id="1416f-128">SQL Server Profiler is installed by default.</span></span> <span data-ttu-id="1416f-129">SQL Server アプリケーションと一緒に Windows Server 2012 のアプリ ページにあります。</span><span class="sxs-lookup"><span data-stu-id="1416f-129">You can find it with SQL Server applications on Apps in Windows Server 2012.</span></span>

### <a name="powershell"></a><span data-ttu-id="1416f-130">PowerShell</span><span class="sxs-lookup"><span data-stu-id="1416f-130">PowerShell</span></span>
 <span data-ttu-id="1416f-131">PowerShell コマンドを使用すると、多くの管理タスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="1416f-131">You can use PowerShell commands to perform many administrative tasks.</span></span> <span data-ttu-id="1416f-132">詳細については、「 [Analysis Services PowerShell](analysis-services-powershell.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1416f-132">See [Analysis Services PowerShell](analysis-services-powershell.md) for more information.</span></span>

### <a name="community-and-third-party-tools"></a><span data-ttu-id="1416f-133">コミュニティとサード パーティのツール</span><span class="sxs-lookup"><span data-stu-id="1416f-133">Community and Third-party tools</span></span>
 <span data-ttu-id="1416f-134">コミュニティ コードの例については、「 [Analysis Services Codeplex ページ](https://sqlsrvanalysissrvcs.codeplex.com/) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1416f-134">Check the [Analysis Services codeplex page](https://sqlsrvanalysissrvcs.codeplex.com/) for community code samples.</span></span> <span data-ttu-id="1416f-135">[フォーラム](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlanalysisservices)は、Analysis Services をサポートするサードパーティ製ツールの推奨事項を検索するときに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1416f-135">[Forums](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlanalysisservices) can be helpful when seeking recommendations for third-party tools that support Analysis Services.</span></span>
