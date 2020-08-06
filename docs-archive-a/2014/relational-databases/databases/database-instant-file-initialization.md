---
title: データベースのファイルの瞬時初期化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- initializing files [SQL Server]
- instant file initializations [SQL Server]
- fast file initialization (SQL Server)
- file initialization [SQL Server]
ms.assetid: 1ad468f5-4f75-480b-aac6-0b01b048bd67
author: stevestein
ms.author: sstein
ms.openlocfilehash: dedd2c5b8d075dee8aeeb438904137558c664d95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640067"
---
# <a name="database-instant-file-initialization"></a><span data-ttu-id="159d6-102">データベースのファイルの瞬時初期化</span><span class="sxs-lookup"><span data-stu-id="159d6-102">Database Instant File Initialization</span></span>
  <span data-ttu-id="159d6-103">データおよびログ ファイルの初期化は、ディスクに以前削除したファイルのデータが残っている場合にそれを上書きするために行います。</span><span class="sxs-lookup"><span data-stu-id="159d6-103">Data and log files are initialized to overwrite any existing data left on the disk from previously deleted files.</span></span> <span data-ttu-id="159d6-104">データおよびログ ファイルは、次のいずれかの操作を実行したときに、ファイルを 0 で埋め込むことにより、まず初期化されます。</span><span class="sxs-lookup"><span data-stu-id="159d6-104">Data and log files are first initialized by filling the files with zeros when you perform one of the following operations:</span></span>  
  
-   <span data-ttu-id="159d6-105">データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="159d6-105">Create a database.</span></span>  
  
-   <span data-ttu-id="159d6-106">既存のデータベースへのファイル、ログまたはデータの追加。</span><span class="sxs-lookup"><span data-stu-id="159d6-106">Add files, log or data, to an existing database.</span></span>  
  
-   <span data-ttu-id="159d6-107">既存のファイルのサイズを大きくする (自動拡張操作を含む)。</span><span class="sxs-lookup"><span data-stu-id="159d6-107">Increase the size of an existing file (including autogrow operations).</span></span>  
  
-   <span data-ttu-id="159d6-108">データベースまたはファイル グループの復元。</span><span class="sxs-lookup"><span data-stu-id="159d6-108">Restore a database or filegroup.</span></span>  
  
 <span data-ttu-id="159d6-109">上記の操作は、ファイルの初期化によって余分な時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="159d6-109">File initialization causes these operations to take longer.</span></span> <span data-ttu-id="159d6-110">ただし、データを初めてファイルに書き込む際には、オペレーティング システムがファイルを 0 で埋め込む必要はありません。</span><span class="sxs-lookup"><span data-stu-id="159d6-110">However, when data is written to the files for the first time, the operating system does not have to fill the files with zeros.</span></span>  
  
## <a name="instant-file-initialization"></a><span data-ttu-id="159d6-111">ファイルの瞬時初期化</span><span class="sxs-lookup"><span data-stu-id="159d6-111">Instant File Initialization</span></span>  
 <span data-ttu-id="159d6-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、データ ファイルを瞬時に初期化できます。</span><span class="sxs-lookup"><span data-stu-id="159d6-112">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], data files can be initialized instantaneously.</span></span> <span data-ttu-id="159d6-113">これにより、上記のファイル操作を高速に実行することが可能になります。</span><span class="sxs-lookup"><span data-stu-id="159d6-113">This allows for fast execution of the previously mentioned file operations.</span></span> <span data-ttu-id="159d6-114">ファイルの瞬時初期化では、0 で埋め込むことなく、使用中のディスク領域の返還を要求します。</span><span class="sxs-lookup"><span data-stu-id="159d6-114">Instant file initialization reclaims used disk space without filling that space with zeros.</span></span> <span data-ttu-id="159d6-115">代わりに、新しいデータがファイルに書き込まれるときに、ディスクの内容が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="159d6-115">Instead, disk content is overwritten as new data is written to the files.</span></span> <span data-ttu-id="159d6-116">ログ ファイルを瞬時に初期化することはできません。</span><span class="sxs-lookup"><span data-stu-id="159d6-116">Log files cannot be initialized instantaneously.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="159d6-117">ファイルの瞬時初期化は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[winxppro](../../includes/winxppro-md.md)] または [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 以降のバージョンでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="159d6-117">Instant file initialization is available only on [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[winxppro](../../includes/winxppro-md.md)] or [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] or later versions.</span></span>  
  
 <span data-ttu-id="159d6-118">ファイルの瞬時初期化は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER) サービス アカウントに SE_MANAGE_VOLUME_NAME が許可されている場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="159d6-118">Instant file initialization is only available if the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER) service account has been granted SE_MANAGE_VOLUME_NAME.</span></span> <span data-ttu-id="159d6-119">Windows Administrator グループのメンバーにはこの権限があり、他のユーザーを **ボリュームの保守タスクを実行** セキュリティ ポリシーに追加することにより、これらのユーザーにこの権限を許可することができます。</span><span class="sxs-lookup"><span data-stu-id="159d6-119">Members of the Windows Administrator group have this right and can grant it to other users by adding them to the **Perform Volume Maintenance Tasks** security policy.</span></span> <span data-ttu-id="159d6-120">ユーザー権利の割り当ての詳細については、Windows のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="159d6-120">For more information about assigning user rights, see the Windows documentation.</span></span>  
  
 <span data-ttu-id="159d6-121">ファイルの瞬時初期化は、TDE が有効になっている場合は使用できません。</span><span class="sxs-lookup"><span data-stu-id="159d6-121">Instant file initialization is not available when TDE is enabled.</span></span>  
  
 <span data-ttu-id="159d6-122">アカウントに `Perform volume maintenance tasks` 権限を許可する方法。</span><span class="sxs-lookup"><span data-stu-id="159d6-122">To grant an account the `Perform volume maintenance tasks` permission:</span></span>  
  
