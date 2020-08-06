---
title: MSSQLSERVER_17204 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17204 (Database Engine error)
ms.assetid: 40db66f9-dd5e-478c-891e-a06d363a2552
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c63f0b3d2aff8b909e3a7fc841c9038cf95a475e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640041"
---
# <a name="mssqlserver_17204"></a><span data-ttu-id="29ae9-102">MSSQLSERVER_17204</span><span class="sxs-lookup"><span data-stu-id="29ae9-102">MSSQLSERVER_17204</span></span>
    
## <a name="details"></a><span data-ttu-id="29ae9-103">詳細</span><span class="sxs-lookup"><span data-stu-id="29ae9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="29ae9-104">製品名</span><span class="sxs-lookup"><span data-stu-id="29ae9-104">Product Name</span></span>|<span data-ttu-id="29ae9-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="29ae9-105">SQL Server</span></span>|  
|<span data-ttu-id="29ae9-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="29ae9-106">Event ID</span></span>|<span data-ttu-id="29ae9-107">17204</span><span class="sxs-lookup"><span data-stu-id="29ae9-107">17204</span></span>|  
|<span data-ttu-id="29ae9-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="29ae9-108">Event Source</span></span>|<span data-ttu-id="29ae9-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="29ae9-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="29ae9-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="29ae9-110">Component</span></span>|<span data-ttu-id="29ae9-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="29ae9-111">SQLEngine</span></span>|  
|<span data-ttu-id="29ae9-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="29ae9-112">Symbolic Name</span></span>|<span data-ttu-id="29ae9-113">DBLKIO_DEVOPENFAILED</span><span class="sxs-lookup"><span data-stu-id="29ae9-113">DBLKIO_DEVOPENFAILED</span></span>|  
|<span data-ttu-id="29ae9-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="29ae9-114">Message Text</span></span>|<span data-ttu-id="29ae9-115">%ls:ファイル番号 %d のファイル %ls を開けませんでした。</span><span class="sxs-lookup"><span data-stu-id="29ae9-115">%ls: Could not open file %ls for file number %d.</span></span>  <span data-ttu-id="29ae9-116">OS エラー: %ls。</span><span class="sxs-lookup"><span data-stu-id="29ae9-116">OS error: %ls.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="29ae9-117">説明</span><span class="sxs-lookup"><span data-stu-id="29ae9-117">Explanation</span></span>  
 <span data-ttu-id="29ae9-118">SQL Server は、指定されたエラーが原因で指定されたファイルを開くことができませんでした。</span><span class="sxs-lookup"><span data-stu-id="29ae9-118">SQL Server was unable to open the specified file due to the specified error.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="29ae9-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="29ae9-119">User Action</span></span>  
 <span data-ttu-id="29ae9-120">オペレーティング システムを診断して修正してから、操作を再試行してください。</span><span class="sxs-lookup"><span data-stu-id="29ae9-120">Diagnose and correct the operating system, then retry the operation.</span></span>  
  
  
