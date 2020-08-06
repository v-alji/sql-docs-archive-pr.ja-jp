---
title: フルテキストカタログ名の長さは、120文字に制限されます。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text catalogs names
ms.assetid: 50633373-83f6-4ed9-99b9-71f92479a14f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fa9b06fa6fe4acd79782c19a8814357721e59c24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645994"
---
# <a name="length-of-full-text-catalog-names-restricted-to-120-characters"></a><span data-ttu-id="bf694-102">フルテキスト カタログ名が最長 120 文字に制限されている</span><span class="sxs-lookup"><span data-stu-id="bf694-102">Length of full-text catalog names restricted to 120 characters</span></span>
  <span data-ttu-id="bf694-103">フルテキスト カタログ名の長さが 120 文字に制限されており、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] における最大長 (128 文字) より文字数が少なくなっています。</span><span class="sxs-lookup"><span data-stu-id="bf694-103">The length of full-text catalog names is restricted to 120 characters, reduced from the 128 character restriction in previous releases of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="description"></a><span data-ttu-id="bf694-104">説明</span><span class="sxs-lookup"><span data-stu-id="bf694-104">Description</span></span>  
 <span data-ttu-id="bf694-105">この変更は既存のカタログ名には影響しません。ただし、120 文字よりも長い名前を持つフルテキスト カタログを作成するスクリプトはエラーになります。</span><span class="sxs-lookup"><span data-stu-id="bf694-105">This change does not affect existing catalog names; however, scripts that create full-text catalogs with names longer than 120 characters result in an error.</span></span> <span data-ttu-id="bf694-106">カタログ名は、カタログに対応する論理ファイル名の生成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="bf694-106">The catalog names are used to generate logical file names that correspond to catalogs.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="bf694-107">修正措置</span><span class="sxs-lookup"><span data-stu-id="bf694-107">Corrective Action</span></span>  
 <span data-ttu-id="bf694-108">フルテキスト カタログを作成するすべてのスクリプトを変更し、カタログ名を 120 文字までにします。</span><span class="sxs-lookup"><span data-stu-id="bf694-108">Modify all scripts that create full-text catalogs to ensure that they restrict catalog names to 120 characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf694-109">参照</span><span class="sxs-lookup"><span data-stu-id="bf694-109">See Also</span></span>  
 [<span data-ttu-id="bf694-110">アップグレード アドバイザーの使用</span><span class="sxs-lookup"><span data-stu-id="bf694-110">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
