---
title: MSSQLSERVER_3937 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3937 (Database Engine error)
ms.assetid: 312d5bbe-c8de-42db-af4b-4ccb448ce6ef
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cac466e6eb50ad4b7a8848a1159963cb0fd35e22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715306"
---
# <a name="mssqlserver_3937"></a><span data-ttu-id="1d48d-102">MSSQLSERVER_3937</span><span class="sxs-lookup"><span data-stu-id="1d48d-102">MSSQLSERVER_3937</span></span>
    
## <a name="details"></a><span data-ttu-id="1d48d-103">詳細</span><span class="sxs-lookup"><span data-stu-id="1d48d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1d48d-104">製品名</span><span class="sxs-lookup"><span data-stu-id="1d48d-104">Product Name</span></span>|<span data-ttu-id="1d48d-105">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1d48d-105">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1d48d-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="1d48d-106">Event ID</span></span>|<span data-ttu-id="1d48d-107">3937</span><span class="sxs-lookup"><span data-stu-id="1d48d-107">3937</span></span>|  
|<span data-ttu-id="1d48d-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="1d48d-108">Event Source</span></span>|<span data-ttu-id="1d48d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1d48d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1d48d-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="1d48d-110">Component</span></span>|<span data-ttu-id="1d48d-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1d48d-111">SQLEngine</span></span>|  
|<span data-ttu-id="1d48d-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="1d48d-112">Symbolic Name</span></span>|<span data-ttu-id="1d48d-113">XACT_FILESTREAM_ROLLBACK_ERROR</span><span class="sxs-lookup"><span data-stu-id="1d48d-113">XACT_FILESTREAM_ROLLBACK_ERROR</span></span>|  
|<span data-ttu-id="1d48d-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="1d48d-114">Message Text</span></span>|<span data-ttu-id="1d48d-115">ファイル ストリーム フィルター ドライバーに、トランザクションがロールバックされたことを通知しようとして、エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="1d48d-115">An error occurred while trying to notify the FILESTREAM filter driver that a transaction was rolled back.</span></span> <span data-ttu-id="1d48d-116">エラー コード:0x%0x。</span><span class="sxs-lookup"><span data-stu-id="1d48d-116">Error code: 0x%0x.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1d48d-117">説明</span><span class="sxs-lookup"><span data-stu-id="1d48d-117">Explanation</span></span>  
 <span data-ttu-id="1d48d-118">トランザクションのロールバック通知の発行時に、RsFx ドライバーからエラーが返されました。</span><span class="sxs-lookup"><span data-stu-id="1d48d-118">An error was returned by the RsFx driver when issuing a rollback notification for a transaction.</span></span> <span data-ttu-id="1d48d-119">これは、リソース不足が原因である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1d48d-119">This is probably caused by a resource shortage.</span></span> <span data-ttu-id="1d48d-120">これにより、RsFx フィルター ドライバーで小規模なメモリ リークが発生する場合があります。ただし、このメモリ リークはトランザクションを作成した sqlservr.exe プロセスの終了時に解放されます。</span><span class="sxs-lookup"><span data-stu-id="1d48d-120">This can cause a small memory leak in the RsFx filter driver, but this will be freed when the sqlservr.exe process that created the transaction exits.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1d48d-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="1d48d-121">User Action</span></span>  
  