1.  <span data-ttu-id="159d6-123">バックアップ ファイルを作成するコンピューター上で、`Local Security Policy` アプリケーション (`secpol.msc`) を開きます。</span><span class="sxs-lookup"><span data-stu-id="159d6-123">On the computer where the backup file will be created, open the `Local Security Policy` application (`secpol.msc`).</span></span>  
  
2.  <span data-ttu-id="159d6-124">左側のペインで **[ローカル ポリシー]** を展開し、 **[ユーザー権利の割り当て]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="159d6-124">In the left pane, expand **Local Policies**, and then click **User Rights Assignment**.</span></span>  
  
3.  <span data-ttu-id="159d6-125">右側のペインで、 **[ボリュームの保守タスクを実行]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="159d6-125">In the right pane, double-click **Perform volume maintenance tasks**.</span></span>  
  
4.  <span data-ttu-id="159d6-126">**[ユーザーまたはグループの追加]** をクリックし、バックアップに使用される任意のユーザー アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="159d6-126">Click **Add User or Group** and add any user accounts that are used for backups.</span></span>  
  
5.  <span data-ttu-id="159d6-127">[**適用**] をクリックし、すべての `Local Security Policy` ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="159d6-127">Click **Apply**, and then close all `Local Security Policy` dialog boxes.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="159d6-128">セキュリティの考慮事項</span><span class="sxs-lookup"><span data-stu-id="159d6-128">Security Considerations</span></span>  
 <span data-ttu-id="159d6-129">削除されたディスクの内容は、新しいデータがファイルに書き込まれるときにのみ上書きされるため、許可されていないプリンシパルがこの削除された内容にアクセスする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="159d6-129">Because the deleted disk content is overwritten only as new data is written to the files, the deleted content might be accessed by an unauthorized principal.</span></span> <span data-ttu-id="159d6-130">データベース ファイルが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスにアタッチされている間は、ファイル上の任意のアクセス制御リスト (DACL) により、このような情報公開の脅威は低減されます。</span><span class="sxs-lookup"><span data-stu-id="159d6-130">While the database file is attached to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this information disclosure threat is reduced by the discretionary access control list (DACL) on the file.</span></span> <span data-ttu-id="159d6-131">この DACL により、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントとローカル管理者のみにファイル アクセスが許可されます。</span><span class="sxs-lookup"><span data-stu-id="159d6-131">This DACL allows file access only to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account and the local administrator.</span></span> <span data-ttu-id="159d6-132">しかし、ファイルがデタッチされると、SE_MANAGE_VOLUME_NAME のないユーザーまたはサービスによりアクセスされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="159d6-132">However, when the file is detached, it may be accessed by a user or service that does not have SE_MANAGE_VOLUME_NAME.</span></span> <span data-ttu-id="159d6-133">データベースがバックアップされる際にも、同様の脅威が存在します。</span><span class="sxs-lookup"><span data-stu-id="159d6-133">A similar threat exists when the database is backed up.</span></span> <span data-ttu-id="159d6-134">バックアップ ファイルが適切な DACL で保護されていないと、許可されていないユーザーやサービスが削除された内容を利用できるようになる場合があります。</span><span class="sxs-lookup"><span data-stu-id="159d6-134">The deleted content can become available to an unauthorized user or service if the backup file is not protected with an appropriate DACL.</span></span>  
  
 <span data-ttu-id="159d6-135">削除された内容が公開される可能性が懸念される場合は、次のいずれか、または両方を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="159d6-135">If the potential for disclosing deleted content is a concern, you should do one or both of the following:</span></span>  
  
-   <span data-ttu-id="159d6-136">デタッチされたすべてのデータ ファイルおよびバックアップ ファイルに、常に限定的な DACL が設定されるようにする。</span><span class="sxs-lookup"><span data-stu-id="159d6-136">Always make sure that any detached data files and backup files have restrictive DACLs.</span></span>  
  
-   <span data-ttu-id="159d6-137">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントの SE_MANAGE_VOLUME_NAME を禁止して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに対するファイルの瞬時初期化を無効にする。</span><span class="sxs-lookup"><span data-stu-id="159d6-137">Disable instant file initialization for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by revoking SE_MANAGE_VOLUME_NAME from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="159d6-138">ファイルの瞬時初期化の無効化で効果があるのは、ユーザー権限が禁止された後で作成またはサイズ増加されたファイルのみです。</span><span class="sxs-lookup"><span data-stu-id="159d6-138">Disabling instant file initialization only affects files that are created or increased in size after the user right is revoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="159d6-139">参照</span><span class="sxs-lookup"><span data-stu-id="159d6-139">See Also</span></span>  
 [<span data-ttu-id="159d6-140">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="159d6-140">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
  
