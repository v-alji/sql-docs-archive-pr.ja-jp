---
title: Analysis Services の旧バージョンとの互換性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- installing Analysis Services, backward compatibility
- backward compatibility [Analysis Services]
- compatibility [Analysis Services]
- Analysis Services, backward compatibility
- upgrading Analysis Services
- SSAS, backward compatibility
- SQL Server Analysis Services, backward compatibility
ms.assetid: 618b6c3a-e20d-47a9-b2c6-6d848dfba05a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44a5296bfbd2bae746eb9936d416fd696de16cb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633673"
---
# <a name="analysis-services-backward-compatibility"></a><span data-ttu-id="3339a-102">Analysis Services の旧バージョンとの互換性</span><span class="sxs-lookup"><span data-stu-id="3339a-102">Analysis Services Backward Compatibility</span></span>
  <span data-ttu-id="3339a-103">このセクションのトピックでは、のバージョン間の動作の変更について説明し [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="3339a-103">The topics in this section describe the changes in behavior between versions of  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3339a-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="3339a-104">In This Section</span></span>  
  
|<span data-ttu-id="3339a-105">トピック</span><span class="sxs-lookup"><span data-stu-id="3339a-105">Topics</span></span>|<span data-ttu-id="3339a-106">説明</span><span class="sxs-lookup"><span data-stu-id="3339a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3339a-107">SQL Server 2014 に含まれている非推奨の Analysis Services 機能</span><span class="sxs-lookup"><span data-stu-id="3339a-107">Deprecated Analysis Services Features in SQL Server 2014</span></span>](deprecated-analysis-services-features-in-sql-server-2014.md)|<span data-ttu-id="3339a-108">現在のバージョンでは旧バージョンとの互換性を維持するために引き続き使用できるものの、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の今後のバージョンでは削除される予定になっている機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="3339a-108">Describes features that have been retained in the current version to maintain backward compatibility,  but which will be removed in a future version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="3339a-109">SQL Server 2014 で提供が中止された Analysis Services の機能</span><span class="sxs-lookup"><span data-stu-id="3339a-109">Discontinued Analysis Services Functionality in SQL Server 2014</span></span>](discontinued-analysis-services-functionality-in-sql-server-2014.md)|<span data-ttu-id="3339a-110">以前のバージョンの  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] には存在したものの、以降のバージョンからは削除されている機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="3339a-110">Describes features that existed in earlier versions of  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] but that have since been removed in later versions.</span></span>|  
|[<span data-ttu-id="3339a-111">SQL Server 2014 の Analysis Services 機能における重大な変更</span><span class="sxs-lookup"><span data-stu-id="3339a-111">Breaking Changes to Analysis Services Features in SQL Server 2014</span></span>](breaking-changes-to-analysis-services-features-in-sql-server-2014.md)|<span data-ttu-id="3339a-112">以前のバージョンのソフトウェアで作成したモデル、カスタム アプリケーション、スクリプトが使用できなくなる可能性のある、このリリースの [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で導入されたコードの変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="3339a-112">Describes code changes introduced in this release of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that could potentially break a model or custom applications or script created in previous versions of the software .</span></span>|  
|[<span data-ttu-id="3339a-113">SQL Server 2014 における Analysis Services 機能の動作の変更</span><span class="sxs-lookup"><span data-stu-id="3339a-113">Behavior Changes to Analysis Services Features in SQL Server 2014</span></span>](behavior-changes-to-analysis-services-features-in-sql-server-2014.md)|<span data-ttu-id="3339a-114">このリリースの [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]において動作が異なる既存の機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="3339a-114">Describes existing features that have different behaviors in this release of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="3339a-115">一般的な例としては、既定値が新しい値や異なる値に変更される、以前は許可されていた操作や構成が許可されなくなる、アップグレード中に失われる設定や構成を手動で修正したり置き換えたりするための要件が生じる、といったことがあります。</span><span class="sxs-lookup"><span data-stu-id="3339a-115">Common examples include changing a default to a new or different value, disallowing a previously allowable operation or configuration, or a introducing a requirement to manually revise or replace a setting or configuration that is lost during upgrade.</span></span><br /> <span data-ttu-id="3339a-116">.</span><span class="sxs-lookup"><span data-stu-id="3339a-116">.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3339a-117">参照</span><span class="sxs-lookup"><span data-stu-id="3339a-117">See Also</span></span>  
 <span data-ttu-id="3339a-118">[Analysis Services とビジネスインテリジェンスの新機能](what-s-new-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="3339a-118">[What's New in Analysis Services and Business Intelligence](what-s-new-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="3339a-119">Analysis Services のアップグレード</span><span class="sxs-lookup"><span data-stu-id="3339a-119">Upgrade Analysis Services</span></span>](../database-engine/install-windows/upgrade-analysis-services.md)  
  
  
