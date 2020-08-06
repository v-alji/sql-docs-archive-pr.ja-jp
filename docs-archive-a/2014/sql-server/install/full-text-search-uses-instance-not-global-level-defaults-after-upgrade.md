---
title: アップグレードすると、フルテキスト検索では、グローバルではなくインスタンスレベルのワードブレーカーとフィルターが既定で使用されるようになります。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- filters [Full-Text Search]
- word breakers [Full-Text Search]
ms.assetid: 93ee8fcb-d11c-49fa-8fac-51ed31a8f008
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0b6cea7ab63351fad25f0205a614e364328171a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646003"
---
# <a name="upgrading-will-cause-full-text-search-to-use-instance-level-not-global-word-breakers-and-filters-by-default"></a><span data-ttu-id="516d5-102">既定では、アップグレードにより、グローバルではなく、インスタンス レベルのワード ブレーカーおよびフィルターがフルテキスト検索で使用される</span><span class="sxs-lookup"><span data-stu-id="516d5-102">Upgrading will cause Full-Text Search to use instance-level, not global, word breakers and filters by default</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="516d5-103">では、新しいワード ブレーカーおよびフィルターをインスタンス レベルで登録できる方法が提供されます。</span><span class="sxs-lookup"><span data-stu-id="516d5-103">provides a way to allow instance-level registration of new word breakers and filters.</span></span>  
  
## <a name="component"></a><span data-ttu-id="516d5-104">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="516d5-104">Component</span></span>  
 <span data-ttu-id="516d5-105">フルテキスト検索</span><span class="sxs-lookup"><span data-stu-id="516d5-105">Full-Text Search</span></span>  
  
## <a name="description"></a><span data-ttu-id="516d5-106">説明</span><span class="sxs-lookup"><span data-stu-id="516d5-106">Description</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="516d5-107">では、新しいワード ブレーカーおよびフィルターをインスタンス レベルで登録できます。</span><span class="sxs-lookup"><span data-stu-id="516d5-107">allows the instance-level registration of new word breakers and filters.</span></span> <span data-ttu-id="516d5-108">このインスタンス レベルの登録により、インスタンス間で機能とセキュリティが分離されます。</span><span class="sxs-lookup"><span data-stu-id="516d5-108">This instance-level registration provides functional and security isolation between instances.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="516d5-109">修正措置</span><span class="sxs-lookup"><span data-stu-id="516d5-109">Corrective Action</span></span>  
 <span data-ttu-id="516d5-110">アップグレードした後、`sp_fulltext_service` を使用してサービス プロパティと `load_os_resources` を設定します。これにより、コンポーネントを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="516d5-110">After upgrading, use the `sp_fulltext_service` to set the service property and `load_os_resources`, which allows the components to be loaded.</span></span> <span data-ttu-id="516d5-111">次のコードを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="516d5-111">You must run the following:</span></span>  
  
 `sp_fulltext_service 'load_os_resources', 1`  
  
## <a name="see-also"></a><span data-ttu-id="516d5-112">参照</span><span class="sxs-lookup"><span data-stu-id="516d5-112">See Also</span></span>  
 [<span data-ttu-id="516d5-113">アップグレード アドバイザーの使用</span><span class="sxs-lookup"><span data-stu-id="516d5-113">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
