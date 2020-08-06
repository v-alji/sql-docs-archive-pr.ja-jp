---
title: データベース エンジン アクセスのファイル システム アクセス許可の構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- file system permissions
- service account [SQL Server], file system permissions
- permissions [SQL Server], file system
ms.assetid: 78bba43c-4edb-4216-84ac-d6246ae5546d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1d9abbd095f2d5be7415ed28a17fb710ff8ab504
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645856"
---
# <a name="configure-file-system-permissions-for-database-engine-access"></a><span data-ttu-id="49a09-102">データベース エンジン アクセスのファイル システム権限の構成</span><span class="sxs-lookup"><span data-stu-id="49a09-102">Configure File System Permissions for Database Engine Access</span></span>
  <span data-ttu-id="49a09-103">このトピックでは [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]にデータベース ファイルの格納場所へのファイル システム アクセス権を付与する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="49a09-103">This topic describes how to grant the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], file system access to the location where database files are stored.</span></span> <span data-ttu-id="49a09-104">[!INCLUDE[ssDE](../../includes/ssde-md.md)] サービスには、データベース ファイルが格納されているファイル フォルダーにアクセスするための Windows ファイル システム権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="49a09-104">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] service must have permission of the Windows file system to access the file folder where database files are stored.</span></span> <span data-ttu-id="49a09-105">既定の場所への権限は、セットアップ中に構成されます。</span><span class="sxs-lookup"><span data-stu-id="49a09-105">Permission to the default location is configured during setup.</span></span> <span data-ttu-id="49a09-106">別の場所にデータベース ファイルを配置した場合は、次の手順に従って、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] にその場所へのフル コントロール権限を付与する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="49a09-106">If you place your database files in a different location, you might need to follow these steps to grant the [!INCLUDE[ssDE](../../includes/ssde-md.md)] the full control permission to that location.</span></span>  
  
 <span data-ttu-id="49a09-107">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降では、権限は各サービスのサービスごとの SID に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="49a09-107">Beginning with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] permissions are assigned to the per-service SID for each of its services.</span></span> <span data-ttu-id="49a09-108">このシステムはサービスの分離と多層防御を提供するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="49a09-108">This system helps provide service isolation and defense in depth.</span></span> <span data-ttu-id="49a09-109">サービスごとの SID はサービス名から取得され、各サービスに固有です。</span><span class="sxs-lookup"><span data-stu-id="49a09-109">The per-service SID is derived from the service name and is unique to each service.</span></span> <span data-ttu-id="49a09-110">トピック「 [Windows サービス アカウントと権限の構成](configure-windows-service-accounts-and-permissions.md) 」にはサービスごとの SID についての記載があり、「 **Windows の特権および権限**」で名前が指定されています。</span><span class="sxs-lookup"><span data-stu-id="49a09-110">The topic [Configure Windows Service Accounts and Permissions](configure-windows-service-accounts-and-permissions.md) describes the per-service SID and provides the names in the section **Windows Privileges and Rights**.</span></span> <span data-ttu-id="49a09-111">サービスごとの SID に対して、ファイルの場所へのアクセス権を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="49a09-111">It is the per-service SID that must be assigned the access permission on the file location.</span></span>  
  
## <a name="to-grant-file-system-permission-to-the-per-service-sid"></a><span data-ttu-id="49a09-112">サービスごとの SID にファイル システム権限を付与するには</span><span class="sxs-lookup"><span data-stu-id="49a09-112">To Grant File System Permission to the Per-service SID</span></span>  
  
1.  <span data-ttu-id="49a09-113">エクスプローラーを使用して、データベース ファイルが格納されているファイル システムの場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="49a09-113">Using Windows Explorer, navigate to the file system location where the database files are stored.</span></span> <span data-ttu-id="49a09-114">ファイル システム フォルダーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49a09-114">Right-click the file system folder, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="49a09-115">**[セキュリティ]** タブで **[編集]** をクリックし、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49a09-115">On the **Security** tab, click **Edit**, and then **Add**.</span></span>  
  
