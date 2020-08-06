---
title: データベース ミラーリング監視サーバーを追加または置き換える方法 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- witness [SQL Server], establishing
- database mirroring [SQL Server], witness
ms.assetid: 4b5ecffd-f025-4ab7-b69d-8958c6477127
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5dd14ace23956ceef114f1f032b5d4db5febcec7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634044"
---
# <a name="add-or-replace-a-database-mirroring-witness-sql-server-management-studio"></a><span data-ttu-id="9b643-102">データベース ミラーリング監視サーバーを追加または置き換える方法 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="9b643-102">Add or Replace a Database Mirroring Witness (SQL Server Management Studio)</span></span>
  <span data-ttu-id="9b643-103">データベース ミラーリング エンドポイントで Windows 認証を使用している場合、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用してミラーリング監視サーバーを追加または置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="9b643-103">If the database mirroring endpoints use Windows Authentication,, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to add or replace a witness.</span></span> <span data-ttu-id="9b643-104">また、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] でミラーリング監視サーバーを追加すると、動作モードが自動フェールオーバーを伴う高い安全性モードに変更されます。</span><span class="sxs-lookup"><span data-stu-id="9b643-104">Adding a witness in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] also changes the operating mode to high-safety mode with automatic failover.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9b643-105">ミラーリング監視サーバーは、どちらのパートナーにも属さない別のコンピューターに常駐させることを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9b643-105">We strongly recommend that the witness reside on a separate computer from either of the partners.</span></span> <span data-ttu-id="9b643-106">ミラーリング監視サーバーで使用するサービス アカウントのドメインは、プリンシパル サーバー インスタンスおよびミラー サーバー インスタンスで使用するサービス アカウントのドメインと同じであるか、信頼関係のあるドメインのアカウントである必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b643-106">The service account used by the witness must be in the same domain as the service accounts used by the principal and mirror server instances, or it must be in a trusted domain.</span></span>  
  
### <a name="to-add-or-replace-a-witness"></a><span data-ttu-id="9b643-107">ミラーリング監視サーバーを追加または置き換えるには</span><span class="sxs-lookup"><span data-stu-id="9b643-107">To Add or Replace a Witness</span></span>  
  
1.  <span data-ttu-id="9b643-108">プリンシパル サーバー インスタンスに接続した後、オブジェクト エクスプローラーでサーバー名をクリックして、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="9b643-108">After connecting to the principal server instance, in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="9b643-109">**[データベース]** を展開し、ミラーリング監視サーバーを追加または置き換えるセッションのプリンシパル データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="9b643-109">Expand **Databases**, and select the principal database of the session to which you are adding or replacing a witness.</span></span>  
  
