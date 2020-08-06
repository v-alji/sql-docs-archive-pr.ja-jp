---
title: SQL Server 2014 サービス更新プログラムのインストール |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 7d6c962b-c8d0-49f7-a2ac-00ad8dca930a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ace0fd187386d9a9d96e82f61d1efaa254f08c6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713434"
---
# <a name="install-sql-server-2014-servicing-updates"></a><span data-ttu-id="d6ba9-102">SQL Server 2014 サービス更新プログラムのインストール</span><span class="sxs-lookup"><span data-stu-id="d6ba9-102">Install SQL Server 2014 Servicing Updates</span></span>
  <span data-ttu-id="d6ba9-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の更新プログラムのインストールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d6ba9-103">This topic provides information about installing updates for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="d6ba9-104">このセクションでは、次の項目について説明します。</span><span class="sxs-lookup"><span data-stu-id="d6ba9-104">This section provides information about the following:</span></span>  
  
-   <span data-ttu-id="d6ba9-105">新規インストール時に [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の更新プログラムをインストールする</span><span class="sxs-lookup"><span data-stu-id="d6ba9-105">Installing updates for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] during a new installation</span></span>  
  
-   <span data-ttu-id="d6ba9-106">既にインストールされている [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の更新プログラムをインストールする</span><span class="sxs-lookup"><span data-stu-id="d6ba9-106">Installing updates for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] after it has already been installed.</span></span>  
  
 <span data-ttu-id="d6ba9-107">常に最新のセキュリティ更新プログラムがインストールされた状態になるように、適切なタイミングで最新の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新プログラムを評価してインストールすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d6ba9-107">We recommend that customers evaluate and install latest [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] updates in a timely manner to make sure that systems are up-to-date with the most recent security updates.</span></span>  
  
## <a name="installing-updates-for-sscurrent-during-a-new-installation"></a><span data-ttu-id="d6ba9-108">新規インストール時に [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の更新プログラムをインストールする</span><span class="sxs-lookup"><span data-stu-id="d6ba9-108">Installing Updates for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] During a New Installation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d6ba9-109">セットアップでは、メインの製品とそれに適用可能な更新プログラムが同時にインストールされるように、最新の製品の更新プログラムとメインの製品のインストールが統合されています。</span><span class="sxs-lookup"><span data-stu-id="d6ba9-109">setup integrates the latest product updates with the main product installation so that the main product and its applicable updates are installed at the same time.</span></span> <span data-ttu-id="d6ba9-110">製品の更新プログラムでは、次の場所から適用可能な更新プログラムが検索されます。</span><span class="sxs-lookup"><span data-stu-id="d6ba9-110">Product Update can search for the applicable updates from:</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="d6ba9-111">Update</span><span class="sxs-lookup"><span data-stu-id="d6ba9-111">Update</span></span>  
  
-   <span data-ttu-id="d6ba9-112">Windows Server Update Services (WSUS)</span><span class="sxs-lookup"><span data-stu-id="d6ba9-112">Windows Server Update Services (WSUS)</span></span>  
  
-   <span data-ttu-id="d6ba9-113">ローカル フォルダー</span><span class="sxs-lookup"><span data-stu-id="d6ba9-113">A local folder</span></span>  
  
