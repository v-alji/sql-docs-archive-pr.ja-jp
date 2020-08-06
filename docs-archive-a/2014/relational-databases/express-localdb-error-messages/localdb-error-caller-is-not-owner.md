---
title: LOCALDB_ERROR_CALLER_IS_NOT_OWNER |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: f3303072-2b44-4443-936c-f024b0b2a8c5
author: stevestein
ms.author: sstein
ms.openlocfilehash: ce4fd6d84929ce7d1338f5fd688d3c24f1e1858a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645107"
---
# <a name="localdb_error_caller_is_not_owner"></a><span data-ttu-id="3332e-102">LOCALDB_ERROR_CALLER_IS_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3332e-102">LOCALDB_ERROR_CALLER_IS_NOT_OWNER</span></span>
    
## <a name="details"></a><span data-ttu-id="3332e-103">詳細</span><span class="sxs-lookup"><span data-stu-id="3332e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3332e-104">製品名</span><span class="sxs-lookup"><span data-stu-id="3332e-104">Product Name</span></span>|<span data-ttu-id="3332e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="3332e-105">SQL Server</span></span>|  
|<span data-ttu-id="3332e-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3332e-106">Event ID</span></span>|<span data-ttu-id="3332e-107">282</span><span class="sxs-lookup"><span data-stu-id="3332e-107">282</span></span>|  
|<span data-ttu-id="3332e-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="3332e-108">Event Source</span></span>|<span data-ttu-id="3332e-109">SQL Server Local Database Runtime 12.0</span><span class="sxs-lookup"><span data-stu-id="3332e-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="3332e-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="3332e-110">Component</span></span>|<span data-ttu-id="3332e-111">Local Database Runtime API</span><span class="sxs-lookup"><span data-stu-id="3332e-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="3332e-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="3332e-112">Message Text</span></span>|<span data-ttu-id="3332e-113">API 呼び出し元は、ローカル データベース インスタンスの所有者ではありません。</span><span class="sxs-lookup"><span data-stu-id="3332e-113">API caller is not Local Database instance owner.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3332e-114">説明</span><span class="sxs-lookup"><span data-stu-id="3332e-114">Explanation</span></span>  
 <span data-ttu-id="3332e-115">要求された操作を実行するには、ユーザーがインスタンスの所有者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="3332e-115">User needs to be the instance owner to be able to execute the requested operation.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3332e-116">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="3332e-116">User Action</span></span>  
 <span data-ttu-id="3332e-117">インスタンスの所有者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="3332e-117">Contact the instance owner for help.</span></span>  
  
  
