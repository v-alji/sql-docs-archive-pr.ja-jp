---
title: open objects サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- open objects option
ms.assetid: c8424d3c-86ba-4cc5-bf0c-be4ce44bdd04
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6d22a3d6dd358afe9cf921376664c2d25705a6a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712354"
---
# <a name="open-objects-server-configuration-option"></a><span data-ttu-id="256cc-102">open objects サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="256cc-102">open objects Server Configuration Option</span></span>
  <span data-ttu-id="256cc-103">このオプションは引き続き **sp_configure** に存在しますが、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではその機能は無効になっています。</span><span class="sxs-lookup"><span data-stu-id="256cc-103">This option is still present in **sp_configure**, although its functionality has been disabled in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="256cc-104">(設定しても効果はありません)。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、開いているデータベース オブジェクトの数が動的に管理され、使用できるメモリ量によってのみ制限されます。</span><span class="sxs-lookup"><span data-stu-id="256cc-104">(The setting has no effect.) In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the number of open database objects is managed dynamically and is limited only by the available memory.</span></span> <span data-ttu-id="256cc-105">**open objects** オプションは、既存スクリプトとの互換性のために **sp_configure** で使用できます。</span><span class="sxs-lookup"><span data-stu-id="256cc-105">The **open objects** option available in **sp_configure** for backward compatibility with existing scripts.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="256cc-106">参照</span><span class="sxs-lookup"><span data-stu-id="256cc-106">See Also</span></span>  
 [<span data-ttu-id="256cc-107">サーバー構成オプション &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="256cc-107">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
