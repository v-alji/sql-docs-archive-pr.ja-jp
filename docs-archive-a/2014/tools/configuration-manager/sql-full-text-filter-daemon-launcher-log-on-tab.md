---
title: SQL フルテキスト フィルター デーモン ランチャー ([ログオン] タブ) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 13e260f9-a75f-430b-88a3-959ddcead8fe
author: stevestein
ms.author: sstein
ms.openlocfilehash: cb3f23907e96214929617bf2923e46148c0ab1f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644726"
---
# <a name="sql-full-text-filter-daemon-launcher-log-on-tab"></a><span data-ttu-id="20911-102">SQL フルテキスト フィルター デーモン ランチャー ([ログオン] タブ)</span><span class="sxs-lookup"><span data-stu-id="20911-102">SQL Full-text Filter Daemon Launcher (Log On Tab)</span></span>
  <span data-ttu-id="20911-103">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]以降では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フルテキスト検索で SQL フルテキスト フィルター デーモン ランチャー (FDHOST ランチャー) サービスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="20911-103">Beginning in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the SQL Full-text Filter Daemon Launcher (FDHOST Launcher) service is used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] full-text search.</span></span> <span data-ttu-id="20911-104">フルテキスト検索を使用する場合はこのサービスが実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="20911-104">This service must be running if you use full-text search.</span></span> <span data-ttu-id="20911-105">フィルター デーモン ホスト プロセスの詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「フルテキスト検索のアーキテクチャ」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20911-105">For information about the filter daemon host processes, see "Full-Text Search Architecture" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="20911-106">**[SQL フルテキスト フィルター デーモン ランチャーのプロパティ]** ダイアログ ボックスの **[ログオン]** タブでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フルテキスト サービスが使用するアカウントの指定、アカウントのパスワードの変更、サービスの開始や停止を行います。</span><span class="sxs-lookup"><span data-stu-id="20911-106">Use the **Log On** tab of the **SQL Full-text Filter Daemon Launcher  Properties** dialog box to specify the account used by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] full-text service, to change the password of an account, and to start and stop the service.</span></span> <span data-ttu-id="20911-107">アカウントのパスワードを変更した場合、その変更はサービスの再起動後に有効になります。</span><span class="sxs-lookup"><span data-stu-id="20911-107">Changing the password of an account takes affect after restarting the service.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="20911-108">クラスター化されたインスタンス上のサービスで使用するアカウント名を変更する場合、新しいアカウントは、そのサービスのセットアップ時に指定したドメイン グループに属している必要があります。または、そのグループにメンバーを追加する権限が与えられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="20911-108">When changing the account name used by a service on a clustered instance, either the new account must be a member of the domain group specified during setup for the service, or you must have permission to add members to that group.</span></span> <span data-ttu-id="20911-109">グループのメンバーシップを変更する権限がない場合は、ドメイン管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="20911-109">If you do not have permission to modify group membership, contact the domain administrator.</span></span>  
