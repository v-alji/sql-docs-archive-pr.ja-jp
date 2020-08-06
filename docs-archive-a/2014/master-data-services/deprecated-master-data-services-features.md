---
title: 非推奨のマスターデータサービス SQL Server 2014 | の機能Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: d8506bda-66dd-45a4-bfc9-3a10fa665acc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ce532e9f407ec475f7e59c0d79659265a9e0bf3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712089"
---
# <a name="deprecated-master-data-services-features-in-sql-server-2014"></a><span data-ttu-id="4909a-102">SQL Server 2014 に含まれている非推奨のマスター データ サービス機能</span><span class="sxs-lookup"><span data-stu-id="4909a-102">Deprecated Master Data Services Features in SQL Server 2014</span></span>
  <span data-ttu-id="4909a-103">このトピックでは、[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] でまだ使用できるものの、非推奨とされた [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]の機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="4909a-103">This topic describes the deprecated [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] features that are still available in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="4909a-104">これらの機能は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の今後のリリースで削除される予定です。</span><span class="sxs-lookup"><span data-stu-id="4909a-104">These features are scheduled to be removed in a future release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4909a-105">非推奨の機能を新しいアプリケーションで使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="4909a-105">Deprecated features should not be used in new applications.</span></span>  
  
## <a name="staging-process"></a><span data-ttu-id="4909a-106">ステージング処理</span><span class="sxs-lookup"><span data-stu-id="4909a-106">Staging Process</span></span>  
 <span data-ttu-id="4909a-107">[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] で使用されていたステージング処理は、[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションでは使用できなくなりましたが、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] では引き続き使用できます。</span><span class="sxs-lookup"><span data-stu-id="4909a-107">The staging process that was used in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] is no longer available in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application; however it is still available in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="4909a-108">[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] のステージング処理のステージング エラーは、UI に表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="4909a-108">Staging errors from the [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] staging process are no longer displayed in the UI.</span></span> <span data-ttu-id="4909a-109">ステージング処理中に設定されたエラーコードは、ステージングテーブルで引き続き使用できます。これについては、「」を参照して [https://msdn.microsoft.com/library/ff487022.aspx](https://msdn.microsoft.com/library/ff487022.aspx) ください。</span><span class="sxs-lookup"><span data-stu-id="4909a-109">Error codes that are populated during the staging process are still available in the staging tables, and can be found here: [https://msdn.microsoft.com/library/ff487022.aspx](https://msdn.microsoft.com/library/ff487022.aspx).</span></span>  
  
 <span data-ttu-id="4909a-110">ステージング テーブル (tblStgMember、tblStgMemberAttribute、および tblStgRelationship) は、データベースで引き続き使用できます。</span><span class="sxs-lookup"><span data-stu-id="4909a-110">The staging tables (tblStgMember, tblStgMemberAttribute, and tblStgRelationship) are still available in the database.</span></span> <span data-ttu-id="4909a-111">ステージング処理 (mdm.udpStagingSweep) を起動するために使用していたストアド プロシージャは、データベースで引き続き使用できます。</span><span class="sxs-lookup"><span data-stu-id="4909a-111">The stored procedure used to initiate the staging process (mdm.udpStagingSweep) is still available in the database.</span></span>  
  
 <span data-ttu-id="4909a-112">ステージング処理を呼び出す web サービス メソッドは引き続き使用できます。</span><span class="sxs-lookup"><span data-stu-id="4909a-112">The web service methods that call the staging process are still available.</span></span>  
  
 <span data-ttu-id="4909a-113">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]で設定するステージングの間隔は、[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] および [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] の両方のステージング処理に適用されます。</span><span class="sxs-lookup"><span data-stu-id="4909a-113">The staging interval set in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] applies to the staging process in both [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] and [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="4909a-114">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] には、新しくパフォーマンスの高いステージング処理が実装されています。</span><span class="sxs-lookup"><span data-stu-id="4909a-114">A new, higher performance staging process has been implemented in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="4909a-115">詳細については、「[データのインポート &#40;マスター データ サービス&#41;](overview-importing-data-from-tables-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4909a-115">For more information, see [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).</span></span>  
  
## <a name="metadata"></a><span data-ttu-id="4909a-116">Metadata</span><span class="sxs-lookup"><span data-stu-id="4909a-116">Metadata</span></span>  
 <span data-ttu-id="4909a-117">メタデータ モデルは[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションに引き続き表示されますが、使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="4909a-117">Though the Metadata model is still displayed in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application, it should not be used.</span></span> <span data-ttu-id="4909a-118">将来のリリースでは削除される予定です。</span><span class="sxs-lookup"><span data-stu-id="4909a-118">It will be removed in a future release.</span></span> <span data-ttu-id="4909a-119">また、ユーザーは [**エクスプローラー** ] 機能領域でメタデータを表示できなくなります。また、メタデータモデルのバージョンを作成することもできなくなります。</span><span class="sxs-lookup"><span data-stu-id="4909a-119">Users can also no longer view metadata in the **Explorer** functional area, and you can no longer create versions of the Metadata model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4909a-120">参照</span><span class="sxs-lookup"><span data-stu-id="4909a-120">See Also</span></span>  
 [<span data-ttu-id="4909a-121">SQL Server 2014 で提供が中止されたマスター データ サービス機能</span><span class="sxs-lookup"><span data-stu-id="4909a-121">Discontinued Master Data Services Features in SQL Server 2014</span></span>](discontinued-master-data-services-features.md)  
  
  
