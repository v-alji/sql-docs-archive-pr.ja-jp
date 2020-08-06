---
title: MSSQL_ENG014144 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014144 error
ms.assetid: fdc744d5-530e-48c4-9420-cca032fd482b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0d93f06a585bcc01c52438ff7b99bbd635532402
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630926"
---
# <a name="mssql_eng014144"></a><span data-ttu-id="8a3ef-102">MSSQL_ENG014144</span><span class="sxs-lookup"><span data-stu-id="8a3ef-102">MSSQL_ENG014144</span></span>
    
## <a name="message-details"></a><span data-ttu-id="8a3ef-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="8a3ef-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8a3ef-104">製品名</span><span class="sxs-lookup"><span data-stu-id="8a3ef-104">Product Name</span></span>|<span data-ttu-id="8a3ef-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8a3ef-105">SQL Server</span></span>|  
|<span data-ttu-id="8a3ef-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="8a3ef-106">Event ID</span></span>|<span data-ttu-id="8a3ef-107">14144</span><span class="sxs-lookup"><span data-stu-id="8a3ef-107">14144</span></span>|  
|<span data-ttu-id="8a3ef-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="8a3ef-108">Event Source</span></span>|<span data-ttu-id="8a3ef-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8a3ef-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8a3ef-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="8a3ef-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="8a3ef-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="8a3ef-111">Symbolic Name</span></span>||  
|<span data-ttu-id="8a3ef-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="8a3ef-112">Message Text</span></span>|<span data-ttu-id="8a3ef-113">サブスクライバー '%s' を削除できません。</span><span class="sxs-lookup"><span data-stu-id="8a3ef-113">Cannot drop Subscriber '%s'.</span></span> <span data-ttu-id="8a3ef-114">そのサブスクライバーのサブスクリプションがパブリケーション データベース '%s' にあります。</span><span class="sxs-lookup"><span data-stu-id="8a3ef-114">There are subscriptions for it in the publication database '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8a3ef-115">説明</span><span class="sxs-lookup"><span data-stu-id="8a3ef-115">Explanation</span></span>  
 <span data-ttu-id="8a3ef-116">サブスクライバーとして構成されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスは、そのインスタンスに対して構成されているアクティブなサブスクリプションがあると、サブスクライバーの役割から削除できません。</span><span class="sxs-lookup"><span data-stu-id="8a3ef-116">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that is configured as a Subscriber cannot be removed from the role of Subscriber while there are active subscriptions configured for the instance.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8a3ef-117">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="8a3ef-117">User Action</span></span>  
 <span data-ttu-id="8a3ef-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのサブスクライバーの状態を変更する前に、関連付けられているすべてのサブスクリプションを削除します。</span><span class="sxs-lookup"><span data-stu-id="8a3ef-118">Drop all associated subscriptions before attempting to change the Subscriber status of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance:</span></span>  
  
1.  <span data-ttu-id="8a3ef-119">パブリッシャーのパブリケーション データベースで [sp_helpsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql) を実行して、サブスクリプションを検索します。</span><span class="sxs-lookup"><span data-stu-id="8a3ef-119">Execute [sp_helpsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql) in the publication database at the Publisher to find subscriptions.</span></span>  
  
2.  <span data-ttu-id="8a3ef-120">パブリケーション データベースで [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql) を実行して、サブスクリプションを削除します。</span><span class="sxs-lookup"><span data-stu-id="8a3ef-120">Execute [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql) in the publication database to drop subscriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a3ef-121">参照</span><span class="sxs-lookup"><span data-stu-id="8a3ef-121">See Also</span></span>  
 <span data-ttu-id="8a3ef-122">[エラーとイベントのリファレンス &#40;レプリケーション&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="8a3ef-122">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 [<span data-ttu-id="8a3ef-123">パブリケーションのサブスクライブ</span><span class="sxs-lookup"><span data-stu-id="8a3ef-123">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