3.  <span data-ttu-id="9b643-110">データベースを右クリックして **[タスク]** を選択し、 **[ミラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b643-110">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="9b643-111">**[データベースのプロパティ]** ダイアログ ボックスの **[ミラーリング]** ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="9b643-111">This opens the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="9b643-112">**[セキュリティの構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b643-112">Click **Configure Security**.</span></span>  
  
5.  <span data-ttu-id="9b643-113">**[データベース ミラーリング セキュリティ構成ウィザード]** 開始ページが表示されたら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b643-113">If the **Configure Database Mirroring Security Wizard** welcome screen appears, click **Next**.</span></span>  
  
6.  <span data-ttu-id="9b643-114">**[ミラーリング監視サーバーを含める]** ページで **[はい]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b643-114">In the **Include Witness Server** dialog box, click **Yes**, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="9b643-115">**[構成するサーバーを選択する]** ページでは、 **[ミラーリング監視サーバー インスタンス]** チェック ボックスが自動的にオンになっています。</span><span class="sxs-lookup"><span data-stu-id="9b643-115">In the **Choose Servers to Configure** dialog box, the **Witness server instance** check box is automatically checked.</span></span> <span data-ttu-id="9b643-116">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b643-116">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="9b643-117">**[プリンシパル サーバー インスタンス]** ページで、既定で設定されているポートとエンドポイントをそのままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="9b643-117">On the **Principal Server Instance** dialog box, keep the existing port and endpoint.</span></span> <span data-ttu-id="9b643-118">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b643-118">Click **Next**.</span></span>  
  
9. <span data-ttu-id="9b643-119">**[ミラーリング監視サーバー インスタンス]** ページで、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b643-119">On the **Witness Server Instance** dialog box, click **Connect**.</span></span>  
  
10. <span data-ttu-id="9b643-120">**[サーバーへの接続]** ページの **[サーバー名]** フィールドでミラーリング監視サーバー インスタンスを指定し、既定の Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="9b643-120">In the **Connect to Server** dialog box, specify the witness server instance in the **Server name** field, and use Windows Authentication (the default).</span></span> <span data-ttu-id="9b643-121">**[Connect]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b643-121">Click **Connect**.</span></span>  
  
11. <span data-ttu-id="9b643-122">接続が確立されると、ミラーリング監視サーバー インスタンスのリスナー ポートとデータベース ミラーリング エンドポイントが **[ミラーリング監視サーバー インスタンス]** ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9b643-122">Once a connection is established, the listener port and database mirroring endpoint of the witness server instance are displayed on the **Witness Server Instance** dialog box.</span></span> <span data-ttu-id="9b643-123">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b643-123">Click **Next**.</span></span>  
  
12. <span data-ttu-id="9b643-124">**[サービス アカウント]** ページには、プリンシパル サーバー インスタンス、ミラー サーバー インスタンス、およびミラーリング監視サーバー インスタンスのドメイン サービス アカウントの各フィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="9b643-124">The **Service Accounts** dialog box contains fields for the domain service accounts of the principal, mirror, and witness server instances.</span></span>  
  
    -   <span data-ttu-id="9b643-125">すべてのサーバー インスタンスで同じサービス アカウントを使用する場合は、これらのフィールドを空白のままにします。</span><span class="sxs-lookup"><span data-stu-id="9b643-125">If the server instances all use the same service account, leave the fields blank.</span></span>  
  
    -   <span data-ttu-id="9b643-126">ミラーリング監視サーバー インスタンスで、どちらかのパートナーと異なるサービス アカウントを使用する場合は、 **[プリンシパル]** 、 **[ミラー]** 、および **[ミラーリング監視]** の各フィールドに、次のようにしてアカウント名を指定します。</span><span class="sxs-lookup"><span data-stu-id="9b643-126">If the witness server instance uses a different service account from either of the partners, fill in the **Principal**, **Mirror**, and **Witness** fields with the account name:</span></span>  
  
         <span data-ttu-id="9b643-127">*DOMAINNAME* **\\** *username*</span><span class="sxs-lookup"><span data-stu-id="9b643-127">*DOMAINNAME* **\\** *username*</span></span>  
  
         <span data-ttu-id="9b643-128">ドメイン名は大文字にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b643-128">The domain name must be in upper case.</span></span>  
  
     <span data-ttu-id="9b643-129">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b643-129">Click **Next**.</span></span>  
  
13. <span data-ttu-id="9b643-130">**[ウィザードの完了]** 概要ページで必要に応じてミラーリング監視サーバーの構成を確認し、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b643-130">On the **Complete the Wizard** summary screen, optionally, verify the witness configuration, and then click **Finish**.</span></span>  
  
14. <span data-ttu-id="9b643-131">完了時に、ウィザードによって **[データベースのプロパティ]** ダイアログ ボックスが表示されます。このダイアログ ボックスの **[ミラーリング監視]** フィールドには、ミラーリング監視サーバーのサーバー ネットワーク アドレスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9b643-131">On finishing, the wizard returns you to the **Database Properties** dialog box where the server network address of the witness now appears in **Witness** field.</span></span> <span data-ttu-id="9b643-132">また、ミラーリング監視サーバーに必要な **[自動フェールオーバーを伴う高い安全性 (同期)]** が自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="9b643-132">Also, **High-safety mode with automatic failover (synchronous)**, which is required with a witness, is automatically selected.</span></span>  
  
     <span data-ttu-id="9b643-133">ミラーリング監視サーバーを有効にし、自動フェールオーバーを伴う高い安全性モードにセッションを変更するには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b643-133">To enable the witness and change the session to high-safety mode with automatic failover, Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b643-134">参照</span><span class="sxs-lookup"><span data-stu-id="9b643-134">See Also</span></span>  
 <span data-ttu-id="9b643-135">[データベース ミラーリング監視サーバー](database-mirroring-witness.md) </span><span class="sxs-lookup"><span data-stu-id="9b643-135">[Database Mirroring Witness](database-mirroring-witness.md) </span></span>  
 <span data-ttu-id="9b643-136">[データベース ミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9b643-136">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="9b643-137">[データベース プロパティ &#40;[ミラーリング] ページ&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="9b643-137">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="9b643-138">[Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md) </span><span class="sxs-lookup"><span data-stu-id="9b643-138">[Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md) </span></span>  
 [<span data-ttu-id="9b643-139">データベース ミラーリング監視サーバー</span><span class="sxs-lookup"><span data-stu-id="9b643-139">Database Mirroring Witness</span></span>](database-mirroring-witness.md)  
  
  
