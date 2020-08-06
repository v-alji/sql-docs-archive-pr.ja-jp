---
title: 分析サーバーのプロパティ ([ログオン] タブ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: a82e0c98-efaa-4b0b-9582-3c879ee42444
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8db5576e48e7f12ef1733175875d2cd065e376fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741514"
---
# <a name="analysis-server-properties-log-on-tab"></a><span data-ttu-id="c5fcb-102">[SQL Server Analysis Services のプロパティ] ダイアログ ボックス ([ログオン] タブ)</span><span class="sxs-lookup"><span data-stu-id="c5fcb-102">Analysis Server Properties (Log On Tab)</span></span>
  <span data-ttu-id="c5fcb-103">**[SQL Server Analysis Services のプロパティ]** ダイアログ ボックスの **[ログオン]** タブでは、 [!INCLUDE[ssAS](../../includes/ssas-md.md)] サービスが使用するアカウントの指定や、そのサービスの開始、停止を行います。</span><span class="sxs-lookup"><span data-stu-id="c5fcb-103">Use the **Log On** tab of the **Analysis Server Properties** dialog box to specify the account used by the [!INCLUDE[ssAS](../../includes/ssas-md.md)] service, and to start and stop the service.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c5fcb-104">クラスター化されたインスタンス上のサービスで使用する **[アカウント名]** を変更する場合、変更後の新しいアカウントは、そのサービスのセットアップ時に指定したドメイン グループに属している必要があります。または、そのグループにメンバーを追加する権限が与えられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5fcb-104">When changing the **Account Name** used by a service on a clustered instance, the new account must either be a member of the domain group specified during setup for the service being changed, or you must have permission to add members to that group.</span></span> <span data-ttu-id="c5fcb-105">グループのメンバーシップを変更する権限がない場合は、ドメイン管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="c5fcb-105">If you do not have permission to modify group membership, contact the domain administrator.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c5fcb-106">オプション</span><span class="sxs-lookup"><span data-stu-id="c5fcb-106">Options</span></span>  
 <span data-ttu-id="c5fcb-107">**[ローカル システム アカウント]**</span><span class="sxs-lookup"><span data-stu-id="c5fcb-107">**Local System account**</span></span>  
 <span data-ttu-id="c5fcb-108">ローカル システム アカウントを指定します。このアカウントはパスワードを必要としません。</span><span class="sxs-lookup"><span data-stu-id="c5fcb-108">Specify a local system account, which does not require a password.</span></span> <span data-ttu-id="c5fcb-109">ただし、ローカル システム アカウントに与えられている特権によっては、そのサービスと他のサーバーとの対話が制限されることもあります。</span><span class="sxs-lookup"><span data-stu-id="c5fcb-109">However, the local system account may restrict the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="c5fcb-110">**[このアカウント]**</span><span class="sxs-lookup"><span data-stu-id="c5fcb-110">**This account**</span></span>  
 <span data-ttu-id="c5fcb-111">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証を使用するローカル ユーザー アカウントまたはドメイン ユーザー アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="c5fcb-111">Specify a local or domain user account that uses [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="c5fcb-112">では、サービスを実行できる必要最小限の権限が設定されたドメイン ユーザー アカウントを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c5fcb-112">recommends using a domain user account with minimal rights for services.</span></span> <span data-ttu-id="c5fcb-113">アカウントの選択の詳細については、オンライン ブックの「Windows サービス アカウントの設定」を検索してください。</span><span class="sxs-lookup"><span data-stu-id="c5fcb-113">For information about selecting an account, search Books Online for the topic Setting Up Windows Service Accounts.</span></span>  
  
 <span data-ttu-id="c5fcb-114">**アカウント名**</span><span class="sxs-lookup"><span data-stu-id="c5fcb-114">**Account Name**</span></span>  
 <span data-ttu-id="c5fcb-115">ローカル ユーザー アカウント名またはドメイン ユーザー アカウント名を指定します。</span><span class="sxs-lookup"><span data-stu-id="c5fcb-115">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="c5fcb-116">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="c5fcb-116">**Password**</span></span>  
 <span data-ttu-id="c5fcb-117">アカウントのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="c5fcb-117">Type the password of the account.</span></span>  
  
 <span data-ttu-id="c5fcb-118">**[パスワードの確認入力]**</span><span class="sxs-lookup"><span data-stu-id="c5fcb-118">**Confirm password**</span></span>  
 <span data-ttu-id="c5fcb-119">アカウントのパスワードを再度入力します。</span><span class="sxs-lookup"><span data-stu-id="c5fcb-119">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="c5fcb-120">**[開始]**</span><span class="sxs-lookup"><span data-stu-id="c5fcb-120">**Start**</span></span>  
 <span data-ttu-id="c5fcb-121">サービスを開始します。</span><span class="sxs-lookup"><span data-stu-id="c5fcb-121">Start the service.</span></span>  
  
 <span data-ttu-id="c5fcb-122">**Stop**</span><span class="sxs-lookup"><span data-stu-id="c5fcb-122">**Stop**</span></span>  
 <span data-ttu-id="c5fcb-123">サービスを停止します。</span><span class="sxs-lookup"><span data-stu-id="c5fcb-123">Stop the service.</span></span>  
  
 <span data-ttu-id="c5fcb-124">**[一時停止]**</span><span class="sxs-lookup"><span data-stu-id="c5fcb-124">**Pause**</span></span>  
 <span data-ttu-id="c5fcb-125">サービスを一時停止します。</span><span class="sxs-lookup"><span data-stu-id="c5fcb-125">Pause the service.</span></span>  
  
 <span data-ttu-id="c5fcb-126">**[再開]**</span><span class="sxs-lookup"><span data-stu-id="c5fcb-126">**Resume**</span></span>  
 <span data-ttu-id="c5fcb-127">一時停止したサービスを再開します。</span><span class="sxs-lookup"><span data-stu-id="c5fcb-127">Resume a paused service.</span></span>  
  
  
