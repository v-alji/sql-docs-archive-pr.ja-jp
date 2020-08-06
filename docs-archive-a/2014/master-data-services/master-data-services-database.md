---
title: マスター データ サービス データベース | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- database [Master Data Services], about the database
- database [Master Data Services]
ms.assetid: 5f590cc1-6ec2-4b8c-a598-03de0f6051a0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7e4bae180dfb7c9051d5445a689c44978ef73bfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642136"
---
# <a name="master-data-services-database"></a><span data-ttu-id="6ef43-102">マスター データ サービス データベース</span><span class="sxs-lookup"><span data-stu-id="6ef43-102">Master Data Services Database</span></span>
  <span data-ttu-id="6ef43-103">データベースには、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] システムに関するすべての情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6ef43-103">The database contains all of the information for the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] system.</span></span> <span data-ttu-id="6ef43-104">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 配置の中心となる要素です。</span><span class="sxs-lookup"><span data-stu-id="6ef43-104">It is central to a [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] deployment.</span></span> <span data-ttu-id="6ef43-105">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースの機能は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6ef43-105">The [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database:</span></span>  
  
-   <span data-ttu-id="6ef43-106">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] システムで必要となる設定、データベース オブジェクト、およびデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="6ef43-106">Stores the settings, database objects, and data required by the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] system.</span></span>  
  
-   <span data-ttu-id="6ef43-107">ソース システムのデータを処理するために使用されるステージング テーブルを含みます。</span><span class="sxs-lookup"><span data-stu-id="6ef43-107">Contains staging tables that are used to process data from source systems.</span></span>  
  
-   <span data-ttu-id="6ef43-108">ソース システムのマスター データを格納するためのスキーマおよびデータベース オブジェクトを提供します。</span><span class="sxs-lookup"><span data-stu-id="6ef43-108">Provides a schema and database objects to store master data from source systems.</span></span>  
  
-   <span data-ttu-id="6ef43-109">ビジネス ルールの検証や電子メール通知など、バージョン管理機能をサポートします。</span><span class="sxs-lookup"><span data-stu-id="6ef43-109">Supports versioning functionality, including business rule validation and e-mail notifications.</span></span>  
  
-   <span data-ttu-id="6ef43-110">データベースからデータを取得するために必要なサブスクライブ システムのビューを提供します。</span><span class="sxs-lookup"><span data-stu-id="6ef43-110">Provides views for subscribing systems that need to retrieve data from the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6ef43-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="6ef43-111">In This Section</span></span>  
  
-   [<span data-ttu-id="6ef43-112">リーフ メンバー ステージング テーブル (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="6ef43-112">Leaf Member Staging Table &#40;Master Data Services&#41;</span></span>](leaf-member-staging-table-master-data-services.md)  
  
-   [<span data-ttu-id="6ef43-113">統合メンバー ステージング テーブル (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="6ef43-113">Consolidated Member Staging Table &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/consolidated-member-staging-table-master-data-services.md)  
  
-   [<span data-ttu-id="6ef43-114">リレーションシップ ステージング テーブル (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="6ef43-114">Relationship Staging Table &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/relationship-staging-table-master-data-services.md)  
  
-   [<span data-ttu-id="6ef43-115">ステージング処理のエラー (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="6ef43-115">Staging Process Errors &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/staging-process-errors-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="6ef43-116">参照</span><span class="sxs-lookup"><span data-stu-id="6ef43-116">See Also</span></span>  
 <span data-ttu-id="6ef43-117">[マスターデータサービスデータベースを作成する](install-windows/create-a-master-data-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="6ef43-117">[Create a Master Data Services Database](install-windows/create-a-master-data-services-database.md) </span></span>  
 <span data-ttu-id="6ef43-118">[データベースオブジェクトセキュリティ &#40;マスターデータサービス&#41;](../../2014/master-data-services/database-object-security-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="6ef43-118">[Database Object Security &#40;Master Data Services&#41;](../../2014/master-data-services/database-object-security-master-data-services.md) </span></span>  
 [<span data-ttu-id="6ef43-119">データベース ログイン、ユーザー、およびロール &#40;マスター データ サービス&#41;</span><span class="sxs-lookup"><span data-stu-id="6ef43-119">Database Logins, Users, and Roles &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/database-logins-users-and-roles-master-data-services.md)  
  
  
