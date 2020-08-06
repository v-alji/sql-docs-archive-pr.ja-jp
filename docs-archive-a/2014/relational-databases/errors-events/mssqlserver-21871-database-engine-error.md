---
title: MSSQLSERVER_21871 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21871 (Database Engine error)
ms.assetid: d3215378-9282-444f-a18b-00b96fd0133d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f26211da21829a0a898dfb36ff9fefd453c7ad44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715322"
---
# <a name="mssqlserver_21871"></a><span data-ttu-id="da077-102">MSSQLSERVER_21871</span><span class="sxs-lookup"><span data-stu-id="da077-102">MSSQLSERVER_21871</span></span>
    
## <a name="details"></a><span data-ttu-id="da077-103">詳細</span><span class="sxs-lookup"><span data-stu-id="da077-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="da077-104">製品名</span><span class="sxs-lookup"><span data-stu-id="da077-104">Product Name</span></span>|<span data-ttu-id="da077-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="da077-105">SQL Server</span></span>|  
|<span data-ttu-id="da077-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="da077-106">Event ID</span></span>|<span data-ttu-id="da077-107">21871</span><span class="sxs-lookup"><span data-stu-id="da077-107">21871</span></span>|  
|<span data-ttu-id="da077-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="da077-108">Event Source</span></span>|<span data-ttu-id="da077-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="da077-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="da077-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="da077-110">Component</span></span>|<span data-ttu-id="da077-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="da077-111">SQLEngine</span></span>|  
|<span data-ttu-id="da077-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="da077-112">Symbolic Name</span></span>|<span data-ttu-id="da077-113">SQLErrorNum21871</span><span class="sxs-lookup"><span data-stu-id="da077-113">SQLErrorNum21871</span></span>|  
|<span data-ttu-id="da077-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="da077-114">Message Text</span></span>|<span data-ttu-id="da077-115">データベース %s のパブリッシャー %s がリダイレクトされていません。</span><span class="sxs-lookup"><span data-stu-id="da077-115">Publisher %s of database %s has not been redirected.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="da077-116">説明</span><span class="sxs-lookup"><span data-stu-id="da077-116">Explanation</span></span>  
 <span data-ttu-id="da077-117">`sp_validate_replica_hosts_as_publishers` は、ディストリビューション データベースのテーブル MSredirected_publishers で、識別されたパブリッシャーおよびパブリッシャー データベースのエントリがあるかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="da077-117">`sp_validate_replica_hosts_as_publishers` checks the table MSredirected_publishers in the distribution database for an entry for the identified publisher and publisher database.</span></span>  <span data-ttu-id="da077-118">エントリが見つからない場合、`sp_validate_replica_hosts_as_publishers` はエラー 21871 を返します。</span><span class="sxs-lookup"><span data-stu-id="da077-118">`sp_validate_replica_hosts_as_publishers` returns error 21871 when no entry is found.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="da077-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="da077-119">User Action</span></span>  
 <span data-ttu-id="da077-120">`sp_validate_replica_hosts_as_publishers` は、リダイレクトされたパブリッシャーにのみ関連しています。</span><span class="sxs-lookup"><span data-stu-id="da077-120">`sp_validate_replica_hosts_as_publishers` is only relevant for redirected publishers.</span></span> <span data-ttu-id="da077-121">パブリッシャー データベースが可用性グループのメンバーである場合、ストアド プロシージャ `sp_redirect_publisher` を使用して、パブリッシャーおよびパブリッシャー データベースを可用性グループの可用性グループ リスナー名に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="da077-121">If the publisher database is a member of an availability group, use the stored procedure `sp_redirect_publisher` to associate the publisher and publisher database with the Availability Group Listener Name of the availability group.</span></span>  
  
  
