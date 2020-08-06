---
title: Master、tempdb、および model データベースのフルテキストインデックスはサポートされていません |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes
ms.assetid: f7992965-42c1-4eb8-a7fb-afb38b67c740
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fbd5e3133ed87fed9bdaf6d668df62c6471df766
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646006"
---
# <a name="full-text-indexes-on-master-tempdb-and-model-databases-are-not-supported"></a><span data-ttu-id="03597-102">master、tempdb、および model データベースに対するフルテキスト インデックスはサポートされない</span><span class="sxs-lookup"><span data-stu-id="03597-102">Full-text indexes on master, tempdb and model databases are not supported</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="03597-103">では、いずれのシステム データベースに対してもフルテキスト インデックスが許可されません。</span><span class="sxs-lookup"><span data-stu-id="03597-103">does not allow full-text indexes on any system database.</span></span>  
  
## <a name="description"></a><span data-ttu-id="03597-104">説明</span><span class="sxs-lookup"><span data-stu-id="03597-104">Description</span></span>  
 <span data-ttu-id="03597-105">[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] では、フルテキスト インデックスが master、tempdb、および model の各データベースでサポートされていました。</span><span class="sxs-lookup"><span data-stu-id="03597-105">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], full-text indexes were supported on the master, tempdb, and model databases.</span></span>  
  
 <span data-ttu-id="03597-106">Master、tempdb、および model の各データベース内のフルテキストカタログは、アップグレード中に削除されます。</span><span class="sxs-lookup"><span data-stu-id="03597-106">Any full-text catalogs in the master, tempdb, and model databases are removed during the upgrade.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03597-107">参照</span><span class="sxs-lookup"><span data-stu-id="03597-107">See Also</span></span>  
 [<span data-ttu-id="03597-108">アップグレード アドバイザーの使用</span><span class="sxs-lookup"><span data-stu-id="03597-108">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
