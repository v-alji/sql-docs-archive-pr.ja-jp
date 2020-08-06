---
title: Upgrade Advisor を使用してアップグレードを準備する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server]
- upgrading SQL Server, Upgrade Advisor
- upgrading SQL Server, preparing to upgrade
- SQL Server Upgrade Advisor
- analyzing installations for upgrading [SQL Server]
ms.assetid: d85b0833-ddeb-42e3-9397-97ea60d521b7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e53d895cb19a172d0810ae9d6c2bda3406732da1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715938"
---
# <a name="use-upgrade-advisor-to-prepare-for-upgrades"></a><span data-ttu-id="b4ccf-102">アップグレード アドバイザーを使用したアップグレードの準備</span><span class="sxs-lookup"><span data-stu-id="b4ccf-102">Use Upgrade Advisor to Prepare for Upgrades</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b4ccf-103">アップグレード アドバイザーは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] へのアップグレードの準備に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-103">Upgrade Advisor helps you prepare for upgrades to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="b4ccf-104">アップグレード アドバイザーでは、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でインストールされたコンポーネントが分析され、アップグレードの前または後に修正する必要がある問題を示すレポートが生成されます。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-104">Upgrade Advisor analyzes installed components from earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and then generates a report that identifies issues to fix either before or after you upgrade.</span></span>  
  
## <a name="how-upgrade-advisor-works"></a><span data-ttu-id="b4ccf-105">アップグレード アドバイザーの機能</span><span class="sxs-lookup"><span data-stu-id="b4ccf-105">How Upgrade Advisor Works</span></span>  
 <span data-ttu-id="b4ccf-106">アップグレード アドバイザーを実行すると、アップグレード アドバイザーのホーム ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-106">When you run Upgrade Advisor, the Upgrade Advisor Home page appears.</span></span> <span data-ttu-id="b4ccf-107">ホーム ページからは、次のツールを起動できます。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-107">From the Home page, you can run the following tools:</span></span>  
  
-   <span data-ttu-id="b4ccf-108">アップグレード アドバイザー分析ウィザード</span><span class="sxs-lookup"><span data-stu-id="b4ccf-108">Upgrade Advisor Analysis Wizard</span></span>  
  
-   <span data-ttu-id="b4ccf-109">アップグレード アドバイザー レポート ビューアー</span><span class="sxs-lookup"><span data-stu-id="b4ccf-109">Upgrade Advisor Report Viewer</span></span>  
  
-   <span data-ttu-id="b4ccf-110">アップグレード アドバイザーのヘルプ</span><span class="sxs-lookup"><span data-stu-id="b4ccf-110">Upgrade Advisor Help</span></span>  
  
 <span data-ttu-id="b4ccf-111">最初にアップグレード アドバイザーを使用するときに、アップグレード アドバイザーの分析ウィザードを実行して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のコンポーネントを分析します。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-111">The first time that you use Upgrade Advisor, run the Upgrade Advisor Analysis Wizard to analyze [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span> <span data-ttu-id="b4ccf-112">ウィザードによる分析が完了したら、アップグレード アドバイザー レポート ビューアーで結果のレポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-112">When the wizard finishes the analysis, view the resulting reports in the Upgrade Advisor Report Viewer.</span></span> <span data-ttu-id="b4ccf-113">各レポートにはアップグレード アドバイザーのヘルプへのリンクが示されており、既知の問題の修正または影響の軽減に役立つ情報を参照できるようになっています。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-113">Each report provides links to information in Upgrade Advisor Help that will help you fix or reduce the effect of the known issues.</span></span>  
  
