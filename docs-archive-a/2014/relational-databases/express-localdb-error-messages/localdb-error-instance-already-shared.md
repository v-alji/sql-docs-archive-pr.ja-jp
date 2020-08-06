---
title: LOCALDB_ERROR_INSTANCE_ALREADY_SHARED |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: 35b4d6fa-ebb9-49d3-aaab-d4e37b6f3760
author: stevestein
ms.author: sstein
ms.openlocfilehash: 300f9753b721bc3e0a821a6b77929a9bec09312b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631938"
---
# <a name="localdb_error_instance_already_shared"></a><span data-ttu-id="13662-102">LOCALDB_ERROR_INSTANCE_ALREADY_SHARED</span><span class="sxs-lookup"><span data-stu-id="13662-102">LOCALDB_ERROR_INSTANCE_ALREADY_SHARED</span></span>
    
## <a name="details"></a><span data-ttu-id="13662-103">詳細</span><span class="sxs-lookup"><span data-stu-id="13662-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="13662-104">製品名</span><span class="sxs-lookup"><span data-stu-id="13662-104">Product Name</span></span>|<span data-ttu-id="13662-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="13662-105">SQL Server</span></span>|  
|<span data-ttu-id="13662-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="13662-106">Event ID</span></span>|<span data-ttu-id="13662-107">284</span><span class="sxs-lookup"><span data-stu-id="13662-107">284</span></span>|  
|<span data-ttu-id="13662-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="13662-108">Event Source</span></span>|<span data-ttu-id="13662-109">SQL Server Local Database Runtime 12.0</span><span class="sxs-lookup"><span data-stu-id="13662-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="13662-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="13662-110">Component</span></span>|<span data-ttu-id="13662-111">Local Database Runtime API</span><span class="sxs-lookup"><span data-stu-id="13662-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="13662-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="13662-112">Message Text</span></span>|<span data-ttu-id="13662-113">指定したローカル データベース インスタンスは既に共有されています。</span><span class="sxs-lookup"><span data-stu-id="13662-113">The specified Local Database Instance is already shared.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="13662-114">説明</span><span class="sxs-lookup"><span data-stu-id="13662-114">Explanation</span></span>  
 <span data-ttu-id="13662-115">指定したローカル データベース インスタンスは既に別の共有名で共有されています。</span><span class="sxs-lookup"><span data-stu-id="13662-115">The specified Local Database Instance is already shared with a different shared name.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="13662-116">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="13662-116">User Action</span></span>  
 <span data-ttu-id="13662-117">共有インスタンスを別の共有名で再度共有する前に、そのインスタンスの共有を解除してください。</span><span class="sxs-lookup"><span data-stu-id="13662-117">Unshare the shared instance before sharing it again with a different shared name.</span></span>  
  
  
