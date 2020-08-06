---
title: '[SQL Server のプロパティ] ダイアログ ボックス ([ログオン] タブ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 405073fc-eaa3-43c6-bf82-2cd58cacc1c3
author: stevestein
ms.author: sstein
ms.openlocfilehash: adec9ed7c69023218baa96ab8f8edbb6f2b365bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641372"
---
# <a name="sql-server-properties-log-on-tab"></a><span data-ttu-id="bcc1d-102">[SQL Server のプロパティ] ダイアログ ボックス ([ログオン] タブ)</span><span class="sxs-lookup"><span data-stu-id="bcc1d-102">SQL Server Properties (Log On Tab)</span></span>
  <span data-ttu-id="bcc1d-103">**[SQL Server のプロパティ]** ダイアログ ボックスの **[ログオン]** タブでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが使用するアカウントの指定、アカウントのパスワードの変更、およびそのサービスの開始、停止を行います。</span><span class="sxs-lookup"><span data-stu-id="bcc1d-103">Use the **Log On** tab of the **SQL Server Properties** dialog box to specify the account used by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service, to change the password of an account, and to start and stop the service.</span></span> <span data-ttu-id="bcc1d-104">アカウントのパスワードを変更すると、その変更はすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="bcc1d-104">Changing the password of an account takes effect immediately.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bcc1d-105">クラスター化されたインスタンス上のサービスで使用するアカウント名を変更する場合、新しいアカウントは、そのサービスのセットアップ時に指定したドメイン グループに属している必要があります。または、そのグループにメンバーを追加する権限が与えられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcc1d-105">When changing the account name used by a service on a clustered instance, the new account must be a member of the domain group specified during setup for the service being changed, or you must have permission to add members to that group.</span></span> <span data-ttu-id="bcc1d-106">グループのメンバーシップを変更する権限がない場合は、ドメイン管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="bcc1d-106">If you do not have permission to modify group membership, contact the domain administrator.</span></span>  