## <a name="upgrade-advisor-analysis"></a><span data-ttu-id="b4ccf-114">アップグレード アドバイザーの分析</span><span class="sxs-lookup"><span data-stu-id="b4ccf-114">Upgrade Advisor Analysis</span></span>  
 <span data-ttu-id="b4ccf-115">アップグレード アドバイザーでは、次の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントを分析します。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-115">Upgrade Advisor analyzes the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components:</span></span>  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
 <span data-ttu-id="b4ccf-116">分析では、スクリプト、ストアド プロシージャ、トリガー、トレース ファイルなどのアクセス可能なオブジェクトが調べられます。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-116">The analysis examines objects that can be accessed, such as scripts, stored procedures, triggers, and trace files.</span></span> <span data-ttu-id="b4ccf-117">デスクトップ アプリケーションや暗号化されたストアド プロシージャは、アップグレード アドバイザーで分析できません。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-117">Upgrade Advisor cannot analyze desktop applications or encrypted stored procedures.</span></span>  
  
 <span data-ttu-id="b4ccf-118">出力は XML レポートの形式で行われます。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-118">Output is in the form of an XML report.</span></span> <span data-ttu-id="b4ccf-119">XML レポートを表示するには、アップグレード アドバイザー レポート ビューアーを使用します。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-119">View the XML report by using the Upgrade Advisor report viewer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b4ccf-120">レポートに "アップグレードに関するその他の問題" という項目が示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-120">Reports might contain an "other upgrade issues" item.</span></span> <span data-ttu-id="b4ccf-121">この項目は、サーバーやアプリケーションに存在する可能性があってもアップグレード アドバイザーでは検出されない問題の一覧にリンクされています。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-121">This item links to a list of issues that are not detected by Upgrade Advisor, but might exist on your server or in your applications.</span></span> <span data-ttu-id="b4ccf-122">この検出できない問題の一覧を確認し、これらの問題のためにサーバーやアプリケーションを変更する必要があるかどうかを判断してください。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-122">You should review the list of undetectable issues and determine whether you must change your server or applications because of the undetectable issues.</span></span>  
  
