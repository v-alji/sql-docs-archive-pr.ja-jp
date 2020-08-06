---
title: SQL Server Agent のプロパティ ([ログオン] タブ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 01fc6329-5d6b-4186-9565-395f375477bb
author: stevestein
ms.author: sstein
ms.openlocfilehash: cd899e8824adacd07fa1d8d7d51b2143d10cadd4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640297"
---
# <a name="sql-server-agent-properties-log-on-tab"></a><span data-ttu-id="67da2-102">[SQL Server Agent のプロパティ] ダイアログ ボックス ([ログオン] タブ)</span><span class="sxs-lookup"><span data-stu-id="67da2-102">SQL Server Agent Properties (Log On Tab)</span></span>
  <span data-ttu-id="67da2-103">**[SQL Server Agent のプロパティ]** ダイアログ ボックスの **[ログオン]** タブでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスで使用するアカウントを指定します。また、このサービスの開始と停止も行えます。</span><span class="sxs-lookup"><span data-stu-id="67da2-103">Use the **Log On** tab of the **SQL Server Agent Properties** dialog box to specify the account used by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service, and to start and stop the service.</span></span> <span data-ttu-id="67da2-104">アカウントのパスワードを変更した場合、サービスを再起動しなくても、すぐにその変更が有効になります。</span><span class="sxs-lookup"><span data-stu-id="67da2-104">Changing the password of an account takes effect immediately without restarting the service.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="67da2-105">クラスター化されたインスタンス上のサービスで使用するアカウント名を変更する場合、新しいアカウントは、そのサービスのセットアップ時に指定したドメイン グループに属している必要があります。または、そのグループにメンバーを追加する権限が与えられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="67da2-105">When changing the account name used by a service on a clustered instance, the new account must be a member of the domain group specified during setup for the service being changed, or you must have permission to add members to that group.</span></span> <span data-ttu-id="67da2-106">グループのメンバーシップを変更する権限がない場合は、ドメイン管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="67da2-106">If you do not have permission to modify group membership, contact the domain administrator.</span></span>  
  
## <a name="options"></a><span data-ttu-id="67da2-107">オプション</span><span class="sxs-lookup"><span data-stu-id="67da2-107">Options</span></span>  
 <span data-ttu-id="67da2-108">**[ローカル システム アカウント]**</span><span class="sxs-lookup"><span data-stu-id="67da2-108">**Local System account**</span></span>  
 <span data-ttu-id="67da2-109">ローカル システム アカウントを指定します。このアカウントはパスワードを必要としません。</span><span class="sxs-lookup"><span data-stu-id="67da2-109">Specify a local system account, which does not require a password.</span></span> <span data-ttu-id="67da2-110">ただし、ローカル システム アカウントに与えられている特権によっては、そのサービスと他のサーバーとの対話が制限されることもあります。</span><span class="sxs-lookup"><span data-stu-id="67da2-110">However, the local system account may restrict the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="67da2-111">**[このアカウント]**</span><span class="sxs-lookup"><span data-stu-id="67da2-111">**This account**</span></span>  
 <span data-ttu-id="67da2-112">Windows 認証を使用するローカル ユーザー アカウントまたはドメイン ユーザー アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="67da2-112">Specify a local or domain user account that uses Windows Authentication.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="67da2-113">では、サービスを実行できる必要最小限の権限が設定されたドメイン ユーザー アカウントを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="67da2-113">recommends using a domain user account with minimal rights for services.</span></span> <span data-ttu-id="67da2-114">アカウントの選択の詳細については、オンライン ブックの「Windows サービス アカウントの設定」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67da2-114">For information about selecting an account, search Books Online for "Setting Up Windows Service Accounts."</span></span>  
  
 <span data-ttu-id="67da2-115">**アカウント名**</span><span class="sxs-lookup"><span data-stu-id="67da2-115">**Account Name**</span></span>  
 <span data-ttu-id="67da2-116">ローカル ユーザー アカウント名またはドメイン ユーザー アカウント名を指定します。</span><span class="sxs-lookup"><span data-stu-id="67da2-116">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="67da2-117">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="67da2-117">**Password**</span></span>  
 <span data-ttu-id="67da2-118">アカウントのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="67da2-118">Type the password of the account.</span></span>  
  
 <span data-ttu-id="67da2-119">**[パスワードの確認入力]**</span><span class="sxs-lookup"><span data-stu-id="67da2-119">**Confirm password**</span></span>  
 <span data-ttu-id="67da2-120">アカウントのパスワードを再度入力します。</span><span class="sxs-lookup"><span data-stu-id="67da2-120">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="67da2-121">**[開始]**</span><span class="sxs-lookup"><span data-stu-id="67da2-121">**Start**</span></span>  
 <span data-ttu-id="67da2-122">サービスを開始します。</span><span class="sxs-lookup"><span data-stu-id="67da2-122">Start the service.</span></span>  
  
 <span data-ttu-id="67da2-123">**Stop**</span><span class="sxs-lookup"><span data-stu-id="67da2-123">**Stop**</span></span>  
 <span data-ttu-id="67da2-124">サービスを停止します。</span><span class="sxs-lookup"><span data-stu-id="67da2-124">Stop the service.</span></span>  
  
 <span data-ttu-id="67da2-125">**[一時停止]**</span><span class="sxs-lookup"><span data-stu-id="67da2-125">**Pause**</span></span>  
 <span data-ttu-id="67da2-126">サービスを一時停止します。</span><span class="sxs-lookup"><span data-stu-id="67da2-126">Pause the service.</span></span>  
  
 <span data-ttu-id="67da2-127">**[再開]**</span><span class="sxs-lookup"><span data-stu-id="67da2-127">**Resume**</span></span>  
 <span data-ttu-id="67da2-128">一時停止したサービスを再開します。</span><span class="sxs-lookup"><span data-stu-id="67da2-128">Resume a paused service.</span></span>  
  
  
