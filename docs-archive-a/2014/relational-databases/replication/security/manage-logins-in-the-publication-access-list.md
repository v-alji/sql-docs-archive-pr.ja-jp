---
title: パブリケーション アクセス リストのログインの管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server replication], publication access list
- publications [SQL Server replication], publication access lists
- publication access list (PAL)
- PAL (publication access list)
- logins [SQL Server replication], managing
ms.assetid: fceb216b-0b18-4e3b-8ae0-13e35920dcbc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b96e6f46403cf3a482f00a3f5155527177920967
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634379"
---
# <a name="manage-logins-in-the-publication-access-list"></a><span data-ttu-id="36562-102">パブリケーション アクセス リストのログインの管理</span><span class="sxs-lookup"><span data-stu-id="36562-102">Manage Logins in the Publication Access List</span></span>
  <span data-ttu-id="36562-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、パブリケーション アクセス リストのログインを管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="36562-103">This topic describes how to manage logins in the Publication Access List in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="36562-104">パブリケーションへのアクセスは、パブリケーション アクセス リスト (PAL) によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="36562-104">Access to a publication is controlled by the publication access list (PAL).</span></span> <span data-ttu-id="36562-105">ログインおよびグループの PAL への追加および PAL からの削除を実行できます。</span><span class="sxs-lookup"><span data-stu-id="36562-105">Logins and groups can be added and removed from the PAL.</span></span>  
  
 <span data-ttu-id="36562-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="36562-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="36562-107">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="36562-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="36562-108">前提条件</span><span class="sxs-lookup"><span data-stu-id="36562-108">Prerequisites</span></span>](#Prerequisites)  
  
