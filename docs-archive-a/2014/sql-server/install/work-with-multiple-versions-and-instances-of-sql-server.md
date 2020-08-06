---
title: SQL Server の複数のバージョンおよびインスタンスの使用 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- concurrent installations [SQL Server]
- versions [SQL Server], multiple
- side-by-side installations [SQL Server]
- multiple SQL Server component versions
- installing SQL Server, side-by-side installations
- Setup [SQL Server], side-by-side installations
- 64-bit edition [SQL Server]
- 32-bit edition [SQL Server]
- editions [SQL Server], side-by-side installations
ms.assetid: 93acefa8-bb41-4ccc-b763-7801f51134e0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 81d582a863c451fc818243373f3841a9e840562d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640340"
---
# <a name="work-with-multiple-versions-and-instances-of-sql-server"></a><span data-ttu-id="cab36-102">SQL Server の複数のバージョンおよびインスタンスの使用</span><span class="sxs-lookup"><span data-stu-id="cab36-102">Work with Multiple Versions and Instances of SQL Server</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cab36-103">同じコンピューター上で [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の複数のインスタンスをサポートします。</span><span class="sxs-lookup"><span data-stu-id="cab36-103">supports multiple instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] on the same computer.</span></span> <span data-ttu-id="cab36-104">また、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をアップグレードしたり、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が既にインストールされているコンピューターに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="cab36-104">You can also upgrade earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a computer where earlier [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions are already installed.</span></span> <span data-ttu-id="cab36-105">サポートされるアップグレード シナリオについては、「 [サポートされるバージョンとエディションのアップグレード](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cab36-105">For supported upgrade scenarios, see [Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md).</span></span>  
  
## <a name="version-components-and-numbering"></a><span data-ttu-id="cab36-106">バージョンのコンポーネントと番号付け</span><span class="sxs-lookup"><span data-stu-id="cab36-106">Version Components and Numbering</span></span>  
 <span data-ttu-id="cab36-107">次に示す概念は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のサイド バイ サイドのインスタンスでの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の動作について理解するうえで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="cab36-107">The following concepts are useful in understanding the behavior of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for side-by-side instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="cab36-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の製品バージョンの標準の形式は MM.nn.bbbb.rr であり、各セグメントは次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="cab36-108">The standard product version format for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is MM.nn.bbbb.rr where each segment is defined as:</span></span>  
  
 <span data-ttu-id="cab36-109">MM: メジャー バージョン</span><span class="sxs-lookup"><span data-stu-id="cab36-109">MM - Major version</span></span>  
  
 <span data-ttu-id="cab36-110">nn: マイナー バージョン</span><span class="sxs-lookup"><span data-stu-id="cab36-110">nn - Minor version</span></span>  
  
 <span data-ttu-id="cab36-111">bbbb: ビルド番号</span><span class="sxs-lookup"><span data-stu-id="cab36-111">bbbb - Build number</span></span>  
  
 <span data-ttu-id="cab36-112">rr: ビルドのリビジョン番号</span><span class="sxs-lookup"><span data-stu-id="cab36-112">rr - Build revision number</span></span>  
  
 <span data-ttu-id="cab36-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、以前のバージョンと区別するために、メジャー リリースやマイナー リリースごとにバージョン番号を増加させています。</span><span class="sxs-lookup"><span data-stu-id="cab36-113">In each major or minor release of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], there is an increment to the version number to differentiate it from earlier versions.</span></span> <span data-ttu-id="cab36-114">このバージョンに対する変更は、さまざまな目的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="cab36-114">This change to the version is used for many purposes.</span></span> <span data-ttu-id="cab36-115">たとえば、ユーザー インターフェイスでのバージョン情報の表示、アップグレード時のファイルの置換方法の制御、およびサービス パックの適用に使用されることも、一連のバージョン間での機能の違いを区別するためのメカニズムとして使用されることもあります。</span><span class="sxs-lookup"><span data-stu-id="cab36-115">This includes displaying version information in the user interface, controlling how files are replaced during upgrade, applying service packs, and also as a mechanism for functional differentiation between the successive versions.</span></span>  
  
### <a name="components-shared-by-all-versions-of-ssnoversion"></a><span data-ttu-id="cab36-116">すべてのバージョンで共有されるコンポーネント [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cab36-116">Components shared by all versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 <span data-ttu-id="cab36-117">特定のコンポーネントは、インストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのバージョンのすべてのインスタンスで共有されます。</span><span class="sxs-lookup"><span data-stu-id="cab36-117">Certain components are shared by all instances of all installed versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="cab36-118">同じコンピューターにバージョンが異なる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をサイド バイ サイドでインストールすると、それらのコンポーネントは自動的に最新バージョンにアップグレードされます。</span><span class="sxs-lookup"><span data-stu-id="cab36-118">When you install different versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] side-by-side on the same machine, these components are automatically upgraded to the latest version.</span></span> <span data-ttu-id="cab36-119">通常、このようなコンポーネントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の最後のインスタンスがアンインストールされると自動的にアンインストールされます。</span><span class="sxs-lookup"><span data-stu-id="cab36-119">Such components are usually uninstalled automatically when the last instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is uninstalled.</span></span>  
  
 <span data-ttu-id="cab36-120">例 :[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser および Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] VSS Writer。</span><span class="sxs-lookup"><span data-stu-id="cab36-120">Examples: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser and Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] VSS Writer.</span></span>  
  
