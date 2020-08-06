---
title: SQL Server の旧バージョンとの互換性 |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ac47cb74-5578-417d-bcef-f970d9527705
author: rothja
ms.author: jroth
ms.openlocfilehash: a4d38041ce4daa12911dc706d382460324931c90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714526"
---
# <a name="sql-server-backward-compatibility"></a><span data-ttu-id="da739-102">SQL Server の旧バージョンとの互換性</span><span class="sxs-lookup"><span data-stu-id="da739-102">SQL Server Backward Compatibility</span></span>
  <span data-ttu-id="da739-103">「旧バージョンとの互換性」セクションのトピックでは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のバージョン間の動作の変更について説明し [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="da739-103">Topics in the backward compatibility section describe changes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] behavior between versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="da739-104">このトピック領域に含まれる機能には、データ プログラミング、セキュリティ構成ツール、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] セットアップ、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] サービス、およびその他の幅広い機能の変更が含まれます。</span><span class="sxs-lookup"><span data-stu-id="da739-104">Features included in this topic area include data programmability, surface area configuration tools, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Setup, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] services, and other broad functionality changes.</span></span>  
  
|<span data-ttu-id="da739-105">トピック</span><span class="sxs-lookup"><span data-stu-id="da739-105">Topic</span></span>|<span data-ttu-id="da739-106">説明</span><span class="sxs-lookup"><span data-stu-id="da739-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="da739-107">SQL Server 2014 の非推奨の SQL Server 機能</span><span class="sxs-lookup"><span data-stu-id="da739-107">Deprecated SQL Server Features in SQL Server 2014</span></span>](../../2014/getting-started/deprecated-sql-server-features-in-sql-server-2014.md)|<span data-ttu-id="da739-108">このリリースで非推奨とされた [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 機能。</span><span class="sxs-lookup"><span data-stu-id="da739-108">Deprecated [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] features in this release.</span></span> <span data-ttu-id="da739-109">このトピックでは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の構成とセットアップ機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="da739-109">This topic covers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration, and Setup functionality.</span></span>|  
|[<span data-ttu-id="da739-110">SQL Server 2014 で提供が中止された機能</span><span class="sxs-lookup"><span data-stu-id="da739-110">Discontinued SQL Server Features in SQL Server 2014</span></span>](../../2014/getting-started/discontinued-sql-server-features-in-sql-server-2014.md)|<span data-ttu-id="da739-111">このリリースで廃止された [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 機能。</span><span class="sxs-lookup"><span data-stu-id="da739-111">Discontinued [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] functionality in this release.</span></span> <span data-ttu-id="da739-112">このトピックでは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の構成とセットアップ機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="da739-112">This topic covers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration, and Setup functionality.</span></span>|  
|[<span data-ttu-id="da739-113">SQL Server 2014 における SQL Server 機能の重大な変更</span><span class="sxs-lookup"><span data-stu-id="da739-113">Breaking Changes to SQL Server Features in SQL Server 2014</span></span>](../../2014/getting-started/breaking-changes-to-sql-server-features-in-sql-server-2014.md)|<span data-ttu-id="da739-114">場合によっては、アプリケーションの修正が必要となる変更。</span><span class="sxs-lookup"><span data-stu-id="da739-114">Changes that might require changes to applications.</span></span> <span data-ttu-id="da739-115">このトピックでは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の構成とセットアップ機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="da739-115">This topic covers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration, and Setup functionality.</span></span>|  
|[<span data-ttu-id="da739-116">SQL Server 2014 における SQL Server 機能の動作の変更</span><span class="sxs-lookup"><span data-stu-id="da739-116">Behavior Changes to SQL Server Features in SQL Server 2014</span></span>](../../2014/getting-started/behavior-changes-to-sql-server-features-in-sql-server-2014.md)|<span data-ttu-id="da739-117">今回のリリースで [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 機能に加えられた動作の変更。</span><span class="sxs-lookup"><span data-stu-id="da739-117">Behavioral  changes to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] features in this release.</span></span> <span data-ttu-id="da739-118">このトピックでは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の構成とセットアップ機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="da739-118">This topic covers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration, and Setup functionality.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="da739-119">参照</span><span class="sxs-lookup"><span data-stu-id="da739-119">See Also</span></span>  
 [<span data-ttu-id="da739-120">旧バージョンとの互換性</span><span class="sxs-lookup"><span data-stu-id="da739-120">Backward Compatibility</span></span>](../../2014/getting-started/backward-compatibility.md)  
  
  
