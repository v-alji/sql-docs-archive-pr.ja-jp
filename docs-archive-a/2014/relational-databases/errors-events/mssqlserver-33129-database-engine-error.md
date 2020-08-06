---
title: MSSQLSERVER_33129 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33129 (Database Engine error)
ms.assetid: 83b5f368-f1a1-4a40-9bb6-c77e2dec690f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: da7735889dce8bfc33e624115e8245f8a02f46b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640019"
---
# <a name="mssqlserver_33129"></a><span data-ttu-id="5ca59-102">MSSQLSERVER_33129</span><span class="sxs-lookup"><span data-stu-id="5ca59-102">MSSQLSERVER_33129</span></span>
    
## <a name="details"></a><span data-ttu-id="5ca59-103">詳細</span><span class="sxs-lookup"><span data-stu-id="5ca59-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5ca59-104">製品名</span><span class="sxs-lookup"><span data-stu-id="5ca59-104">Product Name</span></span>|<span data-ttu-id="5ca59-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5ca59-105">SQL Server</span></span>|  
|<span data-ttu-id="5ca59-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="5ca59-106">Event ID</span></span>|<span data-ttu-id="5ca59-107">33129</span><span class="sxs-lookup"><span data-stu-id="5ca59-107">33129</span></span>|  
|<span data-ttu-id="5ca59-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="5ca59-108">Event Source</span></span>|<span data-ttu-id="5ca59-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5ca59-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5ca59-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="5ca59-110">Component</span></span>|<span data-ttu-id="5ca59-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5ca59-111">SQLEngine</span></span>|  
|<span data-ttu-id="5ca59-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="5ca59-112">Symbolic Name</span></span>|<span data-ttu-id="5ca59-113">SEC_CANNOT_DISABLE_WIN_GROUP</span><span class="sxs-lookup"><span data-stu-id="5ca59-113">SEC_CANNOT_DISABLE_WIN_GROUP</span></span>|  
|<span data-ttu-id="5ca59-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="5ca59-114">Message Text</span></span>|<span data-ttu-id="5ca59-115">ALTER_LOGIN を DISABLE 引数と共に使用して Windows グループへのアクセスを拒否することはできません。</span><span class="sxs-lookup"><span data-stu-id="5ca59-115">Cannot use ALTER_LOGIN with the DISABLE argument to deny access to a Windows group.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5ca59-116">説明</span><span class="sxs-lookup"><span data-stu-id="5ca59-116">Explanation</span></span>  
 <span data-ttu-id="5ca59-117">このメッセージは、Windows グループのログインを無効にしようとしたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="5ca59-117">This message occurs when attempting to disable the login of a Windows Group.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5ca59-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="5ca59-118">User Action</span></span>  
 <span data-ttu-id="5ca59-119">Windows グループのログインを無効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="5ca59-119">The login of a Windows Group cannot be disabled.</span></span> <span data-ttu-id="5ca59-120">Windows グループに許可されているアクセス権限を一時的に削除するには、Windows グループのログインの CONNECT 権限を REVOKE (取り消し) します。</span><span class="sxs-lookup"><span data-stu-id="5ca59-120">To temporarily remove access permission granted to a Windows Group, REVOKE the CONNECT permission of the login for the Windows Group.</span></span> <span data-ttu-id="5ca59-121">この場合、Windows ユーザーは個人のログインまたは別の Windows グループを介してアクセスできる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5ca59-121">Windows users might still have access through their individual login or through another Windows Group.</span></span> <span data-ttu-id="5ca59-122">次の例では、WESTCOAST ドメインの Accounting グループに対する CONNECT 権限を取り消します。</span><span class="sxs-lookup"><span data-stu-id="5ca59-122">The following example revokes the connect permission to the Accounting Group of the WESTCOAST domain.</span></span>  
  
```sql  
REVOKE CONNECT TO [WESTCOAST\Accounting];  
```  
  
  
