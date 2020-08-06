---
title: LOCALDB_ERROR_INSTANCE_BUSY |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: 0ed9d0f8-3297-4e31-a3e9-4a827f381789
author: stevestein
ms.author: sstein
ms.openlocfilehash: c587ada5f08d3743f4fe7eafccfc923c38a2b7b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639964"
---
# <a name="localdb_error_instance_busy"></a><span data-ttu-id="2f720-102">LOCALDB_ERROR_INSTANCE_BUSY</span><span class="sxs-lookup"><span data-stu-id="2f720-102">LOCALDB_ERROR_INSTANCE_BUSY</span></span>
    
## <a name="details"></a><span data-ttu-id="2f720-103">詳細</span><span class="sxs-lookup"><span data-stu-id="2f720-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2f720-104">製品名</span><span class="sxs-lookup"><span data-stu-id="2f720-104">Product Name</span></span>|<span data-ttu-id="2f720-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2f720-105">SQL Server</span></span>|  
|<span data-ttu-id="2f720-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2f720-106">Event ID</span></span>|<span data-ttu-id="2f720-107">274</span><span class="sxs-lookup"><span data-stu-id="2f720-107">274</span></span>|  
|<span data-ttu-id="2f720-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="2f720-108">Event Source</span></span>|<span data-ttu-id="2f720-109">SQL Server Local Database Runtime 12.0</span><span class="sxs-lookup"><span data-stu-id="2f720-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="2f720-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="2f720-110">Component</span></span>|<span data-ttu-id="2f720-111">Local Database Runtime API</span><span class="sxs-lookup"><span data-stu-id="2f720-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="2f720-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="2f720-112">Message Text</span></span>|<span data-ttu-id="2f720-113">ローカル データベース インスタンスで要求された操作は、指定されたインスタンスが現在使用中であるため実行できません。</span><span class="sxs-lookup"><span data-stu-id="2f720-113">Requested operation on Local Database instance cannot be performed because specified instance is currently in use.</span></span> <span data-ttu-id="2f720-114">インスタンスを停止して、再度実行してください。</span><span class="sxs-lookup"><span data-stu-id="2f720-114">Stop the instance and try again.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2f720-115">説明</span><span class="sxs-lookup"><span data-stu-id="2f720-115">Explanation</span></span>  
 <span data-ttu-id="2f720-116">指定したインスタンスは実行中です。</span><span class="sxs-lookup"><span data-stu-id="2f720-116">The specified instance is running.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2f720-117">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="2f720-117">User Action</span></span>  
 <span data-ttu-id="2f720-118">指定した Local Database Runtime インスタンスを停止して、再度実行してください。</span><span class="sxs-lookup"><span data-stu-id="2f720-118">Stop the specified Local Database Runtime instance and try again.</span></span>  
  
  
