---
title: MSSQLSERVER_21893 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21893 (Database Engine error)
ms.assetid: 1ab1195a-fe2a-4e06-b871-b177b6bea1fe
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 92479d7727ac2300d6a60d02492667d99a69b022
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643399"
---
# <a name="mssqlserver_21893"></a><span data-ttu-id="ad875-102">MSSQLSERVER_21893</span><span class="sxs-lookup"><span data-stu-id="ad875-102">MSSQLSERVER_21893</span></span>
    
## <a name="details"></a><span data-ttu-id="ad875-103">詳細</span><span class="sxs-lookup"><span data-stu-id="ad875-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ad875-104">製品名</span><span class="sxs-lookup"><span data-stu-id="ad875-104">Product Name</span></span>|<span data-ttu-id="ad875-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ad875-105">SQL Server</span></span>|  
|<span data-ttu-id="ad875-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="ad875-106">Event ID</span></span>|<span data-ttu-id="ad875-107">21893</span><span class="sxs-lookup"><span data-stu-id="ad875-107">21893</span></span>|  
|<span data-ttu-id="ad875-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="ad875-108">Event Source</span></span>|<span data-ttu-id="ad875-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ad875-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ad875-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ad875-110">Component</span></span>|<span data-ttu-id="ad875-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ad875-111">SQLEngine</span></span>|  
|<span data-ttu-id="ad875-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="ad875-112">Symbolic Name</span></span>|<span data-ttu-id="ad875-113">SQLErrorNum21893</span><span class="sxs-lookup"><span data-stu-id="ad875-113">SQLErrorNum21893</span></span>|  
|<span data-ttu-id="ad875-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="ad875-114">Message Text</span></span>|<span data-ttu-id="ad875-115">元のパブリッシャー '%s' のサブスクライバー (%s) は、リダイレクトされたパブリッシャー '%s' でリモート サーバーとして表示されていません。</span><span class="sxs-lookup"><span data-stu-id="ad875-115">The subscribers ( %s ) of original publisher '%s' do not appear as remote servers at redirected publisher '%s'.</span></span> <span data-ttu-id="ad875-116">`sp_addlinkedserver`リダイレクトされたパブリッシャーでを実行して、これらのサブスクライバーをリモートサーバーとして追加します。</span><span class="sxs-lookup"><span data-stu-id="ad875-116">Run `sp_addlinkedserver` at the redirected publisher to add these subscribers as remote servers .</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ad875-117">説明</span><span class="sxs-lookup"><span data-stu-id="ad875-117">Explanation</span></span>  
 <span data-ttu-id="ad875-118">`sp_validate_redirected_publisher` は、リモート サーバーでパブリッシャー データベースのサブスクリプション メタデータ テーブルを使用して関連付けられているサブスクライバーを特定し、サブスクライバーの master.dbo.sysservers に関連付けられているエントリがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ad875-118">`sp_validate_redirected_publisher` uses the subscription metadata tables of the publisher database at the remote server to identify its associated subscribers and verifies that there are associated entries in master.dbo.sysservers for the subscribers.</span></span> <span data-ttu-id="ad875-119">このエラーは、特定されたサブスクライバーのいずれかが存在しない場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="ad875-119">This error is returned if any of the identified subscribers are not present.</span></span>  
  
 <span data-ttu-id="ad875-120">このエラーは重大なエラーとは見なされません。</span><span class="sxs-lookup"><span data-stu-id="ad875-120">This error is not considered a fatal error.</span></span> <span data-ttu-id="ad875-121">新しいパブリッシャーで適切なサブスクライバー エントリを取得できなくてもレプリケーションに対する影響は限定的なため、このエラーが発生するとエージェントは情報としてエラーをログに記録しますが、終了することはありません。</span><span class="sxs-lookup"><span data-stu-id="ad875-121">Agents encountering this error will log the error as informational but will not terminate, since a failure to have appropriate subscriber entries at the new publisher has limited impact on replication.</span></span> <span data-ttu-id="ad875-122">sysservers にサブスクライバーの適切なエントリがないと、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を介して一部のサブスクリプション管理操作を実行したときに失敗する場合があります。</span><span class="sxs-lookup"><span data-stu-id="ad875-122">Without an appropriate entry for a subscriber in sysservers, some subscription management activities may fail when executed through [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="ad875-123">ただし、これらと同じ操作は、管理ストアド プロシージャを明示的に実行することによって正常に実行できます。</span><span class="sxs-lookup"><span data-stu-id="ad875-123">However, these same activities can be successfully performed by executing the management stored procedures explicitly.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ad875-124">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="ad875-124">User Action</span></span>  
 <span data-ttu-id="ad875-125">特定されたサブスクライバーのそれぞれについてリダイレクトされたパブリッシャーで `sp_addlinkedserver` を実行し、これらをリモート サーバーとして追加します。</span><span class="sxs-lookup"><span data-stu-id="ad875-125">Run `sp_addlinkedserver` at the redirected publisher for each of the identified subscribers to add them as remote servers.</span></span> <span data-ttu-id="ad875-126">次に、`sp_serveroption` を実行し、サーバーにサブスクライバー ビットを設定します。</span><span class="sxs-lookup"><span data-stu-id="ad875-126">Then, run `sp_serveroption` to set the subscriber bit for the server.</span></span>  
  
  
