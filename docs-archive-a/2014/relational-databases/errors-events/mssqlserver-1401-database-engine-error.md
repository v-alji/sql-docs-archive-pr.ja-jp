---
title: MSSQLSERVER_1401 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1401 (Database Engine error)
ms.assetid: 02928770-aa63-4509-8713-406c73e4cedc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 720263939e2f1685649fc41896e8ea10907d92ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643925"
---
# <a name="mssqlserver_1401"></a><span data-ttu-id="22ce4-102">MSSQLSERVER_1401</span><span class="sxs-lookup"><span data-stu-id="22ce4-102">MSSQLSERVER_1401</span></span>
    
## <a name="details"></a><span data-ttu-id="22ce4-103">詳細</span><span class="sxs-lookup"><span data-stu-id="22ce4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="22ce4-104">製品名</span><span class="sxs-lookup"><span data-stu-id="22ce4-104">Product Name</span></span>|<span data-ttu-id="22ce4-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="22ce4-105">SQL Server</span></span>|  
|<span data-ttu-id="22ce4-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="22ce4-106">Event ID</span></span>|<span data-ttu-id="22ce4-107">1401</span><span class="sxs-lookup"><span data-stu-id="22ce4-107">1401</span></span>|  
|<span data-ttu-id="22ce4-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="22ce4-108">Event Source</span></span>|<span data-ttu-id="22ce4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="22ce4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="22ce4-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="22ce4-110">Component</span></span>|<span data-ttu-id="22ce4-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="22ce4-111">SQLEngine</span></span>|  
|<span data-ttu-id="22ce4-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="22ce4-112">Symbolic Name</span></span>|<span data-ttu-id="22ce4-113">DBM_MASTERSTARTUP</span><span class="sxs-lookup"><span data-stu-id="22ce4-113">DBM_MASTERSTARTUP</span></span>|  
|<span data-ttu-id="22ce4-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="22ce4-114">Message Text</span></span>|<span data-ttu-id="22ce4-115">データベース ミラーリングのマスター スレッド ルーチンのスタートアップが次の理由により失敗しました: %ls。</span><span class="sxs-lookup"><span data-stu-id="22ce4-115">Startup of the database-mirroring master thread routine failed for the following reason: %ls.</span></span> <span data-ttu-id="22ce4-116">このエラーの原因を解決して SQL Server サービスを再開してください。</span><span class="sxs-lookup"><span data-stu-id="22ce4-116">Correct the cause of this error, and restart the SQL Server service.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="22ce4-117">説明</span><span class="sxs-lookup"><span data-stu-id="22ce4-117">Explanation</span></span>  
 <span data-ttu-id="22ce4-118">ミラーリングを制御するスレッドのスタートアップに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="22ce4-118">Startup of the mirroring control thread failed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="22ce4-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="22ce4-119">User Action</span></span>  
 <span data-ttu-id="22ce4-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログを調べ、このメッセージの前に関連するエラーが記録されているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="22ce4-120">In the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, look for the associated error that preceded this message.</span></span> <span data-ttu-id="22ce4-121">このエラーの原因を解決したら、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス (MSSQLSERVER) を再開します。</span><span class="sxs-lookup"><span data-stu-id="22ce4-121">Correct the cause of this error, and then restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service (MSSQLSERVER).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22ce4-122">参照</span><span class="sxs-lookup"><span data-stu-id="22ce4-122">See Also</span></span>  
 [<span data-ttu-id="22ce4-123">データベース エンジン、SQL Server エージェント、SQL Server Browser サービスの開始、停止、一時停止、再開、および再起動</span><span class="sxs-lookup"><span data-stu-id="22ce4-123">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
  
