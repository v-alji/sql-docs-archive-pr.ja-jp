---
title: MSSQLSERVER_945 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 945 (Database Engine error)
ms.assetid: ee501d13-0bd9-4627-896c-ed5b1bdb88b3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 51284cdcf48f1bf713a853f9c87457cb5291cc4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640001"
---
# <a name="mssqlserver_945"></a><span data-ttu-id="243f4-102">MSSQLSERVER_945</span><span class="sxs-lookup"><span data-stu-id="243f4-102">MSSQLSERVER_945</span></span>
    
## <a name="details"></a><span data-ttu-id="243f4-103">詳細</span><span class="sxs-lookup"><span data-stu-id="243f4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="243f4-104">製品名</span><span class="sxs-lookup"><span data-stu-id="243f4-104">Product Name</span></span>|<span data-ttu-id="243f4-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="243f4-105">SQL Server</span></span>|  
|<span data-ttu-id="243f4-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="243f4-106">Event ID</span></span>|<span data-ttu-id="243f4-107">945</span><span class="sxs-lookup"><span data-stu-id="243f4-107">945</span></span>|  
|<span data-ttu-id="243f4-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="243f4-108">Event Source</span></span>|<span data-ttu-id="243f4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="243f4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="243f4-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="243f4-110">Component</span></span>|<span data-ttu-id="243f4-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="243f4-111">SQLEngine</span></span>|  
|<span data-ttu-id="243f4-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="243f4-112">Symbolic Name</span></span>|<span data-ttu-id="243f4-113">DB_IS_SHUTDOWN</span><span class="sxs-lookup"><span data-stu-id="243f4-113">DB_IS_SHUTDOWN</span></span>|  
|<span data-ttu-id="243f4-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="243f4-114">Message Text</span></span>|<span data-ttu-id="243f4-115">ファイルにアクセスできないか、メモリまたはディスク領域が不足しているので、データベース '%.\*ls' を開けません。</span><span class="sxs-lookup"><span data-stu-id="243f4-115">Database '%.\*ls' cannot be opened due to inaccessible files or insufficient memory or disk space.</span></span>  <span data-ttu-id="243f4-116">詳細については、SQL Server エラー ログを確認してください。</span><span class="sxs-lookup"><span data-stu-id="243f4-116">See the SQL Server error log for details.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="243f4-117">説明</span><span class="sxs-lookup"><span data-stu-id="243f4-117">Explanation</span></span>  
 <span data-ttu-id="243f4-118">ファイルなどのリソースが存在しないため、データベースにアクセスできませんでした。</span><span class="sxs-lookup"><span data-stu-id="243f4-118">The database could not be accessed because files or other resources are missing.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="243f4-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="243f4-119">User Action</span></span>  
 <span data-ttu-id="243f4-120">エラー ログを参照し、メモリ、ディスク領域、または権限のエラーに関する追加情報を確認してください。</span><span class="sxs-lookup"><span data-stu-id="243f4-120">Check the error log for additional information about memory, disk space, or permission failure.</span></span> <span data-ttu-id="243f4-121">影響を受けたデータベースの .mdf ファイルと .ndf ファイルの場所を確認し、[!INCLUDE[ssDE](../../includes/ssde-md.md)]で使用するアカウントにこれらのファイルへのアクセス権が与えられていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="243f4-121">Confirm the location of the .mdf and .ndf files for the affected database and confirm that the account used by the [!INCLUDE[ssDE](../../includes/ssde-md.md)] has permission to access those files.</span></span> <span data-ttu-id="243f4-122">問題を解決した後、データベースを再起動します。この操作を行うには、ALTER DATABASE を使用して、データベースを ONLINE に設定します。</span><span class="sxs-lookup"><span data-stu-id="243f4-122">After correcting the problem, restart the database by using ALTER DATABASE to set it ONLINE.</span></span>  
  
  
