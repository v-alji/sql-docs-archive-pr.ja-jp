---
title: チェックアウトの管理 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- source controls [SQL Server Management Studio], checkouts
- checkouts [SQL Server Management Studio]
- checking out files
ms.assetid: ddd4adba-d432-4005-9cb2-bb9ee3163d8e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cdfa25cdc27e707d4be705e66b215130c9d70ce1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645780"
---
# <a name="manage-checkouts"></a><span data-ttu-id="8485f-102">チェックアウトの管理</span><span class="sxs-lookup"><span data-stu-id="8485f-102">Manage Checkouts</span></span>
  <span data-ttu-id="8485f-103">ソース管理にファイルを追加した後にそのファイルを変更するには、まずファイルをチェックアウトする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8485f-103">After a file has been added to source control, you must check out the file before you can modify it.</span></span> <span data-ttu-id="8485f-104">ソース管理からファイルをチェックアウトすると、ソース管理プロバイダーによって、最新バージョンのコピーがローカル ディスクに作成され、ファイルの読み取り専用属性が解除されます。</span><span class="sxs-lookup"><span data-stu-id="8485f-104">When you check a file out of source control, the source control provider creates a copy of the latest version on your local disk and removes the read-only attribute of the file.</span></span> <span data-ttu-id="8485f-105">状況によっては、ファイルをチェックアウトしないで編集することが必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="8485f-105">In some circumstances you might need to edit a file without checking out the file.</span></span> <span data-ttu-id="8485f-106">ファイルをチェックアウトせずにファイルを編集する方法の詳細については、「チェックインされた[ファイルの編集](../../2014/database-engine/edit-checked-in-files.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8485f-106">For more information about editing a file without checking the file out, see [Edit Checked-In Files](../../2014/database-engine/edit-checked-in-files.md).</span></span>  
  
 <span data-ttu-id="8485f-107">を使用すると、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 手動または自動でファイルをチェックアウトできます。</span><span class="sxs-lookup"><span data-stu-id="8485f-107">You can use [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to check out files manually or automatically.</span></span> <span data-ttu-id="8485f-108">ファイルを手動でチェックアウトするには、環境内のファイルを含むソリューションを開き、 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] [チェックアウト**Check Out** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8485f-108">You check out files manually by opening the solution that contains the files in the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment, and then clicking the **Check Out** command.</span></span> <span data-ttu-id="8485f-109">ファイルを自動的にチェックアウトするには、[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 環境でそのための設定を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="8485f-109">You can check out files automatically if you configure the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment to do so.</span></span>  
  
 <span data-ttu-id="8485f-110">管理者がソース管理プロバイダーに対して設定したオプションによっては、ファイルのチェックアウトを排他モードで行うことも、共有モードで行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="8485f-110">Depending on the options that your administrator sets on your source control provider, you can also check out files in exclusive or shared mode.</span></span> <span data-ttu-id="8485f-111">ファイルを排他モードでチェックアウトする場合は、チェックアウトしたユーザーだけがそのファイルを変更できます。このユーザーがファイルをチェックインするまで、他のユーザーはそのファイルをチェックアウトできません。</span><span class="sxs-lookup"><span data-stu-id="8485f-111">When you check out a file exclusively, only you can modify it, and no other user can check out the file until you check it in.</span></span> <span data-ttu-id="8485f-112">ファイルを共有モードでチェックアウトする場合は、複数のユーザーが同じファイルをチェックアウトできます。</span><span class="sxs-lookup"><span data-stu-id="8485f-112">When you check out a file in shared mode, any number of users can check out the same file.</span></span> <span data-ttu-id="8485f-113">その場合、それぞれのユーザーがファイルをチェックインすると、ソース管理プロバイダーは、そのファイルを最新のサーバー バージョンにマージしようとします。</span><span class="sxs-lookup"><span data-stu-id="8485f-113">As each user checks in the file, the source control provider attempts to merge the file with the latest server version of the file.</span></span> <span data-ttu-id="8485f-114">チェックインするバージョンと最新バージョンの間に競合がある場合は、ソース管理プロバイダーによって、競合を解決するための画面が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8485f-114">If conflicts arise between the version that is being checked in and the latest version, the source control provider prompts the user to resolve the conflicts.</span></span>  
  
 <span data-ttu-id="8485f-115">このトピックでは、次の内容について紹介します。</span><span class="sxs-lookup"><span data-stu-id="8485f-115">The following table describes the topics in this section.</span></span>  
  
|<span data-ttu-id="8485f-116">トピック</span><span class="sxs-lookup"><span data-stu-id="8485f-116">Topic</span></span>|<span data-ttu-id="8485f-117">説明</span><span class="sxs-lookup"><span data-stu-id="8485f-117">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="8485f-118">ファイルのチェックアウト</span><span class="sxs-lookup"><span data-stu-id="8485f-118">Check Out Files</span></span>](../../2014/database-engine/check-out-files.md)|<span data-ttu-id="8485f-119">ファイルを変更できるようにチェックアウトする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="8485f-119">Provides instructions on how to check out a file so you can modify it.</span></span>|  
|[<span data-ttu-id="8485f-120">チェックアウトの取り消し</span><span class="sxs-lookup"><span data-stu-id="8485f-120">Undo Checkouts</span></span>](../../2014/database-engine/undo-checkouts.md)|<span data-ttu-id="8485f-121">既存のチェックアウトを取り消す方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="8485f-121">Explains how to cancel an existing checkout.</span></span>|  
|[<span data-ttu-id="8485f-122">編集するファイルの自動的なチェックアウト</span><span class="sxs-lookup"><span data-stu-id="8485f-122">Automatically Check Out Files Upon Edit</span></span>](../../2014/database-engine/automatically-check-out-files-upon-edit.md)|<span data-ttu-id="8485f-123">ファイルの編集を始めるとファイルが自動的にチェックアウトされるようにソース管理を設定する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="8485f-123">Explains how to configure source control to check out a file when you start to edit it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8485f-124">参照</span><span class="sxs-lookup"><span data-stu-id="8485f-124">See Also</span></span>  
 <span data-ttu-id="8485f-125">[チェックインの管理](../../2014/database-engine/manage-checkins.md) </span><span class="sxs-lookup"><span data-stu-id="8485f-125">[Manage Checkins](../../2014/database-engine/manage-checkins.md) </span></span>  
 [<span data-ttu-id="8485f-126">チェックインされているファイルの編集</span><span class="sxs-lookup"><span data-stu-id="8485f-126">Edit Checked-In Files</span></span>](../../2014/database-engine/edit-checked-in-files.md)  
  
  
