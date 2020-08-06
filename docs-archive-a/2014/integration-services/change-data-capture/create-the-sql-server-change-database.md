---
title: SQL Server 変更データベースの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- oraIns
ms.assetid: 4f79c24a-e99a-4a06-8637-51eeec406259
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0eaeb26d5bea4c9e50db29aaa45297ba763dbbfa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740218"
---
# <a name="create-the-sql-server-change-database"></a><span data-ttu-id="8beab-102">SQL Server 変更データベースの作成</span><span class="sxs-lookup"><span data-stu-id="8beab-102">Create the SQL Server Change Database</span></span>
  <span data-ttu-id="8beab-103">新しいインスタンス ウィザードを起動すると、[CDC データベースの作成] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8beab-103">When you start the New Instance wizard, the Create CDC Database page opens.</span></span> <span data-ttu-id="8beab-104">[CDC データベースの作成] ページを使用して、新しい CDC インスタンスに関する情報を提供し、新しい変更データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="8beab-104">Use the Create CDC Database page to provide information about the new CDC instance and create a new Change database.</span></span>  
  
 <span data-ttu-id="8beab-105">作成した新しい CDC データベースは、SQL Server CDC に対して有効になります。このように有効にするには、ログインが `sysadmin` 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="8beab-105">When you create a new CDC database it is enabled for SQL Server CDC and this enablement requires a login that is a member of the `sysadmin` fixed-server role.</span></span>  
  
 <span data-ttu-id="8beab-106">Oracle CDC インスタンスの作成ウィザードを開始したユーザーが `sysadmin` 固定サーバー ロールのメンバーではない場合、[SQL Server への接続] ダイアログ ボックスが表示され、SQL Server CDC に対してデータベースを有効にするタスクを実行するために sysadmin ロールのメンバーの資格情報を入力するよう求められます。</span><span class="sxs-lookup"><span data-stu-id="8beab-106">When a user that starts the Create an Oracle CDC Instance wizard is not a member of the `sysadmin` fixed-server role, the Connect to SQL Server dialog box opens and requests the credentials for a member of the sysadmin role to carry out the Enable the database for SQL Server CDC task.</span></span> <span data-ttu-id="8beab-107">CDC データベースが作成されると、 `sysadmin` ログインは破棄され、Oracle デザイナー コンソールが入力されたときに使用された元の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインで作業が再開されます。</span><span class="sxs-lookup"><span data-stu-id="8beab-107">When the CDC database is created, the `sysadmin` login is discarded and work resumes with the original [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login used when the Oracle Designer Console was entered.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8beab-108">SQL Server CDC に対してデータベースを有効にするタスク以外のタスクでは、新しいインスタンス ウィザードの実行に使用された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインに、 `dbcreator` 固定サーバー ロールと、MSXDBCDC データベースに対する UPDATE 権限が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8beab-108">For tasks other than Enable the database for SQL Server CDC of, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login used for running the New Instance Wizard must have the `dbcreator` fixed-server role and UPDATE permissions on the MSXDBCDC database.</span></span>  
  
 <span data-ttu-id="8beab-109">[SQL Server への接続] ダイアログ ボックスへのデータの入力については、「 [SQL Server Connection for Instance Creation](sql-server-connection-for-instance-creation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8beab-109">For information on entering the data in the Connect to SQL Server dialog box, see [SQL Server Connection for Instance Creation](sql-server-connection-for-instance-creation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="8beab-110">オプション</span><span class="sxs-lookup"><span data-stu-id="8beab-110">Options</span></span>  
 <span data-ttu-id="8beab-111">**[Oracle CDC インスタンス]**</span><span class="sxs-lookup"><span data-stu-id="8beab-111">**Oracle CDC Instance**</span></span>  
 <span data-ttu-id="8beab-112">作成する CDC インスタンスに関する次の情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="8beab-112">Type the following information about the CDC instance you are creating.</span></span>  
  
-   <span data-ttu-id="8beab-113">**[名前]** : 新しいサービスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="8beab-113">**Name**: Type a name for the new service.</span></span> <span data-ttu-id="8beab-114">この名前は、新しい変更データベースの名前にもなります。</span><span class="sxs-lookup"><span data-stu-id="8beab-114">This will also be the name of the new Change database.</span></span>  
  
-   <span data-ttu-id="8beab-115">**[説明]** : 新しいインスタンスを識別するのに役立つ説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="8beab-115">**Description**: Type a description for the new instance to help you identify it.</span></span> <span data-ttu-id="8beab-116">これは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="8beab-116">This is optional.</span></span>  
  
 <span data-ttu-id="8beab-117">**[SQL Server 変更データベース]**</span><span class="sxs-lookup"><span data-stu-id="8beab-117">**SQL Server Change Database**</span></span>  
 <span data-ttu-id="8beab-118">このセクションは、データベースの作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="8beab-118">This section is used to create the database.</span></span>  
  
1.  <span data-ttu-id="8beab-119">**[データベースの変更]** : 新しい変更データベースの名前です。</span><span class="sxs-lookup"><span data-stu-id="8beab-119">**Change Database**: The name of the new Change database.</span></span> <span data-ttu-id="8beab-120">データベースの名前は、インスタンスに指定した名前と同じです。</span><span class="sxs-lookup"><span data-stu-id="8beab-120">The name of the database is the same as the name that you gave to the instance.</span></span> <span data-ttu-id="8beab-121">この読み取り専用フィールドには、データベースへの完全なパスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8beab-121">This read-only field displays the full path to the database.</span></span>  
  
2.  <span data-ttu-id="8beab-122">**[データベースの作成]** : データベースを作成するには、 **[データベースの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8beab-122">**Create Database**: Click **Create Database** to create the database.</span></span>  
  
     <span data-ttu-id="8beab-123">データベースを作成するには、ログインに `sysasmin` サーバー ロールが必要です。</span><span class="sxs-lookup"><span data-stu-id="8beab-123">To create the database, the login must have the `sysasmin` server role.</span></span> <span data-ttu-id="8beab-124">詳細については、上記のセキュリティに関する注意を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8beab-124">See the security note above for more information.</span></span>  
  
     <span data-ttu-id="8beab-125">データベースを作成したら、 **[次へ]** をクリックして「 [Connect to an Oracle Source Database](connect-to-an-oracle-source-database.md)」に進みます。</span><span class="sxs-lookup"><span data-stu-id="8beab-125">After you create the database, you can click **Next** to [Connect to an Oracle Source Database](connect-to-an-oracle-source-database.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8beab-126">参照</span><span class="sxs-lookup"><span data-stu-id="8beab-126">See Also</span></span>  
 <span data-ttu-id="8beab-127">[SQL Server 変更データベース インスタンスを作成する方法](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="8beab-127">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 [<span data-ttu-id="8beab-128">Oracle CDC Service</span><span class="sxs-lookup"><span data-stu-id="8beab-128">The Oracle CDC Service</span></span>](the-oracle-cdc-service.md)  
  
  
