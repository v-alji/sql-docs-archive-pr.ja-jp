---
title: 検証ストアド プロシージャ (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 332d3c86-4440-4f12-a6cb-ffbfbccde52c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8fa6b01d950c87768d10b0252c1ccbab2b932fe1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641028"
---
# <a name="validation-stored-procedure-master-data-services"></a><span data-ttu-id="9c122-102">検証ストアド プロシージャ (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="9c122-102">Validation Stored Procedure (Master Data Services)</span></span>
  <span data-ttu-id="9c122-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、ビジネス ルールをモデル バージョンのすべてのメンバーに適用するためにバージョンが検証されます。</span><span class="sxs-lookup"><span data-stu-id="9c122-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], validate a version to apply business rules to all members in the model version.</span></span>  
  
 <span data-ttu-id="9c122-104">このトピックでは、 **mdm.udpValidateModel** ストアド プロシージャを使用してデータを検証する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9c122-104">This topic explains how to use the **mdm.udpValidateModel** stored procedure to validate data.</span></span> <span data-ttu-id="9c122-105">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションの管理者であれば、代わりに UI で検証を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="9c122-105">If you are an administrator in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application, you can do validation in the UI instead.</span></span> <span data-ttu-id="9c122-106">詳細については、「 [ビジネス ルールに対してバージョンを検証する (マスター データ サービス)](validate-a-version-against-business-rules-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c122-106">For more information, see [Validate a Version against Business Rules &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9c122-107">ステージング処理が完了する前に検証を呼び出すと、ステージングが終了していないメンバーは検証されません。</span><span class="sxs-lookup"><span data-stu-id="9c122-107">If you invoke validation before the staging process is complete, members that have not finished staging will not be validated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c122-108">例</span><span class="sxs-lookup"><span data-stu-id="9c122-108">Example</span></span>  
  
```  
DECLARE @ModelName nVarchar(50) = 'Customer'   
DECLARE @Model_id int   
DECLARE @UserName nvarchar(50)= 'DOMAIN\user_name'   
DECLARE @User_ID int   
DECLARE @Version_ID int   
  
SET @User_ID = (SELECT ID    
                 FROM mdm.tblUser u   
                 WHERE u.UserName = @UserName)   
SET @Model_ID = (SELECT Top 1 Model_ID   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_Name = @ModelName)   
SET @Version_ID = (SELECT MAX(ID)   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_ID = @Model_ID)  
  
EXECUTE mdm.udpValidateModel @User_ID, @Model_ID, @Version_ID, 1  
  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c122-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9c122-109">Parameters</span></span>  
 <span data-ttu-id="9c122-110">このプロシージャのパラメーターを次に示します。</span><span class="sxs-lookup"><span data-stu-id="9c122-110">The parameters of this procedure are as follows:</span></span>  
  
|<span data-ttu-id="9c122-111">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9c122-111">Parameter</span></span>|<span data-ttu-id="9c122-112">説明</span><span class="sxs-lookup"><span data-stu-id="9c122-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9c122-113">UserID</span><span class="sxs-lookup"><span data-stu-id="9c122-113">UserID</span></span>|<span data-ttu-id="9c122-114">ユーザー ID。</span><span class="sxs-lookup"><span data-stu-id="9c122-114">The user ID.</span></span>|  
|<span data-ttu-id="9c122-115">Model_ID</span><span class="sxs-lookup"><span data-stu-id="9c122-115">Model_ID</span></span>|<span data-ttu-id="9c122-116">モデル ID。</span><span class="sxs-lookup"><span data-stu-id="9c122-116">The model ID.</span></span>|  
|<span data-ttu-id="9c122-117">Version_ID</span><span class="sxs-lookup"><span data-stu-id="9c122-117">Version_ID</span></span>|<span data-ttu-id="9c122-118">バージョン ID。</span><span class="sxs-lookup"><span data-stu-id="9c122-118">The version ID.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9c122-119">参照</span><span class="sxs-lookup"><span data-stu-id="9c122-119">See Also</span></span>  
 <span data-ttu-id="9c122-120">[データのインポート &#40;マスターデータサービス&#41;](overview-importing-data-from-tables-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="9c122-120">[Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md) </span></span>  
 [<span data-ttu-id="9c122-121">ビジネス ルールに対してバージョンを検証する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="9c122-121">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](validate-a-version-against-business-rules-master-data-services.md)  
  
  
