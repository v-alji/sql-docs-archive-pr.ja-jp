---
title: MSSQLSERVER_5242 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5242 (Database Engine error)
ms.assetid: 712b1a10-2f87-41df-a111-1ed9f14102d4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c979d0a788e80cf5c7e1ab9b9a1ca8eccc0eea19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640017"
---
# <a name="mssqlserver_5242"></a><span data-ttu-id="4c310-102">MSSQLSERVER_5242</span><span class="sxs-lookup"><span data-stu-id="4c310-102">MSSQLSERVER_5242</span></span>
    
## <a name="details"></a><span data-ttu-id="4c310-103">詳細</span><span class="sxs-lookup"><span data-stu-id="4c310-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4c310-104">製品名</span><span class="sxs-lookup"><span data-stu-id="4c310-104">Product Name</span></span>|<span data-ttu-id="4c310-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="4c310-105">SQL Server</span></span>|  
|<span data-ttu-id="4c310-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4c310-106">Event ID</span></span>|<span data-ttu-id="4c310-107">5242</span><span class="sxs-lookup"><span data-stu-id="4c310-107">5242</span></span>|  
|<span data-ttu-id="4c310-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="4c310-108">Event Source</span></span>|<span data-ttu-id="4c310-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="4c310-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="4c310-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="4c310-110">Component</span></span>|<span data-ttu-id="4c310-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="4c310-111">SQLEngine</span></span>|  
|<span data-ttu-id="4c310-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="4c310-112">Symbolic Name</span></span>||  
|<span data-ttu-id="4c310-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="4c310-113">Message Text</span></span>|<span data-ttu-id="4c310-114">データベース '%.\*ls'(ID:%d) のページ %S_PGID で内部操作中に、一貫性が損なわれていることが検出されました。</span><span class="sxs-lookup"><span data-stu-id="4c310-114">An inconsistency was detected during an internal operation in database '%.\*ls'(ID:%d) on page %S_PGID.</span></span> <span data-ttu-id="4c310-115">テクニカル サポートにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="4c310-115">Please contact technical support.</span></span> <span data-ttu-id="4c310-116">参照番号 %ld。</span><span class="sxs-lookup"><span data-stu-id="4c310-116">Reference number %ld.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4c310-117">説明</span><span class="sxs-lookup"><span data-stu-id="4c310-117">Explanation</span></span>  
 <span data-ttu-id="4c310-118">エラー メッセージで参照されているデータベース ページで構造の一貫性が損なわれています。</span><span class="sxs-lookup"><span data-stu-id="4c310-118">A structural inconsistency occurred on the database page that is referenced in the error message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c310-119">参照</span><span class="sxs-lookup"><span data-stu-id="4c310-119">See Also</span></span>  
 <span data-ttu-id="4c310-120">[DBCC CHECKDB &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4c310-120">[DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span></span>  
 [<span data-ttu-id="4c310-121">データベース ファイルとファイル グループ</span><span class="sxs-lookup"><span data-stu-id="4c310-121">Database Files and Filegroups</span></span>](../databases/database-files-and-filegroups.md)  
  
  
