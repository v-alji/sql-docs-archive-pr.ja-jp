---
title: MSSQLSERVER_9003 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9003 (Database Engine error)
ms.assetid: 7fdfb391-5c6f-428b-b434-6c3d0b30fd7b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6f67e4184ea54be6bcd5c2a74d3c0e0711b702f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642811"
---
# <a name="mssqlserver_9003"></a><span data-ttu-id="6a828-102">MSSQLSERVER_9003</span><span class="sxs-lookup"><span data-stu-id="6a828-102">MSSQLSERVER_9003</span></span>
    
## <a name="details"></a><span data-ttu-id="6a828-103">詳細</span><span class="sxs-lookup"><span data-stu-id="6a828-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6a828-104">製品名</span><span class="sxs-lookup"><span data-stu-id="6a828-104">Product Name</span></span>|<span data-ttu-id="6a828-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6a828-105">SQL Server</span></span>|  
|<span data-ttu-id="6a828-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="6a828-106">Event ID</span></span>|<span data-ttu-id="6a828-107">9003</span><span class="sxs-lookup"><span data-stu-id="6a828-107">9003</span></span>|  
|<span data-ttu-id="6a828-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="6a828-108">Event Source</span></span>|<span data-ttu-id="6a828-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6a828-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6a828-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6a828-110">Component</span></span>|<span data-ttu-id="6a828-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6a828-111">SQLEngine</span></span>|  
|<span data-ttu-id="6a828-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="6a828-112">Symbolic Name</span></span>|<span data-ttu-id="6a828-113">LOG_INVALID_LSN</span><span class="sxs-lookup"><span data-stu-id="6a828-113">LOG_INVALID_LSN</span></span>|  
|<span data-ttu-id="6a828-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="6a828-114">Message Text</span></span>|<span data-ttu-id="6a828-115">データベース '%.\*ls' のログ スキャンに渡されたログ スキャン番号 %S_LSN は無効です。</span><span class="sxs-lookup"><span data-stu-id="6a828-115">The log scan number %S_LSN passed to log scan in database '%.\*ls' is not valid.</span></span> <span data-ttu-id="6a828-116">このエラーはデータの破損か、またはログ ファイル (.ldf) がデータ ファイル (.mdf) に一致しないことを示している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6a828-116">This error may indicate data corruption or that the log file (.ldf) does not match the data file (.mdf).</span></span> <span data-ttu-id="6a828-117">このエラーがレプリケーション中に発生した場合は、パブリケーションを再作成してください。</span><span class="sxs-lookup"><span data-stu-id="6a828-117">If this error occurred during replication, re-create the publication.</span></span> <span data-ttu-id="6a828-118">この問題が原因でスタートアップ中にエラーが発生した場合は、バックアップから復元してください。</span><span class="sxs-lookup"><span data-stu-id="6a828-118">Otherwise, restore from backup if the problem results in a failure during startup.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6a828-119">説明</span><span class="sxs-lookup"><span data-stu-id="6a828-119">Explanation</span></span>  
 <span data-ttu-id="6a828-120">コンポーネントによって、無効なログ シーケンス番号がデータベースのログ マネージャーに渡されました。</span><span class="sxs-lookup"><span data-stu-id="6a828-120">A component passed an invalid log sequence number to the log manager for the database.</span></span> <span data-ttu-id="6a828-121">レプリケーション、破損、またはプライマリ データ ファイルとログの間の不整合が考えられます。</span><span class="sxs-lookup"><span data-stu-id="6a828-121">This could be replication, corruption, or an inconsistency between the primary data file and the log.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6a828-122">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="6a828-122">User Action</span></span>  
 <span data-ttu-id="6a828-123">これがレプリケーション中に発生した場合は、パブリケーションを再作成してください。</span><span class="sxs-lookup"><span data-stu-id="6a828-123">If this occurred during replication, recreate the publication.</span></span> <span data-ttu-id="6a828-124">それ以外の場合は、バックアップから復元してください。</span><span class="sxs-lookup"><span data-stu-id="6a828-124">Otherwise, restore from backup.</span></span>  
  
  
