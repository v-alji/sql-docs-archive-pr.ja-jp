---
title: '[不明なサービス] ([ログオン] タブ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: e9b35cb5-d8ae-42ea-b59e-deedc99c4823
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0bda49cd95475d4f922f41ebe1701a814c3f60fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632875"
---
# <a name="unknown-service-log-on-tab"></a><span data-ttu-id="50028-102">[不明なサービス] ダイアログ ボックス ([ログオン] タブ)</span><span class="sxs-lookup"><span data-stu-id="50028-102">Unknown Service (Log On Tab)</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="50028-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーで、このサービスを識別できません。</span><span class="sxs-lookup"><span data-stu-id="50028-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager is unable to identify this service.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="50028-104">構成マネージャーは、サービスを実行しているコンピューターの WMI プロバイダーからそのサービスの情報を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="50028-104">Configuration Manager receives service information from the WMI provider on the computer running the service.</span></span> <span data-ttu-id="50028-105">そのサービスのプロパティの読み取り中にエラーが発生したか、そのサービスのプロパティに不備がありました。</span><span class="sxs-lookup"><span data-stu-id="50028-105">Either there was an error while reading the service properties, or the service properties are not complete.</span></span> <span data-ttu-id="50028-106">この問題を解決するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーをいったん閉じてから再び開くか、そのサービスを実行しているコンピューターの WMI プロバイダーをチェックします。</span><span class="sxs-lookup"><span data-stu-id="50028-106">To resolve the problem, try closing and reopening [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or check the WMI provider on the computer running the service.</span></span>  
  
 <span data-ttu-id="50028-107">WMI プロバイダーは、Windows のコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="50028-107">The WMI provider is a Windows component.</span></span> <span data-ttu-id="50028-108">WMI プロバイダーの権限をチェックする方法については、SQL Server オンライン ブックの「SQL Server ツールでサーバーの状態を表示できるように WMI を構成する方法」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50028-108">For information on how to check permissions on the WMI provider, see "How to: Configure WMI to Show Server Status in SQL Server Tools" in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="50028-109">適切なサービスを表示していると確信できる場合は、 **[不明なサービス]** ダイアログ ボックスの **[ログオン]** タブで、そのサービスが使用するアカウントの指定や、そのサービスの開始と停止を行います。</span><span class="sxs-lookup"><span data-stu-id="50028-109">If you believe you are viewing the correct service, use the **Log On** tab of the **Unknown Service Properties** dialog box to specify the account used by this service, and to start and stop the service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="50028-110">オプション</span><span class="sxs-lookup"><span data-stu-id="50028-110">Options</span></span>  
 <span data-ttu-id="50028-111">**[ローカル システム アカウント]**</span><span class="sxs-lookup"><span data-stu-id="50028-111">**Local System account**</span></span>  
 <span data-ttu-id="50028-112">ローカル システム アカウントを指定します。このアカウントはパスワードを必要としません。</span><span class="sxs-lookup"><span data-stu-id="50028-112">Specify a local system account, which does not require a password.</span></span> <span data-ttu-id="50028-113">ただし、ローカル システム アカウントに与えられている特権によっては、そのサービスが他のサーバーと対話できないこともあります。</span><span class="sxs-lookup"><span data-stu-id="50028-113">However, the local system account may prevent the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="50028-114">**[このアカウント]**</span><span class="sxs-lookup"><span data-stu-id="50028-114">**This account**</span></span>  
 <span data-ttu-id="50028-115">Windows 認証を使用するローカル ユーザー アカウントまたはドメイン ユーザー アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="50028-115">Specify a local or domain user account that uses Windows Authentication.</span></span> <span data-ttu-id="50028-116">サービスを実行できる必要最小限の権限が設定されたドメイン ユーザー アカウントを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="50028-116">We recommend using a domain user account with minimal rights for services.</span></span> <span data-ttu-id="50028-117">アカウントの選択の詳細については、オンライン ブックの「Windows サービス アカウントの設定」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50028-117">For information about selecting an account, "Setting Up Windows Service Accounts" in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="50028-118">**アカウント名**</span><span class="sxs-lookup"><span data-stu-id="50028-118">**Account Name**</span></span>  
 <span data-ttu-id="50028-119">ローカル ユーザー アカウント名またはドメイン ユーザー アカウント名を指定します。</span><span class="sxs-lookup"><span data-stu-id="50028-119">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="50028-120">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="50028-120">**Password**</span></span>  
 <span data-ttu-id="50028-121">アカウントのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="50028-121">Type the password of the account.</span></span>  
  
 <span data-ttu-id="50028-122">**[パスワードの確認入力]**</span><span class="sxs-lookup"><span data-stu-id="50028-122">**Confirm password**</span></span>  
 <span data-ttu-id="50028-123">アカウントのパスワードを再度入力します。</span><span class="sxs-lookup"><span data-stu-id="50028-123">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="50028-124">**[開始]**</span><span class="sxs-lookup"><span data-stu-id="50028-124">**Start**</span></span>  
 <span data-ttu-id="50028-125">サービスを開始します。</span><span class="sxs-lookup"><span data-stu-id="50028-125">Start the service.</span></span>  
  
 <span data-ttu-id="50028-126">**Stop**</span><span class="sxs-lookup"><span data-stu-id="50028-126">**Stop**</span></span>  
 <span data-ttu-id="50028-127">サービスを停止します。</span><span class="sxs-lookup"><span data-stu-id="50028-127">Stop the service.</span></span>  
  
 <span data-ttu-id="50028-128">**[一時停止]**</span><span class="sxs-lookup"><span data-stu-id="50028-128">**Pause**</span></span>  
 <span data-ttu-id="50028-129">サービスを一時停止します。</span><span class="sxs-lookup"><span data-stu-id="50028-129">Pause the service.</span></span>  
  
 <span data-ttu-id="50028-130">**[再開]**</span><span class="sxs-lookup"><span data-stu-id="50028-130">**Resume**</span></span>  
 <span data-ttu-id="50028-131">一時停止したサービスを再開します。</span><span class="sxs-lookup"><span data-stu-id="50028-131">Resume a paused service.</span></span>  
  
  
