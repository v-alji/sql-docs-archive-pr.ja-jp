---
title: マスター データ サービス データベースの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 8373bb35-f0f9-4c3c-a53c-dfaa2ce567ac
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9ee90ac5d02489da3b411b12389e949ff3136287
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633176"
---
# <a name="create-a-master-data-services-database"></a><span data-ttu-id="eaad9-102">マスター データ サービス データベースの作成</span><span class="sxs-lookup"><span data-stu-id="eaad9-102">Create a Master Data Services Database</span></span>
  <span data-ttu-id="eaad9-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web アプリケーションと [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web サービスをサポートする新しいデータベースが必要な場合は、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="eaad9-103">Create a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database when you need a new database to support the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application and [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web service.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="eaad9-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="eaad9-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="eaad9-105">データベースをホストするコンピューターの要件の詳細については、「[データベース要件 &#40;マスター データ サービス&#41;](database-requirements-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eaad9-105">For information about the requirements for the computer that hosts the database, see [Database Requirements &#40;Master Data Services&#41;](database-requirements-master-data-services.md).</span></span>  
  
### <a name="to-create-a-master-data-services-database"></a><span data-ttu-id="eaad9-106">Master Data Services データベースを作成するには</span><span class="sxs-lookup"><span data-stu-id="eaad9-106">To create a Master Data Services database</span></span>  
  
1.  <span data-ttu-id="eaad9-107">[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]を開きます。</span><span class="sxs-lookup"><span data-stu-id="eaad9-107">Open [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
2.  <span data-ttu-id="eaad9-108">左ペインで **[データベース構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eaad9-108">In the left pane, click **Database Configuration**.</span></span>  
  
3.  <span data-ttu-id="eaad9-109">**[データベース構成]** ページで **[データベースの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eaad9-109">On the **Database Configuration** page, click **Create Database**.</span></span>  
  
4.  <span data-ttu-id="eaad9-110">データベースを作成および構成する **データベースの作成** ウィザードを完了します。</span><span class="sxs-lookup"><span data-stu-id="eaad9-110">Complete the **Create Database** wizard to create and configure the database.</span></span> <span data-ttu-id="eaad9-111">ウィザードのユーザー インターフェイス (UI) オプションの詳細については、「[データベースの作成ウィザード &#40;マスター データ サービス構成マネージャー&#41;](../create-database-wizard-master-data-services-configuration-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eaad9-111">For information about the user interface (UI) options in the wizard, see [Create Database Wizard &#40;Master Data Services Configuration Manager&#41;](../create-database-wizard-master-data-services-configuration-manager.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="eaad9-112">次の手順</span><span class="sxs-lookup"><span data-stu-id="eaad9-112">Next Steps</span></span>  
  
-   <span data-ttu-id="eaad9-113">データベースと Web アプリケーションのシステム設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="eaad9-113">Configure system settings for the database and web application.</span></span> <span data-ttu-id="eaad9-114">詳細については、「[システム設定 &#40;マスター データ サービス&#41;](../system-settings-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eaad9-114">For more information, see [System Settings &#40;Master Data Services&#41;](../system-settings-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="eaad9-115">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションを作成して、このデータベースに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="eaad9-115">Create a [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application to associate with this database.</span></span> <span data-ttu-id="eaad9-116">詳細については、「[マスター データ マネージャー Web アプリケーションを作成する方法 &#40;マスター データ サービス&#41;](create-a-master-data-manager-web-application-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eaad9-116">For more information, see [Create a Master Data Manager Web Application &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="eaad9-117">データベースとトランザクション ログをバックアップするように、メンテナンス プランを構成します。</span><span class="sxs-lookup"><span data-stu-id="eaad9-117">Configure a maintenance plan to back up the database and transaction logs.</span></span> <span data-ttu-id="eaad9-118">詳細については、「[データベース要件 &#40;マスター データ サービス&#41;](database-requirements-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eaad9-118">For more information, see [Database Requirements &#40;Master Data Services&#41;](database-requirements-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaad9-119">参照</span><span class="sxs-lookup"><span data-stu-id="eaad9-119">See Also</span></span>  
 [<span data-ttu-id="eaad9-120">マスター データ サービスのインストール</span><span class="sxs-lookup"><span data-stu-id="eaad9-120">Install Master Data Services</span></span>](install-master-data-services.md)  
  
  
