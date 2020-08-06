---
title: データベースメンテナンスプランの置き換え |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- suspended database maintenance plans
- database maintenance plans [SQL Server Agent]
- maintenance plans [SQL Server Agent]
ms.assetid: efac127c-6c81-4c7a-a6c4-9aae5d15545d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3aea75cc4ecc94ccbaeb1f35cecd0b18ff3a65ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631500"
---
# <a name="database-maintenance-plans-superseded"></a><span data-ttu-id="e9d0a-102">データベース メンテナンス プランが新しくなった</span><span class="sxs-lookup"><span data-stu-id="e9d0a-102">Database maintenance plans superseded</span></span>
    
## <a name="component"></a><span data-ttu-id="e9d0a-103">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="e9d0a-103">Component</span></span>  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="e9d0a-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント</span><span class="sxs-lookup"><span data-stu-id="e9d0a-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent</span></span>  
  
## <a name="description"></a><span data-ttu-id="e9d0a-105">説明</span><span class="sxs-lookup"><span data-stu-id="e9d0a-105">Description</span></span>  
 <span data-ttu-id="e9d0a-106">既存のデータベース メンテナンス プランはアップグレードされ、引き続き機能します。</span><span class="sxs-lookup"><span data-stu-id="e9d0a-106">Existing database maintenance plans are upgraded and continue to work.</span></span> <span data-ttu-id="e9d0a-107">ただし、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して新しいデータベース メンテナンス プランを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="e9d0a-107">However, you will not be able to create new database maintenance plans by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="e9d0a-108">オブジェクト エクスプローラーでメンテナンス プランを表示するには、[管理]、[レガシ] の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="e9d0a-108">To view the maintenance plans in Object Explorer, expand Management, and then expand Legacy.</span></span> <span data-ttu-id="e9d0a-109">既存のデータベースメンテナンスプランを新しい形式に移行するには、任意のデータベースメンテナンスプランのコンテキストメニューから [**移行**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e9d0a-109">You can migrate existing database maintenance plans to the new format by selecting **Migrate** from the context menu for any database maintenance plan.</span></span> <span data-ttu-id="e9d0a-110">新しいメンテナンス プランの機能がデータベース メンテナンス プランとそのまま置き換わるわけではないため、移行後に機能の一部が失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e9d0a-110">Because the new maintenance plan feature is not a direct replacement of database maintenance plans, some functionality might be lost after migration.</span></span> <span data-ttu-id="e9d0a-111">データベース メンテナンス プランを移行しても古いプランは削除されません。このため、古いプランを削除する前にメンテナンス プランとしての機能をテストできます。</span><span class="sxs-lookup"><span data-stu-id="e9d0a-111">Migrating a database maintenance plan does not delete the old plan, so you can test its functionality as a maintenance plan before removing the old plan.</span></span>  
  
 <span data-ttu-id="e9d0a-112">次の機能は、データベース メンテナンス プラン内ではサポートされなくなります。</span><span class="sxs-lookup"><span data-stu-id="e9d0a-112">The following features are no longer supported within database maintenance plans:</span></span>  
  
-   <span data-ttu-id="e9d0a-113">ログ配布</span><span class="sxs-lookup"><span data-stu-id="e9d0a-113">Log shipping</span></span>  
  
-   <span data-ttu-id="e9d0a-114">**データベースの整合性チェック**タスクの**軽微な問題を修復しようとしまし**た</span><span class="sxs-lookup"><span data-stu-id="e9d0a-114">The **Attempt to repair any minor problems** option of the **Database Integrity Check** task</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="e9d0a-115">修正措置</span><span class="sxs-lookup"><span data-stu-id="e9d0a-115">Corrective Action</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e9d0a-116">では、ログ配布をデータベース メンテナンス プランに含めることができません。</span><span class="sxs-lookup"><span data-stu-id="e9d0a-116">prevents log shipping from being included in a database maintenance plan.</span></span> <span data-ttu-id="e9d0a-117">詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「ログ配布」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9d0a-117">For more information, see "Log Shipping" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
  