3.  <span data-ttu-id="49a09-116">**[ユーザー、コンピューター、サービス アカウント、またはグループの選択]** ダイアログ ボックスで、場所の一覧の上部にある **[場所]** をクリックし、コンピューター名を選択して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49a09-116">In the **Select Users, Computer, Service Account, or Groups** dialog box, click **Locations**, at the top of the location list, select your computer name, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="49a09-117">**[選択するオブジェクト名を入力**してください] ボックスに、オンラインブックのトピック「 **Windows サービスアカウントと権限の構成**」に記載されているサービスごとの SID の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="49a09-117">In the **Enter the object names to select** box, type the name of the per-service SID listed in the Books Online topic **Configure Windows Service Accounts and Permissions**.</span></span> <span data-ttu-id="49a09-118">(サービスごとの SID について [!INCLUDE[ssDE](../../includes/ssde-md.md)] は、既定のインスタンスの場合は**nt servicemssqlserver** 、名前付きインスタンスの場合は**nt Service\ MSSQL $ InstanceName**を使用します。)</span><span class="sxs-lookup"><span data-stu-id="49a09-118">(For the [!INCLUDE[ssDE](../../includes/ssde-md.md)] per service SID, use **NT SERVICE\MSSQLSERVER** for a default instance, or **NT SERVICE\MSSQL$InstanceName** for a named instance.)</span></span>  
  
5.  <span data-ttu-id="49a09-119">**[名前の確認]** をクリックして、このエントリを検証します。</span><span class="sxs-lookup"><span data-stu-id="49a09-119">Click **Check Names** to validate the entry.</span></span> <span data-ttu-id="49a09-120">検証は多くの場合に失敗し、名前が見つからないことが示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="49a09-120">The validation often fails, and might advise you that the name was not found.</span></span> <span data-ttu-id="49a09-121">**[OK]** をクリックすると、 **[複数の名前が見つかりました]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="49a09-121">When you click **OK**, a **Multiple Names Found** dialog box appears.</span></span>  
  
6.  <span data-ttu-id="49a09-122">ここで、サービスごとの SID ( **MSSQLSERVER**または**NT service\ MSSQL $ InstanceName**) を選択し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49a09-122">Now select the per-service SID, either **MSSQLSERVER** or **NT SERVICE\MSSQL$InstanceName**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="49a09-123">もう一度 [ **OK** ] をクリックして、[**アクセス許可**] ダイアログボックスに戻ります。</span><span class="sxs-lookup"><span data-stu-id="49a09-123">Click **OK** again to return to the **Permissions** dialog box.</span></span>  
  
8.  <span data-ttu-id="49a09-124">[**グループ名またはユーザー**名] ボックスで、サービスごとの SID を選択し、[**のアクセス許可** \<name> ] ボックスで [**フルコントロール**] の [**許可する**] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="49a09-124">In the **Group or user** names box, select the per-service SID, and then in the **Permissions for** \<name> box, select the **Allow** check box for **Full control**.</span></span>  
  
9. <span data-ttu-id="49a09-125">**[適用]** をクリックし、 **[OK]** を 2 回クリックして終了します。</span><span class="sxs-lookup"><span data-stu-id="49a09-125">Click **Apply**, and then click **OK** twice to exit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49a09-126">参照</span><span class="sxs-lookup"><span data-stu-id="49a09-126">See Also</span></span>  
 <span data-ttu-id="49a09-127">[データベース エンジン サービスの管理](manage-the-database-engine-services.md) </span><span class="sxs-lookup"><span data-stu-id="49a09-127">[Manage the Database Engine Services](manage-the-database-engine-services.md) </span></span>  
 <span data-ttu-id="49a09-128">[システム データベースの移動](../../relational-databases/databases/system-databases.md) </span><span class="sxs-lookup"><span data-stu-id="49a09-128">[Move System Databases](../../relational-databases/databases/system-databases.md) </span></span>  
 [<span data-ttu-id="49a09-129">ユーザー データベースの移動</span><span class="sxs-lookup"><span data-stu-id="49a09-129">Move User Databases</span></span>](../../relational-databases/databases/move-user-databases.md)  
  
  