## <a name="how-to-install-and-run-upgrade-advisor"></a><span data-ttu-id="b4ccf-123">アップグレード アドバイザーのインストールおよび実行方法</span><span class="sxs-lookup"><span data-stu-id="b4ccf-123">How to Install and Run Upgrade Advisor</span></span>  
 <span data-ttu-id="b4ccf-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アップグレード アドバイザーのインストール先は、分析対象のコンポーネントによって異なります。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-124">The location where you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor depends on what you will be analyzing.</span></span> <span data-ttu-id="b4ccf-125">アップグレード アドバイザーでは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 以外のサポートされているすべてのコンポーネントをリモートで分析できます。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-125">Upgrade Advisor supports remote analysis of all supported components except [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="b4ccf-126">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインスタンスをスキャンしない場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続でき、かつアップグレード アドバイザーの前提条件を満たす任意のコンピューターにアップグレード アドバイザーをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-126">If you are not scanning instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can install Upgrade Advisor on any computer that can connect to your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and that meets the Upgrade Advisor prerequisites.</span></span> <span data-ttu-id="b4ccf-127">詳細については、「 [サポートされているバージョンとエディションのアップグレード](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-127">For more information, see [Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md).</span></span> <span data-ttu-id="b4ccf-128">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインスタンスをスキャンする場合は、アップグレード アドバイザーをレポート サーバーにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-128">If you are scanning instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you must install Upgrade Advisor on the report server.</span></span>  
  
 <span data-ttu-id="b4ccf-129">アップグレード アドバイザーは機能パックで提供されています。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-129">Upgrade Advisor is available in a feature pack.</span></span>  
  
 <span data-ttu-id="b4ccf-130">アップグレード アドバイザーをインストールして実行するための前提条件は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-130">Prerequisites for installing and running Upgrade Advisor are as follows:</span></span>  
  
-   [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] <span data-ttu-id="b4ccf-131">SP2、Windows 7 SP1、および [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-131">SP2, Windows 7 SP1, and [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1.</span></span>  
  
-   <span data-ttu-id="b4ccf-132">Windows インストーラー 4.5 以降のバージョン。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-132">Windows Installer beginning with version 4.5.</span></span> <span data-ttu-id="b4ccf-133">[Windows インストーラー Web サイト](https://www.microsoft.com/download/details.aspx?id=8483)から Windows インストーラーをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-133">You can install Windows Installer from the [Windows Installer Web site](https://www.microsoft.com/download/details.aspx?id=8483).</span></span>  
  
-   <span data-ttu-id="b4ccf-134">Microsoft .NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-134">Microsoft .NET Framework 4.</span></span> <span data-ttu-id="b4ccf-135">.NET Framework 4 は、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 製品メディアおよび[.NET Framework 4 ダウンロードページ](https://go.microsoft.com/fwlink/?LinkId=209895)から入手できます。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-135">.NET Framework 4 is available on the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] product media, and from the [.NET Framework 4 download page](https://go.microsoft.com/fwlink/?LinkId=209895).</span></span>  
  
    -   <span data-ttu-id="b4ccf-136">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] メディアから .NET Framework 4 をインストールするには、ディスク ドライブのルートに移動します。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-136">To install the .NET Framework 4 from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] media, locate the root of the disk drive.</span></span> <span data-ttu-id="b4ccf-137">次に、[]、[redist] フォルダーの順にダブルクリックし、[DotNetFrameworks] フォルダーをダブルクリックして dotNetFx40_Full_x86_x64.exe (32 ビットオペレーティングシステムの場合は、64ビットオペレーティングシステムの場合) を実行します。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-137">Then, double-click the \redist folder, double-click the DotNetFrameworks folder, and run dotNetFx40_Full_x86_x64.exe (for 32-bit operating systems or for 64-bit operating systems).</span></span>  
  
 <span data-ttu-id="b4ccf-138">アップグレード アドバイザーを Web からインストールするには、ダウンロード ページのダウンロード ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-138">To install Upgrade Advisor from the Web, click the download button on the download page.</span></span> <span data-ttu-id="b4ccf-139">その後すぐにインストールを実行するか、または SQLUA.msi ファイルを保存して後から実行できます。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-139">You can then run installation immediately, or save the SQLUA.msi file to run later.</span></span> <span data-ttu-id="b4ccf-140">製品ディスクからをインストールする場合は、製品ディスクから直接 SQLUA.msi を実行します。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-140">If you are installing from the product disc, run SQLUA.msi directly from the product disk.</span></span>  
  
 <span data-ttu-id="b4ccf-141">アップグレードアドバイザーをインストールすると、[**スタート**] メニューから開くことができます。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-141">After you install Upgrade Advisor, you can open it from the **Start** menu:</span></span>  
  
-   <span data-ttu-id="b4ccf-142">[**スタート**] をクリックし、[**すべてのプログラム**]、[] の順にポイントして、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] \*\* [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] アップグレードアドバイザー\*\*] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-142">Click **Start**, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], and then click **[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor**.</span></span>  
  
 <span data-ttu-id="b4ccf-143">詳細については、アップグレード アドバイザーのダウンロードおよび [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のリリース ノートに収録されているアップグレード アドバイザーのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-143">For more information, see the Upgrade Advisor documentation included in the Upgrade Advisor download and the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Release Notes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4ccf-144">参照</span><span class="sxs-lookup"><span data-stu-id="b4ccf-144">See Also</span></span>  
 <span data-ttu-id="b4ccf-145">[SQL Server の複数のバージョンおよびインスタンスの操作](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b4ccf-145">[Work with Multiple Versions and Instances of SQL Server](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md) </span></span>  
 <span data-ttu-id="b4ccf-146">[サポートされているバージョンとエディションのアップグレード](../../database-engine/install-windows/supported-version-and-edition-upgrades.md) </span><span class="sxs-lookup"><span data-stu-id="b4ccf-146">[Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md) </span></span>  
 [<span data-ttu-id="b4ccf-147">旧バージョンとの互換性</span><span class="sxs-lookup"><span data-stu-id="b4ccf-147">Backward Compatibility</span></span>](../../../2014/getting-started/backward-compatibility.md)  
  
  
