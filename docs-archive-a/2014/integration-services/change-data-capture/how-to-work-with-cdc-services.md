---
title: CDC Service の操作方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: db5c718a-6e7f-48ec-82a3-9d5b131716e5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7cfb5a0ed0e9ded8e0be118deb3c819626448896
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639600"
---
# <a name="how-to-work-with-cdc-services"></a><span data-ttu-id="c79e1-102">CDC Service の操作方法</span><span class="sxs-lookup"><span data-stu-id="c79e1-102">How to Work with CDC Services</span></span>
  <span data-ttu-id="c79e1-103">この手順では、CDC Service 構成コンソールを使用して、Oracle CDC Service の操作用に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを準備し、新しい CDC サービスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c79e1-103">This procedure describes how to use the CDC Service Configuration Console to prepare a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to work with Oracle CDC Services and to create a new CDC service.</span></span>  
  
### <a name="to-work-with-cdc-services"></a><span data-ttu-id="c79e1-104">CDC サービスを操作するには</span><span class="sxs-lookup"><span data-stu-id="c79e1-104">To work with CDC services</span></span>  
  
1.  <span data-ttu-id="c79e1-105">**[スタート]** メニューの **[CDC Service Configuration for Oracle]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c79e1-105">From the **Start** menu, select the **CDC Service Configuration for Oracle**.</span></span>  
  
2.  <span data-ttu-id="c79e1-106">左ペインで **[ローカルの CDC Service]** (ルート レベル) を選択します。</span><span class="sxs-lookup"><span data-stu-id="c79e1-106">From the left pane, select **Local CDC Services** (the root level).</span></span>  
  
3.  <span data-ttu-id="c79e1-107">次のいずれか、または両方のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="c79e1-107">You carry out the one or both of the following tasks:</span></span>  
  
    -   <span data-ttu-id="c79e1-108">**[SQL Server の準備]**</span><span class="sxs-lookup"><span data-stu-id="c79e1-108">**Prepare SQL Server**</span></span>  
  
         <span data-ttu-id="c79e1-109">CDC Service 構成コンソールの右側にある **[アクション]** ペインで、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="c79e1-109">Select this option from the **Actions** pane on the right side of the CDC Service Configuration Console.</span></span>  
  
         <span data-ttu-id="c79e1-110">**[ローカルの CDC Service]** を右クリックして **[SQLServer の準備]** をクリックすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c79e1-110">You can also right-click **Local CDC Services** and select **Prepare SQL Server**.</span></span>  
  
         <span data-ttu-id="c79e1-111">[Oracle CDC 用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの準備] ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c79e1-111">The Preparing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instance for Oracle CDC dialog box opens.</span></span>  
  
         <span data-ttu-id="c79e1-112">Oracle CDC サービス用に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを準備するには、ログインが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固定サーバー ロールを持つ `dbcreator` ログインを持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c79e1-112">To prepare the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance for Oracle CDC services, the login must have a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login with the `dbcreator` fixed server role.</span></span> <span data-ttu-id="c79e1-113">このログインは、MSXDBCDC データベースの作成に使用されます。このデータベースは、Oracle CDC Service を追加する際、および後で Oracle CDC インスタンスを追加する際に必要です。</span><span class="sxs-lookup"><span data-stu-id="c79e1-113">This login is used to create the MSXDBCDC database that is required for adding Oracle CDC Services and, later on, Oracle CDC Instances.</span></span>  
  
         <span data-ttu-id="c79e1-114">このダイアログ ボックスの使用方法の詳細については、「 [Prepare SQL Server for CDC](prepare-sql-server-for-cdc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c79e1-114">For information on how to use this dialog box, see [Prepare SQL Server for CDC](prepare-sql-server-for-cdc.md).</span></span> <span data-ttu-id="c79e1-115">CDC 用の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを有効にする方法の詳細については、「 [CDC 用に SQL Server を準備する方法](how-to-prepare-sql-server-for-cdc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c79e1-115">For information on how to enable a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance for CDC, see [How to Prepare SQL Server for CDC](how-to-prepare-sql-server-for-cdc.md).</span></span>  
  
    -   <span data-ttu-id="c79e1-116">**[新しい CDC サービスの作成]**</span><span class="sxs-lookup"><span data-stu-id="c79e1-116">**Create a new CDC service**</span></span>  
  
         <span data-ttu-id="c79e1-117">CDC Service 構成コンソールの右側にある **[アクション]** ペインで **[新しいサービス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c79e1-117">Click **New Service** from the **Actions** pane on the right side of the CDC Service Configuration Console.</span></span>  
  
         <span data-ttu-id="c79e1-118">**[ローカルの CDC Service]** を右クリックして **[新しいサービス]** をクリックすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c79e1-118">You can also right-Click **Local CDC Services** and select **New Service**.</span></span>  
  
         <span data-ttu-id="c79e1-119">[新しい Oracle CDC Service] ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c79e1-119">The New Oracle CDC Service dialog box opens.</span></span>  
  
         <span data-ttu-id="c79e1-120">このダイアログ ボックスの使用方法の詳細については、「 [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c79e1-120">For information on how to use this dialog box, see [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md).</span></span> <span data-ttu-id="c79e1-121">CDC サービスを作成または編集する方法の詳細については、「 [CDC Service を作成および編集する方法](how-to-create-and-edit-a-cdc-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c79e1-121">For information on how to create or edit a CDC service, see [How to Create and Edit a CDC Service](how-to-create-and-edit-a-cdc-service.md).</span></span>  
  
         <span data-ttu-id="c79e1-122">Oracle CDC Service によって使用される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインは、 `public` 固定サーバー ロールのメンバーであることだけが必要です。その他の権限は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="c79e1-122">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login used by the Oracle CDC Service only needs to be a member of the `public` fixed-server role, no other privileges are needed.</span></span> <span data-ttu-id="c79e1-123">ただし、Oracle CDC Service を作成するには、ログインが MSXDBCDC データベースに対する書き込み権限を持っている必要があります。たとえば、ログインに **db_owner** データベース ロールが割り当てられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c79e1-123">However, to create the Oracle CDC Service, the login must have write permission to the MSXDBCDC database, for example the **db_owner** database role must be assigned to the login.</span></span> <span data-ttu-id="c79e1-124">MSXDBDCDC データベースに対する書き込み権限を持たないログインが新しい Oracle CDC インスタンスの作成を試みると、エラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c79e1-124">When a login without write permission to the MSXDBDCDC database attempts to create a new Oracle CDC instance an error message is displayed.</span></span> <span data-ttu-id="c79e1-125">そのダイアログ ボックスで **[OK]** をクリックします。[SQL Server への接続] ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c79e1-125">Click **OK** in that dialog box to display the Connect to SQL Server dialog box.</span></span>  
  
         <span data-ttu-id="c79e1-126">**db_owner** データベース ロールなど、MSXDBCDC データベースに対する書き込み権限を持つログインの資格情報を入力する方法については、「 [Oracle CDC Service の作成と編集](create-and-edit-an-oracle-cdc-service.md) 」および「 [SQL Server への接続](connection-to-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c79e1-126">For information on how to enter the credentials for a login that has write permission to the MSXDBCDC database, such the **db_owner** database role, see [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md) and [Connection to SQL Server](connection-to-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c79e1-127">参照</span><span class="sxs-lookup"><span data-stu-id="c79e1-127">See Also</span></span>  
 [<span data-ttu-id="c79e1-128">CDC Service の操作</span><span class="sxs-lookup"><span data-stu-id="c79e1-128">Work with CDC Services</span></span>](work-with-cdc-services.md)  
  
  
