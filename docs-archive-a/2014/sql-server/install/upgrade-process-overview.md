---
title: アップグレードプロセスの概要 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- upgrading SQL Server
- Upgrade Advisor [SQL Server], process description
- SQL Server Upgrade Advisor, process description
- upgrade process [Upgrade Advisor]
ms.assetid: f77ffbab-a195-4124-acce-9c538f7ca9ce
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5da6dc3b3e6d6c7058193801100bf2552bfde7cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742774"
---
# <a name="upgrade-process-overview"></a><span data-ttu-id="22314-102">アップグレード プロセスの概要</span><span class="sxs-lookup"><span data-stu-id="22314-102">Upgrade Process Overview</span></span>
  <span data-ttu-id="22314-103">ここでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] アップグレード アドバイザーのベスト プラクティス情報、および [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードするための推奨プロセスの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="22314-103">This topic provides best practice information for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor and a summary of the recommended process for upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="upgrade-process"></a><span data-ttu-id="22314-104">アップグレード プロセス</span><span class="sxs-lookup"><span data-stu-id="22314-104">Upgrade Process</span></span>  
 <span data-ttu-id="22314-105">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、または [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] を実行しているサーバーは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードできます。</span><span class="sxs-lookup"><span data-stu-id="22314-105">Servers that are running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] can be upgraded to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="22314-106">ただし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のコンポーネントには、適切にアップグレードできるもの、移行が必要なもの、新しいコンポーネントに置き換わるものがあります。</span><span class="sxs-lookup"><span data-stu-id="22314-106">Whereas some [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components can be upgraded in place, others must be migrated, and still others have been superseded by new components.</span></span> <span data-ttu-id="22314-107">たとえば、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降、データ変換サービス (DTS) は [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) に置き換えられており、DTS は [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ではサポートされなくなります。</span><span class="sxs-lookup"><span data-stu-id="22314-107">For example, starting with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) supersedes Data Transformation Services (DTS), and DTS is no longer supported in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="22314-108">アップグレード プランを作成する場合は、現在の DTS パッケージを [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージに更新する計画を立てることが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="22314-108">When you formulate your upgrade plan, you might need to plan for updating your current DTS packages to [!INCLUDE[ssIS](../../includes/ssis-md.md)] packages.</span></span>  
  
 <span data-ttu-id="22314-109">アップグレード アドバイザーを使用すると、現在の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール、コンポーネント、および関連ファイルを評価して、アップグレード中またはアップグレード後、あるいは [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] に移行後にエラーを引き起こす既知の問題を特定できます。</span><span class="sxs-lookup"><span data-stu-id="22314-109">Upgrade Advisor enables you to evaluate current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installations, components, and related files to identify known issues that will cause problems both during and after you upgrade or migrate to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="22314-110">これらの既知の問題のいくつかによって、アップグレードがブロックさ [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] れます。</span><span class="sxs-lookup"><span data-stu-id="22314-110">A few of these known issues block the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] upgrade.</span></span> <span data-ttu-id="22314-111">アップグレード アドバイザーのレポートには、このような問題がアップグレード ブロッカーとして示されます。</span><span class="sxs-lookup"><span data-stu-id="22314-111">In the Upgrade Advisor report, these issues are identified as Upgrade Blockers.</span></span> <span data-ttu-id="22314-112">セットアップを実行する前にアップグレード ブロッカーに対処していない場合は、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のセットアップが終了し、アップグレード アドバイザーを実行してアップグレードをブロックしている問題を特定するように勧めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="22314-112">If you have not addressed the Upgrade Blockers before you run Setup, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup exits and recommends that you run Upgrade Advisor to identify the specific issues that are blocking the upgrade.</span></span>  
  
 <span data-ttu-id="22314-113">ベスト プラクティスとして、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードする前に、データとシステム設定をバックアップしておき、所属する組織向けに定義されている操作上のガイドラインに従って戦略的な手順を実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="22314-113">As a best practice before upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], we recommend that you back up your data and system settings, and take strategic steps as outlined in the operational guidelines defined for your organization.</span></span> <span data-ttu-id="22314-114">次の手順に従ってアップグレードを完了してください。</span><span class="sxs-lookup"><span data-stu-id="22314-114">Use the following steps to complete the upgrade:</span></span>  
  
1.  <span data-ttu-id="22314-115">「 [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)」を確認します。</span><span class="sxs-lookup"><span data-stu-id="22314-115">Review [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="22314-116">データとシステム設定をバックアップします。</span><span class="sxs-lookup"><span data-stu-id="22314-116">Back up data and system settings.</span></span>  
  
3.  <span data-ttu-id="22314-117">アップグレード アドバイザーを実行します。</span><span class="sxs-lookup"><span data-stu-id="22314-117">Run Upgrade Advisor.</span></span>  
  
     <span data-ttu-id="22314-118">アップグレード アドバイザーを実行しても、コンピューター上のデータや設定が変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="22314-118">Upgrade Advisor does not modify your data or change settings on your computer.</span></span>  
  
4.  <span data-ttu-id="22314-119">アップグレード アドバイザーのレポートで検出された問題を確認します。</span><span class="sxs-lookup"><span data-stu-id="22314-119">Review the issues identified in the Upgrade Advisor report.</span></span>  
  
5.  <span data-ttu-id="22314-120">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] へのアップグレードに支障をきたす問題をすべて解決します。</span><span class="sxs-lookup"><span data-stu-id="22314-120">Resolve any blocking issues that would prevent you from upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
6.  <span data-ttu-id="22314-121">その他のアップグレード前の問題を解決します。</span><span class="sxs-lookup"><span data-stu-id="22314-121">Resolve any other pre-upgrade issues.</span></span>  
  
7.  <span data-ttu-id="22314-122">アップグレード アドバイザーを実行して、既知の問題がすべて解消されたかどうか検証します。</span><span class="sxs-lookup"><span data-stu-id="22314-122">Run Upgrade Advisor to verify that all known issues have been addressed.</span></span>  
  
8.  <span data-ttu-id="22314-123">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] セットアップを実行します。</span><span class="sxs-lookup"><span data-stu-id="22314-123">Run [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup.</span></span>  
  
9. <span data-ttu-id="22314-124">アップグレード後の問題と移行の問題を解決します。</span><span class="sxs-lookup"><span data-stu-id="22314-124">Resolve any post-upgrade and migration issues.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22314-125">参照</span><span class="sxs-lookup"><span data-stu-id="22314-125">See Also</span></span>  
 <span data-ttu-id="22314-126">[アップグレードアドバイザー &#40;ユーザーインターフェイス&#41;を実行しています](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md) </span><span class="sxs-lookup"><span data-stu-id="22314-126">[Running Upgrade Advisor &#40;User Interface&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md) </span></span>  
 <span data-ttu-id="22314-127">[レポートの使用](../../../2014/sql-server/install/using-reports.md) </span><span class="sxs-lookup"><span data-stu-id="22314-127">[Using Reports](../../../2014/sql-server/install/using-reports.md) </span></span>  
 [<span data-ttu-id="22314-128">アップグレード アドバイザーの使用</span><span class="sxs-lookup"><span data-stu-id="22314-128">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
