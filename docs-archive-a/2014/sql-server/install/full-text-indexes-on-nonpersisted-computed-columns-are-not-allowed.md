---
title: なのフルテキストインデックス、計算列は使用できません |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes
ms.assetid: cba737f7-b187-47d0-8458-23dc18d18aca
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: de153d45e2f652bfea6e9dce68428af84be68b6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646005"
---
# <a name="full-text-indexes-on-nonpersisted-computed-columns-are-not-allowed"></a><span data-ttu-id="1a341-102">保存されない計算列にフルテキスト インデックスを使用できない</span><span class="sxs-lookup"><span data-stu-id="1a341-102">Full-text indexes on nonpersisted, computed columns are not allowed</span></span>
  <span data-ttu-id="1a341-103">非決定的な計算列と不正確な計算列に対してフルテキスト インデックスを作成できません。</span><span class="sxs-lookup"><span data-stu-id="1a341-103">You cannot create full-text indexes on nondeterministic and imprecise computed columns.</span></span> <span data-ttu-id="1a341-104">このような列は、型列やフルテキスト キー列として使用できません。</span><span class="sxs-lookup"><span data-stu-id="1a341-104">Such columns cannot be used as type columns or as full-text key columns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1a341-105">説明</span><span class="sxs-lookup"><span data-stu-id="1a341-105">Description</span></span>  
 <span data-ttu-id="1a341-106">[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] では、非決定的な計算列と不正確な計算列を型列やフルテキスト キー列として使用してフルテキスト インデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1a341-106">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], a full-text index can be created by using a nondeterministic and imprecise computed column as the type column or the full-text key column.</span></span> <span data-ttu-id="1a341-107">この機能はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="1a341-107">This functionality is not supported.</span></span> <span data-ttu-id="1a341-108">アップグレードすると、古くて互換性のない、サポート対象外のフルテキスト インデックスは無効になります。</span><span class="sxs-lookup"><span data-stu-id="1a341-108">When you upgrade, older, incompatible, and unsupported full-text indexes are disabled.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="1a341-109">修正措置</span><span class="sxs-lookup"><span data-stu-id="1a341-109">Corrective Action</span></span>  
 <span data-ttu-id="1a341-110">このようなフルテキスト インデックスを有効にするには、列の定義を変更して決定的かつ正確にします。</span><span class="sxs-lookup"><span data-stu-id="1a341-110">To enable these full-text indexes, modify the column definitions so that the columns are deterministic and precise.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a341-111">参照</span><span class="sxs-lookup"><span data-stu-id="1a341-111">See Also</span></span>  
 [<span data-ttu-id="1a341-112">アップグレード アドバイザーの使用</span><span class="sxs-lookup"><span data-stu-id="1a341-112">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
