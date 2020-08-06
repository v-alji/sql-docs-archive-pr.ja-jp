---
title: Master Data Services データベースと Web アプリケーションの関連付け | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: ccb25672-f71d-4135-b548-f50eb45d8fa5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 01afde6aea5065a51cb9e7ae5dc4151e9f1e9fc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713230"
---
# <a name="associate-a-master-data-services-database-and-web-application"></a><span data-ttu-id="6c4f4-102">Master Data Services データベースと Web アプリケーションの関連付け</span><span class="sxs-lookup"><span data-stu-id="6c4f4-102">Associate a Master Data Services Database and Web Application</span></span>
  <span data-ttu-id="6c4f4-103">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションを [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースに関連付け、Web 操作に使用するデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="6c4f4-103">Associate your [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application with a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database to specify the database to use for web operations.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6c4f4-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="6c4f4-104">Prerequisites</span></span>  
  
-   [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] <span data-ttu-id="6c4f4-105">がローカル コンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c4f4-105">must be installed on the local computer.</span></span> <span data-ttu-id="6c4f4-106">詳細については、「 [マスター データ サービスのインストール](install-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c4f4-106">For more information, see [Install Master Data Services](install-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="6c4f4-107">ローカルの [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションが存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c4f4-107">A local [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application must exist.</span></span> <span data-ttu-id="6c4f4-108">詳細については、「[マスター データ マネージャー Web アプリケーションを作成する方法 &#40;マスター データ サービス&#41;](create-a-master-data-manager-web-application-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c4f4-108">For more information, see [Create a Master Data Manager Web Application &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="6c4f4-109">ローカルまたはリモートの [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースのどちらかが存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c4f4-109">Either a local or remote [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database must exist.</span></span> <span data-ttu-id="6c4f4-110">詳細については、「 [マスター データ サービス データベースの作成](create-a-master-data-services-database.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6c4f4-110">For more information, see [Create a Master Data Services Database](create-a-master-data-services-database.md).</span></span>  
  
### <a name="to-associate-a-master-data-services-database-and-web-application"></a><span data-ttu-id="6c4f4-111">Master Data Services データベースと Web アプリケーションを関連付けるには</span><span class="sxs-lookup"><span data-stu-id="6c4f4-111">To associate a Master Data Services database and web application</span></span>  
  
1.  <span data-ttu-id="6c4f4-112">[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]を開きます。</span><span class="sxs-lookup"><span data-stu-id="6c4f4-112">Open [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
2.  <span data-ttu-id="6c4f4-113">左ペインで **[Web の構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6c4f4-113">In the left pane, click **Web Configuration**.</span></span>  
  
3.  <span data-ttu-id="6c4f4-114">**[Web の構成]** ページで、 **[Web アプリケーション]** の下の **[Web サイト]** ボックスの一覧から [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションを含む Web サイトを選択します。</span><span class="sxs-lookup"><span data-stu-id="6c4f4-114">On the **Web Configuration** page, under **Web application**, from the **Website** list, select the website that contains your [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span>  
  
4.  <span data-ttu-id="6c4f4-115">**[Web アプリケーション]** ボックスで、 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]をホストする Web アプリケーションを選択します。</span><span class="sxs-lookup"><span data-stu-id="6c4f4-115">In the **Web application** box, select the web application that hosts [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span></span>  
  
5.  <span data-ttu-id="6c4f4-116">**[アプリケーションとデータベースの関連付け]** で、 **[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6c4f4-116">Under **Associate Application with Database**, click **Select**.</span></span> <span data-ttu-id="6c4f4-117">**[データベースへの接続]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="6c4f4-117">The **Connect to Database** dialog box opens.</span></span>  
  
6.  <span data-ttu-id="6c4f4-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースをホストする [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] のインスタンスの接続情報を指定し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6c4f4-118">Specify connection information for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that hosts the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database, and click **Connect**.</span></span>  
  
7.  <span data-ttu-id="6c4f4-119">**[Master Data Services データベース]** ボックスの一覧から、Web アプリケーションに関連付けるデータベースを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6c4f4-119">From the **Master Data Services database** list, select the database you want to associate the web application with and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="6c4f4-120">**[アプリケーションとデータベースの関連付け]** で、インスタンスおよびデータベースの情報が正しいことを確認し、 **[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6c4f4-120">Under **Associate Application with Database**, verify that the instance and database information are correct, and then click **Apply**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="6c4f4-121">次の手順</span><span class="sxs-lookup"><span data-stu-id="6c4f4-121">Next Steps</span></span>  
  
-   <span data-ttu-id="6c4f4-122">Web アプリケーションが作成されると、プログラムによる [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web サービスへのアクセスが自動的に有効になります。</span><span class="sxs-lookup"><span data-stu-id="6c4f4-122">Programmatic access to [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web services is automatically enabled when the web application is created.</span></span> <span data-ttu-id="6c4f4-123">開発者がサービス メタデータにアクセスし、プログラムからプロキシ クラスを簡単に生成するには、メタデータ パブリッシュを有効にします。</span><span class="sxs-lookup"><span data-stu-id="6c4f4-123">To let developers access the service metadata to easily generate proxy classes for programmatic access, enable metadata publishing.</span></span> <span data-ttu-id="6c4f4-124">詳細については、「 [マスター データ マネージャー Web サービス プロキシ クラスの作成](../develop/create-master-data-manager-web-service-proxy-classes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c4f4-124">For more information, see [Create Master Data Manager Web Service Proxy Classes](../develop/create-master-data-manager-web-service-proxy-classes.md).</span></span>  
  
-   <span data-ttu-id="6c4f4-125">ユーザーおよびグループを [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]に追加します。</span><span class="sxs-lookup"><span data-stu-id="6c4f4-125">Add users and groups to [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span></span> <span data-ttu-id="6c4f4-126">どのユーザーまたはグループも [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]へのアクセス権が付与されていない場合は、 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] システム管理者の資格情報を使用して、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] を開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c4f4-126">If no users or groups have been granted access to [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], you must open [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] using the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] system administrator credentials.</span></span> <span data-ttu-id="6c4f4-127">詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../administrators-master-data-services.md)」および「[Users and Groups &#40;Master Data Services&#41; (ユーザーおよびグループ &#40;Master Data Services&#41;)](../users-and-groups-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c4f4-127">For more information, see [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md) and [Users and Groups &#40;Master Data Services&#41;](../users-and-groups-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c4f4-128">参照</span><span class="sxs-lookup"><span data-stu-id="6c4f4-128">See Also</span></span>  
 <span data-ttu-id="6c4f4-129">[マスターデータサービスのインストール](install-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="6c4f4-129">[Install Master Data Services](install-master-data-services.md) </span></span>  
 <span data-ttu-id="6c4f4-130">[[Web の構成] ページ &#40;マスター データ サービス構成マネージャー&#41;](../web-configuration-page-master-data-services-configuration-manager.md)</span><span class="sxs-lookup"><span data-stu-id="6c4f4-130">[Web Configuration Page &#40;Master Data Services Configuration Manager&#41;](../web-configuration-page-master-data-services-configuration-manager.md)</span></span>  
  
  
