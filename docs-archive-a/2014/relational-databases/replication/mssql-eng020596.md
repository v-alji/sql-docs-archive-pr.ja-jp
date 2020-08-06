---
title: MSSQL_ENG020596 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020596 error
ms.assetid: fa33627c-2e99-4be3-9424-52ab83446e07
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8b1c61f3683442e0d474ff36a65c89446dbd7bd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645544"
---
# <a name="mssql_eng020596"></a><span data-ttu-id="ecea9-102">MSSQL_ENG020596</span><span class="sxs-lookup"><span data-stu-id="ecea9-102">MSSQL_ENG020596</span></span>
    
## <a name="message-details"></a><span data-ttu-id="ecea9-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="ecea9-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ecea9-104">製品名</span><span class="sxs-lookup"><span data-stu-id="ecea9-104">Product Name</span></span>|<span data-ttu-id="ecea9-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ecea9-105">SQL Server</span></span>|  
|<span data-ttu-id="ecea9-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="ecea9-106">Event ID</span></span>|<span data-ttu-id="ecea9-107">20596</span><span class="sxs-lookup"><span data-stu-id="ecea9-107">20596</span></span>|  
|<span data-ttu-id="ecea9-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="ecea9-108">Event Source</span></span>|<span data-ttu-id="ecea9-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ecea9-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ecea9-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ecea9-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="ecea9-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="ecea9-111">Symbolic Name</span></span>||  
|<span data-ttu-id="ecea9-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="ecea9-112">Message Text</span></span>|<span data-ttu-id="ecea9-113">'%s' または db_owner のメンバーだけが匿名エージェントを削除できます。</span><span class="sxs-lookup"><span data-stu-id="ecea9-113">Only '%s' or members of db_owner can drop the anonymous agent.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ecea9-114">説明</span><span class="sxs-lookup"><span data-stu-id="ecea9-114">Explanation</span></span>  
 <span data-ttu-id="ecea9-115">匿名サブスクリプションのエージェントを削除するために必要な権限がありません。</span><span class="sxs-lookup"><span data-stu-id="ecea9-115">You do not have sufficient permissions to drop the agent for the anonymous subscription.</span></span> <span data-ttu-id="ecea9-116">[sp_dropanonymousagent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropanonymousagent-transact-sql) を呼び出すときに使用するログインは、ディストリビューターの固定サーバー ロール **sysadmin** またはディストリビューション データベースの固定データベース ロール **db_owner** のメンバーであるか、エージェントを最初に起動したユーザーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="ecea9-116">The login used when calling [sp_dropanonymousagent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropanonymousagent-transact-sql) must be a member of the **sysadmin** fixed server role at the Distributor or **db_owner** fixed database role in the distribution database, or the user must be the one that initiated the first run of the agent.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ecea9-117">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="ecea9-117">User Action</span></span>  
 <span data-ttu-id="ecea9-118">適切な資格情報でログインして **sp_dropanonymousagent**を実行します。</span><span class="sxs-lookup"><span data-stu-id="ecea9-118">Login with the appropriate credentials, and execute **sp_dropanonymousagent**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecea9-119">参照</span><span class="sxs-lookup"><span data-stu-id="ecea9-119">See Also</span></span>  
 [<span data-ttu-id="ecea9-120">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="ecea9-120">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
