---
title: '[ログ リーダー エージェントのセキュリティ] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.LRA.f1
helpviewer_keywords:
- Log Reader Agent Security dialog box
ms.assetid: d6981e74-ddb8-41b8-9ea1-56c2ece63b8a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4be41aa9135e20a334616b9cb9d76a773f8d0e9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739691"
---
# <a name="log-reader-agent-security"></a><span data-ttu-id="e99d3-102">[ログ リーダー エージェントのセキュリティ]</span><span class="sxs-lookup"><span data-stu-id="e99d3-102">Log Reader Agent Security</span></span>
  <span data-ttu-id="e99d3-103">**[ログ リーダー エージェントのセキュリティ]** ダイアログ ボックスを使用すると、次の指定ができます。</span><span class="sxs-lookup"><span data-stu-id="e99d3-103">The **Log Reader Agent Security** dialog box allows you to specify:</span></span>  
  
-   <span data-ttu-id="e99d3-104">ログ リーダー エージェントをディストリビューターで実行する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウント。</span><span class="sxs-lookup"><span data-stu-id="e99d3-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the Log Reader Agent runs at the Distributor.</span></span> <span data-ttu-id="e99d3-105">エージェント プロセスがこのアカウントで実行されるため、Windows アカウントは *プロセス アカウント*とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="e99d3-105">The Windows account is also referred to as the *process account*, because the agent process runs under this account.</span></span>  
  
-   <span data-ttu-id="e99d3-106">ログ リーダー エージェントが [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャーへの接続を作成するコンテキスト。</span><span class="sxs-lookup"><span data-stu-id="e99d3-106">The context under which the Log Reader Agent makes connections to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher.</span></span> <span data-ttu-id="e99d3-107">接続は、Windows アカウントを借用して作成されるか、指定した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントのコンテキストで作成されます。</span><span class="sxs-lookup"><span data-stu-id="e99d3-107">The connection can be made by impersonating the Windows account or under the context of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account you specify.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e99d3-108">パブリッシャーおよびディストリビューターが同じコンピューター上にある場合でも、ログ リーダー エージェントはパブリッシャーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="e99d3-108">The Log Reader Agent makes connections to the Publisher even if the Publisher and Distributor are on the same computer.</span></span> <span data-ttu-id="e99d3-109">ログ リーダー エージェントはディストリビューターへの接続も作成します。これらの接続は必ず、エージェントが実行される Windows アカウントを借用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="e99d3-109">The Log Reader Agent also makes connections to the Distributor; these connections are always made by impersonating the Windows account under which the agent runs.</span></span>  
  
     <span data-ttu-id="e99d3-110">Oracle パブリッシャーの場合、ログ リーダー エージェントがパブリッシャーに接続するコンテキストを **[パブリッシャーのプロパティ]** ダイアログ ボックス ( **[ディストリビューターのプロパティ]** ダイアログ ボックスから使用可能) で指定します。</span><span class="sxs-lookup"><span data-stu-id="e99d3-110">For Oracle Publishers, specify the context under which the Log Reader Agent connects to the Publisher in the **Publisher Properties** dialog box (available from the **Distributor Properties** dialog box).</span></span> <span data-ttu-id="e99d3-111">詳細については、「 [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e99d3-111">For more information, see [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="e99d3-112">各アカウントに正しいパスワードが指定され、すべてのアカウントが有効である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e99d3-112">All accounts must be valid, with the correct password specified for each account.</span></span> <span data-ttu-id="e99d3-113">アカウントとパスワードは、エージェントが実行されるまで検証されません。</span><span class="sxs-lookup"><span data-stu-id="e99d3-113">Accounts and passwords are not validated until an agent runs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e99d3-114">オプション</span><span class="sxs-lookup"><span data-stu-id="e99d3-114">Options</span></span>  
 <span data-ttu-id="e99d3-115">**[プロセス アカウント]**</span><span class="sxs-lookup"><span data-stu-id="e99d3-115">**Process account**</span></span>  
 <span data-ttu-id="e99d3-116">ログ リーダー エージェントをディストリビューターで実行する Windows アカウントを入力します。</span><span class="sxs-lookup"><span data-stu-id="e99d3-116">Enter a Windows account under which the Log Reader Agent runs at the Distributor.</span></span> <span data-ttu-id="e99d3-117">指定した Windows アカウントは少なくともディストリビューション データベースで **db_owner** 固定データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="e99d3-117">The Windows account you specify must at minimum be a member of the **db_owner** fixed database role in the distribution database.</span></span>  
  
 <span data-ttu-id="e99d3-118">**[パスワード]** と **[パスワードの確認入力]**</span><span class="sxs-lookup"><span data-stu-id="e99d3-118">**Password** and **Confirm password**</span></span>  
 <span data-ttu-id="e99d3-119">Windows アカウントのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="e99d3-119">Enter the password for the Windows account.</span></span>  
  
 <span data-ttu-id="e99d3-120">**[パブリッシャーに接続]**</span><span class="sxs-lookup"><span data-stu-id="e99d3-120">**Connect to the Publisher**</span></span>  
 <span data-ttu-id="e99d3-121">ログ リーダー エージェントがパブリッシャーに接続するのに **[プロセス アカウント]** テキスト ボックスで指定されたアカウントを借用する必要があるか、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントを使用する必要があるかを選択します。</span><span class="sxs-lookup"><span data-stu-id="e99d3-121">Select whether the Log Reader Agent should make connections to the Publisher by impersonating the account specified in the **Process account** text box or by using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span> <span data-ttu-id="e99d3-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントの使用を選択した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインとパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="e99d3-122">If you select to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account, enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and password.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="e99d3-123">は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のアカウントの使用ではなく、Windows アカウントの借用を選択することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e99d3-123">recommends that you select to impersonate the Windows account rather than using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
 <span data-ttu-id="e99d3-124">接続に使用される Windows アカウントまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントは、少なくとも、パブリケーション データベースの **db_owner** 固定データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="e99d3-124">The Windows account or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account used for the connection must at minimum be a member of the **db_owner** fixed database role in the publication database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e99d3-125">参照</span><span class="sxs-lookup"><span data-stu-id="e99d3-125">See Also</span></span>  
 <span data-ttu-id="e99d3-126">[レプリケーションのログインとパスワードの管理](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="e99d3-126">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="e99d3-127">[レプリケーション エージェントのセキュリティ モデル](security/replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="e99d3-127">[Replication Agent Security Model](security/replication-agent-security-model.md) </span></span>  
 <span data-ttu-id="e99d3-128">[レプリケーション エージェントの概要](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="e99d3-128">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 [<span data-ttu-id="e99d3-129">レプリケーション セキュリティの推奨事項</span><span class="sxs-lookup"><span data-stu-id="e99d3-129">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
