---
title: 廃止されたフルテキスト検索プロパティを使用するストアドプロシージャの変更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- discontinued properties [Full-Text Search]
- stored procedures [Full-Text Search]
ms.assetid: 8d9392d9-a9ba-4378-84e4-59f516b67ddb
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 12262a588742f0e3be094e32a2a0208a85b6f28a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640434"
---
# <a name="modify-stored-procedures-that-use-discontinued-full-text-search-properties"></a><span data-ttu-id="83521-102">廃止されたフルテキスト検索プロパティを使用するストアド プロシージャを変更する</span><span class="sxs-lookup"><span data-stu-id="83521-102">Modify stored procedures that use discontinued Full-Text Search properties</span></span>
  <span data-ttu-id="83521-103">ストアド プロシージャが正しく実行されるようにするには、既存のプロシージャを編集し、削除または非推奨とされたフルテキスト関連のプロパティおよび設定を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83521-103">To ensure that your stored procedures perform correctly, you should edit existing procedures and remove those full-text related properties and settings that have been removed or deprecated.</span></span>  
  
## <a name="component"></a><span data-ttu-id="83521-104">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="83521-104">Component</span></span>  
 <span data-ttu-id="83521-105">フルテキスト検索</span><span class="sxs-lookup"><span data-stu-id="83521-105">Full-Text Search</span></span>  
  
## <a name="description"></a><span data-ttu-id="83521-106">説明</span><span class="sxs-lookup"><span data-stu-id="83521-106">Description</span></span>  
 <span data-ttu-id="83521-107">以下のフルテキスト検索関連のプロパティおよび設定が削除されています。</span><span class="sxs-lookup"><span data-stu-id="83521-107">The following Full-Text Search-related properties and settings have been removed.</span></span>  
  
-   <span data-ttu-id="83521-108">**DataTimeout**</span><span class="sxs-lookup"><span data-stu-id="83521-108">**DataTimeout**</span></span>  
  
-   <span data-ttu-id="83521-109">**ConnectTimeout**</span><span class="sxs-lookup"><span data-stu-id="83521-109">**ConnectTimeout**</span></span>  
  
-   <span data-ttu-id="83521-110">**Clean_up**</span><span class="sxs-lookup"><span data-stu-id="83521-110">**Clean_up**</span></span>  
  
-   <span data-ttu-id="83521-111">**LogSize**</span><span class="sxs-lookup"><span data-stu-id="83521-111">**LogSize**</span></span>  
  
 <span data-ttu-id="83521-112">以下のフルテキスト検索関連のプロパティおよび設定が削除または非推奨とされています：</span><span class="sxs-lookup"><span data-stu-id="83521-112">The following Full-Text Search-related properties and settings have been removed or deprecated:</span></span>  
  
-   <span data-ttu-id="83521-113">フルテキスト カタログの "パス"。</span><span class="sxs-lookup"><span data-stu-id="83521-113">'Path' of the Full-Text Catalog.</span></span> <span data-ttu-id="83521-114">フルテキスト カタログは、システムでの特定のファイル パスを持たない論理オブジェクトになります。</span><span class="sxs-lookup"><span data-stu-id="83521-114">The Full-Text Catalog will be a logic object without a specific file path in the system.</span></span>  
  
-   <span data-ttu-id="83521-115">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ではデータベースがフルテキスト検索に対して常に既定で有効になっているので、SP_FULLTEXT_DATABASE の有効化/無効化は効力がありません。</span><span class="sxs-lookup"><span data-stu-id="83521-115">Enable/disable in SP_FULLTEXT_DATABASE has no effect anymore as databases are enabled for Full-Text Search at all times and by default in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="83521-116">修正措置</span><span class="sxs-lookup"><span data-stu-id="83521-116">Corrective Action</span></span>  
 <span data-ttu-id="83521-117">お使いのストアド プロシージャを変更して、これらのプロパティを削除してください。</span><span class="sxs-lookup"><span data-stu-id="83521-117">Modify your stored procedures to remove these properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83521-118">参照</span><span class="sxs-lookup"><span data-stu-id="83521-118">See Also</span></span>  
 [<span data-ttu-id="83521-119">アップグレード アドバイザーの使用</span><span class="sxs-lookup"><span data-stu-id="83521-119">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
