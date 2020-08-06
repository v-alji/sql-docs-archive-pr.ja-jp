---
title: 使用中のファイルを確認する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ccd65867-d4c0-43b2-8361-7fd41c6f79ac
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 51505b0dece146b7f6fcdf982e6f88a5715357e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640475"
---
# <a name="check-files-in-use"></a><span data-ttu-id="849ab-102">使用中のファイルの確認</span><span class="sxs-lookup"><span data-stu-id="849ab-102">Check Files In Use</span></span>
  <span data-ttu-id="849ab-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新プログラムのインストール後に Windows が再起動されないようにするには、[使用中のファイルの確認] ページを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新プログラムのセットアップ プログラムで必要とされるファイルをロックしているプロセスを特定します。</span><span class="sxs-lookup"><span data-stu-id="849ab-103">To avoid restarting Windows after you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] updates, use the Check Files in Use page to identify processes that are locking files required by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] update Setup program.</span></span>  
  
 <span data-ttu-id="849ab-104">更新する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続しているすべてのアプリケーションとサービスを停止します。</span><span class="sxs-lookup"><span data-stu-id="849ab-104">Stop all applications and services that make connections to the instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are being updated.</span></span> <span data-ttu-id="849ab-105">これには [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] および [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]を停止することが含まれます。</span><span class="sxs-lookup"><span data-stu-id="849ab-105">This includes stopping [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="849ab-106">セットアップで、インストール中にファイルがロックされていると認識された場合、インストール完了後にコンピューターの再起動が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="849ab-106">If Setup determines that files are locked during installation, you might have to restart your computer after installation is completed.</span></span> <span data-ttu-id="849ab-107">再起動が必要な場合は、コンピューターの再起動を促すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="849ab-107">If necessary, Setup prompts you to restart your computer.</span></span> <span data-ttu-id="849ab-108">セットアップ プログラムで、インストール中にサービスを終了する必要がある場合は、インストールの完了後にそのサービスが再起動されます。</span><span class="sxs-lookup"><span data-stu-id="849ab-108">If the Setup program must stop a service during installation, it will restart the service after installation is completed.</span></span>  
  
 <span data-ttu-id="849ab-109">インストール後にコンピューターを再起動しなくてもいいように、セットアップ時に、ファイルをロックしているプロセスの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="849ab-109">To eliminate the requirement to restart your computer after installation, Setup displays a list of processes that are locking files.</span></span> <span data-ttu-id="849ab-110">一覧表示されたプロセスおよびアプリケーションを停止または終了します。</span><span class="sxs-lookup"><span data-stu-id="849ab-110">Stop or end the processes and applications in the list.</span></span> <span data-ttu-id="849ab-111">次に、 **[確認の更新]** をクリックしてチェックを再実行します。</span><span class="sxs-lookup"><span data-stu-id="849ab-111">Then click **Refresh check** to rerun the check.</span></span> <span data-ttu-id="849ab-112">実行中のチェックを終了するには **[確認の停止]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="849ab-112">Click **Stop check** to end a check that is running.</span></span> <span data-ttu-id="849ab-113">ロックされているファイルが見つからなかった場合、表には何も表示されません。</span><span class="sxs-lookup"><span data-stu-id="849ab-113">If locked files are not found, the table is empty.</span></span> <span data-ttu-id="849ab-114">ロックされていたプロセスが終了または停止したら、 **[次へ]** をクリックして続行します。</span><span class="sxs-lookup"><span data-stu-id="849ab-114">When all locked processes have been closed or stopped, click **Next** to continue.</span></span>  
  
 <span data-ttu-id="849ab-115">セットアップにより、情報がログ ファイルに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="849ab-115">Setup logs the information in the log files.</span></span> <span data-ttu-id="849ab-116">ログ ファイルを表示する方法の詳細については、「 [SQL Server セットアップ ログ ファイルの表示と読み取り](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md) 」および「 [SQL Server のセットアップ ログ ファイルを読み取る方法](https://go.microsoft.com/fwlink/?LinkID=134490)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="849ab-116">For more information about how to view the log files, see [View and Read SQL Server Setup Log Files](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md) and [How to: Read a SQL Server Setup Log File](https://go.microsoft.com/fwlink/?LinkID=134490).</span></span>  
  
 <span data-ttu-id="849ab-117">次の情報がログ ファイルに含まれます。</span><span class="sxs-lookup"><span data-stu-id="849ab-117">The following information is included in the log file:</span></span>  
  
-   <span data-ttu-id="849ab-118">プロセスの名前</span><span class="sxs-lookup"><span data-stu-id="849ab-118">Name of the process</span></span>  
  
-   <span data-ttu-id="849ab-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の名前</span><span class="sxs-lookup"><span data-stu-id="849ab-119">Name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] feature</span></span>  
  
-   <span data-ttu-id="849ab-120">プロセスの種類</span><span class="sxs-lookup"><span data-stu-id="849ab-120">Process type</span></span>  
  
-   <span data-ttu-id="849ab-121">プロセスが実行されているアカウント</span><span class="sxs-lookup"><span data-stu-id="849ab-121">Account under which the process is running</span></span>  
  
-   <span data-ttu-id="849ab-122">プロセス ID</span><span class="sxs-lookup"><span data-stu-id="849ab-122">Process ID</span></span>  
  
-   <span data-ttu-id="849ab-123">ロックされているファイルの名前</span><span class="sxs-lookup"><span data-stu-id="849ab-123">Name of the file that is locked</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="849ab-124">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="849ab-124">UI element list</span></span>  
  
|<span data-ttu-id="849ab-125">名前</span><span class="sxs-lookup"><span data-stu-id="849ab-125">Name</span></span>|<span data-ttu-id="849ab-126">説明</span><span class="sxs-lookup"><span data-stu-id="849ab-126">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="849ab-127">Process</span><span class="sxs-lookup"><span data-stu-id="849ab-127">Process</span></span>|<span data-ttu-id="849ab-128">更新対象のファイルを使用しているプロセスの完全な名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="849ab-128">Displays the full name of the process that is using the files to be updated.</span></span>|  
|<span data-ttu-id="849ab-129">Type</span><span class="sxs-lookup"><span data-stu-id="849ab-129">Type</span></span>|<span data-ttu-id="849ab-130">プロセスの種類を表示します。</span><span class="sxs-lookup"><span data-stu-id="849ab-130">Displays the type of process.</span></span>|  
|<span data-ttu-id="849ab-131">Account</span><span class="sxs-lookup"><span data-stu-id="849ab-131">Account</span></span>|<span data-ttu-id="849ab-132">プロセスが実行されているアカウントを表示します。</span><span class="sxs-lookup"><span data-stu-id="849ab-132">Displays the account under which the process is running.</span></span>|  
|<span data-ttu-id="849ab-133">プロセス ID</span><span class="sxs-lookup"><span data-stu-id="849ab-133">Process ID</span></span>|<span data-ttu-id="849ab-134">プロセス ID を表示します。</span><span class="sxs-lookup"><span data-stu-id="849ab-134">Displays the process ID.</span></span>|  
  
  
