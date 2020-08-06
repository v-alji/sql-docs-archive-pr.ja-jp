---
title: アプリケーション ロールの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.approle.general.f1
helpviewer_keywords:
- application roles [SQL Server], creating
ms.assetid: 6b8da1f5-3d8e-4f88-b111-b915788b06f1
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 51272dad57558cdb771f9b98a2f5e5b3da7609cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643745"
---
# <a name="create-an-application-role"></a><span data-ttu-id="f57ce-102">アプリケーション ロールの作成</span><span class="sxs-lookup"><span data-stu-id="f57ce-102">Create an Application Role</span></span>
  <span data-ttu-id="f57ce-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]でアプリケーション ロールを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f57ce-103">This topic describes how to create an application role in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="f57ce-104">アプリケーション ロールは、特定のアプリケーションを使用する場合を除き、データベースへのユーザー アクセスを制限します。</span><span class="sxs-lookup"><span data-stu-id="f57ce-104">Application roles restrict user access to a database except through specific applications.</span></span> <span data-ttu-id="f57ce-105">アプリケーション ロールにはユーザーが含まれないため、 **[アプリケーション ロール]** が選択されている場合には、 **[ロール メンバー]** の一覧は表示されません。</span><span class="sxs-lookup"><span data-stu-id="f57ce-105">Application roles have no users, so the **Role Members** list is not displayed when **Application role** is selected.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f57ce-106">アプリケーション ロールのパスワードを設定するときには、パスワードの複雑性が確認されます。</span><span class="sxs-lookup"><span data-stu-id="f57ce-106">Password complexity is checked when application role passwords are set.</span></span> <span data-ttu-id="f57ce-107">アプリケーション ロールを呼び出すアプリケーションは、これらのパスワードを格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f57ce-107">Applications that invoke application roles must store their passwords.</span></span> <span data-ttu-id="f57ce-108">アプリケーション ロールのパスワードは常に暗号化して保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f57ce-108">Application role passwords should always be stored encrypted.</span></span>  
  
 <span data-ttu-id="f57ce-109">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="f57ce-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f57ce-110">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="f57ce-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f57ce-111">Security</span><span class="sxs-lookup"><span data-stu-id="f57ce-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f57ce-112">**アプリケーション ロールを作成する方法:**</span><span class="sxs-lookup"><span data-stu-id="f57ce-112">**To create an application role, using:**</span></span>  
  
     [<span data-ttu-id="f57ce-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f57ce-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f57ce-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f57ce-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f57ce-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="f57ce-115">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f57ce-116">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f57ce-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f57ce-117">Permissions</span><span class="sxs-lookup"><span data-stu-id="f57ce-117">Permissions</span></span>  
 <span data-ttu-id="f57ce-118">データベースに対する ALTER ANY APPLICATION ROLE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="f57ce-118">Requires ALTER ANY APPLICATION ROLE permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f57ce-119">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="f57ce-119">Using SQL Server Management Studio</span></span>  
  
##### <a name="to-create-an-application-role"></a><span data-ttu-id="f57ce-120">アプリケーション ロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="f57ce-120">To create an application role</span></span>  
  
1.  <span data-ttu-id="f57ce-121">オブジェクト エクスプローラーで、アプリケーション ロールを作成するデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="f57ce-121">In Object Explorer, expand the database where you want to create an application role.</span></span>  
  
2.  <span data-ttu-id="f57ce-122">**[セキュリティ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="f57ce-122">Expand the **Security** folder.</span></span>  
  
3.  <span data-ttu-id="f57ce-123">**[ロール]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="f57ce-123">Expand the **Roles** folder.</span></span>  
  
4.  <span data-ttu-id="f57ce-124">**[アプリケーション ロール]** フォルダーを右クリックし、 **[新しいアプリケーション ロール...]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f57ce-124">Right-click the **Application Roles** folder and select **New Application Role...**.</span></span>  
  
5.  <span data-ttu-id="f57ce-125">**[アプリケーション ロール - 新規]** ダイアログ ボックスの **[全般]** ページで、 **[ロール名]** ボックスに、新しいアプリケーション ロールの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="f57ce-125">In the **Application Role - New** dialog box, on the **General Page**, enter the new name of the new application role in the **Role name** box.</span></span>  
  
6.  <span data-ttu-id="f57ce-126">**[既定のスキーマ]** ボックスで、オブジェクト名の入力によってこのロールが作成するオブジェクトを所有するスキーマを指定します。</span><span class="sxs-lookup"><span data-stu-id="f57ce-126">In the **Default Schema** box, specify the schema that will own objects created by this role by entering the object names.</span></span> <span data-ttu-id="f57ce-127">または、省略記号 **[...]** をクリックして、 **[スキーマの検索]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="f57ce-127">Alternately, click the ellipsis **(...)** to open the **Locate Schema** dialog box.</span></span>  
  
7.  <span data-ttu-id="f57ce-128">**[パスワード]** ボックスに、新しいロールのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="f57ce-128">In the **Password** box, enter a password for the new role.</span></span> <span data-ttu-id="f57ce-129">**[パスワードの確認]** ボックスに、パスワードを再度入力します。</span><span class="sxs-lookup"><span data-stu-id="f57ce-129">Enter that password again into the **Confirm Password** box.</span></span>  
  
8.  <span data-ttu-id="f57ce-130">**[このロールが所有するスキーマ]** から、このロールが所有するスキーマを選択または表示します。</span><span class="sxs-lookup"><span data-stu-id="f57ce-130">Under **Schemas owned by this role**, select or view schemas that will be owned by this role.</span></span> <span data-ttu-id="f57ce-131">スキーマを所有できるのは、1 つのスキーマまたはロールのみです。</span><span class="sxs-lookup"><span data-stu-id="f57ce-131">A schema can be owned by only one schema or role.</span></span>  
  
9. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a><span data-ttu-id="f57ce-132">追加オプション</span><span class="sxs-lookup"><span data-stu-id="f57ce-132">Additional Options</span></span>  
 <span data-ttu-id="f57ce-133">**[アプリケーション ロール - 新規 ]** ダイアログ ボックスには次の 2 つのページもあり、それぞれにオプションが用意されています: **[セキュリティ保護可能なリソース]** 、 **[拡張プロパティ]** 。</span><span class="sxs-lookup"><span data-stu-id="f57ce-133">The **Application Role - New** dialog box also offers options on two additional pages: **Securables** and **Extended Properties**.</span></span>  
  
-   <span data-ttu-id="f57ce-134">**[セキュリティ保護可能なリソース]** ページには、すべてのセキュリティ保護可能なリソースと、ログインに付与できる、セキュリティ保護可能なリソースに対する権限が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="f57ce-134">The **Securables** page lists all possible securables and the permissions on those securables that can be granted to the login.</span></span>  
  
-   <span data-ttu-id="f57ce-135">**[拡張プロパティ]** ページでは、カスタム プロパティをデータベース ユーザーに追加できます。</span><span class="sxs-lookup"><span data-stu-id="f57ce-135">The **Extended properties** page allows you to add custom properties to database users.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f57ce-136">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="f57ce-136">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-application-role"></a><span data-ttu-id="f57ce-137">アプリケーション ロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="f57ce-137">To create an application role</span></span>  
  
1.  <span data-ttu-id="f57ce-138">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="f57ce-138">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f57ce-139">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f57ce-139">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f57ce-140">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f57ce-140">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates an application role called "weekly_receipts" that has the password "987Gbv876sPYY5m23" and "Sales" as its default schema.  
  
    CREATE APPLICATION ROLE weekly_receipts   
        WITH PASSWORD = '987G^bv876sPY)Y5m23'   
        , DEFAULT_SCHEMA = Sales;  
    GO  
    ```  
  
 <span data-ttu-id="f57ce-141">詳細については、「[CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-application-role-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f57ce-141">For more information, see [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-application-role-transact-sql).</span></span>  
  
  
