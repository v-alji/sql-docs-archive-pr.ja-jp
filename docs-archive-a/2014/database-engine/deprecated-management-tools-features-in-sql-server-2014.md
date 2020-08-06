---
title: SQL Server 2014 | の非推奨の管理ツール機能Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: a08d1354-cc91-4ab7-a73f-3ad815af3d5a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 484e4078e25249e17a1d8b87426a395c3cfa1725
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634012"
---
# <a name="deprecated-management-tools-features-in-sql-server-2014"></a><span data-ttu-id="290d2-102">SQL Server 2014 の非推奨の管理ツール機能</span><span class="sxs-lookup"><span data-stu-id="290d2-102">Deprecated Management Tools Features in SQL Server 2014</span></span>
  <span data-ttu-id="290d2-103">このトピックでは、[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] でまだ使用できるものの、非推奨の管理ツール機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="290d2-103">This topic describes the deprecated Management Tools features that are still available in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="290d2-104">これらの機能は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の今後のリリースで削除される予定です。</span><span class="sxs-lookup"><span data-stu-id="290d2-104">These features are scheduled to be removed in a future release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="290d2-105">非推奨の機能を新しいアプリケーションで使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="290d2-105">Deprecated features should not be used in new applications.</span></span>  
  
|<span data-ttu-id="290d2-106">特徴量</span><span class="sxs-lookup"><span data-stu-id="290d2-106">Feature</span></span>|<span data-ttu-id="290d2-107">非推奨の段階</span><span class="sxs-lookup"><span data-stu-id="290d2-107">Deprecation stage</span></span>|  
|-------------|-----------------------|  
|[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]<span data-ttu-id="290d2-108">登録済みサーバー API</span><span class="sxs-lookup"><span data-stu-id="290d2-108">Registered Server API</span></span>|<span data-ttu-id="290d2-109">告知</span><span class="sxs-lookup"><span data-stu-id="290d2-109">Announcement</span></span>|  
|<span data-ttu-id="290d2-110">sqlps.exe</span><span class="sxs-lookup"><span data-stu-id="290d2-110">sqlps.exe</span></span>|<span data-ttu-id="290d2-111">警告</span><span class="sxs-lookup"><span data-stu-id="290d2-111">Warning</span></span>|  
|<span data-ttu-id="290d2-112">osql.exe</span><span class="sxs-lookup"><span data-stu-id="290d2-112">osql.exe</span></span>|<span data-ttu-id="290d2-113">警告</span><span class="sxs-lookup"><span data-stu-id="290d2-113">Warning</span></span>|  
|<span data-ttu-id="290d2-114">SQLMail</span><span class="sxs-lookup"><span data-stu-id="290d2-114">SQLMail</span></span>|<span data-ttu-id="290d2-115">警告</span><span class="sxs-lookup"><span data-stu-id="290d2-115">Warning</span></span>|  
|<span data-ttu-id="290d2-116">SMO クラス : Microsoft.SQLServer.Management.Smo.Information クラス</span><span class="sxs-lookup"><span data-stu-id="290d2-116">SMO class: Microsoft.SQLServer.Management.Smo.Information class</span></span>|<span data-ttu-id="290d2-117">告知</span><span class="sxs-lookup"><span data-stu-id="290d2-117">Announcement</span></span>|  
|<span data-ttu-id="290d2-118">SMO クラス : Microsoft.SQLServer.Management.Smo.Settings クラス</span><span class="sxs-lookup"><span data-stu-id="290d2-118">SMO class: Microsoft.SQLServer.Management.Smo.Settings class</span></span>|<span data-ttu-id="290d2-119">告知</span><span class="sxs-lookup"><span data-stu-id="290d2-119">Announcement</span></span>|  
|<span data-ttu-id="290d2-120">SMO クラス : Microsoft.SQLServer.Management.Smo.DatabaseOptions クラス</span><span class="sxs-lookup"><span data-stu-id="290d2-120">SMO Class: Microsoft.SQLServer.Management.Smo.DatabaseOptions class</span></span>|<span data-ttu-id="290d2-121">告知</span><span class="sxs-lookup"><span data-stu-id="290d2-121">Announcement</span></span>|  
|<span data-ttu-id="290d2-122">SMO クラス : Microsoft.SqlServer.Management.Smo.DatabaseDdlTrigger.NotForReplication プロパティ</span><span class="sxs-lookup"><span data-stu-id="290d2-122">SMO Class: Microsoft.SqlServer.Management.Smo.DatabaseDdlTrigger.NotForReplication property</span></span>|<span data-ttu-id="290d2-123">告知</span><span class="sxs-lookup"><span data-stu-id="290d2-123">Announcement</span></span>|  
|<span data-ttu-id="290d2-124">SSMS のデータベース プロジェクト システム (ソース管理の統合を含む)</span><span class="sxs-lookup"><span data-stu-id="290d2-124">The Database Project System, including source-control integration, in SSMS</span></span>|<span data-ttu-id="290d2-125">告知</span><span class="sxs-lookup"><span data-stu-id="290d2-125">Announcement</span></span>|  
|<span data-ttu-id="290d2-126">Net Send による通知 ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント)</span><span class="sxs-lookup"><span data-stu-id="290d2-126">Net send notifications ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent)</span></span>|<span data-ttu-id="290d2-127">告知</span><span class="sxs-lookup"><span data-stu-id="290d2-127">Announcement</span></span>|  
|<span data-ttu-id="290d2-128">ポケットベルによる通知 ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント)</span><span class="sxs-lookup"><span data-stu-id="290d2-128">Pager notifications ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent)</span></span>|<span data-ttu-id="290d2-129">告知</span><span class="sxs-lookup"><span data-stu-id="290d2-129">Announcement</span></span>|  
|<span data-ttu-id="290d2-130">ActiveX サブシステム ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント)</span><span class="sxs-lookup"><span data-stu-id="290d2-130">The ActiveX subsystem ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent)</span></span>|<span data-ttu-id="290d2-131">告知</span><span class="sxs-lookup"><span data-stu-id="290d2-131">Announcement</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="290d2-132">参照</span><span class="sxs-lookup"><span data-stu-id="290d2-132">See Also</span></span>  
 [<span data-ttu-id="290d2-133">旧バージョンとの互換性</span><span class="sxs-lookup"><span data-stu-id="290d2-133">Backward Compatibility</span></span>](../../2014/getting-started/backward-compatibility.md)  
  
  
