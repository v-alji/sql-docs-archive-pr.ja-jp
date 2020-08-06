---
title: 資格情報の作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- credentials [SQL Server], creating
- authentication [SQL Server], credentials
- logins [SQL Server], credentials
ms.assetid: c1e77e91-2a69-40d9-b8b3-97cffc710586
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 23221424699449ac3775b0e805bb02ae0ad233f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714073"
---
# <a name="create-a-credential"></a><span data-ttu-id="95577-102">資格情報の作成</span><span class="sxs-lookup"><span data-stu-id="95577-102">Create a Credential</span></span>
  <span data-ttu-id="95577-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、資格情報を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="95577-103">This topic describes how to create a credential in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="95577-104">資格情報によって、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証ユーザーは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]外部の ID を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="95577-104">Credentials provide a way to allow [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication users to have an identity outside of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="95577-105">これは、主に EXTERNAL_ACCESS 権限セットを使用してアセンブリのコードを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="95577-105">This is primarily used to execute code in Assemblies with EXTERNAL_ACCESS permission set.</span></span> <span data-ttu-id="95577-106">また、バックアップを格納するファイルの場所などのドメイン リソースに、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証ユーザーがアクセスする必要がある場合にも、資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="95577-106">Credentials can also be used when a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication user needs access to a domain resource, such as a file location to store a backup.</span></span>  
  
 <span data-ttu-id="95577-107">資格情報は、複数の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインに同時にマップできます。</span><span class="sxs-lookup"><span data-stu-id="95577-107">A credential can be mapped to several [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logins at the same time.</span></span> <span data-ttu-id="95577-108">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインは、一度に 1 つの資格情報にのみマップできます。</span><span class="sxs-lookup"><span data-stu-id="95577-108">A [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login can only be mapped to one credential at a time.</span></span> <span data-ttu-id="95577-109">資格情報を作成したら、 **[ログインのプロパティ]\([全般] ページ)** を使用してログインを資格情報にマップします。</span><span class="sxs-lookup"><span data-stu-id="95577-109">After a credential is created, use the **Login Properties (General Page)** to map a login to a credential.</span></span>  
  
 <span data-ttu-id="95577-110">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="95577-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="95577-111">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="95577-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="95577-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="95577-112">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="95577-113">Security</span><span class="sxs-lookup"><span data-stu-id="95577-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="95577-114">**資格情報を作成する方法:**</span><span class="sxs-lookup"><span data-stu-id="95577-114">**To create a credential, using:**</span></span>  
  
     [<span data-ttu-id="95577-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="95577-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="95577-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="95577-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="95577-117">はじめに</span><span class="sxs-lookup"><span data-stu-id="95577-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="95577-118">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="95577-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="95577-119">ログインにマップされたプロバイダーの資格情報がない場合は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービス アカウントにマップされた資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="95577-119">If there is no login mapped credential for the provider, the credential mapped to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account is used.</span></span>  
  
-   <span data-ttu-id="95577-120">それぞれが異なるプロバイダーで使用される資格情報であれば、1 つのログインに複数の資格情報をマップできます。</span><span class="sxs-lookup"><span data-stu-id="95577-120">A login can have multiple credentials mapped to it as long as they are used with distinctive providers.</span></span> <span data-ttu-id="95577-121">マップされた資格情報は、各ログインで各プロバイダーにつき 1 つだけ存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95577-121">There must be only one mapped credential per provider per login.</span></span> <span data-ttu-id="95577-122">同じ資格情報を他のログインにマップすることはできます。</span><span class="sxs-lookup"><span data-stu-id="95577-122">The same credential can be mapped to other logins.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="95577-123">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="95577-123">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="95577-124">Permissions</span><span class="sxs-lookup"><span data-stu-id="95577-124">Permissions</span></span>  
 <span data-ttu-id="95577-125">資格情報の作成や変更には、ALTER ANY CREDENTIAL 権限が必要です。資格情報にログインをマップするには、ALTER ANY LOGIN 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="95577-125">Requires ALTER ANY CREDENTIAL permission to create or modify a credential and ALTER ANY LOGIN permission to map a login to a credential.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="95577-126">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="95577-126">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-credential"></a><span data-ttu-id="95577-127">資格情報を作成するには</span><span class="sxs-lookup"><span data-stu-id="95577-127">To create a credential</span></span>  
  
1.  <span data-ttu-id="95577-128">オブジェクト エクスプローラーで、 **[セキュリティ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="95577-128">In Object Explorer, expand  the **Security** folder.</span></span>  
  
2.  <span data-ttu-id="95577-129">**[資格情報]** フォルダーを右クリックし、 **[新しい資格情報...]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95577-129">Right-click the **Credentials** folder and select **New Credential...**.</span></span>  
  
3.  <span data-ttu-id="95577-130">**[新しい資格情報]** ダイアログ ボックスで、 **[資格情報名]** ボックスに資格情報の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="95577-130">In the **New Credential** dialog box, in the **Credential Name** box, type a name for the credential.</span></span>  
  
4.  <span data-ttu-id="95577-131">**[ID]** ボックスに、送信用の接続に使用するアカウントの名前を入力します ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のコンテキストが適用されない場合)。</span><span class="sxs-lookup"><span data-stu-id="95577-131">In the **Identity** box, type the name of the account used for outgoing connections (when leaving the context of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]).</span></span> <span data-ttu-id="95577-132">通常、これは Windows ユーザー アカウントですが、ID を別の種類のアカウントにすることができます。</span><span class="sxs-lookup"><span data-stu-id="95577-132">Typically, this will be a Windows user account, but the identity can be an account of another type.</span></span>  
  
     <span data-ttu-id="95577-133">または、省略記号 **[...]** をクリックして **[ユーザーまたはグループの選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="95577-133">Alternately, click the ellipsis **(...)** to open the **Select User or Group** dialog box.</span></span>  
  
5.  <span data-ttu-id="95577-134">**[パスワード]** ボックスと **[パスワードの確認入力]** ボックスに、 **[ID]** ボックスに指定したアカウントのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="95577-134">In the **Password** and **Confirm password** boxes, type the password of the account specified in the **Identity** box.</span></span> <span data-ttu-id="95577-135">**[ID]** ボックスの値が Windows ユーザー アカウントである場合は、Windows パスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="95577-135">If **Identity** is a Windows user account, this is the Windows password.</span></span> <span data-ttu-id="95577-136">パスワードが不要である場合は、 **[パスワード]** ボックスを空にできます。</span><span class="sxs-lookup"><span data-stu-id="95577-136">The **Password** can be blank, if no password is required.</span></span>  
  
6.  <span data-ttu-id="95577-137">**[暗号化サービス プロバイダーの使用]** をクリックし、拡張キー管理 (EKM) プロバイダーによって確認される資格情報を設定します。</span><span class="sxs-lookup"><span data-stu-id="95577-137">Select **Use Encryption Provider** to set the credential to be verified by an Extensible Key Management (EKM) Provider.</span></span> <span data-ttu-id="95577-138">詳細については、「[拡張キー管理 &#40;EKM&#41;](../encryption/extensible-key-management-ekm.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95577-138">For more information, see [Extensible Key Management &#40;EKM&#41;](../encryption/extensible-key-management-ekm.md)</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="95577-139">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="95577-139">Using Transact-SQL</span></span>  
  
###  <a name="to-create-a-credential"></a><a name="Credential"></a><span data-ttu-id="95577-140">資格情報を作成するには</span><span class="sxs-lookup"><span data-stu-id="95577-140">To create a credential</span></span>  
  
1.  <span data-ttu-id="95577-141">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="95577-141">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="95577-142">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95577-142">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="95577-143">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95577-143">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates the credential called "AlterEgo.".   
    -- The credential contains the Windows user "Mary5" and a password.  
    CREATE CREDENTIAL AlterEgo WITH IDENTITY = 'Mary5',   
        SECRET = '<EnterStrongPasswordHere>';  
    GO  
    ```  
  
 <span data-ttu-id="95577-144">詳細については、「[CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95577-144">For more information, see [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql).</span></span>  
  
  
