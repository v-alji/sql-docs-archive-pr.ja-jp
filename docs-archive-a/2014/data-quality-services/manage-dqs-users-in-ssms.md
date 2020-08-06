---
title: SSMS で DQS ユーザーを管理する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 955af01d-00da-4c51-9311-f3848749df54
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bf8789abb59d168f39562f6486bb5c54bfc0fc50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644637"
---
# <a name="manage-dqs-users-in-ssms"></a><span data-ttu-id="236db-102">SSMS による DQS ユーザーの管理</span><span class="sxs-lookup"><span data-stu-id="236db-102">Manage DQS Users in SSMS</span></span>
  <span data-ttu-id="236db-103">このトピックでは、SQL Server Management Studio を使用して SQL Server インスタンスで追加のユーザーを作成し、DQS_MAIN データベースの適切な [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) ロールを付与する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="236db-103">This topic describes how to create additional users in the SQL Server instance using SQL Server Management Studio, and grant them appropriate [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) roles on the DQS_MAIN database.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="236db-104">はじめに</span><span class="sxs-lookup"><span data-stu-id="236db-104">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="236db-105">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="236db-105">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="236db-106">Permissions</span><span class="sxs-lookup"><span data-stu-id="236db-106">Permissions</span></span>  
 <span data-ttu-id="236db-107">SQL ログインを作成し、適切な DQS ロールを付与するには、Windows ユーザー アカウントが適切な固定サーバー ロール (securityadmin、serveradmin、sysadmin など) のメンバーであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="236db-107">Your Windows user account must be a member of the appropriate fixed server role (such as securityadmin, serveradmin, or sysadmin) to create SQL login, and grant appropriate DQS roles.</span></span>  
  
##  <a name="create-a-sql-login-and-grant-dqs-role"></a><a name="GrantRoles"></a><span data-ttu-id="236db-108">SQL ログインを作成し、DQS ロールを付与する</span><span class="sxs-lookup"><span data-stu-id="236db-108">Create a SQL Login and Grant DQS Role</span></span>  
  
1.  <span data-ttu-id="236db-109">Microsoft SQL Server Management Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="236db-109">Start Microsoft SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="236db-110">Microsoft SQL Server Management Studio で、SQL Server インスタンスを展開し、 **[セキュリティ]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="236db-110">In Microsoft SQL Server Management Studio, expand your SQL Server instance, and then expand **Security**.</span></span>  
  
3.  <span data-ttu-id="236db-111">**[セキュリティ]** フォルダーを右クリックし、 **[新規作成]** をポイントして、 **[ログイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="236db-111">Right-click the **Security** folder, point to **New**, and then click **Login**.</span></span>  
  
4.  <span data-ttu-id="236db-112">**[ログイン - 新規作成]** ダイアログ ボックスの **[ログイン名]** ボックスで Windows ユーザーの名前を指定し、認証の種類として **[Windows 認証]** を指定し、**[検索]** をクリックしてユーザーを検証します。</span><span class="sxs-lookup"><span data-stu-id="236db-112">In the **Login - New** dialog box, specify the name of a Windows user in the **Login name** box, specify the type of authentication as **Windows authentication**, and click **Search** to validate the user.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="236db-113">DQS では、Windows 認証のみサポートします。SQL Server 認証はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="236db-113">DQS only supports Windows authentication; SQL Server authentication is not supported.</span></span>  
  
5.  <span data-ttu-id="236db-114">ユーザーの検証後、左ペインの **[ユーザー マッピング]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="236db-114">After the user is validated, click the **User Mapping** page in the left pane.</span></span>  
  
6.  <span data-ttu-id="236db-115">右ペインで、 **[DQS_MAIN]** データベースの **[マップ]** 列のチェック ボックスをオンにし、ユーザーに必要なアクセス レベルに応じて、 **[DQS_MAIN のデータベース ロール メンバーシップ]** ペインで **[dqs_administrator]**、 **[dqs_kb_editor]** 、または **[dqs_kb_operator]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="236db-115">In the right pane, select the check box under the **Map** column for the **DQS_MAIN** database, and then select the **dqs_administrator**, **dqs_kb_editor**, or **dqs_kb_operator** check box in the **Database role membership for: DQS_MAIN** pane, depending on the access level needed for the user.</span></span>  
  
7.  <span data-ttu-id="236db-116">**[ログイン - 新規作成]** ダイアログ ボックスで、**[OK]** をクリックして変更を適用します。</span><span class="sxs-lookup"><span data-stu-id="236db-116">In the **Login - New** dialog box, click **OK** to apply the changes.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="236db-117">**dqs_administrator** ロールをユーザーに付与し、変更を適用してから、ユーザー権限を再びオンにすると、その他の 2 つの DQS ロールのチェック ボックス (**[dq_kb_editor]** および **[dqs_kb_operator]**) もオンになります。</span><span class="sxs-lookup"><span data-stu-id="236db-117">If you grant the **dqs_administrator** role to a user, apply the changes, and then recheck the user permissions, the other two DQS roles check boxes (**dq_kb_editor** and **dqs_kb_operator**) are also selected.</span></span>  
  
  
