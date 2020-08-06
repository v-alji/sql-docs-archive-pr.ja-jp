---
title: マスターデータサービス | のデータベースと Web サイトを設定します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.general.f1
ms.assetid: d50863e7-50d9-4ab8-aabb-fd68e2d132a1
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: da797bc6f9838a2baab6cc440cc7d778a7a6e186
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645712"
---
# <a name="set-up-the-database-and-website-for-master-data-services"></a><span data-ttu-id="ddc7d-102">マスター データ サービスのデータベースと Web サイトの設定</span><span class="sxs-lookup"><span data-stu-id="ddc7d-102">Set up the Database and Website for Master Data Services</span></span>
  <span data-ttu-id="ddc7d-103">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] を使って、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] のデータベースと Web サイトを設定する (MDS)</span><span class="sxs-lookup"><span data-stu-id="ddc7d-103">Use the [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] to set up the database and website for [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS)</span></span>  
  
 <span data-ttu-id="ddc7d-104">データベースと Web サイトを設定するには、次のタスクを実行してください。</span><span class="sxs-lookup"><span data-stu-id="ddc7d-104">To set up the database and website, complete the following tasks.</span></span>  
  
1.  <span data-ttu-id="ddc7d-105">**の** [データベース構成] [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]ページで、データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="ddc7d-105">Create a database using the **Database Configuration** page in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].</span></span>  
  
     <span data-ttu-id="ddc7d-106">詳細については、「データベースの構成」ページを参照して[&#40;マスターデータサービス構成マネージャー&#41;](../../2014/master-data-services/database-configuration-page-master-data-services-configuration-manager.md)と[データベースの作成ウィザード &#40;マスターデータサービス構成マネージャー ](../../2014/master-data-services/create-database-wizard-master-data-services-configuration-manager.md)&#41;を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddc7d-106">For information, see [Database Configuration Page &#40;Master Data Services Configuration Manager&#41;](../../2014/master-data-services/database-configuration-page-master-data-services-configuration-manager.md) and [Create Database Wizard &#40;Master Data Services Configuration Manager&#41;](../../2014/master-data-services/create-database-wizard-master-data-services-configuration-manager.md).</span></span>  
  
2.  <span data-ttu-id="ddc7d-107">**の** [Web 構成] [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]ページで、新しい Web サイトを作成するか、既定の Web サイトを選ぶか、別の既存の Web サイトを選びます。</span><span class="sxs-lookup"><span data-stu-id="ddc7d-107">Create a new website, select the default website, or select another existing website, using the **Web Configuration** page in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].</span></span> <span data-ttu-id="ddc7d-108">その後、MDS データベースを、選んだ Web アプリケーションや作成した Web アプリケーションに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="ddc7d-108">Then associate the MDS database with the web application you select or create.</span></span>  
  
     <span data-ttu-id="ddc7d-109">詳細については、「 [Web 構成ページ &#40;マスターデータサービス構成マネージャー&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) 」と「web[サイトの作成] ダイアログボックス &#40;マスターデータサービス構成マネージャー ](../../2014/master-data-services/create-website-dialog-box-master-data-services-configuration-manager.md)&#41;」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddc7d-109">For information, see [Web Configuration Page &#40;Master Data Services Configuration Manager&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) and [Create Website Dialog Box &#40;Master Data Services Configuration Manager&#41;](../../2014/master-data-services/create-website-dialog-box-master-data-services-configuration-manager.md).</span></span>  
  
3.  <span data-ttu-id="ddc7d-110">(省略可能) **の** [Web 構成] [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]ページで、Data Quality Services との統合を有効にします。</span><span class="sxs-lookup"><span data-stu-id="ddc7d-110">(Optional) Enable integration with Data Quality Services using the **Web Configuration** page in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].</span></span>  
  
     <span data-ttu-id="ddc7d-111">詳細については、「 [Web 構成ページ &#40;マスターデータサービス構成マネージャー&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) 」と「[マスターデータサービスと Data Quality Services の統合を有効にする](install-windows/enable-data-quality-services-integration-with-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddc7d-111">For more information, see [Web Configuration Page &#40;Master Data Services Configuration Manager&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) and [Enable Data Quality Services Integration with Master Data Services](install-windows/enable-data-quality-services-integration-with-master-data-services.md).</span></span>  
  
 <span data-ttu-id="ddc7d-112">また、 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] を使って、MDS データベースに関連付けられている Web アプリケーションとサービスの設定値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ddc7d-112">You can also use [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] to specify settings for the web applications and services associated with the MDS database.</span></span> <span data-ttu-id="ddc7d-113">たとえば、データの読み込み頻度や検証メールの送信頻度を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ddc7d-113">For example, you can specify how frequently data is loaded or how often validation emails are sent.</span></span> <span data-ttu-id="ddc7d-114">詳細については、「[システム設定 &#40;マスター データ サービス&#41;](../../2014/master-data-services/system-settings-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddc7d-114">For more information, see [System Settings &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddc7d-115">参照</span><span class="sxs-lookup"><span data-stu-id="ddc7d-115">See Also</span></span>  
 <span data-ttu-id="ddc7d-116">[マスターデータサービスデータベース](../../2014/master-data-services/master-data-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="ddc7d-116">[Master Data Services Database](../../2014/master-data-services/master-data-services-database.md) </span></span>  
 [<span data-ttu-id="ddc7d-117">マスター データ マネージャー Web アプリケーション</span><span class="sxs-lookup"><span data-stu-id="ddc7d-117">Master Data Manager Web Application</span></span>](../../2014/master-data-services/master-data-manager-web-application.md)  
  
  
