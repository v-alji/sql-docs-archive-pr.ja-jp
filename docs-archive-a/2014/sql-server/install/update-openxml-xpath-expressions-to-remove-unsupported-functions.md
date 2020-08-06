---
title: サポートされていない関数を削除するように OPENXML XPath 式を更新する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- OPENXML queries
ms.assetid: b459abaf-8787-4b65-9231-ae30e5469fd0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2c64408d6d705654014b6d071012001374a5f486
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640391"
---
# <a name="update-openxml-xpath-expressions-to-remove-unsupported-functions"></a><span data-ttu-id="8b71f-102">OPENXML XPath 式の更新によりサポートされていない関数が削除される</span><span class="sxs-lookup"><span data-stu-id="8b71f-102">Update OPENXML XPath expressions to remove unsupported functions</span></span>
  <span data-ttu-id="8b71f-103">アップグレード アドバイザーによって、XPath 機能の使用が検出されました。</span><span class="sxs-lookup"><span data-stu-id="8b71f-103">Upgrade Advisor detected the use of XPath functionality.</span></span> <span data-ttu-id="8b71f-104">OPENXML の XPath 機能が変更されているので、アップグレードした後でその影響を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8b71f-104">You may be affected by changes in XPath functionality for OPENXML features after you upgrade.</span></span>  
  
## <a name="component"></a><span data-ttu-id="8b71f-105">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="8b71f-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="8b71f-106">説明</span><span class="sxs-lookup"><span data-stu-id="8b71f-106">Description</span></span>  
 <span data-ttu-id="8b71f-107">現在では、MSXML 3.0 が、OPENXML クエリ内で使用される XPath 式を処理するための基本エンジンとなっています。</span><span class="sxs-lookup"><span data-stu-id="8b71f-107">MSXML 3.0 is now the underlying engine that is used to process XPath expressions that are used within OPENXML queries.</span></span> <span data-ttu-id="8b71f-108">MSXML 3.0 には、より精密な XPath 1.0 エンジンがあります。これにより、以下の関数のサポートが削除されています。</span><span class="sxs-lookup"><span data-stu-id="8b71f-108">MSXML 3.0 has a stricter XPath 1.0 engine in which support for the following functions has been removed:</span></span>  
  
-   <span data-ttu-id="8b71f-109">format-number()</span><span class="sxs-lookup"><span data-stu-id="8b71f-109">format-number()</span></span>  
  
-   <span data-ttu-id="8b71f-110">formatNumber()</span><span class="sxs-lookup"><span data-stu-id="8b71f-110">formatNumber()</span></span>  
  
-   <span data-ttu-id="8b71f-111">current()</span><span class="sxs-lookup"><span data-stu-id="8b71f-111">current()</span></span>  
  
-   <span data-ttu-id="8b71f-112">element-available()</span><span class="sxs-lookup"><span data-stu-id="8b71f-112">element-available()</span></span>  
  
-   <span data-ttu-id="8b71f-113">function-available()</span><span class="sxs-lookup"><span data-stu-id="8b71f-113">function-available()</span></span>  
  
-   <span data-ttu-id="8b71f-114">system-property()</span><span class="sxs-lookup"><span data-stu-id="8b71f-114">system-property()</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="8b71f-115">修正措置</span><span class="sxs-lookup"><span data-stu-id="8b71f-115">Corrective Action</span></span>  
 <span data-ttu-id="8b71f-116">format-number() と formatNumber() の場合、[!INCLUDE[tsql](../../includes/tsql-md.md)] を使用できます。</span><span class="sxs-lookup"><span data-stu-id="8b71f-116">In the case of format-number() and formatNumber(), you can use [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="8b71f-117">前述したその他のサポートされていない関数については、直接的な対応策はありません。</span><span class="sxs-lookup"><span data-stu-id="8b71f-117">For the other unsupported functions listed earlier, there is no direct workaround.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b71f-118">参照</span><span class="sxs-lookup"><span data-stu-id="8b71f-118">See Also</span></span>  
 <span data-ttu-id="8b71f-119">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="8b71f-119">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="8b71f-120">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="8b71f-120">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
