---
title: '[更新可能なサブスクリプション] のログイン | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.updatablesubscriptionslogin.f1
ms.assetid: 301ea227-0455-40ba-9009-d38f8676b325
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6a5cc9190c77f506b13ba8b5fba0e32d5a925570
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739685"
---
# <a name="login-for-updatable-subscriptions"></a><span data-ttu-id="ddd1b-102">[更新可能なサブスクリプション] のログイン</span><span class="sxs-lookup"><span data-stu-id="ddd1b-102">Login for Updatable Subscriptions</span></span>
  <span data-ttu-id="ddd1b-103">このウィザードの **[更新可能なサブスクリプション]** ページで **[レプリケート]** を選択した場合は、サブスクリプションを即時更新するためにパブリッシャーに接続する際に使用する、サブスクライバーでのアカウントを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddd1b-103">If you selected **Replicate** on the **Updatable Subscriptions** page of this wizard, you must specify an account at the Subscriber under which connections to the Publisher are made for immediate updating subscriptions.</span></span> <span data-ttu-id="ddd1b-104">接続はサブスクライバーで起動されるトリガーによって使用され、サブスクライバーに変更を反映します。</span><span class="sxs-lookup"><span data-stu-id="ddd1b-104">Connections are used by the triggers that fire at the Subscriber and propagate changes to the Publisher.</span></span> <span data-ttu-id="ddd1b-105">このアカウントは、 **[更新可能なサブスクリプション]** ページで **[変更をキューに登録し、可能な場合はコミット]** を選択している場合でも必要です。サブスクリプションの新規作成ウィザードでは、必要に応じて即時更新に切り替えることができるキュー更新が、既定で構成されるためです。</span><span class="sxs-lookup"><span data-stu-id="ddd1b-105">This account is required even if you selected **Queue changes and commit when possible** on the **Updatable Subscriptions** page, because by default the New Subscription Wizard configures queued updating with the ability to switch to immediate updating if required.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ddd1b-106">接続用に指定するアカウントには、レプリケーションによってパブリケーション データベース内に作成されるビューのデータの挿入、更新、および削除だけを実行できる権限を与える必要があります。それ以外の権限は与えないでください。</span><span class="sxs-lookup"><span data-stu-id="ddd1b-106">The account specified for the connection should only be granted permission to insert, update, and delete data on the views that replication creates in the publication database; it should not be given any additional permissions.</span></span> <span data-ttu-id="ddd1b-107">各サブスクライバーで構成したアカウントに、**syncobj_** _\<HexadecimalNumber>_ の形式で名前が指定されたパブリケーション データベース内のビューに対する権限を与えます。</span><span class="sxs-lookup"><span data-stu-id="ddd1b-107">Grant permissions on views in the publication database that are named in the form **syncobj_**_\<HexadecimalNumber>_ to the account you configured at each Subscriber.</span></span>  
  
 <span data-ttu-id="ddd1b-108">接続の種類として、3 つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="ddd1b-108">There are three options available for the type of connection:</span></span>  
  
-   <span data-ttu-id="ddd1b-109">定義済みのリンク サーバーまたはリモート サーバー。</span><span class="sxs-lookup"><span data-stu-id="ddd1b-109">A linked server or remote server that you have already defined.</span></span>  
  
-   <span data-ttu-id="ddd1b-110">レプリケーションによって作成されるリンク サーバー。このウィザードで指定した資格情報を使用して接続を行います。</span><span class="sxs-lookup"><span data-stu-id="ddd1b-110">A linked server that replication creates; the connection is made with the credentials you specify in this wizard.</span></span>  
  
