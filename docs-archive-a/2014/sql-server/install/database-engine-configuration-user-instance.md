---
title: データベースエンジンの構成-ユーザーインスタンス |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- database engine configuration
- database engine configuration, user instance
ms.assetid: dfc27c1e-0fe2-4221-bed5-f52667ddd3c8
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ce1b2aa85989fa847594dc7d8cc8a43c65fb0a47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631505"
---
# <a name="database-engine-configuration---user-instance"></a><span data-ttu-id="2abe3-102">データベース エンジンの構成 - ユーザー インスタンス</span><span class="sxs-lookup"><span data-stu-id="2abe3-102">Database Engine Configuration - User Instance</span></span>
  <span data-ttu-id="2abe3-103">**[ユーザー インスタンス]** ページを使用して、管理者権限のないユーザー用に、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] の個別インスタンスを作成し、それらのユーザーを管理者ロールに追加します。</span><span class="sxs-lookup"><span data-stu-id="2abe3-103">Use the **User Instance** page to generate a separate instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] for users without administrator permissions, and to add users to the administrator role.</span></span>  
  
## <a name="option"></a><span data-ttu-id="2abe3-104">オプション</span><span class="sxs-lookup"><span data-stu-id="2abe3-104">Option</span></span>  
 <span data-ttu-id="2abe3-105">[ユーザー インスタンスを有効にする]</span><span class="sxs-lookup"><span data-stu-id="2abe3-105">Enable User Instances</span></span>  
 <span data-ttu-id="2abe3-106">既定値はオンです。</span><span class="sxs-lookup"><span data-stu-id="2abe3-106">Default is on.</span></span> <span data-ttu-id="2abe3-107">ユーザー インスタンス有効化の機能を無効にするには、このチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="2abe3-107">To disable the functionality of enabling user instances, clear the check box.</span></span>  
  
 <span data-ttu-id="2abe3-108">ユーザー インスタンスは子インスタンスまたはクライアント インスタンスとも呼ばれ、ユーザーに代わって親インスタンス ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] などのサービスを実行するプライマリ インスタンス) によって作成される [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]のインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="2abe3-108">The user instance, also known as a child or client instance, is an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is generated by the parent instance (the primary instance that runs as a service, like [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) on behalf of a user.</span></span> <span data-ttu-id="2abe3-109">ユーザー インスタンスは、そのユーザーのセキュリティ コンテキストでのユーザーのプロセスとして実行します。</span><span class="sxs-lookup"><span data-stu-id="2abe3-109">The user instance runs as a user process under the security context of that user.</span></span> <span data-ttu-id="2abe3-110">親インスタンスやコンピューター上で実行するその他のユーザー インスタンスとは分離されます。</span><span class="sxs-lookup"><span data-stu-id="2abe3-110">The user instance is isolated from the parent instance and any other user instances running on the computer.</span></span> <span data-ttu-id="2abe3-111">ユーザー インスタンス機能は "通常のユーザーとして実行" (Run As Normal User: RANU) とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="2abe3-111">The user instance feature is also referred to as "Run As Normal User" (RANU).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2abe3-112">セットアップ中に **sysadmin** 固定サーバー ロールのメンバーとして準備されたログインは、テンプレート データベース内の管理者として準備されます。</span><span class="sxs-lookup"><span data-stu-id="2abe3-112">Logins provisioned as members of the **sysadmin** fixed server role during setup are provisioned as administrators in the template database.</span></span> <span data-ttu-id="2abe3-113">削除されない限り、これらはユーザー インスタンスのメンバー **sysadmin** 固定サーバー ロールです。</span><span class="sxs-lookup"><span data-stu-id="2abe3-113">They are members **sysadmin** fixed server role on the user instance unless removed</span></span>  
  
 <span data-ttu-id="2abe3-114">[ユーザーを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理者ロールに追加する]</span><span class="sxs-lookup"><span data-stu-id="2abe3-114">Add User to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Administrator role</span></span>  
 <span data-ttu-id="2abe3-115">既定値はオフです。</span><span class="sxs-lookup"><span data-stu-id="2abe3-115">Default is not on.</span></span> <span data-ttu-id="2abe3-116">現在のセットアップ ユーザーを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理者ロールに追加するには、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="2abe3-116">To add the current setup user to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Administrator role, select the check box.</span></span>  
  
 [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] <span data-ttu-id="2abe3-117">ユーザーのうち、BUILTIN\Administrators のメンバーは、[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] への接続時に sysadmin 固定サーバー ロールに自動的に追加されません。</span><span class="sxs-lookup"><span data-stu-id="2abe3-117">users that are members of BUILTIN\Administrators are not automatically added to the sysadmin fixed server role when they connect to [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span> <span data-ttu-id="2abe3-118">サーバーレベルの管理者ロールに明示的に追加されている [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] ユーザーのみが、 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]を管理できます。</span><span class="sxs-lookup"><span data-stu-id="2abe3-118">Only [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] users that have been explicitly added to a server-level administrator role can administer [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span> <span data-ttu-id="2abe3-119">Built-In\Users グループのすべてのメンバーが [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] インスタンスに接続できますが、データベース タスクの実行権限は制限されます。</span><span class="sxs-lookup"><span data-stu-id="2abe3-119">Any member of the Built-In\Users group can connect to the [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] instance, but they will have limited permissions to perform database tasks.</span></span> <span data-ttu-id="2abe3-120">このため、 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 特権を以前のリリースの Windows の BUILTIN\Administrators および Built-In\Users から継承しているユーザーには、 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] で実行している [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)]のインスタンスにおいて、管理特権を明示的に付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2abe3-120">For this reason, users whose [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] privileges are inherited from BUILTIN\Administrators and Built-In\Users in previous releases of Windows must be explicitly granted administrative privileges in instances of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] running on [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)].</span></span>  
  
 <span data-ttu-id="2abe3-121">このインストール プログラムの完了後にユーザー ロールに変更を加えるには、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] セキュリティ構成ツール (SQLSAC.exe) を使用します。</span><span class="sxs-lookup"><span data-stu-id="2abe3-121">To make any changes to the user roles after this installation program ends, use the [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Surface Area Configuration Tool (SQLSAC.exe).</span></span> <span data-ttu-id="2abe3-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム管理者ロールのユーザー一覧を更新するには、 **[新しい管理者の追加]** リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2abe3-122">To update the list of users in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] System Administrator role, click the **Add New Administrator** link.</span></span>  
  
 <span data-ttu-id="2abe3-123">**[準備するユーザー]** フィールドに、権限を更新するユーザーが DomainName\UserName 形式で表示されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="2abe3-123">Ensure that the **User to provision** field lists the DomainName\UserName of the user whose permissions should be updated.</span></span> <span data-ttu-id="2abe3-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [使用できる特権] **ペインの** インスタンスの一覧から、更新するロールを選択して、右矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2abe3-124">Select the role to be updated from the list of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances in the **Available privileges** pane, and then click the right arrow.</span></span> <span data-ttu-id="2abe3-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の使用可能なすべてのインスタンスの、使用できるすべてのロールにユーザーを追加するには、二重右矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2abe3-125">To add the user to all available roles for all available instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances and all available roles, click the double right arrow.</span></span>  
  
 <span data-ttu-id="2abe3-126">選択の完了後に変更を適用するには、 [!INCLUDE[clickOK](../../includes/clickok-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2abe3-126">To implement the changes when your selections are complete, [!INCLUDE[clickOK](../../includes/clickok-md.md)].</span></span> <span data-ttu-id="2abe3-127">変更を適用せずにツールを終了するには、 **[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2abe3-127">To end the tool without making changes, click **Cancel**.</span></span>  
  
  