-   <span data-ttu-id="36562-109">**パブリケーション アクセス リストのログインを管理するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="36562-109">**To manage logins in the Publication Access List, using:**</span></span>  
  
     [<span data-ttu-id="36562-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="36562-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="36562-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="36562-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="36562-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="36562-112">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="36562-113">前提条件</span><span class="sxs-lookup"><span data-stu-id="36562-113">Prerequisites</span></span>  
  
-   <span data-ttu-id="36562-114">PAL にログインを追加する前に、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインをパブリケーション データベースのデータベース ユーザーに関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="36562-114">You must associate the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login with a database user in the publication database before you add the login to the PAL.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="36562-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="36562-115">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="36562-116">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[パブリケーション アクセス リスト]** ページで、パブリケーション アクセス リスト (PAL) を使用してログインを管理します。</span><span class="sxs-lookup"><span data-stu-id="36562-116">You use the publication access list (PAL) on the **Publication Access List** page of the **Publication Properties - \<Publication>** dialog box to manage logins.</span></span> <span data-ttu-id="36562-117">このダイアログ ボックスへのアクセス方法の詳細については、「[パブリケーション プロパティの表示および変更](../publish/view-and-modify-publication-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36562-117">For more information about how to access this dialog box, see [View and Modify Publication Properties](../publish/view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-manage-logins-in-the-pal"></a><span data-ttu-id="36562-118">PAL のログインを管理するには</span><span class="sxs-lookup"><span data-stu-id="36562-118">To manage logins in the PAL</span></span>  
  
1.  <span data-ttu-id="36562-119">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[パブリケーション アクセス リスト]** ページで、 **[追加]** 、 **[削除]** 、および **[すべて削除]** の各ボタンを使用して、PAL のログインやグループを追加および削除します。</span><span class="sxs-lookup"><span data-stu-id="36562-119">On the **Publication Access List** page of the **Publication Properties - \<Publication>** dialog box, use the **Add**, **Remove**, and **Remove All** buttons to add and remove logins and groups from the PAL.</span></span> <span data-ttu-id="36562-120">PAL から **distributor_admin** を削除しないでください。</span><span class="sxs-lookup"><span data-stu-id="36562-120">Do not remove **distributor_admin** from the PAL.</span></span> <span data-ttu-id="36562-121">このアカウントはレプリケーションで使用されます。</span><span class="sxs-lookup"><span data-stu-id="36562-121">This account is used by replication.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="36562-122">リモート ディストリビューターを使用する場合、PAL 内のアカウントは、パブリッシャーとディストリビューターの両方で使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="36562-122">If a remote Distributor is used, accounts in the PAL must be available at both the Publisher and the Distributor.</span></span> <span data-ttu-id="36562-123">このアカウントは、どちらのサーバーでも定義されているドメイン アカウントまたはローカル アカウントにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="36562-123">The account must be either a domain account or a local account that is defined at both servers.</span></span> <span data-ttu-id="36562-124">両方のログインに関連付けられているパスワードは、同じにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="36562-124">The passwords that are associated with both logins must be the same.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="36562-125">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="36562-125">Using Transact-SQL</span></span>  
  
#### <a name="to-view-groups-and-logins-that-belong-to-the-pal"></a><span data-ttu-id="36562-126">PAL に登録されているグループおよびログインを表示するには</span><span class="sxs-lookup"><span data-stu-id="36562-126">To view groups and logins that belong to the PAL</span></span>  
  
1.  <span data-ttu-id="36562-127">パブリッシャー側のパブリケーション データベースに対して、 [sp_help_publication_access](/sql/relational-databases/system-stored-procedures/sp-help-publication-access-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="36562-127">At the Publisher on the publication database, execute [sp_help_publication_access](/sql/relational-databases/system-stored-procedures/sp-help-publication-access-transact-sql).</span></span> <span data-ttu-id="36562-128">[ \*\* \@ パブリケーション\*\*] では、パブリケーション名を指定します。</span><span class="sxs-lookup"><span data-stu-id="36562-128">For **\@publication**, specify the publication name.</span></span> <span data-ttu-id="36562-129">これで、PAL のグループおよびログインに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="36562-129">This displays information about the groups and logins in the PAL.</span></span>  
  
#### <a name="to-add-groups-and-logins-to-the-pal"></a><span data-ttu-id="36562-130">グループおよびログインを PAL に追加するには</span><span class="sxs-lookup"><span data-stu-id="36562-130">To add groups and logins to the PAL</span></span>  
  
1.  <span data-ttu-id="36562-131">パブリッシャー側のパブリケーション データベースに対して、 [sp_grant_publication_access](/sql/relational-databases/system-stored-procedures/sp-grant-publication-access-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="36562-131">At the Publisher on the publication database, execute [sp_grant_publication_access](/sql/relational-databases/system-stored-procedures/sp-grant-publication-access-transact-sql).</span></span> <span data-ttu-id="36562-132">[ \*\* \@ パブリケーション**] にはパブリケーション名を指定し、[ \*\* \@ ログイン**] には追加するログインまたはグループの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="36562-132">For **\@publication**, specify the publication name; and for **\@login**, specify the name of the login or group that is being added.</span></span>  
  
#### <a name="to-remove-groups-and-logins-from-the-pal"></a><span data-ttu-id="36562-133">グループおよびログインを PAL から削除するには</span><span class="sxs-lookup"><span data-stu-id="36562-133">To remove groups and logins from the PAL</span></span>  
  
1.  <span data-ttu-id="36562-134">パブリッシャー側のパブリケーション データベースに対して、 [sp_revoke_publication_access](/sql/relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="36562-134">At the Publisher on the publication database, execute [sp_revoke_publication_access](/sql/relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql).</span></span> <span data-ttu-id="36562-135">[ \*\* \@ パブリケーション**] にはパブリケーション名を指定し、[ \*\* \@ ログイン**] には削除するログインまたはグループの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="36562-135">For **\@publication**, specify the publication name; and for **\@login**, specify the name of the login or group that is being removed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36562-136">参照</span><span class="sxs-lookup"><span data-stu-id="36562-136">See Also</span></span>  
 <span data-ttu-id="36562-137">[レプリケーション エージェントのセキュリティ モデル](replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="36562-137">[Replication Agent Security Model](replication-agent-security-model.md) </span></span>  
 <span data-ttu-id="36562-138">[レプリケーション トポロジのセキュリティ保護](view-and-modify-replication-security-settings.md) </span><span class="sxs-lookup"><span data-stu-id="36562-138">[Secure a Replication Topology](view-and-modify-replication-security-settings.md) </span></span>  
 [<span data-ttu-id="36562-139">パブリッシャーのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="36562-139">Secure the Publisher</span></span>](secure-the-publisher.md)  
  
  