-   <span data-ttu-id="d6ba9-114">ネットワーク共有</span><span class="sxs-lookup"><span data-stu-id="d6ba9-114">A network share</span></span>  
  
 <span data-ttu-id="d6ba9-115">セットアップで最新バージョンの適用可能な更新プログラムが検出されると、ダウンロードが実行されて、現在の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップ プロセスと統合されます。</span><span class="sxs-lookup"><span data-stu-id="d6ba9-115">After Setup finds the latest versions of the applicable updates, it downloads and integrates them with the current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup process.</span></span> <span data-ttu-id="d6ba9-116">製品の更新プログラムには、累積更新プログラム、サービス パック、またはサービス パックと累積更新プログラムが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d6ba9-116">Product Update can include a cumulative update, service pack, or service pack plus cumulative update.</span></span> <span data-ttu-id="d6ba9-117">製品の更新プログラム機能は、PCU1 で提供されていた[スリップストリーム機能](https://go.microsoft.com/fwlink/?LinkId=219945)を拡張したものです [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d6ba9-117">Product Update functionality is an extension of the [Slipstream Functionality](https://go.microsoft.com/fwlink/?LinkId=219945) that was available in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] PCU1.</span></span>  
  
## <a name="installing-updates-for-sscurrent-after-it-has-already-been-installed"></a><span data-ttu-id="d6ba9-118">既にインストールされている [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の更新プログラムをインストールする</span><span class="sxs-lookup"><span data-stu-id="d6ba9-118">Installing Updates for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] after it has already been installed</span></span>  
 <span data-ttu-id="d6ba9-119">のインストール済みインスタンスでは [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、利用可能なすべての更新プログラム (一般配布リリース (GDR-security/critical updates)、Service pack (SP)、および使用可能な最新の累積的な更新プログラム (CU)) を適用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d6ba9-119">On an installed instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], we recommend that you apply all available updates: General Distribution Releases (GDR - security/critical updates), Service Packs (SP), as well as the latest available Cumulative Update (CU).</span></span>  
  
 <span data-ttu-id="d6ba9-120">サービスリリースの種類に応じて、SQL Server の更新プログラムは、Microsoft Update (MU)、Microsoft ダウンロードセンター、またはカスタマーサポートサービス修正プログラムサーバーを通じて入手できます。</span><span class="sxs-lookup"><span data-stu-id="d6ba9-120">Depending on the type of servicing release, SQL Server updates are available via Microsoft Update (MU), the Microsoft Download Center, and/or the Customer Support Services hotfix Server.</span></span> <span data-ttu-id="d6ba9-121">SQL Server のセキュリティ更新プログラムと重要な更新プログラムは、Microsoft Update によって自動的に提供されます (MU にオプトインするために必要なこれらの更新プログラムをコントロールパネルの Windows Update で確認できるようにするため)。</span><span class="sxs-lookup"><span data-stu-id="d6ba9-121">Security and Critical updates for SQL Server are automatically provided by Microsoft Update (to be able to see these updates you need to opt-in to MU through Windows Update in Control panel).</span></span> <span data-ttu-id="d6ba9-122">Service Pack は、MU のダウンロードセンターだけでなく、オプション/重要ダウンロードとしても利用できます。</span><span class="sxs-lookup"><span data-stu-id="d6ba9-122">Service Packs are available on MU as Optional/Important downloads as well as the Download Center.</span></span> <span data-ttu-id="d6ba9-123">累積更新プログラムは、CU サポート技術情報の記事に記載されている Microsoft 修正プログラムダウンロードサーバーから入手できます。</span><span class="sxs-lookup"><span data-stu-id="d6ba9-123">Cumulative updates are available on the Microsoft hotfix download server provided in CU Knowledge Base articles.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6ba9-124">参照</span><span class="sxs-lookup"><span data-stu-id="d6ba9-124">See Also</span></span>  
 <span data-ttu-id="d6ba9-125">[インストールウィザード &#40;セットアップから SQL Server 2014 をインストール&#41;](install-sql-server-from-the-installation-wizard-setup.md) </span><span class="sxs-lookup"><span data-stu-id="d6ba9-125">[Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](install-sql-server-from-the-installation-wizard-setup.md) </span></span>  
 <span data-ttu-id="d6ba9-126">[コマンドプロンプトから更新プログラムをインストール](installing-updates-from-the-command-prompt.md)[する SQL Server 2014 &#40;セットアップのインスタンスに機能を追加&#41;](add-features-to-an-instance-of-sql-server-setup.md) </span><span class="sxs-lookup"><span data-stu-id="d6ba9-126">[Installing updates from the command prompt](installing-updates-from-the-command-prompt.md) [Add Features to an Instance of SQL Server 2014 &#40;Setup&#41;](add-features-to-an-instance-of-sql-server-setup.md) </span></span>  
 [<span data-ttu-id="d6ba9-127">SQL Server 2014 のインストールの削除</span><span class="sxs-lookup"><span data-stu-id="d6ba9-127">Drop a SQL Server 2014 Installation</span></span>](repair-a-failed-sql-server-installation.md)  
  
  
