---
title: MSSQLSERVER_9002 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9002 (Database Engine error)
ms.assetid: 2e50841f-2b99-45f4-aec5-aa4add70cbeb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b40fe70db8849d09f9296a06cbeed65a9c71e5a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642812"
---
# <a name="mssqlserver_9002"></a><span data-ttu-id="5f03f-102">MSSQLSERVER_9002</span><span class="sxs-lookup"><span data-stu-id="5f03f-102">MSSQLSERVER_9002</span></span>
    
## <a name="details"></a><span data-ttu-id="5f03f-103">詳細</span><span class="sxs-lookup"><span data-stu-id="5f03f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5f03f-104">製品名</span><span class="sxs-lookup"><span data-stu-id="5f03f-104">Product Name</span></span>|<span data-ttu-id="5f03f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5f03f-105">SQL Server</span></span>|  
|<span data-ttu-id="5f03f-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="5f03f-106">Event ID</span></span>|<span data-ttu-id="5f03f-107">9002</span><span class="sxs-lookup"><span data-stu-id="5f03f-107">9002</span></span>|  
|<span data-ttu-id="5f03f-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="5f03f-108">Event Source</span></span>|<span data-ttu-id="5f03f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5f03f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5f03f-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="5f03f-110">Component</span></span>|<span data-ttu-id="5f03f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5f03f-111">SQLEngine</span></span>|  
|<span data-ttu-id="5f03f-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="5f03f-112">Symbolic Name</span></span>|<span data-ttu-id="5f03f-113">LOG_IS_FULL</span><span class="sxs-lookup"><span data-stu-id="5f03f-113">LOG_IS_FULL</span></span>|  
|<span data-ttu-id="5f03f-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="5f03f-114">Message Text</span></span>|<span data-ttu-id="5f03f-115">データベース '%.\*ls' のトランザクション ログがいっぱいです。</span><span class="sxs-lookup"><span data-stu-id="5f03f-115">The transaction log for database '%.\*ls' is full.</span></span> <span data-ttu-id="5f03f-116">ログの領域を再利用できない理由を確認するには、sys.databases の log_reuse_wait_desc 列を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f03f-116">To find out why space in the log cannot be reused, see the log_reuse_wait_desc column in sys.databases.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5f03f-117">説明</span><span class="sxs-lookup"><span data-stu-id="5f03f-117">Explanation</span></span>  
 <span data-ttu-id="5f03f-118">データベース ログの容量不足です。</span><span class="sxs-lookup"><span data-stu-id="5f03f-118">The database log is out of space.</span></span> <span data-ttu-id="5f03f-119">**sys.databases** の **log_reuse_wait_desc** 列に、ログの領域を再利用できない理由の説明があります。</span><span class="sxs-lookup"><span data-stu-id="5f03f-119">The **log_reuse_wait_desc** column in **sys.databases** describes why space in the log cannot be reused.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5f03f-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="5f03f-120">User Action</span></span>  
 <span data-ttu-id="5f03f-121">**sys.databases** を使用して、ログがいっぱいになった理由を調べ、その状況を解決します。</span><span class="sxs-lookup"><span data-stu-id="5f03f-121">Use **sys.databases** to determine why the log is full and then correct the condition.</span></span> <span data-ttu-id="5f03f-122">詳細については、SQL Server オンライン ブックの「満杯になったトランザクション ログのトラブルシューティング (エラー 9002)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f03f-122">For more information, see "Troubleshooting a Full Transaction Log (Error 9002)" in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f03f-123">参照</span><span class="sxs-lookup"><span data-stu-id="5f03f-123">See Also</span></span>  
 <span data-ttu-id="5f03f-124">[満杯になったトランザクション ログのトラブルシューティング &#40;SQL Server エラー 9002&#41;](../logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md) </span><span class="sxs-lookup"><span data-stu-id="5f03f-124">[Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;](../logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md) </span></span>  
 [<span data-ttu-id="5f03f-125">sys.databases &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5f03f-125">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
