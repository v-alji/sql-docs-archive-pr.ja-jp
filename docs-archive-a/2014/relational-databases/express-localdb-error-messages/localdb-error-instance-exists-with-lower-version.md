---
title: LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: a7c5ce08-8841-49a3-b252-116807ba469a
author: stevestein
ms.author: sstein
ms.openlocfilehash: aa6db2af138bb2aeefb1a922e55db56c4ea821f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743289"
---
# <a name="localdb_error_instance_exists_with_lower_version"></a><span data-ttu-id="55e25-102">LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION</span><span class="sxs-lookup"><span data-stu-id="55e25-102">LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION</span></span>
    
## <a name="details"></a><span data-ttu-id="55e25-103">詳細</span><span class="sxs-lookup"><span data-stu-id="55e25-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="55e25-104">製品名</span><span class="sxs-lookup"><span data-stu-id="55e25-104">Product Name</span></span>|<span data-ttu-id="55e25-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="55e25-105">SQL Server</span></span>|  
|<span data-ttu-id="55e25-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="55e25-106">Event ID</span></span>|<span data-ttu-id="55e25-107">258</span><span class="sxs-lookup"><span data-stu-id="55e25-107">258</span></span>|  
|<span data-ttu-id="55e25-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="55e25-108">Event Source</span></span>|<span data-ttu-id="55e25-109">SQL Server Local Database Runtime 12.0</span><span class="sxs-lookup"><span data-stu-id="55e25-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="55e25-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="55e25-110">Component</span></span>|<span data-ttu-id="55e25-111">Local Database Runtime API</span><span class="sxs-lookup"><span data-stu-id="55e25-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="55e25-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="55e25-112">Message Text</span></span>|<span data-ttu-id="55e25-113">指定されたバージョンのローカル データベース インスタンスを作成できません。</span><span class="sxs-lookup"><span data-stu-id="55e25-113">Unable to create the Local Database instance with specified version.</span></span> <span data-ttu-id="55e25-114">同じ名前のインスタンスは既に存在しますが、指定されたバージョンよりも下位のバージョンになっています。</span><span class="sxs-lookup"><span data-stu-id="55e25-114">An instance with the same name already exists, but it has lower version than the specified version.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="55e25-115">説明</span><span class="sxs-lookup"><span data-stu-id="55e25-115">Explanation</span></span>  
 <span data-ttu-id="55e25-116">指定したインスタンスは既に存在しますが、そのバージョンは要求よりも低いバージョンです。</span><span class="sxs-lookup"><span data-stu-id="55e25-116">The specified instance already exists but its version is lower than requested.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="55e25-117">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="55e25-117">User Action</span></span>  
 <span data-ttu-id="55e25-118">既存のインスタンスを削除し、操作を再試行してください。</span><span class="sxs-lookup"><span data-stu-id="55e25-118">Delete the existing instance and retry the operation.</span></span>  
  
  
