---
title: MSSQLSERVER_8689 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8689 (Database Engine error)
ms.assetid: 99467a32-6576-4272-a076-b16c06933f2a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2cdca0a3cd9ce47ccb39ebeaf8fd1cd260aafbd9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714369"
---
# <a name="mssqlserver_8689"></a><span data-ttu-id="604c1-102">MSSQLSERVER_8689</span><span class="sxs-lookup"><span data-stu-id="604c1-102">MSSQLSERVER_8689</span></span>
    
## <a name="details"></a><span data-ttu-id="604c1-103">詳細</span><span class="sxs-lookup"><span data-stu-id="604c1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="604c1-104">製品名</span><span class="sxs-lookup"><span data-stu-id="604c1-104">Product Name</span></span>|<span data-ttu-id="604c1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="604c1-105">SQL Server</span></span>|  
|<span data-ttu-id="604c1-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="604c1-106">Event ID</span></span>|<span data-ttu-id="604c1-107">8689</span><span class="sxs-lookup"><span data-stu-id="604c1-107">8689</span></span>|  
|<span data-ttu-id="604c1-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="604c1-108">Event Source</span></span>|<span data-ttu-id="604c1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="604c1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="604c1-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="604c1-110">Component</span></span>|<span data-ttu-id="604c1-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="604c1-111">SQLEngine</span></span>|  
|<span data-ttu-id="604c1-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="604c1-112">Symbolic Name</span></span>|<span data-ttu-id="604c1-113">USEPLAN_ERR_NO_DB</span><span class="sxs-lookup"><span data-stu-id="604c1-113">USEPLAN_ERR_NO_DB</span></span>|  
|<span data-ttu-id="604c1-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="604c1-114">Message Text</span></span>|<span data-ttu-id="604c1-115">USE PLAN ヒントで指定されたデータベース '%.\*ls' は存在しません。</span><span class="sxs-lookup"><span data-stu-id="604c1-115">Database '%.\*ls', specified in the USE PLAN hint, does not exist.</span></span> <span data-ttu-id="604c1-116">既存のデータベースを指定してください。</span><span class="sxs-lookup"><span data-stu-id="604c1-116">Specify an existing database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="604c1-117">説明</span><span class="sxs-lookup"><span data-stu-id="604c1-117">Explanation</span></span>  
 <span data-ttu-id="604c1-118">USE PLAN ヒントで指定したデータベースが存在しません。</span><span class="sxs-lookup"><span data-stu-id="604c1-118">A database that is specified in the USE PLAN hint does not exist.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="604c1-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="604c1-119">User Action</span></span>  
 <span data-ttu-id="604c1-120">USE PLAN ヒントで指定したすべてのデータベースが存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="604c1-120">Ensure all databases that are specified in the USE PLAN hint exist.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="604c1-121">参照</span><span class="sxs-lookup"><span data-stu-id="604c1-121">See Also</span></span>  
 <span data-ttu-id="604c1-122">[クエリ ヒント &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span><span class="sxs-lookup"><span data-stu-id="604c1-122">[Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span></span>  
 [<span data-ttu-id="604c1-123">プラン ガイド</span><span class="sxs-lookup"><span data-stu-id="604c1-123">Plan Guides</span></span>](../performance/plan-guides.md)  
  
  