>   
>  <span data-ttu-id="bcc1d-107">サービスを実行するアカウントの選択の詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「Windows サービス アカウントの設定」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bcc1d-107">For more information about selecting an account to run the service, see "Setting Up Windows Service Accounts" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="options"></a><span data-ttu-id="bcc1d-108">オプション</span><span class="sxs-lookup"><span data-stu-id="bcc1d-108">Options</span></span>  
 <span data-ttu-id="bcc1d-109">**[ビルトイン アカウント]**</span><span class="sxs-lookup"><span data-stu-id="bcc1d-109">**Built-in account**</span></span>  
 <span data-ttu-id="bcc1d-110">**Local System**</span><span class="sxs-lookup"><span data-stu-id="bcc1d-110">**Local System**</span></span>  
 -   <span data-ttu-id="bcc1d-111">ローカル システム アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="bcc1d-111">Specify the local system account.</span></span> <span data-ttu-id="bcc1d-112">このアカウントはパスワードを必要としません。</span><span class="sxs-lookup"><span data-stu-id="bcc1d-112">This account does not require a password.</span></span> <span data-ttu-id="bcc1d-113">ただし、ローカル システム アカウントに与えられている特権によっては、そのサービスが他のサーバーと対話できないこともあります。</span><span class="sxs-lookup"><span data-stu-id="bcc1d-113">However, the local system account may prevent the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="bcc1d-114">**Local Service**</span><span class="sxs-lookup"><span data-stu-id="bcc1d-114">**Local Service**</span></span>  
 -   <span data-ttu-id="bcc1d-115">ローカル サービス アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="bcc1d-115">Specify the local service account.</span></span> <span data-ttu-id="bcc1d-116">このアカウントはパスワードを必要としません。</span><span class="sxs-lookup"><span data-stu-id="bcc1d-116">This account does not require a password.</span></span> <span data-ttu-id="bcc1d-117">ただし、ローカル サービス アカウントに与えられている特権によっては、そのサービスが他のサーバーと対話できないこともあります。</span><span class="sxs-lookup"><span data-stu-id="bcc1d-117">However, the local service account may prevent the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="bcc1d-118">**Network Service**</span><span class="sxs-lookup"><span data-stu-id="bcc1d-118">**Network Service**</span></span>  
 -   <span data-ttu-id="bcc1d-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスには、ネットワーク サービス アカウントを使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bcc1d-119">We recommend that you do not use the Network Service account for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent services.</span></span> <span data-ttu-id="bcc1d-120">これらのサービスには、ローカル ユーザー アカウントまたはドメイン ユーザー アカウントの方が適しています。</span><span class="sxs-lookup"><span data-stu-id="bcc1d-120">Local User or Domain User accounts are more appropriate for these services.</span></span>  
  
 <span data-ttu-id="bcc1d-121">**[このアカウント]**</span><span class="sxs-lookup"><span data-stu-id="bcc1d-121">**This account**</span></span>  
 <span data-ttu-id="bcc1d-122">Windows 認証を使用するローカル ユーザー アカウントまたはドメイン ユーザー アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="bcc1d-122">Specify a local or domain user account that uses Windows Authentication.</span></span> <span data-ttu-id="bcc1d-123">サービスを実行できる必要最小限の権限が設定されたドメイン ユーザー アカウントを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bcc1d-123">We recommend that you use a domain user account that has minimal rights for services.</span></span>  
  
 <span data-ttu-id="bcc1d-124">**アカウント名**</span><span class="sxs-lookup"><span data-stu-id="bcc1d-124">**Account Name**</span></span>  
 <span data-ttu-id="bcc1d-125">ローカル ユーザー アカウント名またはドメイン ユーザー アカウント名を指定します。</span><span class="sxs-lookup"><span data-stu-id="bcc1d-125">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="bcc1d-126">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="bcc1d-126">**Password**</span></span>  
 <span data-ttu-id="bcc1d-127">アカウントのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="bcc1d-127">Type the password of the account.</span></span>  
  
 <span data-ttu-id="bcc1d-128">**[パスワードの確認入力]**</span><span class="sxs-lookup"><span data-stu-id="bcc1d-128">**Confirm password**</span></span>  
 <span data-ttu-id="bcc1d-129">アカウントのパスワードを再度入力します。</span><span class="sxs-lookup"><span data-stu-id="bcc1d-129">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="bcc1d-130">**[開始]**</span><span class="sxs-lookup"><span data-stu-id="bcc1d-130">**Start**</span></span>  
 <span data-ttu-id="bcc1d-131">サービスを開始します。</span><span class="sxs-lookup"><span data-stu-id="bcc1d-131">Start the service.</span></span>  
  
 <span data-ttu-id="bcc1d-132">**Stop**</span><span class="sxs-lookup"><span data-stu-id="bcc1d-132">**Stop**</span></span>  
 <span data-ttu-id="bcc1d-133">サービスを停止します。</span><span class="sxs-lookup"><span data-stu-id="bcc1d-133">Stop the service.</span></span>  
  
 <span data-ttu-id="bcc1d-134">**[一時停止]**</span><span class="sxs-lookup"><span data-stu-id="bcc1d-134">**Pause**</span></span>  
 <span data-ttu-id="bcc1d-135">サービスを一時停止します。</span><span class="sxs-lookup"><span data-stu-id="bcc1d-135">Pause the service.</span></span>  
  
 <span data-ttu-id="bcc1d-136">**[再開]**</span><span class="sxs-lookup"><span data-stu-id="bcc1d-136">**Resume**</span></span>  
 <span data-ttu-id="bcc1d-137">一時停止したサービスを再開します。</span><span class="sxs-lookup"><span data-stu-id="bcc1d-137">Resume a paused service.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bcc1d-138">サービスを開始、停止、一時停止、再開、または再起動できるのは、既定ではローカル管理者グループのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="bcc1d-138">By default, only members of the local administrators group can start, stop, pause, resume or restart a service.</span></span> <span data-ttu-id="bcc1d-139">管理者以外のユーザーがサービスを管理できるようにする方法については、「 [[HOWTO] Windows Server 2003 でサービスを管理する権利をユーザーに付与する](https://support.microsoft.com/kb/325349)」をご覧ください</span><span class="sxs-lookup"><span data-stu-id="bcc1d-139">To grant non-administrators the ability to manage services, see [How to grant users rights to manage services in Windows Server 2003](https://support.microsoft.com/kb/325349).</span></span> <span data-ttu-id="bcc1d-140">(Windows の他のバージョンでも処理は同じです)。</span><span class="sxs-lookup"><span data-stu-id="bcc1d-140">(The process is similar on other versions of Windows.)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bcc1d-141">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の起動時に、"実装されていません (not implemented) [0x80004001]" という語句を含む WMI エラーが発生する場合は、ターゲット コンピューターに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がインストールされていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bcc1d-141">When starting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a WMI error containing the phrase "not implemented [0x80004001]" may indicate that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not installed on the target computer.</span></span>  
  
  
