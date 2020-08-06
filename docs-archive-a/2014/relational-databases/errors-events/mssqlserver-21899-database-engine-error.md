---
title: MSSQLSERVER_21899 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21899 (Database Engine error)
ms.assetid: 32b87a7c-5380-4638-b147-dd78618f6625
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cb1af04b56685d0e1b5a703b812d08d88909b693
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715321"
---
# <a name="mssqlserver_21899"></a><span data-ttu-id="4fc3f-102">MSSQLSERVER_21899</span><span class="sxs-lookup"><span data-stu-id="4fc3f-102">MSSQLSERVER_21899</span></span>
    
## <a name="details"></a><span data-ttu-id="4fc3f-103">詳細</span><span class="sxs-lookup"><span data-stu-id="4fc3f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4fc3f-104">製品名</span><span class="sxs-lookup"><span data-stu-id="4fc3f-104">Product Name</span></span>|<span data-ttu-id="4fc3f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="4fc3f-105">SQL Server</span></span>|  
|<span data-ttu-id="4fc3f-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4fc3f-106">Event ID</span></span>|<span data-ttu-id="4fc3f-107">21899</span><span class="sxs-lookup"><span data-stu-id="4fc3f-107">21899</span></span>|  
|<span data-ttu-id="4fc3f-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="4fc3f-108">Event Source</span></span>|<span data-ttu-id="4fc3f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="4fc3f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="4fc3f-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="4fc3f-110">Component</span></span>|<span data-ttu-id="4fc3f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="4fc3f-111">SQLEngine</span></span>|  
|<span data-ttu-id="4fc3f-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="4fc3f-112">Symbolic Name</span></span>|<span data-ttu-id="4fc3f-113">SQLErrorNum21899</span><span class="sxs-lookup"><span data-stu-id="4fc3f-113">SQLErrorNum21899</span></span>|  
|<span data-ttu-id="4fc3f-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="4fc3f-114">Message Text</span></span>|<span data-ttu-id="4fc3f-115">元のパブリッシャー '%s' のサブスクライバーの sysserver エントリがあるかどうかを判断するために、リダイレクトされたパブリッシャー '%s' で実行したクエリが、エラー '%d'、エラー メッセージ '%s' で失敗しました。</span><span class="sxs-lookup"><span data-stu-id="4fc3f-115">The query at the redirected publisher '%s' to determine whether there were sysserver entries for the subscribers of the original publisher '%s' failed with error '%d', error message '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4fc3f-116">説明</span><span class="sxs-lookup"><span data-stu-id="4fc3f-116">Explanation</span></span>  
 <span data-ttu-id="4fc3f-117">`sp_validate_redirected_publisher` は、リモート サーバーでパブリッシャー データベースのサブスクリプション メタデータ テーブルにクエリを実行し、関連付けられているサブスクライバーを特定します。</span><span class="sxs-lookup"><span data-stu-id="4fc3f-117">`sp_validate_redirected_publisher` queries the subscription metadata tables of the publisher database at the remote server to determine its associated subscribers.</span></span> <span data-ttu-id="4fc3f-118">このクエリが失敗すると、エラー 21899 が返されます。</span><span class="sxs-lookup"><span data-stu-id="4fc3f-118">Error 21899 is returned if this query fails.</span></span> <span data-ttu-id="4fc3f-119">検証のクエリでは、リダイレクトされたパブリッシャーのパブリッシュされたデータベースにアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4fc3f-119">The validation query requires access to the published database at the redirected publisher.</span></span> <span data-ttu-id="4fc3f-120">元のパブリッシャーに対して `sp_adddistpublisher` が呼び出されたときに指定されたログインに、リダイレクトされたパブリッシャーのパブリッシュされたデータベースにアクセスするための権限がない場合、エラー 21899 が返されます。</span><span class="sxs-lookup"><span data-stu-id="4fc3f-120">If the login specified when `sp_adddistpublisher` is called for the original publisher is not authorized to access the published database at the redirected publisher, error 21899 is returned.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4fc3f-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="4fc3f-121">User Action</span></span>  
 <span data-ttu-id="4fc3f-122">示されたエラー メッセージを確認し、エラーの原因を特定して適切な修正措置を行います。</span><span class="sxs-lookup"><span data-stu-id="4fc3f-122">Review the cited error message to determine the cause of the failure and take appropriate corrective action</span></span>  
  
  
