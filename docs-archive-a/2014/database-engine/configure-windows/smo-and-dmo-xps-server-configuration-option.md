---
title: SMO and DMO XPs サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: bcd945ba-5d81-4124-9a2b-d87491c2a369
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f18fc6fafcf033113c983f990700158a10aec92a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740410"
---
# <a name="smo-and-dmo-xps-server-configuration-option"></a><span data-ttu-id="577b0-102">SMO and DMO XPs サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="577b0-102">SMO and DMO XPs Server Configuration Option</span></span>
  <span data-ttu-id="577b0-103">このサーバーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) の拡張ストアド プロシージャを使用するには、SMO and DMO XPs オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="577b0-103">Use the SMO and DMO XPs option to enable [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object (SMO) extended stored procedures on this server.</span></span>  
  
 <span data-ttu-id="577b0-104">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]の DMO は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で削除されました。</span><span class="sxs-lookup"><span data-stu-id="577b0-104">Note than beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], DMO has been removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="577b0-105">次の表に、このオプションで使用可能な値を示します。</span><span class="sxs-lookup"><span data-stu-id="577b0-105">The possible values are described in the following table:</span></span>  
  
|<span data-ttu-id="577b0-106">値</span><span class="sxs-lookup"><span data-stu-id="577b0-106">Value</span></span>|<span data-ttu-id="577b0-107">意味</span><span class="sxs-lookup"><span data-stu-id="577b0-107">Meaning</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="577b0-108">0</span><span class="sxs-lookup"><span data-stu-id="577b0-108">0</span></span>|<span data-ttu-id="577b0-109">SMO 拡張ストアド プロシージャ (XP) を使用できません。</span><span class="sxs-lookup"><span data-stu-id="577b0-109">SMO XPs are not available.</span></span>|  
|<span data-ttu-id="577b0-110">1</span><span class="sxs-lookup"><span data-stu-id="577b0-110">1</span></span>|<span data-ttu-id="577b0-111">SMO 拡張ストアド プロシージャ (XP) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="577b0-111">SMO XPs are available.</span></span> <span data-ttu-id="577b0-112">これは既定値です。</span><span class="sxs-lookup"><span data-stu-id="577b0-112">This is the default.</span></span>|  
  
 <span data-ttu-id="577b0-113">設定はすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="577b0-113">The setting takes effect immediately.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="577b0-114">例</span><span class="sxs-lookup"><span data-stu-id="577b0-114">Examples</span></span>  
 <span data-ttu-id="577b0-115">次の例では、SMO の拡張ストアド プロシージャを有効にします。</span><span class="sxs-lookup"><span data-stu-id="577b0-115">The following example enables SMO extended stored procedures.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'SMO and DMO XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="577b0-116">参照</span><span class="sxs-lookup"><span data-stu-id="577b0-116">See Also</span></span>  
 [<span data-ttu-id="577b0-117">SQL Server 管理オブジェクト &#40;SMO&#41; プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="577b0-117">SQL Server Management Objects &#40;SMO&#41; Programming Guide</span></span>](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
  