>   
>  <span data-ttu-id="20911-110">サービスを実行するアカウントの選択の詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「Windows サービス アカウントの設定」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20911-110">For more information about selecting an account to run the service, see "Setting Up Windows Service Accounts" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="options"></a><span data-ttu-id="20911-111">オプション</span><span class="sxs-lookup"><span data-stu-id="20911-111">Options</span></span>  
 <span data-ttu-id="20911-112">**[ビルトイン アカウント]**</span><span class="sxs-lookup"><span data-stu-id="20911-112">**Built-in account**</span></span>  
 <span data-ttu-id="20911-113">**Local System**</span><span class="sxs-lookup"><span data-stu-id="20911-113">**Local System**</span></span>  
 <span data-ttu-id="20911-114">ローカル システム アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="20911-114">Specify the local system account.</span></span> <span data-ttu-id="20911-115">このアカウントはパスワードを必要としません。</span><span class="sxs-lookup"><span data-stu-id="20911-115">This account does not require a password.</span></span> <span data-ttu-id="20911-116">ただし、ローカル システム アカウントに与えられている特権によっては、そのサービスが他のサーバーと対話できないこともあります。</span><span class="sxs-lookup"><span data-stu-id="20911-116">However, the local system account may prevent the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="20911-117">**Local Service**</span><span class="sxs-lookup"><span data-stu-id="20911-117">**Local Service**</span></span>  
 <span data-ttu-id="20911-118">ローカル サービス アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="20911-118">Specify the local service account.</span></span> <span data-ttu-id="20911-119">このアカウントはパスワードを必要としません。</span><span class="sxs-lookup"><span data-stu-id="20911-119">This account does not require a password.</span></span> <span data-ttu-id="20911-120">ただし、ローカル サービス アカウントに与えられている特権によっては、そのサービスが他のサーバーと対話できないこともあります。</span><span class="sxs-lookup"><span data-stu-id="20911-120">However, the local service account may prevent the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="20911-121">**Network Service**</span><span class="sxs-lookup"><span data-stu-id="20911-121">**Network Service**</span></span>  
 <span data-ttu-id="20911-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスには、ネットワーク サービス アカウントを使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="20911-122">We recommend that you do not use the Network Service account for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent services.</span></span> <span data-ttu-id="20911-123">これらのサービスには、ローカル ユーザー アカウントまたはドメイン ユーザー アカウントの方が適しています。</span><span class="sxs-lookup"><span data-stu-id="20911-123">Local User or Domain User accounts are more appropriate for these services.</span></span>  
  
 <span data-ttu-id="20911-124">**[このアカウント]**</span><span class="sxs-lookup"><span data-stu-id="20911-124">**This account**</span></span>  
 <span data-ttu-id="20911-125">Windows 認証を使用するローカル ユーザー アカウントまたはドメイン ユーザー アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="20911-125">Specify a local or domain user account that uses Windows Authentication.</span></span> <span data-ttu-id="20911-126">サービスを実行できる必要最小限の権限が設定されたドメイン ユーザー アカウントを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="20911-126">We recommend that you use a domain user account that has minimal rights for services.</span></span>  
  
 <span data-ttu-id="20911-127">**アカウント名**</span><span class="sxs-lookup"><span data-stu-id="20911-127">**Account Name**</span></span>  
 <span data-ttu-id="20911-128">ローカル ユーザー アカウント名またはドメイン ユーザー アカウント名を指定します。</span><span class="sxs-lookup"><span data-stu-id="20911-128">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="20911-129">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="20911-129">**Password**</span></span>  
 <span data-ttu-id="20911-130">アカウントのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="20911-130">Type the password of the account.</span></span>  
  
 <span data-ttu-id="20911-131">**[パスワードの確認入力]**</span><span class="sxs-lookup"><span data-stu-id="20911-131">**Confirm password**</span></span>  
 <span data-ttu-id="20911-132">アカウントのパスワードを再度入力します。</span><span class="sxs-lookup"><span data-stu-id="20911-132">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="20911-133">**[開始]**</span><span class="sxs-lookup"><span data-stu-id="20911-133">**Start**</span></span>  
 <span data-ttu-id="20911-134">サービスを開始します。</span><span class="sxs-lookup"><span data-stu-id="20911-134">Start the service.</span></span>  
  
 <span data-ttu-id="20911-135">**Stop**</span><span class="sxs-lookup"><span data-stu-id="20911-135">**Stop**</span></span>  
 <span data-ttu-id="20911-136">サービスを停止します。</span><span class="sxs-lookup"><span data-stu-id="20911-136">Stop the service.</span></span>  
  
 <span data-ttu-id="20911-137">**[一時停止]**</span><span class="sxs-lookup"><span data-stu-id="20911-137">**Pause**</span></span>  
 <span data-ttu-id="20911-138">サービスを一時停止します。</span><span class="sxs-lookup"><span data-stu-id="20911-138">Pause the service.</span></span> <span data-ttu-id="20911-139">このサービスでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="20911-139">Not available for this service.</span></span>  
  
 <span data-ttu-id="20911-140">**[再開]**</span><span class="sxs-lookup"><span data-stu-id="20911-140">**Resume**</span></span>  
 <span data-ttu-id="20911-141">一時停止したサービスを再開します。</span><span class="sxs-lookup"><span data-stu-id="20911-141">Resume a paused service.</span></span>  
  
  
