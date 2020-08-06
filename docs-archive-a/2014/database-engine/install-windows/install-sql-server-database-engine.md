---
title: SQL Server データベースエンジン | についてMicrosoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], installing
ms.assetid: d0876e7f-aa52-4dd7-bd5c-029e2ffded5f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 93e3d7a749fe6be47cc84d43509a6f378476b2ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716585"
---
# <a name="about-the-sql-server-database-engine"></a><span data-ttu-id="a0735-102">SQL Server データベース エンジンについて</span><span class="sxs-lookup"><span data-stu-id="a0735-102">About the SQL Server Database Engine</span></span>
  <span data-ttu-id="a0735-103">[!INCLUDE[ssDE](../../includes/ssde-md.md)] の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントは、データの保存、処理、セキュリティ保護のためのコア サービスです。</span><span class="sxs-lookup"><span data-stu-id="a0735-103">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] component of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is the core service for storing, processing, and securing data.</span></span> <span data-ttu-id="a0735-104">[!INCLUDE[ssDE](../../includes/ssde-md.md)] は、企業において最もデータ処理量の多いアプリケーションの要求を満たすアクセス制御と高速トランザクション処理を提供します。</span><span class="sxs-lookup"><span data-stu-id="a0735-104">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] provides controlled access and rapid transaction processing to meet the requirements of the most demanding data consuming applications in your enterprise.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a0735-105">は、1 台のコンピューターで最大 50 個の [!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスをサポートします。</span><span class="sxs-lookup"><span data-stu-id="a0735-105">supports up to 50 instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on a single computer.</span></span> <span data-ttu-id="a0735-106">一般的なインストールを作成するには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「インストール[ウィザードから SQL Server 2014 をインストールする」 &#40;セットアップ&#41;](install-sql-server-from-the-installation-wizard-setup.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0735-106">To create a typical [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation, see [Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](install-sql-server-from-the-installation-wizard-setup.md).</span></span>  
  
 <span data-ttu-id="a0735-107">**重要** ローカルでのインストールの場合、セットアップを管理者として実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0735-107">**Important** For local installations, you must run Setup as an administrator.</span></span> <span data-ttu-id="a0735-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をリモート共有からインストールする場合は、そのリモート共有に対する読み取り権限と実行権限を持つドメイン アカウントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0735-108">If you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a remote share, you must use a domain account that has read and execute permissions on the remote share.</span></span>  
  
 <span data-ttu-id="a0735-109">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール ウィザードの [インストールするコンポーネント] ページで** データベース エンジン [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を選択すると、次の機能がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a0735-109">The following features are installed when you select **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine** on the Components to Install page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard:</span></span>  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   <span data-ttu-id="a0735-110">レプリケーション (オプションのコンポーネント)</span><span class="sxs-lookup"><span data-stu-id="a0735-110">Replication - is an optional component</span></span>  
  
-   <span data-ttu-id="a0735-111">フルテキスト検索 (オプションのコンポーネント)</span><span class="sxs-lookup"><span data-stu-id="a0735-111">Full-Text Search - is an optional component</span></span>  
  
-   <span data-ttu-id="a0735-112">Data Quality Services (オプションのコンポーネント)</span><span class="sxs-lookup"><span data-stu-id="a0735-112">Data Quality Services - is an optional component</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a0735-113">今回のリリースでは、セットアップで **[Data Quality Services]** チェック ボックスをオンにしても、Data Quality Services (DQS) サーバーはインストールされません。</span><span class="sxs-lookup"><span data-stu-id="a0735-113">In this release, selecting the **Data Quality Services** check box in setup does not install the Data Quality Services (DQS) server.</span></span> <span data-ttu-id="a0735-114">DQS サーバーをインストールするには、インストール後の追加の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0735-114">You will have to perform additional steps post installation to install DQS server.</span></span> <span data-ttu-id="a0735-115">詳細については、「 [Data Quality Services のインストール](../../data-quality-services/install-windows/install-data-quality-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0735-115">For more information, see [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).</span></span>  
  
 <span data-ttu-id="a0735-116">一般的なユーザー シナリオでは、データベース サービスに加えて次の機能もインストールします。</span><span class="sxs-lookup"><span data-stu-id="a0735-116">The following additional features are options for many typical user scenarios:</span></span>  
  
-   <span data-ttu-id="a0735-117">Data Quality クライアント</span><span class="sxs-lookup"><span data-stu-id="a0735-117">Data Quality Client</span></span>  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   <span data-ttu-id="a0735-118">接続コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a0735-118">Connectivity components</span></span>  
  
-   <span data-ttu-id="a0735-119">プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="a0735-119">Programming models</span></span>  
  
-   <span data-ttu-id="a0735-120">管理ツール</span><span class="sxs-lookup"><span data-stu-id="a0735-120">Management tools</span></span>  
  
-   [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]  
  
-   <span data-ttu-id="a0735-121">Documentation コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a0735-121">Documentation components</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a0735-122">既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップ時にサンプル データベースとサンプル コードはインストールされません。</span><span class="sxs-lookup"><span data-stu-id="a0735-122">By default, sample databases and sample code are not installed as part of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span> <span data-ttu-id="a0735-123">サンプル データベースとサンプル コードをインストールする場合は、 [CodePlex Web サイト](https://go.microsoft.com/fwlink/?LinkId=87843)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0735-123">To install sample databases and sample code, see the [CodePlex Web site](https://go.microsoft.com/fwlink/?LinkId=87843).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0735-124">参照</span><span class="sxs-lookup"><span data-stu-id="a0735-124">See Also</span></span>  
 <span data-ttu-id="a0735-125">[SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="a0735-125">[Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span></span>  
 <span data-ttu-id="a0735-126">[SQL Server 2014 のエディションとコンポーネント](../../sql-server/editions-and-components-of-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="a0735-126">[Editions and Components of SQL Server 2014](../../sql-server/editions-and-components-of-sql-server-2016.md) </span></span>  
 <span data-ttu-id="a0735-127">[SQL Server のインストール計画](../../sql-server/install/planning-a-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="a0735-127">[Planning a SQL Server Installation](../../sql-server/install/planning-a-sql-server-installation.md) </span></span>  
 <span data-ttu-id="a0735-128">[高可用性ソリューション &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a0735-128">[High Availability Solutions &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md) </span></span>  
 [<span data-ttu-id="a0735-129">インストールウィザード &#40;セットアップを使用して SQL Server 2014 にアップグレード&#41;</span><span class="sxs-lookup"><span data-stu-id="a0735-129">Upgrade to SQL Server 2014 Using the Installation Wizard &#40;Setup&#41;</span></span>](upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  