### <a name="components-shared-across-all-instances-of-the-same-major-version-of-ssnoversion"></a><span data-ttu-id="cab36-121">メジャー バージョンが同一の すべてのインスタンス間で共有されるコンポーネント [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cab36-121">Components shared across all instances of the same major version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cab36-122">メジャー バージョンが同一ののバージョンでは、一部のコンポーネントをすべてのインスタンス間で共有します。</span><span class="sxs-lookup"><span data-stu-id="cab36-122">versions that have the same major version share some components across all instances.</span></span> <span data-ttu-id="cab36-123">アップグレード時に共有コンポーネントが選択されると、既存のコンポーネントは最新バージョンにアップグレードされます。</span><span class="sxs-lookup"><span data-stu-id="cab36-123">If the shared components are selected during upgrade, the existing components are upgraded to the latest version.</span></span>  
  
 <span data-ttu-id="cab36-124">例: [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブック</span><span class="sxs-lookup"><span data-stu-id="cab36-124">Examples: [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
### <a name="components-shared-across-minor-versions"></a><span data-ttu-id="cab36-125">マイナー バージョン間で共有されるコンポーネント</span><span class="sxs-lookup"><span data-stu-id="cab36-125">Components shared across minor versions</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cab36-126">メジャー バージョンとマイナー バージョンが同一のバージョンでは、コンポーネントを共有していました。</span><span class="sxs-lookup"><span data-stu-id="cab36-126">versions that have the same major.minor version shared components.</span></span>  
  
 <span data-ttu-id="cab36-127">例:セットアップ サポート ファイル。</span><span class="sxs-lookup"><span data-stu-id="cab36-127">Example: Setup support files.</span></span>  
  
### <a name="components-specific-to-an-instance-of-ssnoversion"></a><span data-ttu-id="cab36-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに固有のコンポーネント</span><span class="sxs-lookup"><span data-stu-id="cab36-128">Components specific to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 <span data-ttu-id="cab36-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のコンポーネントまたはサービスには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに固有のものがあります。</span><span class="sxs-lookup"><span data-stu-id="cab36-129">Some [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components or services are specific to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="cab36-130">これらは、インスタンス対応とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="cab36-130">These are also known as instance-aware.</span></span> <span data-ttu-id="cab36-131">また、これらをホストしているインスタンスとバージョンが同じで、そのインスタンスにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="cab36-131">They share the same version as the instance that hosts them, and are used exclusively for that instance.</span></span>  
  
 <span data-ttu-id="cab36-132">例: [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cab36-132">Examples: [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
### <a name="components-that-are-independent-of-the-ssnoversion-versions"></a><span data-ttu-id="cab36-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンに依存しないコンポーネント</span><span class="sxs-lookup"><span data-stu-id="cab36-133">Components that are independent of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions</span></span>  
 <span data-ttu-id="cab36-134">特定のコンポーネントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップ時にインストールされますが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のバージョンに依存しません。</span><span class="sxs-lookup"><span data-stu-id="cab36-134">Certain components are installed during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup, but are independent of the versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="cab36-135">これらは、メジャー バージョン間で共有されたり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのバージョンで共有されたりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="cab36-135">They may be shared across major versions or by all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions.</span></span>  
  
 <span data-ttu-id="cab36-136">例 :Microsoft Sync Framework、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact。</span><span class="sxs-lookup"><span data-stu-id="cab36-136">Examples: Microsoft Sync Framework, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.</span></span>  
  
 <span data-ttu-id="cab36-137">Compact インストールの詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「インストール[ウィザードから SQL Server 2014 をインストールする」 &#40;セットアップ&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cab36-137">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact installation, see [Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).</span></span> <span data-ttu-id="cab36-138">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact のアンインストール方法の詳細については、「[SQL Server の既存のインスタンスのアンインストール &#40;セットアップ&#41;](../../../2014/sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cab36-138">For more information about how to uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, see [Uninstall an Existing Instance of SQL Server &#40;Setup&#41;](../../../2014/sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md).</span></span>  
  
## <a name="using-ssnoversion-side-by-side-with-previous-versions-of-ssnoversion"></a><span data-ttu-id="cab36-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と以前のバージョンの並列使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cab36-139">Using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Side-By-Side with Previous Versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 <span data-ttu-id="cab36-140">以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを既に実行しているコンピューターに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="cab36-140">You can install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a computer that is already running instances of an earlier [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version.</span></span> <span data-ttu-id="cab36-141">既定のインスタンスが既にコンピューターに存在する場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は名前付きインスタンスとしてインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cab36-141">If a default instance already exists on the computer, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be installed as a named instance.</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cab36-142">SysPrep では、以前のバージョンの [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] と同じコンピューターに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の準備済みインスタンスをサイド バイ サイドでインストールすることはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="cab36-142">SysPrep does not support side by side installation of prepared instances of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] with earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the same computer.</span></span> <span data-ttu-id="cab36-143">たとえば、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インスタンスと共に [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]の準備済みインスタンスをサイド バイ サイドで準備することはできません。</span><span class="sxs-lookup"><span data-stu-id="cab36-143">For example, you cannot prepare a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] instance side by side with a prepared instance of [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span> <span data-ttu-id="cab36-144">ただし、同じメジャー バージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の複数の準備済みインスタンスを、同じコンピューターにサイド バイ サイドでインストールできます。</span><span class="sxs-lookup"><span data-stu-id="cab36-144">However, you can install multiple prepared instances of the same major version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] side by side on the same computer.</span></span> <span data-ttu-id="cab36-145">詳細については、「 [SysPrep を使用した SQL Server のインストールに関する注意点](../../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cab36-145">For more information, see [Considerations for Installing SQL Server Using SysPrep](../../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md).</span></span>  
>   
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="cab36-146">Windows Server 2008 R2 Server Core SP1 を搭載するコンピューターに、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] とサイド バイ サイドでインストールすることはできません。</span><span class="sxs-lookup"><span data-stu-id="cab36-146">cannot be installed side-by-side with earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a computer that is running Windows Server 2008 R2 Server Core SP1.</span></span> <span data-ttu-id="cab36-147">Server Core インストールの詳細については、「 [Install SQL Server 2014 On Server core](../../database-engine/install-windows/install-sql-server-on-server-core.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cab36-147">For more information on Server Core installations, see [Install SQL Server 2014 on Server Core](../../database-engine/install-windows/install-sql-server-on-server-core.md).</span></span>  
  
 <span data-ttu-id="cab36-148">次の表に、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のサイド バイ サイドのサポートを示します。</span><span class="sxs-lookup"><span data-stu-id="cab36-148">The following table shows side-by-side support for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]:</span></span>  
  
|<span data-ttu-id="cab36-149">の既存のインスタンス [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cab36-149">Existing instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]</span></span>|<span data-ttu-id="cab36-150">サイド バイ サイドのサポート</span><span class="sxs-lookup"><span data-stu-id="cab36-150">Side-by-side support</span></span>|  
|--------------------------------------------------|----------------------------|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="cab36-151">(32 ビット)</span><span class="sxs-lookup"><span data-stu-id="cab36-151">(32-bit)</span></span>|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="cab36-152">(32 ビット)</span><span class="sxs-lookup"><span data-stu-id="cab36-152">(32-bit)</span></span><br /><br /> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="cab36-153">(64 ビット) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cab36-153">(64-bit) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]</span></span><br /><br /> [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] <span data-ttu-id="cab36-154">(32 ビット)</span><span class="sxs-lookup"><span data-stu-id="cab36-154">(32-bit)</span></span><br /><br /> [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] <span data-ttu-id="cab36-155">(64 ビット) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cab36-155">(64-bit) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]</span></span><br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] <span data-ttu-id="cab36-156">(32 ビット)</span><span class="sxs-lookup"><span data-stu-id="cab36-156">(32-bit)</span></span><br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] <span data-ttu-id="cab36-157">(64 ビット) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cab36-157">(64-bit) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]</span></span><br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="cab36-158">(32 ビット)</span><span class="sxs-lookup"><span data-stu-id="cab36-158">(32-bit)</span></span><br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="cab36-159">(64 ビット) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cab36-159">(64-bit) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]</span></span><br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="cab36-160">(32 ビット)</span><span class="sxs-lookup"><span data-stu-id="cab36-160">(32-bit)</span></span><br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="cab36-161">(64 ビット) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cab36-161">(64-bit) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]</span></span>|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="cab36-162">(64 ビット) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cab36-162">(64-bit) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]</span></span>|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="cab36-163">(32 ビット)</span><span class="sxs-lookup"><span data-stu-id="cab36-163">(32-bit)</span></span><br /><br /> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="cab36-164">(64 ビット) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cab36-164">(64-bit) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]</span></span><br /><br /> [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] <span data-ttu-id="cab36-165">(32 ビット)</span><span class="sxs-lookup"><span data-stu-id="cab36-165">(32-bit)</span></span><br /><br /> [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] <span data-ttu-id="cab36-166">(64 ビット) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cab36-166">(64-bit) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]</span></span><br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] <span data-ttu-id="cab36-167">(32 ビット)</span><span class="sxs-lookup"><span data-stu-id="cab36-167">(32-bit)</span></span><br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] <span data-ttu-id="cab36-168">(64 ビット) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cab36-168">(64-bit) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]</span></span><br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="cab36-169">(32 ビット)</span><span class="sxs-lookup"><span data-stu-id="cab36-169">(32-bit)</span></span><br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="cab36-170">(64 ビット) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cab36-170">(64-bit) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]</span></span><br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="cab36-171">(32 ビット)</span><span class="sxs-lookup"><span data-stu-id="cab36-171">(32-bit)</span></span><br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="cab36-172">(64 ビット) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cab36-172">(64-bit) [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]</span></span>|  
  
