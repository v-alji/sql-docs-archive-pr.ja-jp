---
title: MSSQLSERVER_125 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "125"
helpviewer_keywords:
- 125 (Database Engine error)
ms.assetid: 0f58338d-2ea0-48b8-8a20-c438b0940433
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 59c732d80ccfafc8f242bb1c42fe60e3dea81f19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641008"
---
# <a name="mssqlserver_125"></a><span data-ttu-id="02540-102">MSSQLSERVER_125</span><span class="sxs-lookup"><span data-stu-id="02540-102">MSSQLSERVER_125</span></span>
    
## <a name="details"></a><span data-ttu-id="02540-103">詳細</span><span class="sxs-lookup"><span data-stu-id="02540-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="02540-104">製品名</span><span class="sxs-lookup"><span data-stu-id="02540-104">Product Name</span></span>|<span data-ttu-id="02540-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="02540-105">SQL Server</span></span>|  
|<span data-ttu-id="02540-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="02540-106">Event ID</span></span>|<span data-ttu-id="02540-107">125</span><span class="sxs-lookup"><span data-stu-id="02540-107">125</span></span>|  
|<span data-ttu-id="02540-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="02540-108">Event Source</span></span>|<span data-ttu-id="02540-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="02540-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="02540-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="02540-110">Component</span></span>|<span data-ttu-id="02540-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="02540-111">SQLEngine</span></span>|  
|<span data-ttu-id="02540-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="02540-112">Symbolic Name</span></span>||  
|<span data-ttu-id="02540-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="02540-113">Message Text</span></span>|<span data-ttu-id="02540-114">Case 式は、%d レベルまでしか入れ子にできません。</span><span class="sxs-lookup"><span data-stu-id="02540-114">Case expressions may only be nested to level %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="02540-115">説明</span><span class="sxs-lookup"><span data-stu-id="02540-115">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="02540-116">では、Case 式に入れ子にできるのは 10 レベルまでです。</span><span class="sxs-lookup"><span data-stu-id="02540-116">allows for only 10 levels of nesting in CASE expressions.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="02540-117">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="02540-117">User Action</span></span>  
 <span data-ttu-id="02540-118">Case ステートメントのレベルを 10 以下にします。</span><span class="sxs-lookup"><span data-stu-id="02540-118">Reduce the level of CASE statements to 10 or less.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02540-119">参照</span><span class="sxs-lookup"><span data-stu-id="02540-119">See Also</span></span>  
 [<span data-ttu-id="02540-120">CASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="02540-120">CASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/case-transact-sql)  
  
  
