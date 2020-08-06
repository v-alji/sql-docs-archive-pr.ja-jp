---
title: MSSQLSERVER_3452 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3452 (Database Engine error)
ms.assetid: bf838f02-7186-4b33-b01e-361b0c02de1f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 662d342064e8094400a6b672e21704877b4d0448
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631058"
---
# <a name="mssqlserver_3452"></a><span data-ttu-id="78650-102">MSSQLSERVER_3452</span><span class="sxs-lookup"><span data-stu-id="78650-102">MSSQLSERVER_3452</span></span>
    
## <a name="details"></a><span data-ttu-id="78650-103">詳細</span><span class="sxs-lookup"><span data-stu-id="78650-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="78650-104">製品名</span><span class="sxs-lookup"><span data-stu-id="78650-104">Product Name</span></span>|<span data-ttu-id="78650-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="78650-105">SQL Server</span></span>|  
|<span data-ttu-id="78650-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="78650-106">Event ID</span></span>|<span data-ttu-id="78650-107">3452</span><span class="sxs-lookup"><span data-stu-id="78650-107">3452</span></span>|  
|<span data-ttu-id="78650-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="78650-108">Event Source</span></span>|<span data-ttu-id="78650-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="78650-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="78650-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="78650-110">Component</span></span>|<span data-ttu-id="78650-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="78650-111">SQLEngine</span></span>|  
|<span data-ttu-id="78650-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="78650-112">Symbolic Name</span></span>|<span data-ttu-id="78650-113">REC_CHECKIDENTITY</span><span class="sxs-lookup"><span data-stu-id="78650-113">REC_CHECKIDENTITY</span></span>|  
|<span data-ttu-id="78650-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="78650-114">Message Text</span></span>|<span data-ttu-id="78650-115">データベース '%.\*ls' (%d) の復旧でテーブル %d の ID 値の一貫性が損なわれているのを検出しました。</span><span class="sxs-lookup"><span data-stu-id="78650-115">Recovery of database '%.\*ls' (%d) detected possible identity value inconsistency in table ID %d.</span></span> <span data-ttu-id="78650-116">DBCC CHECKIDENT ('%.\*ls') を実行してください。</span><span class="sxs-lookup"><span data-stu-id="78650-116">Run DBCC CHECKIDENT ('%.\*ls').</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="78650-117">説明</span><span class="sxs-lookup"><span data-stu-id="78650-117">Explanation</span></span>  
 <span data-ttu-id="78650-118">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] へのアップグレード作業中に、データベース内の ID 値を復元するプロセスで、メタデータの不整合が検出されました。</span><span class="sxs-lookup"><span data-stu-id="78650-118">During the upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the process to recover the identity values in the database found an inconsistency in the metadata.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="78650-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="78650-119">User Action</span></span>  
 <span data-ttu-id="78650-120">DBCC CHECKIDENT を実行します。</span><span class="sxs-lookup"><span data-stu-id="78650-120">Run DBCC CHECKIDENT.</span></span>  
  
  
