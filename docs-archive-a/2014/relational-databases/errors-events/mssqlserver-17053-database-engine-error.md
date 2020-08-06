---
title: MSSQLSERVER_17053 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17053 (Database Engine error)
ms.assetid: e0a01f3d-d0aa-4c38-8bcc-82e59de50512
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 11137ba334b66f20c7d9a6caaaf7d1ef42c15dec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631061"
---
# <a name="mssqlserver_17053"></a><span data-ttu-id="81348-102">MSSQLSERVER_17053</span><span class="sxs-lookup"><span data-stu-id="81348-102">MSSQLSERVER_17053</span></span>
    
## <a name="details"></a><span data-ttu-id="81348-103">詳細</span><span class="sxs-lookup"><span data-stu-id="81348-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="81348-104">製品名</span><span class="sxs-lookup"><span data-stu-id="81348-104">Product Name</span></span>|<span data-ttu-id="81348-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="81348-105">SQL Server</span></span>|  
|<span data-ttu-id="81348-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="81348-106">Event ID</span></span>|<span data-ttu-id="81348-107">17053</span><span class="sxs-lookup"><span data-stu-id="81348-107">17053</span></span>|  
|<span data-ttu-id="81348-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="81348-108">Event Source</span></span>|<span data-ttu-id="81348-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="81348-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="81348-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="81348-110">Component</span></span>|<span data-ttu-id="81348-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="81348-111">SQLEngine</span></span>|  
|<span data-ttu-id="81348-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="81348-112">Symbolic Name</span></span>|<span data-ttu-id="81348-113">OS_ERROR</span><span class="sxs-lookup"><span data-stu-id="81348-113">OS_ERROR</span></span>|  
|<span data-ttu-id="81348-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="81348-114">Message Text</span></span>|<span data-ttu-id="81348-115">%ls:オペレーティング システム エラー %ls が発生しました。</span><span class="sxs-lookup"><span data-stu-id="81348-115">%ls: Operating system error %ls encountered.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="81348-116">説明</span><span class="sxs-lookup"><span data-stu-id="81348-116">Explanation</span></span>  
 <span data-ttu-id="81348-117">一般的なオペレーティング システム エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="81348-117">Generic operating system error occurred.</span></span>  <span data-ttu-id="81348-118">結果の状態については明らかではありません。</span><span class="sxs-lookup"><span data-stu-id="81348-118">Not clear what the resulting state is.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="81348-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="81348-119">User Action</span></span>  
 <span data-ttu-id="81348-120">通常、他のエラーと共に表示され、エラーの診断に役立てられます。</span><span class="sxs-lookup"><span data-stu-id="81348-120">Usually this is in conjunction with some other error and should be used to help diagnose that failure.</span></span> <span data-ttu-id="81348-121">たとえば、データまたはログ ファイルに対する読み取りや書き込みの失敗、レジストリの読み取り/書き込み操作、またはその他の予期しない Win32API エラーがあります。</span><span class="sxs-lookup"><span data-stu-id="81348-121">Examples would include reads or writes to data or log files that fail, registry read/write operations, or other unexpected Win32API failures.</span></span>  
  
  
