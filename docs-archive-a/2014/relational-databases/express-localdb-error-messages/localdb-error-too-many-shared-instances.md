---
title: LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: c1595263-6264-4a43-9535-5eb76ece3a57
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0896f3e70e6c65a1fcd0de4169249fb622e6b5f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631932"
---
# <a name="localdb_error_too_many_shared_instances"></a><span data-ttu-id="b1410-102">LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES</span><span class="sxs-lookup"><span data-stu-id="b1410-102">LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES</span></span>
    
## <a name="details"></a><span data-ttu-id="b1410-103">詳細</span><span class="sxs-lookup"><span data-stu-id="b1410-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b1410-104">製品名</span><span class="sxs-lookup"><span data-stu-id="b1410-104">Product Name</span></span>|<span data-ttu-id="b1410-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b1410-105">SQL Server</span></span>|  
|<span data-ttu-id="b1410-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="b1410-106">Event ID</span></span>|<span data-ttu-id="b1410-107">287</span><span class="sxs-lookup"><span data-stu-id="b1410-107">287</span></span>|  
|<span data-ttu-id="b1410-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="b1410-108">Event Source</span></span>|<span data-ttu-id="b1410-109">SQL Server Local Database Runtime 12.0</span><span class="sxs-lookup"><span data-stu-id="b1410-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="b1410-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="b1410-110">Component</span></span>|<span data-ttu-id="b1410-111">Local Database Runtime API</span><span class="sxs-lookup"><span data-stu-id="b1410-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="b1410-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="b1410-112">Message Text</span></span>|<span data-ttu-id="b1410-113">共有インスタンスの数が多すぎるため、一意のユーザー インスタンス名を生成できません。</span><span class="sxs-lookup"><span data-stu-id="b1410-113">There are too many shared instance and we cannot generate unique User Instance Name.</span></span> <span data-ttu-id="b1410-114">いくつかの既存の共有インスタンスの共有を解除してください。</span><span class="sxs-lookup"><span data-stu-id="b1410-114">Unshare some of the existing shared instances.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b1410-115">説明</span><span class="sxs-lookup"><span data-stu-id="b1410-115">Explanation</span></span>  
 <span data-ttu-id="b1410-116">共有インスタンスの数が多すぎるため、一意のユーザー インスタンス名を生成できません。</span><span class="sxs-lookup"><span data-stu-id="b1410-116">There are too many shared instance and we cannot generate unique User Instance Name.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b1410-117">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="b1410-117">User Action</span></span>  
 <span data-ttu-id="b1410-118">1 つ以上の共有 Local Database Runtime インスタンスの共有を解除して、やり直してください。</span><span class="sxs-lookup"><span data-stu-id="b1410-118">Unshare one or more of the shared Local Database Runtime instances and try again.</span></span>  
  
  
