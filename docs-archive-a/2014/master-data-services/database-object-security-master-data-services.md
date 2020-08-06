---
title: データベース オブジェクト セキュリティ (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- database [Master Data Services], object security
- security [Master Data Services], database objects
ms.assetid: dd5ba503-7607-45d9-ad0d-909faaade179
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9713f615a190beee5054ee55471e0db387a8a9e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712105"
---
# <a name="database-object-security-master-data-services"></a><span data-ttu-id="ef610-102">データベース オブジェクト セキュリティ (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="ef610-102">Database Object Security (Master Data Services)</span></span>
  <span data-ttu-id="ef610-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースでは、データは複数のデータベース テーブルに格納されており、ビューで表示できます。</span><span class="sxs-lookup"><span data-stu-id="ef610-103">In the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database, data is stored in multiple database tables and is visible in views.</span></span> <span data-ttu-id="ef610-104">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションで保護されている可能性がある情報は、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースにアクセスできるユーザーであれば参照できます。</span><span class="sxs-lookup"><span data-stu-id="ef610-104">Information that you might have secured in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web application is visible to users with access to the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
 <span data-ttu-id="ef610-105">具体的には、従業員の給与情報が Employee モデルに含まれており、企業の財務情報が Account モデルに含まれている場合を考えることができます。</span><span class="sxs-lookup"><span data-stu-id="ef610-105">Specifically, employee salary information might be contained in an Employee model, or company financial information might be in an Account model.</span></span> <span data-ttu-id="ef610-106">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ユーザー インターフェイスでこれらのモデルへのユーザー アクセスを拒否できますが、データベースへのアクセス権を持つユーザーはこのデータを表示できます。</span><span class="sxs-lookup"><span data-stu-id="ef610-106">You can deny a user access to these models in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] user interface, but users with access to the database can view this data.</span></span>  
  
 <span data-ttu-id="ef610-107">ユーザーが固有のデータを使用できるように、データベース オブジェクトに権限を付与できます。</span><span class="sxs-lookup"><span data-stu-id="ef610-107">You can grant permissions to database objects to make specific data available to users.</span></span> <span data-ttu-id="ef610-108">権限付与の詳細については、「[GRANT (オブジェクトの権限の許可) (Transact-SQL)](/sql/t-sql/statements/grant-object-permissions-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef610-108">For more information on granting permissions, see [GRANT Object Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql).</span></span> <span data-ttu-id="ef610-109">SQL server の保護の詳細については、「 [SQL Server の保護](../relational-databases/security/securing-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef610-109">For more information about securing SQL server, see [Securing SQL Server](../relational-databases/security/securing-sql-server.md).</span></span>  
  
 <span data-ttu-id="ef610-110">次のタスクでは [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースへのアクセスが必要です。</span><span class="sxs-lookup"><span data-stu-id="ef610-110">The following tasks require access to the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database:</span></span>  
  
-   [<span data-ttu-id="ef610-111">データのステージング</span><span class="sxs-lookup"><span data-stu-id="ef610-111">Staging Data</span></span>](#Staging)  
  
-   [<span data-ttu-id="ef610-112">ビジネス ルールに対してデータを検証する</span><span class="sxs-lookup"><span data-stu-id="ef610-112">Validating Data Against Business Rules</span></span>](#rules)  
  
-   [<span data-ttu-id="ef610-113">バージョンを削除する</span><span class="sxs-lookup"><span data-stu-id="ef610-113">Deleting Versions</span></span>](#Versions)  
  
-   [<span data-ttu-id="ef610-114">階層メンバーの権限を直ちに適用する</span><span class="sxs-lookup"><span data-stu-id="ef610-114">Immediately Applying Hierarchy Member Permissions</span></span>](#Hierarchy)  
  
-   [<span data-ttu-id="ef610-115">システム管理者アカウントを変更する</span><span class="sxs-lookup"><span data-stu-id="ef610-115">Changing the System Administrator Account</span></span>](#SysAdmin)  
  
-   [<span data-ttu-id="ef610-116">システム設定を構成する</span><span class="sxs-lookup"><span data-stu-id="ef610-116">Configuring System Settings</span></span>](#SysSettings)  
  
##  <a name="staging-data"></a><a name="Staging"></a> <span data-ttu-id="ef610-117">データをステージングする</span><span class="sxs-lookup"><span data-stu-id="ef610-117">Staging Data</span></span>  
 <span data-ttu-id="ef610-118">次の表では、セキュリティ保護可能な各リソースの名前の一部に "name" を使用しています。</span><span class="sxs-lookup"><span data-stu-id="ef610-118">In the following table, each securable has "name" as part of the name.</span></span> <span data-ttu-id="ef610-119">これは、エンティティの作成時に指定するステージング テーブルの名前を示します。</span><span class="sxs-lookup"><span data-stu-id="ef610-119">This indicates the name of the staging table that is specified when an entity is created.</span></span> <span data-ttu-id="ef610-120">詳細については、「[データのインポート &#40;マスターデータサービス](overview-importing-data-from-tables-master-data-services.md)」を参照してください&#41;</span><span class="sxs-lookup"><span data-stu-id="ef610-120">For more information, see [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)</span></span>  
  
|<span data-ttu-id="ef610-121">アクション</span><span class="sxs-lookup"><span data-stu-id="ef610-121">Action</span></span>|<span data-ttu-id="ef610-122">[セキュリティ保護可能なリソース]</span><span class="sxs-lookup"><span data-stu-id="ef610-122">Securables</span></span>|<span data-ttu-id="ef610-123">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="ef610-123">Permissions</span></span>|  
|------------|----------------|-----------------|  
|<span data-ttu-id="ef610-124">リーフ メンバーとその属性をステージング テーブルに読み込む</span><span class="sxs-lookup"><span data-stu-id="ef610-124">Load leaf members and their attributes into the staging table.</span></span>|<span data-ttu-id="ef610-125">stg.name_Leaf</span><span class="sxs-lookup"><span data-stu-id="ef610-125">stg.name_Leaf</span></span>|<span data-ttu-id="ef610-126">必須: INSERT</span><span class="sxs-lookup"><span data-stu-id="ef610-126">Required: INSERT</span></span><br /><br /> <span data-ttu-id="ef610-127">オプション: SELECT および UPDATE</span><span class="sxs-lookup"><span data-stu-id="ef610-127">Optional: SELECT and UPDATE</span></span>|  
|<span data-ttu-id="ef610-128">リーフ ステージング テーブルから MDS データベースの適切なテーブルにデータを読み込む</span><span class="sxs-lookup"><span data-stu-id="ef610-128">Load the data from the Leaf staging table into the appropriate MDS database tables.</span></span>|<span data-ttu-id="ef610-129">stg.udp_name_Leaf</span><span class="sxs-lookup"><span data-stu-id="ef610-129">stg.udp_name_Leaf</span></span>|<span data-ttu-id="ef610-130">EXECUTE</span><span class="sxs-lookup"><span data-stu-id="ef610-130">EXECUTE</span></span>|  
|<span data-ttu-id="ef610-131">統合メンバーとその属性をステージング テーブルに読み込む</span><span class="sxs-lookup"><span data-stu-id="ef610-131">Load consolidated members and their attributes into the staging table.</span></span>|<span data-ttu-id="ef610-132">stg.name_Consolidated</span><span class="sxs-lookup"><span data-stu-id="ef610-132">stg.name_Consolidated</span></span>|<span data-ttu-id="ef610-133">必須: INSERT</span><span class="sxs-lookup"><span data-stu-id="ef610-133">Required: INSERT</span></span><br /><br /> <span data-ttu-id="ef610-134">オプション: SELECT および UPDATE</span><span class="sxs-lookup"><span data-stu-id="ef610-134">Optional: SELECT and UPDATE</span></span>|  
|<span data-ttu-id="ef610-135">統合ステージング テーブルから MDS データベースの適切なテーブルにデータを読み込む</span><span class="sxs-lookup"><span data-stu-id="ef610-135">Load the data from the Consolidated staging table into the appropriate MDS database tables.</span></span>|<span data-ttu-id="ef610-136">stg.udp_name_Consolidated</span><span class="sxs-lookup"><span data-stu-id="ef610-136">stg.udp_name_Consolidated</span></span>|<span data-ttu-id="ef610-137">EXECUTE</span><span class="sxs-lookup"><span data-stu-id="ef610-137">EXECUTE</span></span>|  
|<span data-ttu-id="ef610-138">明示的階層内のリーフメンバーと統合メンバーのリレーションシップをステージングテーブルに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="ef610-138">Load leaf and consolidated members' relationships to each other in an explicit hierarchy into the staging table.</span></span>|<span data-ttu-id="ef610-139">stg.name_Relationship</span><span class="sxs-lookup"><span data-stu-id="ef610-139">stg.name_Relationship</span></span>|<span data-ttu-id="ef610-140">必須: INSERT</span><span class="sxs-lookup"><span data-stu-id="ef610-140">Required: INSERT</span></span><br /><br /> <span data-ttu-id="ef610-141">オプション: SELECT および UPDATE</span><span class="sxs-lookup"><span data-stu-id="ef610-141">Optional: SELECT and UPDATE</span></span>|  
|<span data-ttu-id="ef610-142">リレーションシップ ステージング テーブルから MDS の適切なテーブルにデータを読み込む</span><span class="sxs-lookup"><span data-stu-id="ef610-142">Load the data from the Relationship staging table into the appropriate MDS tables.</span></span>|<span data-ttu-id="ef610-143">stg.udp_name_Relationship</span><span class="sxs-lookup"><span data-stu-id="ef610-143">stg.udp_name_Relationship</span></span>|<span data-ttu-id="ef610-144">EXECUTE</span><span class="sxs-lookup"><span data-stu-id="ef610-144">EXECUTE</span></span>|  
|<span data-ttu-id="ef610-145">ステージング テーブルのデータが MDS データベース テーブルに挿入されたときに発生したエラーを表示する</span><span class="sxs-lookup"><span data-stu-id="ef610-145">View errors that occurred when data from the staging tables was being inserted into the MDS database tables.</span></span>|<span data-ttu-id="ef610-146">stg.udp_name_Relationship</span><span class="sxs-lookup"><span data-stu-id="ef610-146">stg.udp_name_Relationship</span></span>|<span data-ttu-id="ef610-147">SELECT</span><span class="sxs-lookup"><span data-stu-id="ef610-147">SELECT</span></span>|  
  
 <span data-ttu-id="ef610-148">詳細については、「[データのインポート &#40;マスター データ サービス&#41;](overview-importing-data-from-tables-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef610-148">For more information, see [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).</span></span>  
  
##  <a name="validating-data-against-business-rules"></a><a name="rules"></a><span data-ttu-id="ef610-149">ビジネスルールに対してデータを検証する</span><span class="sxs-lookup"><span data-stu-id="ef610-149">Validating Data Against Business Rules</span></span>  
  
|<span data-ttu-id="ef610-150">アクション</span><span class="sxs-lookup"><span data-stu-id="ef610-150">Action</span></span>|<span data-ttu-id="ef610-151">セキュリティ保護可能</span><span class="sxs-lookup"><span data-stu-id="ef610-151">Securable</span></span>|<span data-ttu-id="ef610-152">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="ef610-152">Permissions</span></span>|  
|------------|---------------|-----------------|  
|<span data-ttu-id="ef610-153">ビジネス ルールに対してデータのバージョンを検証する</span><span class="sxs-lookup"><span data-stu-id="ef610-153">Validate a version of data against business rules</span></span>|<span data-ttu-id="ef610-154">mdm.udpValidateModel</span><span class="sxs-lookup"><span data-stu-id="ef610-154">mdm.udpValidateModel</span></span>|<span data-ttu-id="ef610-155">EXECUTE</span><span class="sxs-lookup"><span data-stu-id="ef610-155">EXECUTE</span></span>|  
  
 <span data-ttu-id="ef610-156">詳細については、「 [検証ストアド プロシージャ (マスター データ サービス)](../../2014/master-data-services/validation-stored-procedure-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef610-156">For more information, see [Validation Stored Procedure &#40;Master Data Services&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md).</span></span>  
  
##  <a name="deleting-versions"></a><a name="Versions"></a><span data-ttu-id="ef610-157">バージョンの削除</span><span class="sxs-lookup"><span data-stu-id="ef610-157">Deleting Versions</span></span>  
  
|<span data-ttu-id="ef610-158">アクション</span><span class="sxs-lookup"><span data-stu-id="ef610-158">Action</span></span>|<span data-ttu-id="ef610-159">[セキュリティ保護可能なリソース]</span><span class="sxs-lookup"><span data-stu-id="ef610-159">Securables</span></span>|<span data-ttu-id="ef610-160">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="ef610-160">Permissions</span></span>|  
|------------|----------------|-----------------|  
|<span data-ttu-id="ef610-161">削除するバージョンの ID を決定する</span><span class="sxs-lookup"><span data-stu-id="ef610-161">Determine the ID of the version you want to delete</span></span>|<span data-ttu-id="ef610-162">mdm.viw_SYSTEM_SCHEMA_VERSION</span><span class="sxs-lookup"><span data-stu-id="ef610-162">mdm.viw_SYSTEM_SCHEMA_VERSION</span></span>|<span data-ttu-id="ef610-163">SELECT</span><span class="sxs-lookup"><span data-stu-id="ef610-163">SELECT</span></span>|  
|<span data-ttu-id="ef610-164">モデルのバージョンを削除する</span><span class="sxs-lookup"><span data-stu-id="ef610-164">Delete a version of a model</span></span>|<span data-ttu-id="ef610-165">mdm.udpVersionDelete</span><span class="sxs-lookup"><span data-stu-id="ef610-165">mdm.udpVersionDelete</span></span>|<span data-ttu-id="ef610-166">EXECUTE</span><span class="sxs-lookup"><span data-stu-id="ef610-166">EXECUTE</span></span>|  
  
 <span data-ttu-id="ef610-167">詳細については、「[バージョンを削除する (マスター データ サービス)](../../2014/master-data-services/delete-a-version-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef610-167">For more information, see [Delete a Version &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-version-master-data-services.md).</span></span>  
  
##  <a name="immediately-applying-hierarchy-member-permissions"></a><a name="Hierarchy"></a><span data-ttu-id="ef610-168">階層メンバーの権限を直ちに適用する</span><span class="sxs-lookup"><span data-stu-id="ef610-168">Immediately Applying Hierarchy Member Permissions</span></span>  
  
|<span data-ttu-id="ef610-169">アクション</span><span class="sxs-lookup"><span data-stu-id="ef610-169">Action</span></span>|<span data-ttu-id="ef610-170">[セキュリティ保護可能なリソース]</span><span class="sxs-lookup"><span data-stu-id="ef610-170">Securables</span></span>|<span data-ttu-id="ef610-171">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="ef610-171">Permissions</span></span>|  
|------------|----------------|-----------------|  
|<span data-ttu-id="ef610-172">メンバー権限を直ちに適用する</span><span class="sxs-lookup"><span data-stu-id="ef610-172">Immediately apply member permissions</span></span>|<span data-ttu-id="ef610-173">mdm.udpSecurityMemberProcessRebuildModel</span><span class="sxs-lookup"><span data-stu-id="ef610-173">mdm.udpSecurityMemberProcessRebuildModel</span></span>|<span data-ttu-id="ef610-174">EXECUTE</span><span class="sxs-lookup"><span data-stu-id="ef610-174">EXECUTE</span></span>|  
  
 <span data-ttu-id="ef610-175">詳細については、「[メンバー権限を直ちに適用する (マスター データ サービス)](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef610-175">For more information, see [Immediately Apply Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md).</span></span>  
  
##  <a name="changing-the-system-administrator-account"></a><a name="SysAdmin"></a><span data-ttu-id="ef610-176">システム管理者アカウントの変更</span><span class="sxs-lookup"><span data-stu-id="ef610-176">Changing the System Administrator Account</span></span>  
  
|<span data-ttu-id="ef610-177">アクション</span><span class="sxs-lookup"><span data-stu-id="ef610-177">Action</span></span>|<span data-ttu-id="ef610-178">[セキュリティ保護可能なリソース]</span><span class="sxs-lookup"><span data-stu-id="ef610-178">Securables</span></span>|<span data-ttu-id="ef610-179">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="ef610-179">Permissions</span></span>|  
|------------|----------------|-----------------|  
|<span data-ttu-id="ef610-180">新しい管理者の SID を決定する</span><span class="sxs-lookup"><span data-stu-id="ef610-180">Determine the SID of the new administrator</span></span>|<span data-ttu-id="ef610-181">mdm.tblUser</span><span class="sxs-lookup"><span data-stu-id="ef610-181">mdm.tblUser</span></span>|<span data-ttu-id="ef610-182">SELECT</span><span class="sxs-lookup"><span data-stu-id="ef610-182">SELECT</span></span>|  
|<span data-ttu-id="ef610-183">システム管理者アカウントを変更する</span><span class="sxs-lookup"><span data-stu-id="ef610-183">Change the system administrator account</span></span>|<span data-ttu-id="ef610-184">mdm.udpSecuritySetAdministrator</span><span class="sxs-lookup"><span data-stu-id="ef610-184">mdm.udpSecuritySetAdministrator</span></span>|<span data-ttu-id="ef610-185">EXECUTE</span><span class="sxs-lookup"><span data-stu-id="ef610-185">EXECUTE</span></span>|  
  
 <span data-ttu-id="ef610-186">詳細については、「[マスターデータサービス&#41;&#40;システム管理者アカウントを変更](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef610-186">For more information, see [Change the System Administrator Account &#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md).</span></span>  
  
##  <a name="configuring-system-settings"></a><a name="SysSettings"></a><span data-ttu-id="ef610-187">システム設定の構成</span><span class="sxs-lookup"><span data-stu-id="ef610-187">Configuring System Settings</span></span>  
 <span data-ttu-id="ef610-188">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]での動作を制御するために構成可能なシステム設定が用意されています。</span><span class="sxs-lookup"><span data-stu-id="ef610-188">There are system settings that you can configure to control behavior in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span></span> <span data-ttu-id="ef610-189">これらの設定は [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] で調整できます。または、UPDATE アクセス権を持つ場合は、mdm.tblSystemSetting データベース テーブルで直接調整できます。</span><span class="sxs-lookup"><span data-stu-id="ef610-189">You can adjust these settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] or if you have UPDATE access, you can adjust these settings directly in the mdm.tblSystemSetting database table.</span></span> <span data-ttu-id="ef610-190">詳細については、「[システム設定 &#40;マスター データ サービス&#41;](../../2014/master-data-services/system-settings-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef610-190">For more information, see [System Settings &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef610-191">参照</span><span class="sxs-lookup"><span data-stu-id="ef610-191">See Also</span></span>  
 [<span data-ttu-id="ef610-192">セキュリティ (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="ef610-192">Security &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/security-master-data-services.md)  
  
  