-   <span data-ttu-id="ddd1b-111">レプリケーションによって作成されるリンク サーバー。サブスクライバーで変更を行うユーザーの資格情報を使用して接続を行います。</span><span class="sxs-lookup"><span data-stu-id="ddd1b-111">A linked server that replication creates; the connection is made with the credentials of the user making the change at the Subscriber.</span></span>  
  
 <span data-ttu-id="ddd1b-112">最初の 2 つのオプションは、このウィザードで指定できます。</span><span class="sxs-lookup"><span data-stu-id="ddd1b-112">The first two options can be specified in this wizard.</span></span> <span data-ttu-id="ddd1b-113">最後のオプションは、 [sp_link_publication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql)を使用した場合にのみ指定できます。パラメーターに値**1**を指定し **@security_mode** ます。</span><span class="sxs-lookup"><span data-stu-id="ddd1b-113">The last option can only be specified using [sp_link_publication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql); specify a value of **1** for the parameter **@security_mode**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ddd1b-114">Options</span><span class="sxs-lookup"><span data-stu-id="ddd1b-114">Options</span></span>  
 <span data-ttu-id="ddd1b-115">**[SQL Server 認証を使用して接続するリンク サーバーを作成する]**</span><span class="sxs-lookup"><span data-stu-id="ddd1b-115">**Create a linked server that connects using the following SQL Server Authentication login:**</span></span>  
 <span data-ttu-id="ddd1b-116">レプリケーションにより、 **[ログイン]** フィールドおよび **[パスワード]** フィールドに指定された資格情報に基づいてリンク サーバーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ddd1b-116">Replication creates a linked server using the credentials specified in the **Login** and **Password** fields.</span></span>  
  
 <span data-ttu-id="ddd1b-117">**Login**</span><span class="sxs-lookup"><span data-stu-id="ddd1b-117">**Login**</span></span>  
 <span data-ttu-id="ddd1b-118">このトピックに記載されたアクセス許可のみを持つ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを入力します。</span><span class="sxs-lookup"><span data-stu-id="ddd1b-118">Enter a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login that has only the permissions described in this topic.</span></span>  
  
 <span data-ttu-id="ddd1b-119">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="ddd1b-119">**Password**</span></span>  
 <span data-ttu-id="ddd1b-120">**[ログイン]** に指定したログインに使用する複雑なパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="ddd1b-120">Enter a strong password for the login specified in **Login**.</span></span>  
  
 <span data-ttu-id="ddd1b-121">**パスワードの確認入力**</span><span class="sxs-lookup"><span data-stu-id="ddd1b-121">**Confirm Password**</span></span>  
 <span data-ttu-id="ddd1b-122">パスワードが正常に入力されていることを確認するために、パスワードを再入力します。</span><span class="sxs-lookup"><span data-stu-id="ddd1b-122">Re-enter the password to confirm that it was entered correctly.</span></span>  
  
 <span data-ttu-id="ddd1b-123">**[定義済みのリンク サーバーまたはリモート サーバーを使用する]**</span><span class="sxs-lookup"><span data-stu-id="ddd1b-123">**Use a linked server or remote server that you have already defined.**</span></span>  
 <span data-ttu-id="ddd1b-124">このオプションを使用するには、定義済みのリンク サーバーまたはリモート サーバーが必要です。</span><span class="sxs-lookup"><span data-stu-id="ddd1b-124">This option requires a linked server or remote server that you have already defined.</span></span> <span data-ttu-id="ddd1b-125">詳細については、「[リンク サーバー &#40;データベース エンジン&#41;](../linked-servers/linked-servers-database-engine.md)」および「[リモート サーバー](../../database-engine/configure-windows/remote-servers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddd1b-125">For more information, see [Linked Servers &#40;Database Engine&#41;](../linked-servers/linked-servers-database-engine.md) and [Remote Servers](../../database-engine/configure-windows/remote-servers.md).</span></span> <span data-ttu-id="ddd1b-126">リンク サーバーまたはリモート サーバーに使用するログインに対して複雑なパスワードが設定されていて、このトピックに記載された権限だけが設定されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ddd1b-126">Ensure that the login used for the linked server or remote server has a strong password and has only the permissions described in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddd1b-127">参照</span><span class="sxs-lookup"><span data-stu-id="ddd1b-127">See Also</span></span>  
 <span data-ttu-id="ddd1b-128">[Create an Updatable Subscription to a Transactional Publication](publish/create-an-updatable-subscription-to-a-transactional-publication.md) </span><span class="sxs-lookup"><span data-stu-id="ddd1b-128">[Create an Updatable Subscription to a Transactional Publication](publish/create-an-updatable-subscription-to-a-transactional-publication.md) </span></span>  
 <span data-ttu-id="ddd1b-129">[レプリケーションのセキュリティ設定の表示および変更](security/view-and-modify-replication-security-settings.md) </span><span class="sxs-lookup"><span data-stu-id="ddd1b-129">[View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md) </span></span>  
 <span data-ttu-id="ddd1b-130">[Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="ddd1b-130">[Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md) </span></span>  
 [<span data-ttu-id="ddd1b-131">パブリケーションのサブスクライブ</span><span class="sxs-lookup"><span data-stu-id="ddd1b-131">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
