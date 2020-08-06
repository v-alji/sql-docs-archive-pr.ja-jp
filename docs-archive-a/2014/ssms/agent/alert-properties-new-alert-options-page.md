---
title: '[警告のプロパティ]: [新しい警告] ([オプション] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.alert.options.f1
ms.assetid: 6e4f41aa-832d-46ba-b6b5-cf1d3b15d33f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a1507372aa1516c2a88b8682faa77a7d57e58f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737495"
---
# <a name="alert-properties-new-alert-options-page"></a><span data-ttu-id="fe5c9-102">[警告のプロパティ]:[新しい警告] ([オプション] ページ)</span><span class="sxs-lookup"><span data-stu-id="fe5c9-102">Alert Properties: New Alert (Options Page)</span></span>
  <span data-ttu-id="fe5c9-103">このページを使用すると、エージェントの警告のオプションを表示および変更 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] できます。</span><span class="sxs-lookup"><span data-stu-id="fe5c9-103">Use this page to view and modify options for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fe5c9-104">Options</span><span class="sxs-lookup"><span data-stu-id="fe5c9-104">Options</span></span>  
 <span data-ttu-id="fe5c9-105">**メッセージ**</span><span class="sxs-lookup"><span data-stu-id="fe5c9-105">**E-mail**</span></span>  
 <span data-ttu-id="fe5c9-106">イベントからのエラー テキストがある場合は、それを電子メール通知に含めます。</span><span class="sxs-lookup"><span data-stu-id="fe5c9-106">Include error text from the event, if any, in e-mail notifications.</span></span>  
  
 <span data-ttu-id="fe5c9-107">**ポケットベル**</span><span class="sxs-lookup"><span data-stu-id="fe5c9-107">**Pager**</span></span>  
 <span data-ttu-id="fe5c9-108">イベントからのエラー テキストがある場合は、それをポケットベル通知に含めます。</span><span class="sxs-lookup"><span data-stu-id="fe5c9-108">Include error text from the event, if any, in pager notifications.</span></span>  
  
 <span data-ttu-id="fe5c9-109">**Net send**</span><span class="sxs-lookup"><span data-stu-id="fe5c9-109">**Net send**</span></span>  
 <span data-ttu-id="fe5c9-110">イベントからのエラー テキストがある場合は、それを Net Send 通知に含めます。</span><span class="sxs-lookup"><span data-stu-id="fe5c9-110">Include error text from the event, if any, in net send notifications.</span></span>  
  
 <span data-ttu-id="fe5c9-111">**[送信する付加通知メッセージ]**</span><span class="sxs-lookup"><span data-stu-id="fe5c9-111">**Additional notification message to send**</span></span>  
 <span data-ttu-id="fe5c9-112">通知メッセージに含める追加のテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="fe5c9-112">Type any additional text to include in notification messages.</span></span>  
  
 <span data-ttu-id="fe5c9-113">**[応答の遅延]**</span><span class="sxs-lookup"><span data-stu-id="fe5c9-113">**Delay between responses**</span></span>  
 <span data-ttu-id="fe5c9-114">反復的に発生するイベントの遅延を指定します。</span><span class="sxs-lookup"><span data-stu-id="fe5c9-114">Specify a delay for repeated occurrences of the event.</span></span> <span data-ttu-id="fe5c9-115">イベントの中には、短時間に頻繁に発生するものがあります。</span><span class="sxs-lookup"><span data-stu-id="fe5c9-115">Some events may occur frequently during a short period of time.</span></span> <span data-ttu-id="fe5c9-116">そのようなイベントに対しては、その発生を認識するだけで、すべてのイベントについて応答を返さないようにする場合があります。</span><span class="sxs-lookup"><span data-stu-id="fe5c9-116">In this case, you may want to know that the event has occurred, but you may not want a response for every event.</span></span> <span data-ttu-id="fe5c9-117">このオプションを使用して、タイムアウトを指定します。遅延が発生すると、警告がイベントに応答した後、エージェントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] イベントが遅延中に発生したかどうかに関係なく、指定された遅延を待機してからもう一度応答します。</span><span class="sxs-lookup"><span data-stu-id="fe5c9-117">Use this option to specify a time-out. With a delay, after the alert responds to an event, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent waits for the delay specified before responding again, regardless of whether the event occurs during the delay.</span></span>  
  
 <span data-ttu-id="fe5c9-118">**分**</span><span class="sxs-lookup"><span data-stu-id="fe5c9-118">**Minutes**</span></span>  
 <span data-ttu-id="fe5c9-119">遅延を分単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="fe5c9-119">Specify a delay in minutes.</span></span> <span data-ttu-id="fe5c9-120">イベントが発生するごとに応答するには、0 分 0 秒を指定します。</span><span class="sxs-lookup"><span data-stu-id="fe5c9-120">To respond every time the event occurs, specify 0 minutes and 0 seconds.</span></span>  
  
 <span data-ttu-id="fe5c9-121">**Seconds**</span><span class="sxs-lookup"><span data-stu-id="fe5c9-121">**Seconds**</span></span>  
 <span data-ttu-id="fe5c9-122">遅延を秒単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="fe5c9-122">Specify a delay in seconds.</span></span> <span data-ttu-id="fe5c9-123">イベントが発生するごとに応答するには、0 分 0 秒を指定します。</span><span class="sxs-lookup"><span data-stu-id="fe5c9-123">To respond every time the event occurs, specify 0 minutes and 0 seconds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe5c9-124">参照</span><span class="sxs-lookup"><span data-stu-id="fe5c9-124">See Also</span></span>  
 [<span data-ttu-id="fe5c9-125">アラート</span><span class="sxs-lookup"><span data-stu-id="fe5c9-125">Alerts</span></span>](alerts.md)  
  
  
