---
title: 複数のサーバーに対するステートメントの同時実行
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- multiserver queries
- executing queries against multiple servers
- queries [SQL Server], multiserver
ms.assetid: 197760f3-0a06-43de-8162-69c27d3fbe56
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b94775029a1501d3e894d84ef4a027fc1595dc10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717192"
---
# <a name="execute-statements-against-multiple-servers-simultaneously-sql-server-management-studio"></a><span data-ttu-id="9f846-102">複数のサーバーに対してステートメントを同時に実行する (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="9f846-102">Execute Statements Against Multiple Servers Simultaneously (SQL Server Management Studio)</span></span>
  <span data-ttu-id="9f846-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]で複数のサーバーに対してクエリを同時に実行する方法について説明します。これを行うには、ローカル サーバー グループ、または 1 つの中央管理サーバーと 1 つ以上のサーバー グループ、およびグループ内の 1 つ以上の登録済みサーバーを作成し、このグループ全体に対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="9f846-103">This topic describes how to query multiple servers at the same time in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], by creating a local server group, or a Central Management Server and one or more server groups, and one or more registered servers within the groups, and then querying the complete group.</span></span> <span data-ttu-id="9f846-104">クエリから返された結果は、結合して 1 つの結果ペインに表示するか、別々の結果ペインに表示することができます。</span><span class="sxs-lookup"><span data-stu-id="9f846-104">The results that are returned by the query can be combined into a single results pane, or can be returned in separate results panes.</span></span> <span data-ttu-id="9f846-105">結果セットには、サーバー名を表示する列と、各サーバーに対するクエリで使用されたログインを表示する列を追加できます。</span><span class="sxs-lookup"><span data-stu-id="9f846-105">The results set can include additional columns for the server name and the login that is used by the query on each server.</span></span> <span data-ttu-id="9f846-106">中央管理サーバーおよび従属サーバーは、Windows 認証を使用しないと登録できません。</span><span class="sxs-lookup"><span data-stu-id="9f846-106">Central Management Servers and subordinate servers can be registered by using only Windows Authentication.</span></span> <span data-ttu-id="9f846-107">ローカル サーバー グループ内のサーバーは、Windows 認証または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用して登録できます。</span><span class="sxs-lookup"><span data-stu-id="9f846-107">Servers in local server groups can be registered by using Windows Authentication or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f846-108">次の手順を実行する前に、中央管理サーバーとサーバー グループを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f846-108">Before you execute the following procedures, create a Central Management Server and server groups.</span></span> <span data-ttu-id="9f846-109">詳細については、「[中央管理サーバーとサーバー グループの作成 &#40;SQL Server Management Studio&#41;](create-a-central-management-server-and-server-group.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f846-109">For more information, see [Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;](create-a-central-management-server-and-server-group.md).</span></span>  
  
 <span data-ttu-id="9f846-110">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="9f846-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9f846-111">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="9f846-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9f846-112">Security</span><span class="sxs-lookup"><span data-stu-id="9f846-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9f846-113">**複数のサーバーに対してステートメントを実行するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="9f846-113">**To execute statements against multiple servers, using:**</span></span>  
  
     [<span data-ttu-id="9f846-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9f846-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9f846-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="9f846-115">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9f846-116">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="9f846-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9f846-117">Permissions</span><span class="sxs-lookup"><span data-stu-id="9f846-117">Permissions</span></span>  
 <span data-ttu-id="9f846-118">中央管理サーバーによって保持される接続は、ユーザーのコンテキスト内で Windows 認証を使用して実行されるため、登録済みサーバーでの有効な権限が変わることがあります。</span><span class="sxs-lookup"><span data-stu-id="9f846-118">Because the connections maintained by a Central Management Server execute in the context of the user, by using Windows Authentication, the effective permissions on the registered servers might vary.</span></span> <span data-ttu-id="9f846-119">たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] A のインスタンスでは sysadmin 固定サーバー ロールのメンバーであるユーザーでも、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] B のインスタンスでは権限が限られていることがあります。</span><span class="sxs-lookup"><span data-stu-id="9f846-119">For example, the user might be a member of the sysadmin fixed server role on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] A, but have limited permissions on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] B.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9f846-120">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="9f846-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-execute-statements-against-multiple-configuration-targets-simultaneously"></a><span data-ttu-id="9f846-121">複数の構成対象に対してステートメントを同時に実行するには</span><span class="sxs-lookup"><span data-stu-id="9f846-121">To execute statements against multiple configuration targets simultaneously</span></span>  
  
1.  <span data-ttu-id="9f846-122">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[表示]** メニューの **[登録済みサーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9f846-122">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Registered Servers**.</span></span>  
  
2.  <span data-ttu-id="9f846-123">中央管理サーバーを展開して、サーバー グループを右クリックし、 **[接続]** をポイントして、 **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9f846-123">Expand a Central Management Server, right-click a server group, point to **Connect**, and then click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9f846-124">クエリ エディターで、次のような [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを入力して実行します。</span><span class="sxs-lookup"><span data-stu-id="9f846-124">In Query Editor, type and execute a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, such as the following:</span></span>  
  
    ```  
    USE master  
    GO  
    SELECT * FROM sysdatabases;  
    GO  
    ```  
  
     <span data-ttu-id="9f846-125">既定では、サーバー グループ内のすべてのサーバーからのクエリ結果が結合されて結果ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9f846-125">By default, the results pane will combine the query results from all the servers in the server group.</span></span>  
  
#### <a name="to-change-the-multiserver-results-options"></a><span data-ttu-id="9f846-126">マルチサーバーの結果オプションを変更するには</span><span class="sxs-lookup"><span data-stu-id="9f846-126">To change the multiserver results options</span></span>  
  
1.  <span data-ttu-id="9f846-127">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で、 **[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9f846-127">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], on the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="9f846-128">**[クエリ結果]**、 **[SQL Server]** の順に展開し、 **[マルチサーバーの結果]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9f846-128">Expand **Query Results**, expand **SQL Server**, and then click **Multiserver Results**.</span></span>  
  
3.  <span data-ttu-id="9f846-129">**[マルチサーバーの結果]** ページで、使用するオプション設定を指定し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9f846-129">On the **Multiserver Results** page, specify the option settings that you want, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f846-130">参照</span><span class="sxs-lookup"><span data-stu-id="9f846-130">See Also</span></span>  
 [<span data-ttu-id="9f846-131">中央管理サーバーを使用して複数のサーバーを管理する</span><span class="sxs-lookup"><span data-stu-id="9f846-131">Administer Multiple Servers Using Central Management Servers</span></span>](../../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  
