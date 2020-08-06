---
title: MSSQLSERVER_21898 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21898 (Database Engine error)
ms.assetid: 02405b21-3d4e-4c2d-b4b3-d7b1ec05edb4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 78ce7eacf7f026bf9977af2c367b954a3639b357
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715325"
---
# <a name="mssqlserver_21898"></a><span data-ttu-id="65472-102">MSSQLSERVER_21898</span><span class="sxs-lookup"><span data-stu-id="65472-102">MSSQLSERVER_21898</span></span>
    
## <a name="details"></a><span data-ttu-id="65472-103">詳細</span><span class="sxs-lookup"><span data-stu-id="65472-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="65472-104">製品名</span><span class="sxs-lookup"><span data-stu-id="65472-104">Product Name</span></span>|<span data-ttu-id="65472-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="65472-105">SQL Server</span></span>|  
|<span data-ttu-id="65472-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="65472-106">Event ID</span></span>|<span data-ttu-id="65472-107">21898</span><span class="sxs-lookup"><span data-stu-id="65472-107">21898</span></span>|  
|<span data-ttu-id="65472-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="65472-108">Event Source</span></span>|<span data-ttu-id="65472-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="65472-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="65472-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="65472-110">Component</span></span>|<span data-ttu-id="65472-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="65472-111">SQLEngine</span></span>|  
|<span data-ttu-id="65472-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="65472-112">Symbolic Name</span></span>|<span data-ttu-id="65472-113">SQLErrorNum21898</span><span class="sxs-lookup"><span data-stu-id="65472-113">SQLErrorNum21898</span></span>|  
|<span data-ttu-id="65472-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="65472-114">Message Text</span></span>|<span data-ttu-id="65472-115">パブリッシャー '%s' は、ディストリビューション データベース '%s' を使用しますが、パブリッシング データベース '%s' をホストするために必要な '%s' を使用していません。</span><span class="sxs-lookup"><span data-stu-id="65472-115">The publisher '%s' uses distribution database '%s' and not '%s' which is required in order to host the publishing database '%s'.</span></span> <span data-ttu-id="65472-116">ディストリビューター '%s' で `sp_changedistpublisher` を実行して、パブリッシャーで使用されるディストリビューション データベースを '%s' に変更してください。</span><span class="sxs-lookup"><span data-stu-id="65472-116">Run `sp_changedistpublisher` at distributor '%s' to change the distribution database used by the publisher to '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="65472-117">説明</span><span class="sxs-lookup"><span data-stu-id="65472-117">Explanation</span></span>  
 <span data-ttu-id="65472-118">`sp_validate_redirected_publisher` は、ローカル ディストリビューターで msdb.dbo.MSdistpublishers にクエリを実行し、新しいパブリッシャーによって使用されるディストリビューション データベースが元のパブリッシャーによって使用されるディストリビューション データベースと同じであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="65472-118">`sp_validate_redirected_publisher` queries msdb.dbo.MSdistpublishers at the local distributor to verify that the distribution database used by the new publisher is the same as the distribution database used by the original publisher.</span></span> <span data-ttu-id="65472-119">このエラーは、これらのデータベースが異なり、パブリッシャーがパブリッシャー データベースに不適切なホストになる場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="65472-119">This error is returned when these databases are different, making the publisher an unsuitable host for the publisher database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="65472-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="65472-120">User Action</span></span>  
 <span data-ttu-id="65472-121">ストアド プロシージャ `sp_changedistpublisher` を実行し、新しいパブリッシャーのディストリビューション データベースを元のパブリッシャーによって使用されるデータベースに変更します。</span><span class="sxs-lookup"><span data-stu-id="65472-121">Execute stored procedure `sp_changedistpublisher` to change the distribution database for the new publisher to that used by the original publisher.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="65472-122">`sp_changedistpublisher` を実行すると、パブリッシャーのディストリビューターで `sp_adddistpublisher` を実行したときに間違ったディストリビューション データベースを入力した場合の問題が解決されます。</span><span class="sxs-lookup"><span data-stu-id="65472-122">Running `sp_changedistpublisher` will address the problem if the wrong distribution database was entered when `sp_adddistpublisher` was run at the distributor for the publisher.</span></span> <span data-ttu-id="65472-123">ただし、識別されたディストリビューション データベースを使用する別のパブリッシング データベースからの既存のパブリケーションがリモート パブリッシャーにある場合、この変更は適切ではありません。</span><span class="sxs-lookup"><span data-stu-id="65472-123">However, if the remote publisher has existing publications from another publishing database that make use of the identified distribution database, this change is not appropriate.</span></span> <span data-ttu-id="65472-124">指定されたディストリビューション データベースを使用するレプリケーションは、新しいパブリッシャーが適切なホストとして機能するために、体系的に削除してから元のパブリッシャーのディストリビューション データベースを使用して再確立する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65472-124">Replication using the named distribution database needs to be systematically removed and then reestablished using the original publisher's distribution database in order for the new publisher to function as a suitable host.</span></span>  
  
  
