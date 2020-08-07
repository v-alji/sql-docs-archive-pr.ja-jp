---
title: Reporting Services の旧バージョンとの互換性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- SSRS, backward compatibility
- SQL Server Reporting Services, backward compatibility
- backward compatibility [Reporting Services]
ms.assetid: 675b0e0e-cfee-4790-9675-80fc3ea6d30f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7203740ba7f52dfc2cd3793a20fed9fecf5f9468
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719508"
---
# <a name="reporting-services-backward-compatibility"></a><span data-ttu-id="ca549-102">Reporting Services の旧バージョンとの互換性</span><span class="sxs-lookup"><span data-stu-id="ca549-102">Reporting Services Backward Compatibility</span></span>
  <span data-ttu-id="ca549-103">ここでは、のバージョン間の動作の変更について説明し [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="ca549-103">This section describes changes in behavior between versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="ca549-104">使用できなくなる機能や、将来のリリースで削除される予定の機能の情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="ca549-104">It covers features that are no longer available or are scheduled to be removed in a future release.</span></span> <span data-ttu-id="ca549-105">また、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 機能を含むカスタム アプリケーションを使用できなくなるような、製品の根本的な変更についても説明します。</span><span class="sxs-lookup"><span data-stu-id="ca549-105">It also describes fundamental changes to the product that are known to break a custom application that includes [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ca549-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ca549-106">In This Section</span></span>  
  
|<span data-ttu-id="ca549-107">トピック</span><span class="sxs-lookup"><span data-stu-id="ca549-107">Topic</span></span>|<span data-ttu-id="ca549-108">説明</span><span class="sxs-lookup"><span data-stu-id="ca549-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ca549-109">SQL Server 2014 で廃止された SQL Server Reporting Services の機能</span><span class="sxs-lookup"><span data-stu-id="ca549-109">Discontinued Functionality to SQL Server Reporting Services in SQL Server 2014</span></span>](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)|<span data-ttu-id="ca549-110">以前のバージョンの [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] には存在するが、以降のバージョンからは削除されている機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="ca549-110">Describes features that existed in earlier versions of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] but that have been removed in later versions.</span></span>|  
|[<span data-ttu-id="ca549-111">SQL Server 2014 における SQL Server Reporting Services の非推奨の機能</span><span class="sxs-lookup"><span data-stu-id="ca549-111">Deprecated Features in SQL Server Reporting Services in SQL Server 2014</span></span>](deprecated-features-in-sql-server-reporting-services-ssrs.md)|<span data-ttu-id="ca549-112">旧バージョンとの互換性を維持するために [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のこのリリースには存在するが、SQL Server の今後のバージョンでは削除される予定の機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="ca549-112">Describes features that exist this release of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] for backward compatibility, but which will be removed in a future version of SQL Server.</span></span>|  
|[<span data-ttu-id="ca549-113">SQL Server 2014 における SQL Server Reporting Services における重大な変更</span><span class="sxs-lookup"><span data-stu-id="ca549-113">Breaking Changes in SQL Server Reporting Services in SQL Server 2014</span></span>](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)|<span data-ttu-id="ca549-114">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]をアップグレードする場合に発生する可能性のある問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="ca549-114">Describes issues that you might encounter when you upgrade [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="ca549-115">SQL Server 2014 における SQL Server Reporting Services の動作変更</span><span class="sxs-lookup"><span data-stu-id="ca549-115">Behavior Changes to SQL Server Reporting Services  in SQL Server 2014</span></span>](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)|<span data-ttu-id="ca549-116">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]で変更されている機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="ca549-116">Describes features that have changed in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ca549-117">参照</span><span class="sxs-lookup"><span data-stu-id="ca549-117">See Also</span></span>  
 <span data-ttu-id="ca549-118">[旧バージョンとの互換性](../../2014/getting-started/backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="ca549-118">[Backward Compatibility](../../2014/getting-started/backward-compatibility.md) </span></span>  
 [<span data-ttu-id="ca549-119">Analysis Services の旧バージョンとの互換性</span><span class="sxs-lookup"><span data-stu-id="ca549-119">Analysis Services Backward Compatibility</span></span>](../../2014/analysis-services/analysis-services-backward-compatibility.md)  
  
  
