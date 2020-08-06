---
title: '[メンテナンス クリーンアップ タスク] (メンテナンス プラン) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.cleanup.f1
helpviewer_keywords:
- Maintenance Cleanup Task dialog box
ms.assetid: 022b679c-6799-4c13-9185-814224a20412
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9023881ff5cf5ba5ddd8c61aa179c5881162bf44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641639"
---
# <a name="maintenance-cleanup-task-maintenance-plan"></a><span data-ttu-id="3ef1b-102">[メンテナンス クリーンアップ タスク] (メンテナンス プラン)</span><span class="sxs-lookup"><span data-stu-id="3ef1b-102">Maintenance Cleanup Task (Maintenance Plan)</span></span>
  <span data-ttu-id="3ef1b-103">**[メンテナンス クリーンアップ タスク]** を使用すると、メンテナンス プランで作成されたテキスト レポートやデータベースのバックアップ ファイルなど、メンテナンス プランに関連する古いファイルを削除できます。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-103">Use the **Maintenance Cleanup Task** to remove old files related to maintenance plans, including text reports created by maintenance plans and database backup files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ef1b-104">メンテナンス クリーンアップ タスクでは、指定したディレクトリのサブフォルダーにあるファイルは自動的に削除されません。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-104">The Maintenance Cleanup task does not automatically delete files in the subfolders of the specified directory.</span></span> <span data-ttu-id="3ef1b-105">この機能によって、メンテナンス クリーンアップ タスクを使ってファイルを削除するなど、悪意のある攻撃を受ける危険性を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-105">This feature reduces the possibility of a malicious attack that uses the Maintenance Cleanup task to delete files.</span></span> <span data-ttu-id="3ef1b-106">直下のサブフォルダーにあるファイルを削除する場合は、 **[直下のサブフォルダーを含める]** を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-106">If you want to delete files in first-level subfolders, you must select **Include first-level subfolders**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3ef1b-107">Options</span><span class="sxs-lookup"><span data-stu-id="3ef1b-107">Options</span></span>  
 <span data-ttu-id="3ef1b-108">**接続**</span><span class="sxs-lookup"><span data-stu-id="3ef1b-108">**Connection**</span></span>  
 <span data-ttu-id="3ef1b-109">現在の接続を表示します。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-109">Displays the current connection.</span></span>  
  
 <span data-ttu-id="3ef1b-110">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="3ef1b-110">**New**</span></span>  
 <span data-ttu-id="3ef1b-111">このタスクを実行するときに使用する新しいサーバー接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-111">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="3ef1b-112">**[新しい接続]** ダイアログ ボックスについては、後で説明します。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-112">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="3ef1b-113">**[バックアップ ファイル]**</span><span class="sxs-lookup"><span data-stu-id="3ef1b-113">**Backup files**</span></span>  
 <span data-ttu-id="3ef1b-114">バックアップ ファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-114">Delete backup files.</span></span>  
  
 <span data-ttu-id="3ef1b-115">**[メンテナンス プラン テキスト レポート]**</span><span class="sxs-lookup"><span data-stu-id="3ef1b-115">**Maintenance Plan text reports**</span></span>  
 <span data-ttu-id="3ef1b-116">以前に実行されたメンテナンス プランのテキスト レポートを削除します。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-116">Delete text reports of previously run maintenance plans.</span></span>  
  
 <span data-ttu-id="3ef1b-117">**[特定のファイルを削除する]**</span><span class="sxs-lookup"><span data-stu-id="3ef1b-117">**Delete specific file**</span></span>  
 <span data-ttu-id="3ef1b-118">**[ファイル名]** ボックスに指定した特定のファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-118">Delete the specific file provided in the **File name** box.</span></span>  
  
 <span data-ttu-id="3ef1b-119">**[ファイル名]**</span><span class="sxs-lookup"><span data-stu-id="3ef1b-119">**File name**</span></span>  
 <span data-ttu-id="3ef1b-120">削除するファイルのパスと名前です。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-120">Path and name of the file to be deleted.</span></span>  
  
 <span data-ttu-id="3ef1b-121">**[フォルダーを検索し、拡張子に基づいてファイルを削除する]**</span><span class="sxs-lookup"><span data-stu-id="3ef1b-121">**Search folder and delete files based on an extension**</span></span>  
 <span data-ttu-id="3ef1b-122">指定したフォルダー内にある、指定した拡張子を持つすべてのファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-122">Delete all files with the specified extension in the specified folder.</span></span> <span data-ttu-id="3ef1b-123">このオプションは、複数のファイル (たとえば、"Tuesday" フォルダー内にある、拡張子が .bak のすべてのバックアップ ファイル) を一度に削除する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-123">Use this to delete multiple files at once, such as all backup files with the .bak extension, in the Tuesday folder.</span></span>  
  
 <span data-ttu-id="3ef1b-124">**フォルダー**</span><span class="sxs-lookup"><span data-stu-id="3ef1b-124">**Folder**</span></span>  
 <span data-ttu-id="3ef1b-125">削除するファイルが格納されているフォルダーのパスと名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-125">Path and name of the folder containing the files to be deleted.</span></span>  
  
 <span data-ttu-id="3ef1b-126">**[ファイル拡張子]**</span><span class="sxs-lookup"><span data-stu-id="3ef1b-126">**File extension**</span></span>  
 <span data-ttu-id="3ef1b-127">削除するファイルのファイル拡張子を指定します。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-127">Provide the file extension of the files to be deleted.</span></span>  
  
 <span data-ttu-id="3ef1b-128">**[直下のサブフォルダーを含める]**</span><span class="sxs-lookup"><span data-stu-id="3ef1b-128">**Include first-level subfolders**</span></span>  
 <span data-ttu-id="3ef1b-129">**[ファイル拡張子]** に指定された拡張子を持つファイルを、 **[フォルダー]** の直下のサブフォルダーから削除します。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-129">Delete files with the extension specified for **File extension** from first-level subfolders under **Folder**.</span></span>  
  
 <span data-ttu-id="3ef1b-130">**[タスク実行時にファイルの経過期間に基づいてファイルを削除する]**</span><span class="sxs-lookup"><span data-stu-id="3ef1b-130">**Delete files based on the age of the file at task run time**</span></span>  
 <span data-ttu-id="3ef1b-131">**[次の期間経過したファイルを削除]** ボックスに数値と時間単位を指定して、削除するファイルの最小経過期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-131">Specify the minimum age of the files that you want to delete by providing a number, and unit of time in the **Delete files older than the following** box.</span></span>  
  
 <span data-ttu-id="3ef1b-132">**[次の期間経過したファイルを削除]**</span><span class="sxs-lookup"><span data-stu-id="3ef1b-132">**Delete files older than the following**</span></span>  
 <span data-ttu-id="3ef1b-133">数値と時間単位 ([日]、[週]、[月]、または [年]) を指定して、削除するファイルの最小経過期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-133">Specify the minimum age of the files that you want to delete by providing a number, and unit of time (Day, Week, Month, or Year).</span></span> <span data-ttu-id="3ef1b-134">指定した期間より古いファイルが削除されます。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-134">Files older than the time frame specified will be deleted.</span></span>  
  
 <span data-ttu-id="3ef1b-135">**[T-SQL の表示]**</span><span class="sxs-lookup"><span data-stu-id="3ef1b-135">**View T-SQL**</span></span>  
 <span data-ttu-id="3ef1b-136">選択したオプションに基づき、このタスクでサーバーに対して実行される [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを表示します。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-136">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ef1b-137">影響を受けるオブジェクトが大量にある場合は、表示にかなりの時間を要する場合があります。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-137">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="3ef1b-138">[新しい接続] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="3ef1b-138">New Connection Dialog Box</span></span>  
 <span data-ttu-id="3ef1b-139">**接続名**</span><span class="sxs-lookup"><span data-stu-id="3ef1b-139">**Connection name**</span></span>  
 <span data-ttu-id="3ef1b-140">新しい接続の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-140">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="3ef1b-141">**[サーバー名の選択または入力]**</span><span class="sxs-lookup"><span data-stu-id="3ef1b-141">**Select or enter a server name**</span></span>  
 <span data-ttu-id="3ef1b-142">このタスクを実行するときに接続するサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-142">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="3ef1b-143">**...**</span><span class="sxs-lookup"><span data-stu-id="3ef1b-143">**...**</span></span>  
 <span data-ttu-id="3ef1b-144">利用可能なサーバーを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-144">Select to view the list of available servers.</span></span>  
  
 <span data-ttu-id="3ef1b-145">**[サーバーにログオンするための情報の入力]**</span><span class="sxs-lookup"><span data-stu-id="3ef1b-145">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="3ef1b-146">サーバーの認証情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-146">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="3ef1b-147">**[Windows NT の統合セキュリティを使用する]**</span><span class="sxs-lookup"><span data-stu-id="3ef1b-147">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="3ef1b-148">Microsoft Windows 認証を使用して [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-148">Connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] with Microsoft Windows Authentication.</span></span>  
  
 <span data-ttu-id="3ef1b-149">**[特定のユーザー名とパスワードを使用する]**</span><span class="sxs-lookup"><span data-stu-id="3ef1b-149">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="3ef1b-150">SQL Server 認証を使用して [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-150">Connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] using SQL Server Authentication.</span></span> <span data-ttu-id="3ef1b-151">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-151">This option is not available.</span></span>  
  
 <span data-ttu-id="3ef1b-152">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="3ef1b-152">**User name**</span></span>  
 <span data-ttu-id="3ef1b-153">認証に使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを指定します。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-153">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="3ef1b-154">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-154">This option is not available.</span></span>  
  
 <span data-ttu-id="3ef1b-155">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="3ef1b-155">**Password**</span></span>  
 <span data-ttu-id="3ef1b-156">認証に使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-156">Provide a password to use when authenticating.</span></span> <span data-ttu-id="3ef1b-157">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="3ef1b-157">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ef1b-158">参照</span><span class="sxs-lookup"><span data-stu-id="3ef1b-158">See Also</span></span>  
 [<span data-ttu-id="3ef1b-159">メンテナンス プラン</span><span class="sxs-lookup"><span data-stu-id="3ef1b-159">Maintenance Plans</span></span>](maintenance-plans.md)  
  
  
