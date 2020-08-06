---
title: MSSQLSERVER_823 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 823 (Database Engine error)
ms.assetid: 0d9fce3c-3772-46ce-a7a3-4f4988dc6cae
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fa5858bbdc9452a33a3d43fdd783e59556a11e57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640959"
---
# <a name="mssqlserver_823"></a><span data-ttu-id="e5768-102">MSSQLSERVER_823</span><span class="sxs-lookup"><span data-stu-id="e5768-102">MSSQLSERVER_823</span></span>
    
## <a name="details"></a><span data-ttu-id="e5768-103">詳細</span><span class="sxs-lookup"><span data-stu-id="e5768-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e5768-104">製品名</span><span class="sxs-lookup"><span data-stu-id="e5768-104">Product Name</span></span>|<span data-ttu-id="e5768-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e5768-105">SQL Server</span></span>|  
|<span data-ttu-id="e5768-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="e5768-106">Event ID</span></span>|<span data-ttu-id="e5768-107">823</span><span class="sxs-lookup"><span data-stu-id="e5768-107">823</span></span>|  
|<span data-ttu-id="e5768-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="e5768-108">Event Source</span></span>|<span data-ttu-id="e5768-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e5768-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e5768-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="e5768-110">Component</span></span>|<span data-ttu-id="e5768-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e5768-111">SQLEngine</span></span>|  
|<span data-ttu-id="e5768-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="e5768-112">Symbolic Name</span></span>|<span data-ttu-id="e5768-113">B_HARDERR</span><span class="sxs-lookup"><span data-stu-id="e5768-113">B_HARDERR</span></span>|  
|<span data-ttu-id="e5768-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="e5768-114">Message Text</span></span>|<span data-ttu-id="e5768-115">オペレーティング システムにより、ファイル '%ls' のオフセット %#016I64x で %S_MSG 中の SQL Server にエラー %ls が返されました。</span><span class="sxs-lookup"><span data-stu-id="e5768-115">The operating system returned error %ls to SQL Server during a %S_MSG at offset %#016I64x in file '%ls'.</span></span> <span data-ttu-id="e5768-116">SQL Server エラー ログとシステム イベント ログ内の別のメッセージで詳細情報が報告されることもあります。</span><span class="sxs-lookup"><span data-stu-id="e5768-116">Additional messages in the SQL Server error log and system event log may provide more detail.</span></span> <span data-ttu-id="e5768-117">このシステムレベルのエラー状態は深刻で、データベースの一貫性を損なう可能性があるので、すぐに解決する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5768-117">This is a severe system-level error condition that threatens database integrity and must be corrected immediately.</span></span> <span data-ttu-id="e5768-118">完全なデータベース整合性確認 (DBCC CHECKDB) を完了させてください。</span><span class="sxs-lookup"><span data-stu-id="e5768-118">Complete a full database consistency check (DBCC CHECKDB).</span></span> <span data-ttu-id="e5768-119">このエラーには多くの要因があります。詳細については、SQL Server オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5768-119">This error can be caused by many factors; for more information, see SQL Server Books Online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e5768-120">説明</span><span class="sxs-lookup"><span data-stu-id="e5768-120">Explanation</span></span>  
 <span data-ttu-id="e5768-121">Windows の読み取り要求または書き込み要求が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="e5768-121">A Windows read or write request has failed.</span></span> <span data-ttu-id="e5768-122">Windows から返されたエラー コードと、対応するテキストがメッセージに挿入されます。</span><span class="sxs-lookup"><span data-stu-id="e5768-122">The error code that is returned by Windows and the corresponding text are inserted into the message.</span></span> <span data-ttu-id="e5768-123">読み取り要求の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって読み取り要求の再試行が既に 4 回行われています。</span><span class="sxs-lookup"><span data-stu-id="e5768-123">In the read case, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will have already retried the read request four times.</span></span> <span data-ttu-id="e5768-124">このエラーは、ハードウェア エラーの結果として生じることが多く、デバイス ドライバーが原因になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="e5768-124">This error is often the result of a hardware error, but may be caused by the device driver.</span></span> <span data-ttu-id="e5768-125">エラー823の詳細については、「」を参照してください [https://support.microsoft.com/kb/828339](https://support.microsoft.com/kb/828339) 。</span><span class="sxs-lookup"><span data-stu-id="e5768-125">For more information about error 823, see [https://support.microsoft.com/kb/828339](https://support.microsoft.com/kb/828339).</span></span> <span data-ttu-id="e5768-126">I/O エラーの詳細については、「[Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))」 (Microsoft SQL Server I/O の基礎 (第 2 章)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5768-126">For more information about I/O errors, see [Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e5768-127">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="e5768-127">User Action</span></span>  
 <span data-ttu-id="e5768-128">システム イベント ログで詳しい情報を調べます。</span><span class="sxs-lookup"><span data-stu-id="e5768-128">Check for additional information in the system event log.</span></span> <span data-ttu-id="e5768-129">原因と対策については、ハードウェアの製造元またはマイクロソフト カスタマー サポート サービスまでお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="e5768-129">Contact the hardware manufacturer or Microsoft Customer Services and Support to determine the cause and corrective action.</span></span> <span data-ttu-id="e5768-130">ハードウェア エラーの修正後、データベースをすべて復元し、DBCC CHECKDB を実行します。</span><span class="sxs-lookup"><span data-stu-id="e5768-130">After the hardware error is fixed, restore all databases and run DBCC CHECKDB.</span></span>  
  
  
