---
title: '[スナップショット エージェントのセキュリティ] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.SSA.f1
helpviewer_keywords:
- Snapshot Agent Security dialog box
ms.assetid: 64e84c67-acc6-4906-98d4-3451767363fe
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 288dc294b7ace9ea5cb098c8deec53c3ae4569a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645505"
---
# <a name="snapshot-agent-security"></a><span data-ttu-id="fefa7-102">[スナップショット エージェントのセキュリティ]</span><span class="sxs-lookup"><span data-stu-id="fefa7-102">Snapshot Agent Security</span></span>
  <span data-ttu-id="fefa7-103">**[スナップショット エージェントのセキュリティ]** ダイアログ ボックスを使用すると、次の項目を指定できます。</span><span class="sxs-lookup"><span data-stu-id="fefa7-103">The **Snapshot Agent Security** dialog box allows you to specify:</span></span>  
  
-   <span data-ttu-id="fefa7-104">ディストリビューターでスナップショット エージェントを実行するときに使用される [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウント。</span><span class="sxs-lookup"><span data-stu-id="fefa7-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the Snapshot Agent runs at the Distributor.</span></span> <span data-ttu-id="fefa7-105">エージェント プロセスがこのアカウントで実行されるため、Windows アカウントは *プロセス アカウント*とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="fefa7-105">The Windows account is also referred to as the *process account*, because the agent process runs under this account.</span></span>  
  
-   <span data-ttu-id="fefa7-106">スナップショット エージェントから [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャーへの接続に使用されるコンテキスト。</span><span class="sxs-lookup"><span data-stu-id="fefa7-106">The context under which the Snapshot Agent makes connections to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher.</span></span> <span data-ttu-id="fefa7-107">接続は、Windows アカウントを借用して作成されるか、指定した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントのコンテキストで作成されます。</span><span class="sxs-lookup"><span data-stu-id="fefa7-107">The connection can be made by impersonating the Windows account or under the context of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account you specify.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fefa7-108">パブリッシャーとディストリビューターが同じコンピューターに置かれている場合でも、スナップショット エージェントからパブリッシャーへの接続が作成されます。</span><span class="sxs-lookup"><span data-stu-id="fefa7-108">The Snapshot Agent makes connections to the Publisher even if the Publisher and Distributor are on the same computer.</span></span> <span data-ttu-id="fefa7-109">スナップショット エージェントからディストリビューターへの接続も作成されます。これらの接続は常に、エージェントの実行に使用される Windows アカウントを借用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="fefa7-109">The Snapshot Agent also makes connections to the Distributor; these connections are always made by impersonating the Windows account under which the agent runs.</span></span>  
  
     <span data-ttu-id="fefa7-110">Oracle パブリッシャーの場合、スナップショット エージェントからパブリッシャーへの接続に使用されるコンテキストを **[パブリッシャーのプロパティ]** ダイアログ ボックス ( **[ディストリビューターのプロパティ]** ダイアログ ボックスから開きます) で指定します。</span><span class="sxs-lookup"><span data-stu-id="fefa7-110">For Oracle Publishers, specify the context under which the Snapshot Agent connects to the Publisher in the **Publisher Properties** dialog box (available from the **Distributor Properties** dialog box).</span></span> <span data-ttu-id="fefa7-111">詳細については、「 [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fefa7-111">For more information, see [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="fefa7-112">各アカウントに正しいパスワードが指定され、すべてのアカウントが有効である必要があります。</span><span class="sxs-lookup"><span data-stu-id="fefa7-112">All accounts must be valid, with the correct password specified for each account.</span></span> <span data-ttu-id="fefa7-113">アカウントとパスワードは、エージェントが実行されるまで検証されません。</span><span class="sxs-lookup"><span data-stu-id="fefa7-113">Accounts and passwords are not validated until an agent runs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fefa7-114">オプション</span><span class="sxs-lookup"><span data-stu-id="fefa7-114">Options</span></span>  
 <span data-ttu-id="fefa7-115">**[プロセス アカウント]**</span><span class="sxs-lookup"><span data-stu-id="fefa7-115">**Process account**</span></span>  
 <span data-ttu-id="fefa7-116">ディストリビューターでスナップショット エージェントを実行するときに使用される  Windows アカウントを入力します。</span><span class="sxs-lookup"><span data-stu-id="fefa7-116">Enter a Windows account under which the Snapshot Agent runs at the Distributor.</span></span> <span data-ttu-id="fefa7-117">指定する Windows アカウントは、次の条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="fefa7-117">The Windows account you specify must:</span></span>  
  
-   <span data-ttu-id="fefa7-118">最低でも、ディストリビューション データベースで **db_owner** 固定データベース ロールのメンバーである。</span><span class="sxs-lookup"><span data-stu-id="fefa7-118">At minimum be a member of the **db_owner** fixed database role in the distribution database.</span></span>  
  
-   <span data-ttu-id="fefa7-119">スナップショット共有に対する書き込み権限がある。</span><span class="sxs-lookup"><span data-stu-id="fefa7-119">Have write permissions on the snapshot share.</span></span>  
  
 <span data-ttu-id="fefa7-120">**[パスワード]** と **[パスワードの確認入力]**</span><span class="sxs-lookup"><span data-stu-id="fefa7-120">**Password** and **Confirm password**</span></span>  
 <span data-ttu-id="fefa7-121">Windows アカウントのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="fefa7-121">Enter the password for the Windows account.</span></span>  
  
 <span data-ttu-id="fefa7-122">**[パブリッシャーに接続]**</span><span class="sxs-lookup"><span data-stu-id="fefa7-122">**Connect to the Publisher**</span></span>  
 <span data-ttu-id="fefa7-123">**[プロセス アカウント]** テキスト ボックスで指定されたアカウントを借用するか、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントを使用して、スナップショット エージェントからパブリッシャーへの接続を作成するかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="fefa7-123">Select whether the Snapshot Agent should make connections to the Publisher by impersonating the account specified in the **Process account** text box or by using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span> <span data-ttu-id="fefa7-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントの使用を選択した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインとパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="fefa7-124">If you select to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account, enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and password.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fefa7-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントの使用ではなく、Windows アカウントの借用を選択することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fefa7-125">It is recommended that you select to impersonate the Windows account rather than using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
 <span data-ttu-id="fefa7-126">接続に使用される Windows アカウントまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントは、少なくとも、パブリケーション データベースの **db_owner** 固定データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="fefa7-126">The Windows account or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account used for the connection must at minimum be a member of the **db_owner** fixed database role in the publication database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fefa7-127">参照</span><span class="sxs-lookup"><span data-stu-id="fefa7-127">See Also</span></span>  
 <span data-ttu-id="fefa7-128">[レプリケーションのログインとパスワードの管理](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="fefa7-128">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="fefa7-129">[レプリケーション エージェントのセキュリティ モデル](security/replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="fefa7-129">[Replication Agent Security Model](security/replication-agent-security-model.md) </span></span>  
 <span data-ttu-id="fefa7-130">[レプリケーション エージェントの概要](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="fefa7-130">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 [<span data-ttu-id="fefa7-131">レプリケーション セキュリティの推奨事項</span><span class="sxs-lookup"><span data-stu-id="fefa7-131">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
