---
title: 既定では、SQL Server 用の Microsoft フルテキストエンジンは、署名されていないサードパーティのコンポーネントを読み込みません。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Full-Text Engine for SQL service
- MSFTESQL service
ms.assetid: 029f9895-7232-4149-9362-3ab1a4133d21
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 12ff188fb6aa6ac286817a7cc1c3ad726483c886
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646008"
---
# <a name="the-microsoft-full-text-engine-for-sql-server-will-not-load-unsigned-third-party-components-by-default"></a><span data-ttu-id="ef980-102">既定では Microsoft Full-Text Engine for SQL Server は署名のないサード パーティ コンポーネントを読み込まない</span><span class="sxs-lookup"><span data-stu-id="ef980-102">The Microsoft Full-Text Engine for SQL Server will not load unsigned third-party components by default</span></span>
  <span data-ttu-id="ef980-103">既定では、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Full-Text Engine for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] によって署名されていないコンポーネントを読み込みません。</span><span class="sxs-lookup"><span data-stu-id="ef980-103">By default, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Full-Text Engine for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will not load components that are not signed by [!INCLUDE[msCoName](../../includes/msconame-md.md)].</span></span>  
  
## <a name="component"></a><span data-ttu-id="ef980-104">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ef980-104">Component</span></span>  
 <span data-ttu-id="ef980-105">フルテキスト検索</span><span class="sxs-lookup"><span data-stu-id="ef980-105">Full-Text Search</span></span>  
  
## <a name="description"></a><span data-ttu-id="ef980-106">説明</span><span class="sxs-lookup"><span data-stu-id="ef980-106">Description</span></span>  
 <span data-ttu-id="ef980-107">既定では、サーバー上に現在インストールされている PDF フィルターなどのサード パーティのフィルターは、アップグレード後に [!INCLUDE[msCoName](../../includes/msconame-md.md)] Full-Text Engine for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって読み込まれません。</span><span class="sxs-lookup"><span data-stu-id="ef980-107">A third-party filter, such as a PDF filter, that is currently installed on the server will not be loaded by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Full-Text Engine for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by default after upgrade.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="ef980-108">修正措置</span><span class="sxs-lookup"><span data-stu-id="ef980-108">Corrective Action</span></span>  
 <span data-ttu-id="ef980-109">サードパーティのフィルターを読み込むには、 *load_os_resource*を設定し、そのインスタンスの*verify_signature*をオフにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef980-109">To load a third party filter, you must set *load_os_resource* and turn off *verify_signature* on that instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef980-110">参照</span><span class="sxs-lookup"><span data-stu-id="ef980-110">See Also</span></span>  
 [<span data-ttu-id="ef980-111">アップグレード アドバイザーの使用</span><span class="sxs-lookup"><span data-stu-id="ef980-111">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
