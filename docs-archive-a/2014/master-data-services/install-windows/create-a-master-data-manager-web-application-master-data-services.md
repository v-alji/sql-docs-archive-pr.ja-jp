---
title: マスター データ マネージャー Web アプリケーションの作成 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 241d46d7-8008-47f6-bebd-0dfff1cc856a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fd81188b499850397aa8ffd2e40cfcb91c648288
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633177"
---
# <a name="create-a-master-data-manager-web-application-master-data-services"></a><span data-ttu-id="60f91-102">マスター データ マネージャー Web アプリケーションの作成 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="60f91-102">Create a Master Data Manager Web Application (Master Data Services)</span></span>
  <span data-ttu-id="60f91-103">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションは、マスター データを操作するためのユーザー用インターフェイスと、MDS を構成および管理するための管理者用インターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="60f91-103">The [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application provides an interface for users to work with master data and for administrators to configure and administer MDS.</span></span>  
  
 <span data-ttu-id="60f91-104">Web アプリケーションは、必ず Web サイトに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="60f91-104">A web application must always be contained by a website.</span></span> <span data-ttu-id="60f91-105">Web アプリケーションを作成するには、次のいずれかを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="60f91-105">To create a web application, you must either:</span></span>  
  
-   <span data-ttu-id="60f91-106">既定の Web サイトを使用し、Web アプリケーションを作成する。</span><span class="sxs-lookup"><span data-stu-id="60f91-106">Use the Default website and then create the web application,</span></span>  
  
-   <span data-ttu-id="60f91-107">既存の Web サイトを使用し、Web アプリケーションを作成する。</span><span class="sxs-lookup"><span data-stu-id="60f91-107">Use an existing website and then create the web application, or</span></span>  
  
-   <span data-ttu-id="60f91-108">新しい Web サイトを作成する (これにより Web アプリケーションが自動的に作成されます)。</span><span class="sxs-lookup"><span data-stu-id="60f91-108">Create a new website, which automatically creates a web application.</span></span>  
  
 <span data-ttu-id="60f91-109">Web アプリケーションを作成したら、それを [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="60f91-109">After you create the web application, you associate it with the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="60f91-110">前提条件</span><span class="sxs-lookup"><span data-stu-id="60f91-110">Prerequisites</span></span>  
  
-   <span data-ttu-id="60f91-111">データベースをホストするコンピューターの要件の詳細については、「[Web アプリケーションの要件 &#40;マスター データ サービス&#41;](web-application-requirements-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60f91-111">For information about the requirements for the computer that hosts the web application, see [Web Application Requirements &#40;Master Data Services&#41;](web-application-requirements-master-data-services.md).</span></span>  
  
## <a name="to-create-a-master-data-manager-web-application-in-a-new-website"></a><span data-ttu-id="60f91-112">新しい Web サイトにマスター データ マネージャー Web アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="60f91-112">To create a Master Data Manager web application in a new website</span></span>  
 <span data-ttu-id="60f91-113">新しい Web サイトを作成した場合、ルート Web アプリケーションは [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="60f91-113">When you create a new website, the root web application is the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span> <span data-ttu-id="60f91-114">また、作成された Web アプリケーションは新しいアプリケーション プールに追加されます。</span><span class="sxs-lookup"><span data-stu-id="60f91-114">The web application is also added to a new application pool.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="60f91-115">この手順を使用した場合、 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションの仮想パスと別名を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="60f91-115">If you follow this procedure, you cannot specify a virtual path and alias of the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span> <span data-ttu-id="60f91-116">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]の仮想パスと別名を指定する場合は、 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションとして構成されていない既存の Web サイトに Web アプリケーションを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="60f91-116">If you want to specify a virtual path and alias for [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], you must create a web application in an existing website that is not already configured as a [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span>  
  
 <span data-ttu-id="60f91-117">また [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] では、HTTP バインドのみを含むサイトの作成もサポートされます。</span><span class="sxs-lookup"><span data-stu-id="60f91-117">Additionally, [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] supports creating sites with HTTP bindings only.</span></span> <span data-ttu-id="60f91-118">HTTPS バインドを追加するには、 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] で新しいサイトとアプリケーションを作成します。詳細については、「 [マスター データ マネージャー Web アプリケーションのセキュリティ保護](secure-a-master-data-manager-web-application.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60f91-118">To add an HTTPS binding, create a new site and application in [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] and then see [Secure a Master Data Manager Web Application](secure-a-master-data-manager-web-application.md) for more information.</span></span>  
  
#### <a name="to-create-a-master-data-manager-web-application-in-a-new-website"></a><span data-ttu-id="60f91-119">新しい Web サイトにマスター データ マネージャー Web アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="60f91-119">To create a Master Data Manager web application in a new website</span></span>  
  
1.  <span data-ttu-id="60f91-120">[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]を開きます。</span><span class="sxs-lookup"><span data-stu-id="60f91-120">Open [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
2.  <span data-ttu-id="60f91-121">左ペインで **[Web の構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="60f91-121">In the left pane, click **Web Configuration**.</span></span>  
  
3.  <span data-ttu-id="60f91-122">**[Web の構成]** ページにある Web サイトの一覧で、 **[新規 Web サイトの作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="60f91-122">On the **Web Configuration** page, in the Website list, select **Create new website**.</span></span>  
  
4.  <span data-ttu-id="60f91-123">**[Web サイトの作成]** ダイアログ ボックスで、新しい Web サイトの情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="60f91-123">On the **Create Website** dialog box, specify information for a new website.</span></span> <span data-ttu-id="60f91-124">ダイアログ ボックスのユーザー インターフェイス (UI) オプションの詳細については、「[[Web サイトの作成] ダイアログ ボックス &#40;マスター データ サービス構成マネージャー&#41;](../create-website-dialog-box-master-data-services-configuration-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60f91-124">For more information about the user interface (UI) options in the dialog box, see [Create Website Dialog Box &#40;Master Data Services Configuration Manager&#41;](../create-website-dialog-box-master-data-services-configuration-manager.md).</span></span>  
  
5.  <span data-ttu-id="60f91-125">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="60f91-125">Click **OK**.</span></span>  
  
## <a name="to-create-a-master-data-manager-web-application-in-an-existing-website"></a><span data-ttu-id="60f91-126">既存の Web サイトにマスター データ マネージャー Web アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="60f91-126">To create a Master Data Manager web application in an existing website</span></span>  
 <span data-ttu-id="60f91-127">既存の Web サイトに Web アプリケーションを作成する場合は、Web アプリケーションの仮想パスと別名を選択できます。</span><span class="sxs-lookup"><span data-stu-id="60f91-127">When you create a web application in an existing website, you can choose the virtual path and alias of the web application.</span></span> <span data-ttu-id="60f91-128">作成された Web アプリケーションは新しいアプリケーション プールに追加されます。</span><span class="sxs-lookup"><span data-stu-id="60f91-128">The web application is added to a new application pool.</span></span>  
  
#### <a name="to-create-a-master-data-manager-web-application-in-an-existing-website"></a><span data-ttu-id="60f91-129">既存の Web サイトにマスター データ マネージャー Web アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="60f91-129">To create a Master Data Manager web application in an existing website</span></span>  
  
1.  <span data-ttu-id="60f91-130">[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]を開きます。</span><span class="sxs-lookup"><span data-stu-id="60f91-130">Open [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
2.  <span data-ttu-id="60f91-131">左ペインで **[Web の構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="60f91-131">In the left pane, click **Web Configuration**.</span></span>  
  
3.  <span data-ttu-id="60f91-132">**[Web の構成]** ページで、 **[Web サイト]** ボックスの一覧から、 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションを作成する Web サイトを選択します。</span><span class="sxs-lookup"><span data-stu-id="60f91-132">On the **Web Configuration** page, from the **Website** list, select the website in which you want to create the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span>  
  
4.  <span data-ttu-id="60f91-133">**[アプリケーションの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="60f91-133">Click **Create Application**.</span></span>  
  
5.  <span data-ttu-id="60f91-134">**[Web アプリケーションの作成]** ダイアログ ボックスで、新しい Web アプリケーションの情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="60f91-134">On the **Create Web Application** dialog box, specify information for a new web application.</span></span> <span data-ttu-id="60f91-135">ウィザードのユーザー インターフェイス (UI) オプションの詳細については、「[[Web アプリケーションの作成] ダイアログ ボックス &#40;マスター データ サービス構成マネージャー&#41;](../create-web-application-dialog-box-master-data-services-configuration-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60f91-135">For more information about the user interface (UI) options in the dialog box, see [Create Web Application Dialog Box &#40;Master Data Services Configuration Manager&#41;](../create-web-application-dialog-box-master-data-services-configuration-manager.md).</span></span>  
  
6.  <span data-ttu-id="60f91-136">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="60f91-136">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="60f91-137">次の手順</span><span class="sxs-lookup"><span data-stu-id="60f91-137">Next Steps</span></span>  
  
-   <span data-ttu-id="60f91-138">Web アプリケーションを [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="60f91-138">Associate the web application with a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="60f91-139">詳細については、「 [Master Data Services データベースと Web アプリケーションの関連付け](associate-a-master-data-services-database-and-web-application.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60f91-139">For more information, see [Associate a Master Data Services Database and Web Application](associate-a-master-data-services-database-and-web-application.md).</span></span>  
  
-   <span data-ttu-id="60f91-140">SSL (Secure Sockets Layer) を使用してコンテンツを暗号化する必要がある場合は、 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションをホストする Web サイトで HTTPS バインドを使用するように構成します。</span><span class="sxs-lookup"><span data-stu-id="60f91-140">Optionally, configure the website that hosts the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application to use an HTTPS binding if you want to encrypt content by using Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="60f91-141">Web サーバー用にサーバー証明書を構成し、サイト用に HTTP バインドと SSL 設定を構成するには、IIS マネージャーなどのインターネット インフォメーション サービス (IIS) ツールを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="60f91-141">You must use an Internet Information Services (IIS) tool, such as IIS Manager, to configure the server certificate for the web server, and to configure an HTTPS binding and the SSL settings for the site.</span></span> <span data-ttu-id="60f91-142">詳細については、「 [マスター データ マネージャー Web アプリケーションのセキュリティ保護](secure-a-master-data-manager-web-application.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60f91-142">For more information, see [Secure a Master Data Manager Web Application](secure-a-master-data-manager-web-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60f91-143">参照</span><span class="sxs-lookup"><span data-stu-id="60f91-143">See Also</span></span>  
 [<span data-ttu-id="60f91-144">マスター データ サービスのインストール</span><span class="sxs-lookup"><span data-stu-id="60f91-144">Install Master Data Services</span></span>](install-master-data-services.md)  
  
  
