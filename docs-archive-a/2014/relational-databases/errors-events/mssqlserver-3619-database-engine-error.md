---
title: MSSQLSERVER_3619 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3619 (Database Engine error)
ms.assetid: 7d94f8d9-65ca-4fde-9c17-7b83e94a3779
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2328ee6366d47130a02c444bce65b7b655af7965
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643853"
---
# <a name="mssqlserver_3619"></a><span data-ttu-id="33edd-102">MSSQLSERVER_3619</span><span class="sxs-lookup"><span data-stu-id="33edd-102">MSSQLSERVER_3619</span></span>
    
## <a name="details"></a><span data-ttu-id="33edd-103">詳細</span><span class="sxs-lookup"><span data-stu-id="33edd-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="33edd-104">製品名</span><span class="sxs-lookup"><span data-stu-id="33edd-104">Product Name</span></span>|<span data-ttu-id="33edd-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="33edd-105">SQL Server</span></span>|  
|<span data-ttu-id="33edd-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="33edd-106">Event ID</span></span>|<span data-ttu-id="33edd-107">3619</span><span class="sxs-lookup"><span data-stu-id="33edd-107">3619</span></span>|  
|<span data-ttu-id="33edd-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="33edd-108">Event Source</span></span>|<span data-ttu-id="33edd-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="33edd-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="33edd-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="33edd-110">Component</span></span>|<span data-ttu-id="33edd-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="33edd-111">SQLEngine</span></span>|  
|<span data-ttu-id="33edd-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="33edd-112">Symbolic Name</span></span>|<span data-ttu-id="33edd-113">SYS_NOLOG</span><span class="sxs-lookup"><span data-stu-id="33edd-113">SYS_NOLOG</span></span>|  
|<span data-ttu-id="33edd-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="33edd-114">Message Text</span></span>|<span data-ttu-id="33edd-115">ログに空き領域がないので、データベース ID %d にチェックポイント レコードを書き込めませんでした。</span><span class="sxs-lookup"><span data-stu-id="33edd-115">Could not write a checkpoint record in database ID %d because the log is out of space.</span></span> <span data-ttu-id="33edd-116">データベース管理者に問い合わせて、ログを切り捨てるか、データベース ログ ファイルに追加領域を割り当ててください。</span><span class="sxs-lookup"><span data-stu-id="33edd-116">Contact the database administrator to truncate the log or allocate more space to the database log files.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="33edd-117">説明</span><span class="sxs-lookup"><span data-stu-id="33edd-117">Explanation</span></span>  
 <span data-ttu-id="33edd-118">トランザクション ログ用のディスク容量が不足しています。</span><span class="sxs-lookup"><span data-stu-id="33edd-118">The transaction log is out of disk space.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="33edd-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="33edd-119">User Action</span></span>  
 <span data-ttu-id="33edd-120">ログの切り捨てを行って容量を解放するか、ログ ファイルに追加領域を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="33edd-120">Truncate the log to release some space, or allocate more space to the log.</span></span> <span data-ttu-id="33edd-121">詳細については、SQL Server オンライン ブックの「満杯になったトランザクション ログのトラブルシューティング (エラー 9002)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="33edd-121">For more information see, "Troubleshooting a Full Transaction Log (Error 9002)" in SQL Server Books Online.</span></span>  
  
  
