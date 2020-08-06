---
title: Server Core に SQL Server 2014 をインストールする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 1dd294cc-5b69-4d0c-9005-3e307b75678b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d2614c43bb763757db7db46b1c7a966221da96f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713465"
---
# <a name="install-sql-server-2014-on-server-core"></a><span data-ttu-id="d772d-102">Server Core への SQL Server 2014 のインストール</span><span class="sxs-lookup"><span data-stu-id="d772d-102">Install SQL Server 2014 on Server Core</span></span>
  <span data-ttu-id="d772d-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 または [!INCLUDE[win8srv](../../includes/win8srv-md.md)]の Server Core インストールにインストールできます。</span><span class="sxs-lookup"><span data-stu-id="d772d-103">You can install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span> <span data-ttu-id="d772d-104">このトピックでは、Server Core に [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] をインストールする場合のセットアップに固有の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="d772d-104">This topic provides setup-specific details for installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on Server Core.</span></span>  
  
 <span data-ttu-id="d772d-105">[!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] または [!INCLUDE[win8srv](../../includes/win8srv-md.md)] オペレーティング システムの Server Core インストール オプションでは、特定のサーバー ロールを実行するための最低限の環境が提供されます。</span><span class="sxs-lookup"><span data-stu-id="d772d-105">The Server Core installation option for the [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] or [!INCLUDE[win8srv](../../includes/win8srv-md.md)] operating system provides a minimal environment for running specific server roles.</span></span> <span data-ttu-id="d772d-106">これにより、必要な保守と管理が減り、これらのサーバー ロールに対する攻撃の危険性が軽減されます。</span><span class="sxs-lookup"><span data-stu-id="d772d-106">This helps to reduce maintenance and management requirements and the attack surface for those server roles.</span></span> <span data-ttu-id="d772d-107">に実装された Server Core の詳細について [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] は、「 [Windows Server 2008 R2 の server core](https://go.microsoft.com/fwlink/?LinkId=202439) 」 (を参照してください https://go.microsoft.com/fwlink/?LinkId=202439) 。</span><span class="sxs-lookup"><span data-stu-id="d772d-107">For more information on Server Core as implemented on [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)], see [Server Core for Windows Server 2008 R2](https://go.microsoft.com/fwlink/?LinkId=202439) (https://go.microsoft.com/fwlink/?LinkId=202439).</span></span> <span data-ttu-id="d772d-108">[!INCLUDE[win8srv](../../includes/win8srv-md.md)] に実装された Server Core の詳細については、[Windows Server 2012 の Server Core](https://msdn.microsoft.com/library/hh846323\(VS.85\).aspx) に関するページ (https://msdn.microsoft.com/library/hh846323(VS.85).aspx) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d772d-108">For more information on Server Core as implemented on [!INCLUDE[win8srv](../../includes/win8srv-md.md)], see [Server Core for Windows Server 2012](https://msdn.microsoft.com/library/hh846323\(VS.85\).aspx) (https://msdn.microsoft.com/library/hh846323(VS.85).aspx).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d772d-109">前提条件</span><span class="sxs-lookup"><span data-stu-id="d772d-109">Prerequisites</span></span>  
  
|<span data-ttu-id="d772d-110">要件</span><span class="sxs-lookup"><span data-stu-id="d772d-110">Requirement</span></span>|<span data-ttu-id="d772d-111">インストール方法</span><span class="sxs-lookup"><span data-stu-id="d772d-111">How to install</span></span>|  
|-----------------|--------------------|  
|[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <span data-ttu-id="d772d-112">2.0 SP2</span><span class="sxs-lookup"><span data-stu-id="d772d-112">2.0 SP2</span></span>|<span data-ttu-id="d772d-113">[!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 および [!INCLUDE[win8srv](../../includes/win8srv-md.md)]の Server Core インストールに含まれています。</span><span class="sxs-lookup"><span data-stu-id="d772d-113">Included in Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 and [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span> <span data-ttu-id="d772d-114">有効になっていない場合、セットアップにおいて既定で有効になります。</span><span class="sxs-lookup"><span data-stu-id="d772d-114">If it is not enabled, Setup enables it by default.</span></span><br /><br /> <span data-ttu-id="d772d-115">コンピューター上で Version 2.0、3.0、および 3.5 を同時に実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="d772d-115">It is not possible to run versions 2.0, 3.0, and 3.5 side by side on a computer.</span></span> <span data-ttu-id="d772d-116">.NET Framework 3.5 SP1 をインストールすると、2.0 と 3.0 のレイヤーが自動的に取得されます。</span><span class="sxs-lookup"><span data-stu-id="d772d-116">When you install the .NET Framework 3.5 SP1, you get the 2.0 and 3.0 layers automatically.</span></span>|  
|[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <span data-ttu-id="d772d-117">3.5 SP1 Full Profile</span><span class="sxs-lookup"><span data-stu-id="d772d-117">3.5 SP1 Full Profile</span></span>|<span data-ttu-id="d772d-118">[!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 の Server Core インストールに含まれています。</span><span class="sxs-lookup"><span data-stu-id="d772d-118">Included in Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1.</span></span> <span data-ttu-id="d772d-119">有効になっていない場合、セットアップにおいて既定で有効になります。</span><span class="sxs-lookup"><span data-stu-id="d772d-119">If it is not enabled, Setup enables it by default.</span></span><br /><br /> <span data-ttu-id="d772d-120">Windows サーバー オペレーティング システム搭載のコンピューターで、.NET 3.5 SP1 に依存するコンポーネントをインストールするには、セットアップを実行する前に .NET Framework 3.5 SP1 をダウンロードしてインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d772d-120">On a computer with Windows server operating system you must download and install .NET Framework 3.5 SP1 before you run Setup, to install components dependent on .NET 3.5 SP1.</span></span><br /><br /> <span data-ttu-id="d772d-121">で .NET Framework 3.5 を取得して有効にする方法に関する推奨事項とガイダンスの詳細については [!INCLUDE[win8srv](../../includes/win8srv-md.md)] 、「 [Microsoft .NET Framework 3.5 の展開に関する考慮事項](https://msdn.microsoft.com/library/windows/hardware/hh975396)」 (を参照してください https://msdn.microsoft.com/library/windows/hardware/hh975396) 。</span><span class="sxs-lookup"><span data-stu-id="d772d-121">For more information about the recommendations and guidance on how to acquire and enable .NET Framework 3.5 in [!INCLUDE[win8srv](../../includes/win8srv-md.md)], see [Microsoft .NET Framework 3.5 Deployment Considerations](https://msdn.microsoft.com/library/windows/hardware/hh975396) (https://msdn.microsoft.com/library/windows/hardware/hh975396).</span></span>|  
|[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <span data-ttu-id="d772d-122">4 Server Core Profile</span><span class="sxs-lookup"><span data-stu-id="d772d-122">4 Server Core Profile</span></span>|<span data-ttu-id="d772d-123">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を除く [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]のすべてのエディションのセットアップで、 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4 Server Core Profile が前提条件としてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="d772d-123">For all editions of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] except [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], Setup installs the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4 Server Core Profile as a prerequisite.</span></span><br /><br /> <span data-ttu-id="d772d-124">の場合は [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)] 、 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4 Server core プロファイルを[server core 用の Microsoft .NET Framework 4 (スタンドアロンインストーラー)](https://www.microsoft.com/download/details.aspx?id=17718)からダウンロード https://www.microsoft.com/download/details.aspx?id=17718) し、セットアップを続行する前にインストールします。</span><span class="sxs-lookup"><span data-stu-id="d772d-124">For [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)], download the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4 Server Core Profile from [Microsoft .NET Framework 4 (Standalone Installer) for Server Core](https://www.microsoft.com/download/details.aspx?id=17718) (https://www.microsoft.com/download/details.aspx?id=17718), and install it before you proceed with the setup.</span></span>|  
|<span data-ttu-id="d772d-125">Windows インストーラー 4.5</span><span class="sxs-lookup"><span data-stu-id="d772d-125">Windows Installer 4.5</span></span>|<span data-ttu-id="d772d-126">[!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 および [!INCLUDE[win8srv](../../includes/win8srv-md.md)]の Server Core インストールに付属します。</span><span class="sxs-lookup"><span data-stu-id="d772d-126">Shipped with Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 and [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span>|  
|<span data-ttu-id="d772d-127">Windows PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="d772d-127">Windows PowerShell 2.0</span></span>|<span data-ttu-id="d772d-128">[!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 および [!INCLUDE[win8srv](../../includes/win8srv-md.md)]の Server Core インストールに付属します。</span><span class="sxs-lookup"><span data-stu-id="d772d-128">Shipped with Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 and [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span>|  
  
##  <a name="supported-features"></a><a name="BK_SupportedFeatures"></a> <span data-ttu-id="d772d-129">サポートされている機能</span><span class="sxs-lookup"><span data-stu-id="d772d-129">Supported Features</span></span>  
 <span data-ttu-id="d772d-130">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SP1 および [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] の Server Core インストールの [!INCLUDE[win8srv](../../includes/win8srv-md.md)]でサポートされている機能については、次の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d772d-130">Use the following table to find which features are supported in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on a Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 and [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span>  
  
|<span data-ttu-id="d772d-131">特徴量</span><span class="sxs-lookup"><span data-stu-id="d772d-131">Feature</span></span>|<span data-ttu-id="d772d-132">サポートされています</span><span class="sxs-lookup"><span data-stu-id="d772d-132">Supported</span></span>|  
|-------------|---------------|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="d772d-133">サービス</span><span class="sxs-lookup"><span data-stu-id="d772d-133">Services</span></span>|<span data-ttu-id="d772d-134">はい</span><span class="sxs-lookup"><span data-stu-id="d772d-134">Yes</span></span>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d772d-135">レプリケーション</span><span class="sxs-lookup"><span data-stu-id="d772d-135">Replication</span></span>|<span data-ttu-id="d772d-136">はい</span><span class="sxs-lookup"><span data-stu-id="d772d-136">Yes</span></span>|  
|<span data-ttu-id="d772d-137">フルテキスト検索</span><span class="sxs-lookup"><span data-stu-id="d772d-137">Full Text Search</span></span>|<span data-ttu-id="d772d-138">はい</span><span class="sxs-lookup"><span data-stu-id="d772d-138">Yes</span></span>|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|<span data-ttu-id="d772d-139">はい</span><span class="sxs-lookup"><span data-stu-id="d772d-139">Yes</span></span>|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|<span data-ttu-id="d772d-140">いいえ</span><span class="sxs-lookup"><span data-stu-id="d772d-140">No</span></span>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d772d-141">Data Tools (SSDT)</span><span class="sxs-lookup"><span data-stu-id="d772d-141">Data Tools (SSDT)</span></span>|<span data-ttu-id="d772d-142">いいえ</span><span class="sxs-lookup"><span data-stu-id="d772d-142">No</span></span>|  
|<span data-ttu-id="d772d-143">クライアント ツール接続</span><span class="sxs-lookup"><span data-stu-id="d772d-143">Client Tools Connectivity</span></span>|<span data-ttu-id="d772d-144">はい</span><span class="sxs-lookup"><span data-stu-id="d772d-144">Yes</span></span>|  
|<span data-ttu-id="d772d-145">Integration Services サーバー<sup>[1]</sup></span><span class="sxs-lookup"><span data-stu-id="d772d-145">Integration Services Server<sup>[1]</sup></span></span>|<span data-ttu-id="d772d-146">はい</span><span class="sxs-lookup"><span data-stu-id="d772d-146">Yes</span></span>|  
|<span data-ttu-id="d772d-147">クライアント ツールの旧バージョンとの互換性</span><span class="sxs-lookup"><span data-stu-id="d772d-147">Client Tools Backward Compatibility</span></span>|<span data-ttu-id="d772d-148">いいえ</span><span class="sxs-lookup"><span data-stu-id="d772d-148">No</span></span>|  
|<span data-ttu-id="d772d-149">クライアント ツール SDK</span><span class="sxs-lookup"><span data-stu-id="d772d-149">Client Tools SDK</span></span>|<span data-ttu-id="d772d-150">いいえ</span><span class="sxs-lookup"><span data-stu-id="d772d-150">No</span></span>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d772d-151">オンライン ブック</span><span class="sxs-lookup"><span data-stu-id="d772d-151">Books Online</span></span>|<span data-ttu-id="d772d-152">いいえ</span><span class="sxs-lookup"><span data-stu-id="d772d-152">No</span></span>|  
|<span data-ttu-id="d772d-153">管理ツール - 基本</span><span class="sxs-lookup"><span data-stu-id="d772d-153">Management Tools - Basic</span></span>|<span data-ttu-id="d772d-154">リモートのみ<sup>[2]</sup></span><span class="sxs-lookup"><span data-stu-id="d772d-154">Remote Only<sup>[2]</sup></span></span>|  
|<span data-ttu-id="d772d-155">管理ツール - 完全</span><span class="sxs-lookup"><span data-stu-id="d772d-155">Management Tools - Complete</span></span>|<span data-ttu-id="d772d-156">リモートのみ<sup>[2]</sup></span><span class="sxs-lookup"><span data-stu-id="d772d-156">Remote Only<sup>[2]</sup></span></span>|  
|<span data-ttu-id="d772d-157">分散再生コントローラー</span><span class="sxs-lookup"><span data-stu-id="d772d-157">Distributed Replay Controller</span></span>|<span data-ttu-id="d772d-158">いいえ</span><span class="sxs-lookup"><span data-stu-id="d772d-158">No</span></span>|  
|<span data-ttu-id="d772d-159">分散再生クライアント</span><span class="sxs-lookup"><span data-stu-id="d772d-159">Distributed Replay Client</span></span>|<span data-ttu-id="d772d-160">リモートのみ<sup>[2]</sup></span><span class="sxs-lookup"><span data-stu-id="d772d-160">Remote Only<sup>[2]</sup></span></span>|  
|<span data-ttu-id="d772d-161">SQL クライアント接続 SDK</span><span class="sxs-lookup"><span data-stu-id="d772d-161">SQL Client Connectivity SDK</span></span>|<span data-ttu-id="d772d-162">はい</span><span class="sxs-lookup"><span data-stu-id="d772d-162">Yes</span></span>|  
|<span data-ttu-id="d772d-163">Microsoft Sync Framework</span><span class="sxs-lookup"><span data-stu-id="d772d-163">Microsoft Sync Framework</span></span>|<span data-ttu-id="d772d-164">はい<sup>[3]</sup></span><span class="sxs-lookup"><span data-stu-id="d772d-164">Yes<sup>[3]</sup></span></span>|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]|<span data-ttu-id="d772d-165">いいえ</span><span class="sxs-lookup"><span data-stu-id="d772d-165">No</span></span>|  
|[!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]|<span data-ttu-id="d772d-166">いいえ</span><span class="sxs-lookup"><span data-stu-id="d772d-166">No</span></span>|  
  
 <span data-ttu-id="d772d-167"><sup>[1]</sup>の新しい Integration Services サーバーとその機能の詳細については [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、「 [SSIS&#41; サーバー &#40;Integration Services](../../integration-services/catalog/integration-services-ssis-server-and-catalog.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d772d-167"><sup>[1]</sup>For more information about the new Integration Services Server and its features in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], see [Integration Services &#40;SSIS&#41; Server](../../integration-services/catalog/integration-services-ssis-server-and-catalog.md).</span></span>  
  
 <span data-ttu-id="d772d-168"><sup>[2]</sup>Server Core へのこれらの機能のインストールはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d772d-168"><sup>[2]</sup>Installation of these features on Server Core is not supported.</span></span> <span data-ttu-id="d772d-169">これらのコンポーネントは、 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 または [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core ではない別のサーバーにインストールし、Server Core にインストールされている [!INCLUDE[ssDE](../../includes/ssde-md.md)] サービスに接続できます。</span><span class="sxs-lookup"><span data-stu-id="d772d-169">These components can be installed on a different server that is not [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core, and connected to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] services installed on Server Core.</span></span>  
  
 <span data-ttu-id="d772d-170"><sup>[3]</sup>Microsoft Sync Framework は、インストールパッケージに含まれていません [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d772d-170"><sup>[3]</sup>Microsoft Sync Framework is not included in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installation package.</span></span> <span data-ttu-id="d772d-171">適切なバージョンの Sync Framework は、この[Microsoft ダウンロードセンター](https://go.microsoft.com/fwlink/?LinkId=221788) (ページからダウンロード https://go.microsoft.com/fwlink/?LinkId=221788) して、SP1 またはの Server Core インストールを実行しているコンピューターにインストールでき [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] [!INCLUDE[win8srv](../../includes/win8srv-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="d772d-171">You can download the appropriate version of Sync Framework from this [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=221788) (https://go.microsoft.com/fwlink/?LinkId=221788) page and install it on a computer that is running Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span>  
  
## <a name="supported-scenario-matrix"></a><span data-ttu-id="d772d-172">サポートされるシナリオのマトリックス</span><span class="sxs-lookup"><span data-stu-id="d772d-172">Supported Scenario Matrix</span></span>  
 <span data-ttu-id="d772d-173">次の表では、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SP1 および [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] の Server Core インストールに [!INCLUDE[win8srv](../../includes/win8srv-md.md)]をインストールする場合のサポートされるシナリオのマトリックスを示します。</span><span class="sxs-lookup"><span data-stu-id="d772d-173">The following table shows the supported scenario matrix for installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on a Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 and [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span>  
  
|||  
|-|-|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d772d-174">のエディション</span><span class="sxs-lookup"><span data-stu-id="d772d-174">editions</span></span>|<span data-ttu-id="d772d-175">すべて [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の 64-bit エディション<sup>[1]</sup></span><span class="sxs-lookup"><span data-stu-id="d772d-175">All [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 64-bit editions<sup>[1]</sup></span></span>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d772d-176">の言語</span><span class="sxs-lookup"><span data-stu-id="d772d-176">language</span></span>|<span data-ttu-id="d772d-177">すべての言語</span><span class="sxs-lookup"><span data-stu-id="d772d-177">All languages</span></span>|  
|<span data-ttu-id="d772d-178">OS の言語とロケール (組み合わせ) での[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の言語</span><span class="sxs-lookup"><span data-stu-id="d772d-178">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] language on OS language/locale (combination)</span></span>|<span data-ttu-id="d772d-179">JPN (日本語) Windows への ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d772d-179">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on JPN (Japanese) Windows</span></span><br /><br /> <span data-ttu-id="d772d-180">GER (ドイツ語) Windows への ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d772d-180">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on GER (German) Windows</span></span><br /><br /> <span data-ttu-id="d772d-181">CHS (中国語 - 中国) Windows への ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d772d-181">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on CHS (Chinese-China) Windows</span></span><br /><br /> <span data-ttu-id="d772d-182">ARA (アラビア語 (SA)) Windows への ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d772d-182">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on ARA (Arabic (SA)) Windows</span></span><br /><br /> <span data-ttu-id="d772d-183">THA (タイ語) Windows への ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d772d-183">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on THA (Thai) Windows</span></span><br /><br /> <span data-ttu-id="d772d-184">TRK (トルコ語) Windows への ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d772d-184">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on TRK (Turkish) Windows</span></span><br /><br /> <span data-ttu-id="d772d-185">pt-PT (ポルトガル語 - ポルトガル) Windows への ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d772d-185">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on pt-PT (Portuguese Portugal) Windows</span></span><br /><br /> <span data-ttu-id="d772d-186">ENG (英語) Windows への ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d772d-186">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on ENG (English) Windows</span></span>|  
|<span data-ttu-id="d772d-187">Windows のエディション</span><span class="sxs-lookup"><span data-stu-id="d772d-187">Windows edition</span></span>|[!INCLUDE[win8srv](../../includes/win8srv-md.md)] <span data-ttu-id="d772d-188">64 ビット x64 Datacenter</span><span class="sxs-lookup"><span data-stu-id="d772d-188">64-bit x64 Datacenter</span></span><br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)] <span data-ttu-id="d772d-189">64 ビット x64 Standard</span><span class="sxs-lookup"><span data-stu-id="d772d-189">64-bit x64 Standard</span></span><br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] <span data-ttu-id="d772d-190">SP1 64 ビット x64 Data Center Server Core</span><span class="sxs-lookup"><span data-stu-id="d772d-190">SP1 64-bit x64 Data Center Server Core</span></span><br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] <span data-ttu-id="d772d-191">SP1 64 ビット x64 Enterprise Server Core</span><span class="sxs-lookup"><span data-stu-id="d772d-191">SP1 64-bit x64 Enterprise Server Core</span></span><br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] <span data-ttu-id="d772d-192">SP1 64 ビット x64 Standard Server Core</span><span class="sxs-lookup"><span data-stu-id="d772d-192">SP1 64-bit x64 Standard Server Core</span></span><br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] <span data-ttu-id="d772d-193">SP1 64 ビット x64 Web Server Core</span><span class="sxs-lookup"><span data-stu-id="d772d-193">SP1 64-bit x64 Web Server Core</span></span>|  
  
 <span data-ttu-id="d772d-194"><sup>[1]</sup>32ビットバージョンのエディションのインストール [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、Server Core ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d772d-194"><sup>[1]</sup>Installing the 32-bit version of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] editions is not supported on Server Core.</span></span>  
  
## <a name="upgrading"></a><span data-ttu-id="d772d-195">アップグレード中</span><span class="sxs-lookup"><span data-stu-id="d772d-195">Upgrading</span></span>  
 <span data-ttu-id="d772d-196">Server Core インストールでは、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] へのアップグレードがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d772d-196">On Server Core installations, upgrading from [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] to [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] is supported.</span></span>  
  
## <a name="installation"></a><span data-ttu-id="d772d-197">インストール</span><span class="sxs-lookup"><span data-stu-id="d772d-197">Installation</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="d772d-198">では、Server Core オペレーティング システムでのインストール ウィザードを使用したセットアップはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d772d-198">does not support setup by using the installation wizard on the Server Core operating system.</span></span> <span data-ttu-id="d772d-199">Server Core にインストールする場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップでは、/Q パラメーターを使用した非表示モード、または /QS パラメーターを使用した簡易非表示モードがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="d772d-199">When installing on Server Core, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup supports full quiet mode by using the /Q parameter, or Quiet Simple mode by using the /QS parameter.</span></span> <span data-ttu-id="d772d-200">詳細については、「[コマンド プロンプトからの SQL Server 2014 のインストール](install-sql-server-from-the-command-prompt.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d772d-200">For more information, see [Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md).</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="d772d-201">は、[!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 または [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core を実行しているコンピューターに、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] とサイド バイ サイドでインストールすることはできません。</span><span class="sxs-lookup"><span data-stu-id="d772d-201">cannot be installed side-by-side with earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a computer that is running [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core.</span></span>  
  
 <span data-ttu-id="d772d-202">どのインストール方法を使用するかにかかわらず、個人として、または組織を代表して、ソフトウェア ライセンス条項に同意するかどうかを確認する必要があります。ただし、ソフトウェアの使用に別の契約 ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] ボリューム ライセンス契約、ISV や OEM とのサード パーティ契約など) が適用される場合を除きます。</span><span class="sxs-lookup"><span data-stu-id="d772d-202">Regardless of the installation method, you are required to confirm acceptance of the software license terms as an individual or on behalf of an entity, unless your use of the software is governed by a separate agreement such as a [!INCLUDE[msCoName](../../includes/msconame-md.md)] volume licensing agreement or a third-party agreement with an ISV or OEM.</span></span>  
  
 <span data-ttu-id="d772d-203">ライセンス条項は、セットアップのユーザー インターフェイスで確認し、同意することができます。</span><span class="sxs-lookup"><span data-stu-id="d772d-203">The license terms are displayed for review and acceptance in the Setup user interface.</span></span> <span data-ttu-id="d772d-204">/Q または /QS パラメーターを使用した自動インストールでは、/IACCEPTSQLSERVERLICENSETERMS パラメーターを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d772d-204">Unattended installations (using the /Q or /QS parameters) must include the /IACCEPTSQLSERVERLICENSETERMS parameter.</span></span> <span data-ttu-id="d772d-205">ライセンス条項は、「 [マイクロソフト ソフトウェア ライセンス条項](https://go.microsoft.com/fwlink/?LinkId=148209)」で別途確認できます。</span><span class="sxs-lookup"><span data-stu-id="d772d-205">You can review the license terms separately at [Microsoft Software License Terms](https://go.microsoft.com/fwlink/?LinkId=148209).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d772d-206">ソフトウェアの入手方法 ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] のボリューム ライセンスを通じて入手した場合など) によっては、ソフトウェアの使用に追加の条件が課されることがあります。</span><span class="sxs-lookup"><span data-stu-id="d772d-206">Depending on how you received the software (for example, through [!INCLUDE[msCoName](../../includes/msconame-md.md)] volume licensing), your use of the software may be subject to additional terms and conditions.</span></span>  
  
 <span data-ttu-id="d772d-207">特定の機能をインストールするには、/FEATURES パラメーターを使用して、親機能の値または機能の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="d772d-207">To install specific features, use the /FEATURES parameter and specify the parent feature or feature values.</span></span> <span data-ttu-id="d772d-208">機能パラメーターとその使用の詳細については、次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d772d-208">For more information about feature parameters and their use, see the following sections.</span></span>  
  
### <a name="feature-parameters"></a><span data-ttu-id="d772d-209">機能パラメーター</span><span class="sxs-lookup"><span data-stu-id="d772d-209">Feature Parameters</span></span>  
  
|<span data-ttu-id="d772d-210">機能パラメーター</span><span class="sxs-lookup"><span data-stu-id="d772d-210">Feature parameter</span></span>|<span data-ttu-id="d772d-211">説明</span><span class="sxs-lookup"><span data-stu-id="d772d-211">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="d772d-212">SQLENGINE</span><span class="sxs-lookup"><span data-stu-id="d772d-212">SQLENGINE</span></span>|<span data-ttu-id="d772d-213">[!INCLUDE[ssDE](../../includes/ssde-md.md)]のみをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d772d-213">Installs only the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>|  
|<span data-ttu-id="d772d-214">レプリケーション</span><span class="sxs-lookup"><span data-stu-id="d772d-214">REPLICATION</span></span>|<span data-ttu-id="d772d-215">[!INCLUDE[ssDE](../../includes/ssde-md.md)]と共にレプリケーション コンポーネントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d772d-215">Installs the Replication component along with [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>|  
|<span data-ttu-id="d772d-216">FULLTEXT</span><span class="sxs-lookup"><span data-stu-id="d772d-216">FULLTEXT</span></span>|<span data-ttu-id="d772d-217">[!INCLUDE[ssDE](../../includes/ssde-md.md)]と共にフルテキスト コンポーネントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d772d-217">Installs the FullText component along with [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>|  
|<span data-ttu-id="d772d-218">AS</span><span class="sxs-lookup"><span data-stu-id="d772d-218">AS</span></span>|<span data-ttu-id="d772d-219">すべての [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] コンポーネントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d772d-219">Installs all [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] components.</span></span>|  
|<span data-ttu-id="d772d-220">IS</span><span class="sxs-lookup"><span data-stu-id="d772d-220">IS</span></span>|<span data-ttu-id="d772d-221">すべての [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] コンポーネントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d772d-221">Installs all [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components.</span></span>|  
|<span data-ttu-id="d772d-222">CONN</span><span class="sxs-lookup"><span data-stu-id="d772d-222">CONN</span></span>|<span data-ttu-id="d772d-223">接続コンポーネントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d772d-223">Installs the connectivity components.</span></span>|  
  
 <span data-ttu-id="d772d-224">機能パラメーターの使い方の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d772d-224">See the following examples of the usage of feature parameters:</span></span>  
  
|<span data-ttu-id="d772d-225">パラメーターおよび値</span><span class="sxs-lookup"><span data-stu-id="d772d-225">Parameter and values</span></span>|<span data-ttu-id="d772d-226">説明</span><span class="sxs-lookup"><span data-stu-id="d772d-226">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="d772d-227">/FEATURES=SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d772d-227">/FEATURES=SQLEngine</span></span>|<span data-ttu-id="d772d-228">[!INCLUDE[ssDE](../../includes/ssde-md.md)]のみをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d772d-228">Installs only the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>|  
|<span data-ttu-id="d772d-229">/FEATURES=SQLEngine,FullText</span><span class="sxs-lookup"><span data-stu-id="d772d-229">/FEATURES=SQLEngine,FullText</span></span>|<span data-ttu-id="d772d-230">[!INCLUDE[ssDE](../../includes/ssde-md.md)] とフルテキストをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d772d-230">Installs the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and full-text.</span></span>|  
|<span data-ttu-id="d772d-231">/FEATURES=SQLEngine,Conn</span><span class="sxs-lookup"><span data-stu-id="d772d-231">/FEATURES=SQLEngine,Conn</span></span>|<span data-ttu-id="d772d-232">[!INCLUDE[ssDE](../../includes/ssde-md.md)] および接続コンポーネントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d772d-232">Installs the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and the connectivity components.</span></span>|  
|<span data-ttu-id="d772d-233">/FEATURES=SQLEngine,AS,IS,Conn</span><span class="sxs-lookup"><span data-stu-id="d772d-233">/FEATURES=SQLEngine,AS,IS,Conn</span></span>|<span data-ttu-id="d772d-234">[!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、および接続コンポーネントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d772d-234">Installs the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], and the connectivity components.</span></span>|  
  
### <a name="installation-options"></a><span data-ttu-id="d772d-235">インストール オプション</span><span class="sxs-lookup"><span data-stu-id="d772d-235">Installation Options</span></span>  
 <span data-ttu-id="d772d-236">Server Core オペレーティング システムへの [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインストール中に、セットアップで次のインストール オプションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="d772d-236">The Setup supports the following installation options while installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on a Server Core operating system:</span></span>  
  
1.  <span data-ttu-id="d772d-237">**コマンド ラインからのインストール**</span><span class="sxs-lookup"><span data-stu-id="d772d-237">**Installation from Command Line**</span></span>  
  
     <span data-ttu-id="d772d-238">コマンド プロンプトのインストール オプションを使用して特定の機能をインストールするには、/FEATURES パラメーターを使用して、親機能の値または機能の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="d772d-238">To install specific features using the command prompt installation option, use the /FEATURES parameter and specify the parent feature or feature values.</span></span> <span data-ttu-id="d772d-239">コマンド ラインからパラメーターを使用する方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d772d-239">The following is an example of using the parameters from the command line:</span></span>  
  
    ```cmd
    setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,Replication /INSTANCENAME=MSSQLSERVER /SQLSVCACCOUNT="<DomainName\UserName>" /SQLSVCPASSWORD="<StrongPassword>" /SQLSYSADMINACCOUNTS="<DomainName\UserName>" /AGTSVCACCOUNT="NT AUTHORITY\Network Service" /TCPENABLED=1 /IACCEPTSQLSERVERLICENSETERMS  
    ```  
  
2.  <span data-ttu-id="d772d-240">**構成ファイルを使用したインストール**</span><span class="sxs-lookup"><span data-stu-id="d772d-240">**Installation using Configuration File**</span></span>  
  
     <span data-ttu-id="d772d-241">セットアップでは、コマンド プロンプトからのみ構成ファイルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d772d-241">Setup supports the use of the configuration file only through the command prompt.</span></span> <span data-ttu-id="d772d-242">構成ファイルは、パラメーター (名前と値のペア) と説明のコメントの基本構造を持つテキスト ファイルです。</span><span class="sxs-lookup"><span data-stu-id="d772d-242">The configuration file is a text file with the basic structure of a parameter (name/value pair) and a descriptive comment.</span></span> <span data-ttu-id="d772d-243">コマンド プロンプトで指定した構成ファイルには、.INI のファイル名拡張子が必要です。</span><span class="sxs-lookup"><span data-stu-id="d772d-243">The configuration file specified at the command prompt should have an .INI file name extension.</span></span> <span data-ttu-id="d772d-244">次の例の ConfigurationFile.INI を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d772d-244">See the following examples of ConfigurationFile.INI:</span></span>  
  
    -   <span data-ttu-id="d772d-245">[!INCLUDE[ssDE](../../includes/ssde-md.md)] をインストールする</span><span class="sxs-lookup"><span data-stu-id="d772d-245">Installing [!INCLUDE[ssDE](../../includes/ssde-md.md)]</span></span>  
  
         <span data-ttu-id="d772d-246">次の例では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)]を含む新しいスタンドアロン インスタンスをインストールする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d772d-246">The following example shows how to install a new stand-alone instance that includes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)]:</span></span>  
  
        ```  
        ; ssNoVersion Configuration File  
        [OPTIONS]  
  
        ; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE. This is a required parameter.   
  
        ACTION="Install"  
  
        ; Specifies features to install, uninstall, or upgrade. The lists of features include SQLEngine, FullText, Replication, AS, IS, and Conn.   
  
        FEATURES=SQLENGINE  
  
        ; Specify a default or named instance. MSSQLSERVER is the default instance for non-Express editions and SQLExpress for Express editions. This parameter is required when installing the ssNoVersion Database Engine, and Analysis Services (AS).  
  
        INSTANCENAME="MSSQLSERVER"  
  
        ; Specify the Instance ID for the ssNoVersion features you have specified. ssNoVersion directory structure, registry structure, and service names will incorporate the instance ID of the ssNoVersion instance.   
  
        INSTANCEID="MSSQLSERVER"  
  
        ; Account for ssNoVersion service: Domain\User or system account.   
  
        SQLSVCACCOUNT="NT Service\MSSQLSERVER"  
  
        ; Windows account(s) to provision as ssNoVersion system administrators.   
  
        SQLSYSADMINACCOUNTS="<DomainName\UserName>"  
  
        ; Accept the License agreement to continue with Installation  
  
        IAcceptSQLServerLicenseTerms="True"
        ```  
  
    -   <span data-ttu-id="d772d-247">接続コンポーネントのインストール</span><span class="sxs-lookup"><span data-stu-id="d772d-247">Installing connectivity components</span></span>  
  
         <span data-ttu-id="d772d-248">次の例では、接続コンポーネントをインストールする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d772d-248">The following example shows how to install the connectivity components:</span></span>  
  
        ```  
        ; ssNoVersion Configuration File  
        [OPTIONS]  
  
        ; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE. This is a required parameter.   
  
        ACTION="Install"  
  
        ; Specifies features to install, uninstall, or upgrade. The lists of features include SQLEngine, FullText, Replication, AS, IS, and Conn.   
  
        FEATURES=Conn  
  
        ; Specifies acceptance of License Terms  
  
        IAcceptSQLServerLicenseTerms="True
        ```  
  
    -   <span data-ttu-id="d772d-249">サポートされるすべての機能のインストール</span><span class="sxs-lookup"><span data-stu-id="d772d-249">Installing all supported features</span></span>  
  
         <span data-ttu-id="d772d-250">次の例では、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のサポートされる全機能を Server Core にインストールする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d772d-250">The following example shows how to install all supported features of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on Server Core:</span></span>  
  
        ```  
        ; ssNoVersion Configuration File  
        [OPTIONS]  
        ; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE. This is a required parameter.   
  
        ACTION="Install"  
  
        ; Specifies features to install, uninstall, or upgrade. The lists of features include SQLEngine, FullText, Replication, AS, IS, and Conn.   
  
        FEATURES=SQLENGINE,FullText,Replication,AS,IS,Conn  
  
        ; Specify a default or named instance. MSSQLSERVER is the default instance for non-Express editions and SQLExpress for Express editions. This parameter is required when installing the ssNoVersion Database Engine (SQL), or Analysis Services (AS).  
  
        INSTANCENAME="MSSQLSERVER"  
  
        ; Specify the Instance ID for the ssNoVersion features you have specified. ssNoVersion directory structure, registry structure, and service names will incorporate the instance ID of the ssNoVersion instance.   
  
        INSTANCEID="MSSQLSERVER"  
  
        ; Account for ssNoVersion service: Domain\User or system account.   
  
        SQLSVCACCOUNT="NT Service\MSSQLSERVER"  
  
        ; Windows account(s) to provision as ssNoVersion system administrators.   
  
        SQLSYSADMINACCOUNTS="<DomainName\UserName>"  
  
        ; The name of the account that the Analysis Services service runs under.   
  
        ASSVCACCOUNT= "NT Service\MSSQLServerOLAPService"  
  
        ; Specifies the list of administrator accounts that need to be provisioned.   
  
        ASSYSADMINACCOUNTS="<DomainName\UserName>"  
  
        ; Specifies the server mode of the Analysis Services instance. Valid values are MULTIDIMENSIONAL, POWERPIVOT or TABULAR. ASSERVERMODE is case-sensitive. All values must be expressed in upper case.   
  
        ASSERVERMODE="MULTIDIMENSIONAL"  
  
        ; Optional value, which specifies the state of the TCP protocol for the ssNoVersion service. Supported values are: 0 to disable the TCP protocol, and 1 to enable the TCP protocol.  
  
        TCPENABLED=1  
  
        ;Specifies acceptance of License Terms  
  
        IAcceptSQLServerLicenseTerms="True"  
        ```  
  
     <span data-ttu-id="d772d-251">次の例では、構成ファイルを使用してセットアップを起動する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d772d-251">The following examples show how you can launch the Setup using a configuration file.</span></span>  
  
    -   <span data-ttu-id="d772d-252">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="d772d-252">Configuration file</span></span>  
  
         <span data-ttu-id="d772d-253">次に、構成ファイルの使用方法の例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="d772d-253">Following are some examples of how to use the configuration file:</span></span>  
  
        -   <span data-ttu-id="d772d-254">コマンド プロンプトで構成ファイルを指定するには</span><span class="sxs-lookup"><span data-stu-id="d772d-254">To specify the configuration file at the command prompt:</span></span>  
  
        ```cmd
        setup.exe /QS /ConfigurationFile=MyConfigurationFile.INI  
        ```  
  
        -   <span data-ttu-id="d772d-255">構成ファイルの代わりにコマンド プロンプトでパスワードを指定するには</span><span class="sxs-lookup"><span data-stu-id="d772d-255">To specify passwords at the command prompt instead of in the configuration file:</span></span>  
  
        ```cmd
        setup.exe /QS /SQLSVCPASSWORD="************" /ASSVCPASSWORD="************"  /ConfigurationFile=MyConfigurationFile.INI  
        ```  
  
    -   <span data-ttu-id="d772d-256">DefaultSetup.ini</span><span class="sxs-lookup"><span data-stu-id="d772d-256">DefaultSetup.ini</span></span>  
  
         <span data-ttu-id="d772d-257">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ソース メディアのルート レベルの \x86 および \x64 フォルダーに DefaultSetup.ini ファイルがある場合は、DefaultSetup.ini ファイルを開き、 *Features* パラメーターをファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="d772d-257">If you have the DefaultSetup.ini file in the \x86 and \x64 folders at the root level of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source media, open the DefaultSetup.ini file, and then add the *Features* parameter to the file.</span></span>  
  
         <span data-ttu-id="d772d-258">DefaultSetup.ini ファイルが存在しない場合は、作成し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ソース メディアのルート レベルの \x86 および \x64 フォルダーにコピーできます。</span><span class="sxs-lookup"><span data-stu-id="d772d-258">If the DefaultSetup.ini file does not exist, you can create it and copy it to the \x86 and \x64 folders at the root level of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source media.</span></span>  
  
## <a name="configuring-remote-access-of-ssnoversion-running-on-server-core"></a><span data-ttu-id="d772d-259">Server Core で実行する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のリモート アクセスの構成</span><span class="sxs-lookup"><span data-stu-id="d772d-259">Configuring Remote Access of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Running on Server Core</span></span>  
 <span data-ttu-id="d772d-260">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SP1 または [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] の Server Core インストールで実行されている [!INCLUDE[win8srv](../../includes/win8srv-md.md)]インスタンスのリモート アクセスを構成するには、以下で説明する処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="d772d-260">Perform the actions described below to configure remote access of a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] instance that is running on a Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span>  
  
### <a name="enable-remote-connections-on-the-instance-of-ssnoversion"></a><span data-ttu-id="d772d-261">のインスタンスでリモート接続を有効にする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d772d-261">Enable remote connections on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 <span data-ttu-id="d772d-262">リモート接続を有効にするには、SQLCMD.exe をローカルで使用して、Server Core インスタンスに対して次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="d772d-262">To enable remote connections, use SQLCMD.exe locally and execute the following statements against the Server Core instance:</span></span>  
  
-   `EXEC sys.sp_configure N'remote access', N'1'`  
  
     `GO`  
  
-   `RECONFIGURE WITH OVERRIDE`  
  
     `GO`  
  
### <a name="enable-and-start-the-ssnoversion-browser-service"></a><span data-ttu-id="d772d-263">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスを有効にして開始する</span><span class="sxs-lookup"><span data-stu-id="d772d-263">Enable and start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service</span></span>  
 <span data-ttu-id="d772d-264">Browser サービスは、既定では無効になっています。</span><span class="sxs-lookup"><span data-stu-id="d772d-264">By default, the Browser service is disabled.</span></span>  <span data-ttu-id="d772d-265">Server Core で実行している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで無効になっている場合、このサービスを有効にするには、コマンド プロンプトから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="d772d-265">If it is disabled on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on Server Core, run the following command from the command prompt to enable it:</span></span>  
  
 `sc config SQLBROWSER start= auto`  
  
 <span data-ttu-id="d772d-266">有効にした後は、コマンド プロンプトから次のコマンドを実行して、サービスを開始します。</span><span class="sxs-lookup"><span data-stu-id="d772d-266">After it is enabled, run the following command from the command prompt to start the service:</span></span>  
  
 `net start SQLBROWSER`  
  
### <a name="create-exceptions-in-windows-firewall"></a><span data-ttu-id="d772d-267">Windows ファイアウォールで例外を作成する</span><span class="sxs-lookup"><span data-stu-id="d772d-267">Create exceptions in Windows Firewall</span></span>  
 <span data-ttu-id="d772d-268">Windows ファイアウォールで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アクセスの例外を作成するには、「 [SQL Server のアクセスを許可するための Windows ファイアウォールの構成](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)」で指定されている手順に従います。</span><span class="sxs-lookup"><span data-stu-id="d772d-268">To create exceptions for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] access in Windows Firewall, follow the steps specified in [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
### <a name="enable-tcpip-on-the-instance-of-ssnoversion"></a><span data-ttu-id="d772d-269">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d772d-269">Enable TCP/IP on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 <span data-ttu-id="d772d-270">Server Core 上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに対して TCP/IP プロトコルを有効にするには、Windows PowerShell を使用します。</span><span class="sxs-lookup"><span data-stu-id="d772d-270">The TCP/IP protocol can be enabled through Windows PowerShell for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on Server Core.</span></span> <span data-ttu-id="d772d-271">次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="d772d-271">Follow these steps:</span></span>  
  
1.  <span data-ttu-id="d772d-272">[!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 または [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core を実行しているコンピューターで、タスク マネージャーを起動します。</span><span class="sxs-lookup"><span data-stu-id="d772d-272">On the computer that is running [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core, launch Task Manager.</span></span>  
  
2.  <span data-ttu-id="d772d-273">**[アプリケーション]** タブで、 **[新しいタスク]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d772d-273">On the **Applications** tab, click **New Task**.</span></span>  
  
3.  <span data-ttu-id="d772d-274">**[新しいタスクの作成]** ダイアログ ボックスで、 **[開く]** フィールドに **sqlps.exe** と入力して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d772d-274">In the **Create New Task** dialog box, type **sqlps.exe** in the **Open** field and then click **OK**.</span></span> <span data-ttu-id="d772d-275">\*\* [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell\*\*ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="d772d-275">This opens the **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell** window.</span></span>  
  
4.  <span data-ttu-id="d772d-276">**[Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell]** ウィンドウで、次のスクリプトを実行して TCP/IP プロトコルを有効にします。</span><span class="sxs-lookup"><span data-stu-id="d772d-276">In the **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell** window, run the following script to enable the TCP/IP protocol:</span></span>  
  
```powershell
$smo = 'Microsoft.SqlServer.Management.Smo.'  
$wmi = New-Object ($smo + 'Wmi.ManagedComputer')  
# Enable the TCP protocol on the default instance.  If the instance is named, replace MSSQLSERVER with the instance name in the following line.  
$uri = "ManagedComputer[@Name='" + (get-item env:\computername).Value + "']/ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
$Tcp = $wmi.GetSmoObject($uri)  
$Tcp.IsEnabled = $true  
$Tcp.Alter()  
$Tcp  
```  
  
## <a name="uninstallation"></a><span data-ttu-id="d772d-277">アンインストール</span><span class="sxs-lookup"><span data-stu-id="d772d-277">Uninstallation</span></span>  
 <span data-ttu-id="d772d-278">[!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 または [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core を実行しているコンピューターにログオンした後は、管理者コマンド プロンプトのデスクトップ環境に制限されます。</span><span class="sxs-lookup"><span data-stu-id="d772d-278">After you log on to a computer that is running [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core, you have a limited desktop environment with an Administrator command prompt.</span></span> <span data-ttu-id="d772d-279">このコマンド プロンプトを使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のインスタンスのアンインストールを開始できます。</span><span class="sxs-lookup"><span data-stu-id="d772d-279">You can use this command prompt to initiate uninstallation of an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="d772d-280">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のインスタンスをアンインストールするには、/Q パラメーターを使用した非表示モード、または /QS パラメーターを使用した簡易非表示モードで、コマンド プロンプトからアンインストールを起動します。</span><span class="sxs-lookup"><span data-stu-id="d772d-280">To uninstall an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], launch the uninstallation from the command prompt in full quiet mode by using the /Q parameter, or quiet simple mode by using the /QS parameter.</span></span> <span data-ttu-id="d772d-281">/QS パラメーターを指定すると、UI に進捗状況が表示されますが、入力は受け付けられません。</span><span class="sxs-lookup"><span data-stu-id="d772d-281">The /QS parameter shows progress through the UI, but does not accept any input.</span></span> <span data-ttu-id="d772d-282">/Q は、ユーザー インターフェイスのない非表示モードで実行します。</span><span class="sxs-lookup"><span data-stu-id="d772d-282">/Q runs in a quiet mode without any user interface.</span></span>  
  
 <span data-ttu-id="d772d-283">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の既存のインスタンスをアンインストールするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="d772d-283">To uninstall an existing instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
```cmd
setup.exe /Q /Action=Uninstall /FEATURES=SQLEngine,AS,IS /INSTANCENAME=MSSQLSERVER  
```  
  
 <span data-ttu-id="d772d-284">名前付きインスタンスを削除する場合は、前に示した例の "MSSQLSERVER" の代わりにインスタンス名を指定します。</span><span class="sxs-lookup"><span data-stu-id="d772d-284">To remove a named instance, specify the name of the instance instead of "MSSQLSERVER" in the preceding example.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="d772d-285">誤ってコマンド プロンプトを閉じた場合は、次の手順で新しいコマンド プロンプトを開始できます。</span><span class="sxs-lookup"><span data-stu-id="d772d-285">If you accidentally close the command prompt, you can start a new command prompt by following these steps:</span></span>  
> 
>  1.  <span data-ttu-id="d772d-286">Ctrl + Shift + Esc キーを押して、タスク マネージャーを表示します。</span><span class="sxs-lookup"><span data-stu-id="d772d-286">Press Ctrl+Shift+Esc to display Task Manager.</span></span>  
> 2.  <span data-ttu-id="d772d-287">**[アプリケーション]** タブで、 **[新しいタスク]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d772d-287">On the **Applications** tab, click **New Task**.</span></span>  
> 3.  <span data-ttu-id="d772d-288">**[新しいタスクの作成]** ダイアログ ボックスで、 **[名前]** フィールドに「 **cmd** 」と入力して、 [!INCLUDE[clickOK](../../includes/clickok-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d772d-288">In the **Create New Task** dialog box, type **cmd** in the **Open** field and then [!INCLUDE[clickOK](../../includes/clickok-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d772d-289">参照</span><span class="sxs-lookup"><span data-stu-id="d772d-289">See Also</span></span>  
 <span data-ttu-id="d772d-290">[構成ファイルを使用して SQL Server 2014 をインストールする](install-sql-server-using-a-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="d772d-290">[Install SQL Server 2014 Using a Configuration File](install-sql-server-using-a-configuration-file.md) </span></span>  
 <span data-ttu-id="d772d-291">[コマンドプロンプトから SQL Server 2014 をインストールする](install-sql-server-from-the-command-prompt.md) </span><span class="sxs-lookup"><span data-stu-id="d772d-291">[Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md) </span></span>  
 <span data-ttu-id="d772d-292">[SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="d772d-292">[Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span></span>  
 <span data-ttu-id="d772d-293">[Server Core インストールオプションはじめにガイド](https://go.microsoft.com/fwlink/?LinkId=221422) </span><span class="sxs-lookup"><span data-stu-id="d772d-293">[Server Core Installation Option Getting Started Guide](https://go.microsoft.com/fwlink/?LinkId=221422) </span></span>  
 <span data-ttu-id="d772d-294">[Server Core インストールの構成: 概要](https://go.microsoft.com/fwlink/?LinkId=221423) </span><span class="sxs-lookup"><span data-stu-id="d772d-294">[Configuring a Server Core installation: Overview](https://go.microsoft.com/fwlink/?LinkId=221423) </span></span>  
 <span data-ttu-id="d772d-295">[タスクフォーカスによって一覧表示された Windows PowerShell のフェールオーバークラスターコマンドレット](https://go.microsoft.com/fwlink/?LinkId=221419) </span><span class="sxs-lookup"><span data-stu-id="d772d-295">[Failover Cluster Cmdlets in Windows PowerShell Listed by Task Focus](https://go.microsoft.com/fwlink/?LinkId=221419) </span></span>  
 [<span data-ttu-id="d772d-296">Mapping Cluster.exe Commands to Windows PowerShell Cmdlets for Failover Clusters (フェールオーバー クラスターの Windows PowerShell コマンドレットへの Cluster.exe コマンドのマッピング)</span><span class="sxs-lookup"><span data-stu-id="d772d-296">Mapping Cluster.exe Commands to Windows PowerShell Cmdlets for Failover Clusters</span></span>](https://go.microsoft.com/fwlink/?LinkId=221421)  
