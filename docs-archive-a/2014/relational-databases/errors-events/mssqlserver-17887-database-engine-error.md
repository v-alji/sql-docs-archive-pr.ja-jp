---
title: MSSQLSERVER_17887 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17887 (Database Engine error)
ms.assetid: ad0806e6-3296-4c32-b103-fccf0f8a8d3d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 006e616d80ef7e8d083f60675b02b4e6a4e8dc24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631994"
---
# <a name="mssqlserver_17887"></a><span data-ttu-id="bf37b-102">MSSQLSERVER_17887</span><span class="sxs-lookup"><span data-stu-id="bf37b-102">MSSQLSERVER_17887</span></span>
    
## <a name="details"></a><span data-ttu-id="bf37b-103">詳細</span><span class="sxs-lookup"><span data-stu-id="bf37b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bf37b-104">製品名</span><span class="sxs-lookup"><span data-stu-id="bf37b-104">Product Name</span></span>|<span data-ttu-id="bf37b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="bf37b-105">SQL Server</span></span>|  
|<span data-ttu-id="bf37b-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="bf37b-106">Event ID</span></span>|<span data-ttu-id="bf37b-107">17887</span><span class="sxs-lookup"><span data-stu-id="bf37b-107">17887</span></span>|  
|<span data-ttu-id="bf37b-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="bf37b-108">Event Source</span></span>|<span data-ttu-id="bf37b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="bf37b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="bf37b-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="bf37b-110">Component</span></span>|<span data-ttu-id="bf37b-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="bf37b-111">SQLEngine</span></span>|  
|<span data-ttu-id="bf37b-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="bf37b-112">Symbolic Name</span></span>|<span data-ttu-id="bf37b-113">SRV_IO_COMP_LISTENER_NONYIELDING</span><span class="sxs-lookup"><span data-stu-id="bf37b-113">SRV_IO_COMP_LISTENER_NONYIELDING</span></span>|  
|<span data-ttu-id="bf37b-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="bf37b-114">Message Text</span></span>|<span data-ttu-id="bf37b-115">IO 完了リスナー (0x%lx) のワーカー 0x%p が、ノード %ld で応答を停止している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bf37b-115">IO Completion Listener (0x%lx) Worker 0x%p appears to be non-yielding on Node %ld.</span></span> <span data-ttu-id="bf37b-116">CPU の概算使用量: カーネル %I64d ミリ秒、ユーザー %I64d ミリ秒、間隔: %I64d。</span><span class="sxs-lookup"><span data-stu-id="bf37b-116">Approx CPU Used: kernel %I64d ms, user %I64d ms, Interval: %I64d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bf37b-117">説明</span><span class="sxs-lookup"><span data-stu-id="bf37b-117">Explanation</span></span>  
 <span data-ttu-id="bf37b-118">ネットワークの読み取りまたは書き込みのイベント用に I/O 完了ルーチンを実行しているときに、指定されたノード上の I/O 完了ポート リスナーに問題が発生している可能性があることを示します。</span><span class="sxs-lookup"><span data-stu-id="bf37b-118">Indicates that there is a possible problem with the I/O Completion Port Listener on the specified node when executing the I/O Completion routine for a network read/write event.</span></span> <span data-ttu-id="bf37b-119">I/O 完了ポート リスナーが I/O 完了ルーチンの実行から戻ると、このエラーは解決します。</span><span class="sxs-lookup"><span data-stu-id="bf37b-119">This error will go away when the I/O Completion Port Listener returns from executing the I/O Completion routine.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bf37b-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="bf37b-120">User Action</span></span>  
 <span data-ttu-id="bf37b-121">マイクロソフト カスタマー サポート サービス (CSS) に連絡してください。</span><span class="sxs-lookup"><span data-stu-id="bf37b-121">Contact Microsoft Customer Support Services (CSS).</span></span>  
  
  
