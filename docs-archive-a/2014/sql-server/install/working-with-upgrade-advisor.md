---
title: Upgrade Advisor を使用する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], when to use
- SQL Server Upgrade Advisor, when to use
- when to use Upgrade Advisor
ms.assetid: 5f26a7b9-1ac2-442c-8316-87b078db3baf
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 75a16e57734493cdd7ac00e7bad3124eb7a99d84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640337"
---
# <a name="working-with-upgrade-advisor"></a><span data-ttu-id="1e274-102">アップグレード アドバイザーの使用</span><span class="sxs-lookup"><span data-stu-id="1e274-102">Working with Upgrade Advisor</span></span>
  <span data-ttu-id="1e274-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] に確実にアップグレードできるように、アップグレード アドバイザーには、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] へのアップグレードの前に、現在のインストールについて対処が必要な問題を検出するための中央コンソールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="1e274-103">To help ensure that your upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] is successful, Upgrade Advisor provides a central console to identify issues to address in your installations before upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="1e274-104">アップグレード アドバイザーでは次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="1e274-104">You can use Upgrade Advisor to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="1e274-105">ローカル サーバーまたはリモート サーバー上にある以前のバージョンのコンポーネントを分析する。</span><span class="sxs-lookup"><span data-stu-id="1e274-105">Analyze previous version's components on local or remote servers.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="1e274-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のリモート インスタンスを分析することはできません。</span><span class="sxs-lookup"><span data-stu-id="1e274-106">You cannot analyze remote instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="1e274-107">分析の結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="1e274-107">View the results of the analysis.</span></span>  
  
 <span data-ttu-id="1e274-108">アップグレード アドバイザーには、アナライザーとビューアーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1e274-108">Upgrade Advisor includes an analyzer and a viewer.</span></span> <span data-ttu-id="1e274-109">アップグレード アドバイザー分析ウィザードでは、選択したコンポーネントを分析します。</span><span class="sxs-lookup"><span data-stu-id="1e274-109">The Upgrade Advisor Analysis Wizard analyzes the components you select.</span></span> <span data-ttu-id="1e274-110">アナライザーでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードするにあたり、事前に処理しておく必要がある問題を示すカスタム レポートが生成されます。</span><span class="sxs-lookup"><span data-stu-id="1e274-110">The analyzer then generates custom reports about issues that you must handle before you can upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="1e274-111">アップグレード アドバイザー レポート ビューアーを使用して、カスタム レポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="1e274-111">You use the Upgrade Advisor Report Viewer to view the custom reports.</span></span> <span data-ttu-id="1e274-112">アップグレードアドバイザー分析によって検出される内容の詳細については、「[アップグレードに関する問題の解決](../../../2014/sql-server/install/resolving-upgrade-issues.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e274-112">For more information about what Upgrade Advisor analysis detects, see [Resolving Upgrade Issues](../../../2014/sql-server/install/resolving-upgrade-issues.md).</span></span>  
  
 <span data-ttu-id="1e274-113">ここでは、アップグレード アドバイザーの機能概要、およびアップグレード アドバイザーとアップグレード アドバイザー レポートの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1e274-113">The topics in this section provide an overview of Upgrade Advisor functionality and information about how to use Upgrade Advisor and Upgrade Advisor reports.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1e274-114">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="1e274-114">In This Section</span></span>  
  
|<span data-ttu-id="1e274-115">トピック</span><span class="sxs-lookup"><span data-stu-id="1e274-115">Topic</span></span>|<span data-ttu-id="1e274-116">説明</span><span class="sxs-lookup"><span data-stu-id="1e274-116">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="1e274-117">アップグレード アドバイザーの概要</span><span class="sxs-lookup"><span data-stu-id="1e274-117">Overview of Upgrade Advisor</span></span>](../../../2014/sql-server/install/overview-of-upgrade-advisor.md)|<span data-ttu-id="1e274-118">アップグレード プロセス、アップグレード アドバイザー分析ウィザード、およびアップグレード アドバイザー レポート ビューアーの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="1e274-118">Provides an overview of the upgrade process, the Upgrade Advisor Analysis Wizard, and the Upgrade Advisor Report Viewer.</span></span>|  
|[<span data-ttu-id="1e274-119">アップグレード アドバイザーの操作方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="1e274-119">Upgrade Advisor How-to Topics</span></span>](../../../2014/sql-server/install/upgrade-advisor-how-to-topics.md)|<span data-ttu-id="1e274-120">アップグレード アドバイザーを実行する一般的な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="1e274-120">Provides instructions to perform common Upgrade Advisor procedures.</span></span>|  
|[<span data-ttu-id="1e274-121">アップグレード アドバイザーのユーザー インターフェイス リファレンス</span><span class="sxs-lookup"><span data-stu-id="1e274-121">Upgrade Advisor User Interface Reference</span></span>](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)|<span data-ttu-id="1e274-122">F1 キーを押すか、アップグレードアドバイザー分析ウィザードのページで [**ヘルプ**] をクリックすると表示されるトピックが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1e274-122">Contains topics that appear if you press the F1 key or click **Help** on the Upgrade Advisor Analysis Wizard pages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1e274-123">参照</span><span class="sxs-lookup"><span data-stu-id="1e274-123">See Also</span></span>  
 <span data-ttu-id="1e274-124">[アップグレードアドバイザーをインストールしています](../../../2014/sql-server/install/installing-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="1e274-124">[Installing Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="1e274-125">アップグレードに関する問題の解決</span><span class="sxs-lookup"><span data-stu-id="1e274-125">Resolving Upgrade Issues</span></span>](../../../2014/sql-server/install/resolving-upgrade-issues.md)  
  
  
