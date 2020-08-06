---
title: PreConnect:Starting イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- PreConnect:Starting Event Class
ms.assetid: d43ed0ad-3dbd-42e0-9cef-8320b8d87497
author: stevestein
ms.author: sstein
ms.openlocfilehash: 67b642d369c73cc144af31f835786613766045f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642772"
---
# <a name="preconnectstarting-event-class"></a><span data-ttu-id="0fc06-102">PreConnect:Starting イベント クラス</span><span class="sxs-lookup"><span data-stu-id="0fc06-102">PreConnect:Starting Event Class</span></span>
  <span data-ttu-id="0fc06-103">PreConnect:Starting イベント クラスは、LOGON トリガーまたはリソース ガバナーの分類関数が実行を開始したことを示します。</span><span class="sxs-lookup"><span data-stu-id="0fc06-103">The PreConnect:Starting event class indicates when a LOGON trigger or the Resource Governor classifier function starts execution.</span></span>  
  
## <a name="preconnectstarting-event-class-data-columns"></a><span data-ttu-id="0fc06-104">PreConnect:Starting イベント クラスのデータ列</span><span class="sxs-lookup"><span data-stu-id="0fc06-104">PreConnect:Starting Event Class Data Columns</span></span>  
  
|<span data-ttu-id="0fc06-105">データ列名</span><span class="sxs-lookup"><span data-stu-id="0fc06-105">Data column name</span></span>|<span data-ttu-id="0fc06-106">データ型</span><span class="sxs-lookup"><span data-stu-id="0fc06-106">Data type</span></span>|<span data-ttu-id="0fc06-107">説明</span><span class="sxs-lookup"><span data-stu-id="0fc06-107">Description</span></span>|<span data-ttu-id="0fc06-108">列 ID</span><span class="sxs-lookup"><span data-stu-id="0fc06-108">Column ID</span></span>|<span data-ttu-id="0fc06-109">フィルターの適用</span><span class="sxs-lookup"><span data-stu-id="0fc06-109">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="0fc06-110">EventClass</span><span class="sxs-lookup"><span data-stu-id="0fc06-110">EventClass</span></span>|`int`|<span data-ttu-id="0fc06-111">215</span><span class="sxs-lookup"><span data-stu-id="0fc06-111">215</span></span>|<span data-ttu-id="0fc06-112">27</span><span class="sxs-lookup"><span data-stu-id="0fc06-112">27</span></span>|<span data-ttu-id="0fc06-113">いいえ</span><span class="sxs-lookup"><span data-stu-id="0fc06-113">No</span></span>|  
|<span data-ttu-id="0fc06-114">SPID</span><span class="sxs-lookup"><span data-stu-id="0fc06-114">SPID</span></span>|`int`|<span data-ttu-id="0fc06-115">このイベントを発生させるサーバー プロセスの ID。</span><span class="sxs-lookup"><span data-stu-id="0fc06-115">The ID of server process that fires this event.</span></span>|<span data-ttu-id="0fc06-116">12</span><span class="sxs-lookup"><span data-stu-id="0fc06-116">12</span></span>|<span data-ttu-id="0fc06-117">はい</span><span class="sxs-lookup"><span data-stu-id="0fc06-117">Yes</span></span>|  
|<span data-ttu-id="0fc06-118">EventSubClass</span><span class="sxs-lookup"><span data-stu-id="0fc06-118">EventSubClass</span></span>|`int`|<span data-ttu-id="0fc06-119">ユーザー定義の分類子関数の場合は 1。</span><span class="sxs-lookup"><span data-stu-id="0fc06-119">1 for the user-defined classifier function.</span></span>|<span data-ttu-id="0fc06-120">21</span><span class="sxs-lookup"><span data-stu-id="0fc06-120">21</span></span>|<span data-ttu-id="0fc06-121">はい</span><span class="sxs-lookup"><span data-stu-id="0fc06-121">Yes</span></span>|  
|<span data-ttu-id="0fc06-122">StartTime</span><span class="sxs-lookup"><span data-stu-id="0fc06-122">StartTime</span></span>|`datetime`|<span data-ttu-id="0fc06-123">ユーザー定義の分類子関数が開始された時刻。</span><span class="sxs-lookup"><span data-stu-id="0fc06-123">The time when the user-defined classifier function starts.</span></span>|<span data-ttu-id="0fc06-124">14</span><span class="sxs-lookup"><span data-stu-id="0fc06-124">14</span></span>|<span data-ttu-id="0fc06-125">はい</span><span class="sxs-lookup"><span data-stu-id="0fc06-125">Yes</span></span>|  
|<span data-ttu-id="0fc06-126">ObjectID</span><span class="sxs-lookup"><span data-stu-id="0fc06-126">ObjectID</span></span>|`int`|<span data-ttu-id="0fc06-127">ユーザー定義の分類オブジェクトの ID。</span><span class="sxs-lookup"><span data-stu-id="0fc06-127">The ID of the user-defined classifier object.</span></span>|<span data-ttu-id="0fc06-128">22</span><span class="sxs-lookup"><span data-stu-id="0fc06-128">22</span></span>|<span data-ttu-id="0fc06-129">はい</span><span class="sxs-lookup"><span data-stu-id="0fc06-129">Yes</span></span>|  
|<span data-ttu-id="0fc06-130">ObjectName</span><span class="sxs-lookup"><span data-stu-id="0fc06-130">ObjectName</span></span>|`nvarchar(256)`|<span data-ttu-id="0fc06-131">ユーザー定義の分類子関数の 2 部構成の名前</span><span class="sxs-lookup"><span data-stu-id="0fc06-131">The two-part name of the classifier user-defined function.</span></span> <span data-ttu-id="0fc06-132">(dbo.classifier など)。</span><span class="sxs-lookup"><span data-stu-id="0fc06-132">For example, dbo.classifier.</span></span>|<span data-ttu-id="0fc06-133">34</span><span class="sxs-lookup"><span data-stu-id="0fc06-133">34</span></span>|<span data-ttu-id="0fc06-134">はい</span><span class="sxs-lookup"><span data-stu-id="0fc06-134">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0fc06-135">参照</span><span class="sxs-lookup"><span data-stu-id="0fc06-135">See Also</span></span>  
 <span data-ttu-id="0fc06-136">[拡張イベント](../extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="0fc06-136">[Extended Events](../extended-events/extended-events.md) </span></span>  
 <span data-ttu-id="0fc06-137">[PreConnect: Completed イベントクラス](preconnect-completed-event-class.md) </span><span class="sxs-lookup"><span data-stu-id="0fc06-137">[PreConnect:Completed Event Class](preconnect-completed-event-class.md) </span></span>  
 [<span data-ttu-id="0fc06-138">リソース ガバナー</span><span class="sxs-lookup"><span data-stu-id="0fc06-138">Resource Governor</span></span>](../resource-governor/resource-governor.md)  
  
  