## <a name="preventing-ip-address-conflicts"></a><span data-ttu-id="cab36-173">IP アドレス競合の回避</span><span class="sxs-lookup"><span data-stu-id="cab36-173">Preventing IP Address Conflicts</span></span>  
 <span data-ttu-id="cab36-174">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のフェールオーバー クラスター インスタンスが [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のスタンドアロン インスタンスとサイド バイ サイドでインストールされている場合は、IP アドレスで TCP ポート番号が競合しないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="cab36-174">When a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Failover Cluster Instance is installed side-by-side with a standalone instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], take care to avoid TCP port number conflicts on the IP addresses.</span></span> <span data-ttu-id="cab36-175">競合は通常、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] の 2 つのインスタンスが両方とも既定の TCP ポート (1433) を使用するように構成されている場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="cab36-175">Conflicts usually occur when two instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] are both configured to use the default TCP port (1433).</span></span> <span data-ttu-id="cab36-176">競合を回避するには、一方のインスタンスが既定以外の固定ポートを使用するように構成します。</span><span class="sxs-lookup"><span data-stu-id="cab36-176">To avoid conflicts, configure one instance to use a non-default fixed port.</span></span> <span data-ttu-id="cab36-177">通常、固定ポートの構成は、スタンドアロン インスタンスに対して行うのが最も簡単です。</span><span class="sxs-lookup"><span data-stu-id="cab36-177">Configuring a fixed port is usually easiest on the standalone instance.</span></span> <span data-ttu-id="cab36-178">[!INCLUDE[ssDE](../../includes/ssde-md.md)] で異なるポートが使用されるように構成すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のフェールオーバー クラスター インスタンスがノードのスタンバイに失敗した場合に、予期しない IP アドレス/TCP ポート競合によってインスタンスの起動がブロックされる問題を回避できます。</span><span class="sxs-lookup"><span data-stu-id="cab36-178">Configuring the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to use different ports will prevent an unexpected IP Address/TCP port conflict that blocks an instance startup when a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Failover Cluster Instance fails to the standby node</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cab36-179">参照</span><span class="sxs-lookup"><span data-stu-id="cab36-179">See Also</span></span>  
 <span data-ttu-id="cab36-180">[SQL Server 2014 をインストールするためのハードウェアおよびソフトウェアの要件](hardware-and-software-requirements-for-installing-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cab36-180">[Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md) </span></span>  
 <span data-ttu-id="cab36-181">[インストールウィザード &#40;セットアップから SQL Server 2014 をインストール&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) </span><span class="sxs-lookup"><span data-stu-id="cab36-181">[Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) </span></span>  
 <span data-ttu-id="cab36-182">[サポートされているバージョンとエディションのアップグレード](../../database-engine/install-windows/supported-version-and-edition-upgrades.md) </span><span class="sxs-lookup"><span data-stu-id="cab36-182">[Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md) </span></span>  
 <span data-ttu-id="cab36-183">[SQL Server 2014 へのアップグレード](../../database-engine/install-windows/upgrade-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cab36-183">[Upgrade to SQL Server 2014](../../database-engine/install-windows/upgrade-sql-server.md) </span></span>  
 <span data-ttu-id="cab36-184">[SQL Server 2014 の各エディションがサポートする機能](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="cab36-184">[Features Supported by the Editions of SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span></span>  
 <span data-ttu-id="cab36-185">[旧バージョンとの互換性](../../../2014/getting-started/backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="cab36-185">[Backward Compatibility](../../../2014/getting-started/backward-compatibility.md) </span></span>  
 [<span data-ttu-id="cab36-186">アップグレード アドバイザーを使用したアップグレードの準備</span><span class="sxs-lookup"><span data-stu-id="cab36-186">Use Upgrade Advisor to Prepare for Upgrades</span></span>](../../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)  
  
  