---
title: MSSQLSERVER_15599 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15599 (Database Engine error)
ms.assetid: 97e427a9-8587-46ea-954b-974b5df9c223
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 15f1b3eb6d97837f1c1c4a9944535cade5b31300
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643907"
---
# <a name="mssqlserver_15599"></a><span data-ttu-id="1cc69-102">MSSQLSERVER_15599</span><span class="sxs-lookup"><span data-stu-id="1cc69-102">MSSQLSERVER_15599</span></span>
    
## <a name="details"></a><span data-ttu-id="1cc69-103">詳細</span><span class="sxs-lookup"><span data-stu-id="1cc69-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1cc69-104">製品名</span><span class="sxs-lookup"><span data-stu-id="1cc69-104">Product Name</span></span>|<span data-ttu-id="1cc69-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1cc69-105">SQL Server</span></span>|  
|<span data-ttu-id="1cc69-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="1cc69-106">Event ID</span></span>|<span data-ttu-id="1cc69-107">15599</span><span class="sxs-lookup"><span data-stu-id="1cc69-107">15599</span></span>|  
|<span data-ttu-id="1cc69-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="1cc69-108">Event Source</span></span>|<span data-ttu-id="1cc69-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1cc69-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1cc69-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="1cc69-110">Component</span></span>|<span data-ttu-id="1cc69-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1cc69-111">SQLEngine</span></span>|  
|<span data-ttu-id="1cc69-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="1cc69-112">Symbolic Name</span></span>|<span data-ttu-id="1cc69-113">SEC_LOCAL_TEMP_AUDIT_PERMISSIONS</span><span class="sxs-lookup"><span data-stu-id="1cc69-113">SEC_LOCAL_TEMP_AUDIT_PERMISSIONS</span></span>|  
|<span data-ttu-id="1cc69-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="1cc69-114">Message Text</span></span>|<span data-ttu-id="1cc69-115">監査と権限をローカルの一時オブジェクトで設定できません。</span><span class="sxs-lookup"><span data-stu-id="1cc69-115">Auditing and permissions can't be set on local temporary objects.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1cc69-116">説明</span><span class="sxs-lookup"><span data-stu-id="1cc69-116">Explanation</span></span>  
 <span data-ttu-id="1cc69-117">監査と権限は、ローカルまたはグローバルの一時オブジェクトに設定する場合にまったく影響しません。</span><span class="sxs-lookup"><span data-stu-id="1cc69-117">Auditing and permissions do not have any effect when set for local or global temp objects.</span></span> <span data-ttu-id="1cc69-118">このステートメントではエラーは発生しません (操作は成功を返します) が、効果はありません。</span><span class="sxs-lookup"><span data-stu-id="1cc69-118">The statements do not result in an error (the operations will return success), but have no effect.</span></span>  
  
 <span data-ttu-id="1cc69-119">この動作は変更されていませんが、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降はこの情報メッセージがユーザーに通知されます。</span><span class="sxs-lookup"><span data-stu-id="1cc69-119">This behavior has not changed, however beginning with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], this informational message alerts the user.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1cc69-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="1cc69-120">User Action</span></span>  
 <span data-ttu-id="1cc69-121">操作は必要ありませんが、ローカルまたはグローバルの一時オブジェクトに監査または権限を設定するステートメントを削除することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="1cc69-121">No action is necessary, but consider removing statements that attempt to set auditing or permissions on local or global temp objects.</span></span>  
  
  
