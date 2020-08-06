---
title: チェックインの管理 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- checkins [SQL Server Management Studio]
- checking in files
- source controls [SQL Server Management Studio], checkins
ms.assetid: 293e60f3-15e3-4258-b73a-8baabe15c760
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a868aafff6d9bd389671544b5f1898e82707d933
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645785"
---
# <a name="manage-checkins"></a><span data-ttu-id="5c96a-102">チェックインの管理</span><span class="sxs-lookup"><span data-stu-id="5c96a-102">Manage Checkins</span></span>
  <span data-ttu-id="5c96a-103">ソース管理の対象ファイルに加えた変更を他のユーザーが利用できるようにするには、そのファイルをチェックインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5c96a-103">To make changes to a source-controlled file available to other users, you must check in the file.</span></span> <span data-ttu-id="5c96a-104">ファイルをチェックインすると、作成したバージョンがソース管理プロバイダーにコピーされ、それがファイルの最新バージョンになり、適切な権限を持ったユーザーからの利用が可能になります。</span><span class="sxs-lookup"><span data-stu-id="5c96a-104">When you check in a file, the version you have created is copied to the source control provider, becomes the latest version of the file, and is generally available to users who have the appropriate permissions.</span></span>  
  
 <span data-ttu-id="5c96a-105">を使用して [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ファイルをチェックインします。</span><span class="sxs-lookup"><span data-stu-id="5c96a-105">Use [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to check in files.</span></span> <span data-ttu-id="5c96a-106">ソース管理ストアを定期的に更新する必要があり、しかも一連のファイルに対する管理を継続しなければならない場合は、チェックインしたファイルをチェックアウト状態のままにするように設定することができます。</span><span class="sxs-lookup"><span data-stu-id="5c96a-106">When you need to update the source control store periodically, but also need to maintain control over a set of files, you can specify that files you check in remain checked out to you.</span></span>  
  
 <span data-ttu-id="5c96a-107">このトピックでは、次の内容について紹介します。</span><span class="sxs-lookup"><span data-stu-id="5c96a-107">The following table describes the topics in this section.</span></span>  
  
|<span data-ttu-id="5c96a-108">トピック</span><span class="sxs-lookup"><span data-stu-id="5c96a-108">Topic</span></span>|<span data-ttu-id="5c96a-109">説明</span><span class="sxs-lookup"><span data-stu-id="5c96a-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5c96a-110">ファイルのチェックイン</span><span class="sxs-lookup"><span data-stu-id="5c96a-110">Check In Files</span></span>](../../2014/database-engine/check-in-files.md)|<span data-ttu-id="5c96a-111">修正したファイルをチェックインする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="5c96a-111">Provides instructions on how to check in a file you have modified.</span></span>|  
|[<span data-ttu-id="5c96a-112">変更されたファイルの一覧表示</span><span class="sxs-lookup"><span data-stu-id="5c96a-112">View a List of Modified Files</span></span>](../../2014/database-engine/view-a-list-of-modified-files.md)|<span data-ttu-id="5c96a-113">修正が加えられているファイルの一覧を表示する方法、および作業の終了時にそれらのファイルを一度にチェックインする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="5c96a-113">Explains how to display a list of modified files that you can check in together when you are finished working.</span></span>|  
|[<span data-ttu-id="5c96a-114">チェックインされているファイルの編集</span><span class="sxs-lookup"><span data-stu-id="5c96a-114">Edit Checked-In Files</span></span>](../../2014/database-engine/edit-checked-in-files.md)|<span data-ttu-id="5c96a-115">チェックアウトしていないファイルを修正できるように [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 環境を構成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="5c96a-115">Explains how to configure the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] environment so that you can modify files that are not checked out.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5c96a-116">参照</span><span class="sxs-lookup"><span data-stu-id="5c96a-116">See Also</span></span>  
 [<span data-ttu-id="5c96a-117">チェックアウトの管理</span><span class="sxs-lookup"><span data-stu-id="5c96a-117">Manage Checkouts</span></span>](../../2014/database-engine/manage-checkouts.md)  
  
  
