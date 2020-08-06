---
title: ステージング ストアド プロシージャ (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 6a613106-9f87-4caf-a23a-a726fc6561c5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9259352350a099db5d9b18411ad4da06dfb19819
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645708"
---
# <a name="staging-stored-procedure-master-data-services"></a><span data-ttu-id="6a28a-102">ステージング ストアド プロシージャ (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="6a28a-102">Staging Stored Procedure (Master Data Services)</span></span>
  <span data-ttu-id="6a28a-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]からステージング処理を開始する場合、次の 3 つのストアド プロシージャのいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="6a28a-103">When initiating the staging process from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], you use one of three stored procedures.</span></span>  
  
-   <span data-ttu-id="6a28a-104">stg.udp_name_Leaf</span><span class="sxs-lookup"><span data-stu-id="6a28a-104">stg.udp_name_Leaf</span></span>  
  
-   <span data-ttu-id="6a28a-105">stg.udp_name_Consolidated</span><span class="sxs-lookup"><span data-stu-id="6a28a-105">stg.udp_name_Consolidated</span></span>  
  
-   <span data-ttu-id="6a28a-106">stg.udp_name_Relationship</span><span class="sxs-lookup"><span data-stu-id="6a28a-106">stg.udp_name_Relationship</span></span>  
  
 <span data-ttu-id="6a28a-107">name は、エンティティの作成時に指定されたステージング テーブルの名前です。</span><span class="sxs-lookup"><span data-stu-id="6a28a-107">Where name is the name of the staging table that was specified when the entity was created.</span></span>  
  
## <a name="staging-process-stored-procedure-parameters"></a><span data-ttu-id="6a28a-108">ステージング処理ストアド プロシージャのパラメーター</span><span class="sxs-lookup"><span data-stu-id="6a28a-108">Staging Process Stored Procedure Parameters</span></span>  
 <span data-ttu-id="6a28a-109">次の表では、これらのストアド プロシージャのパラメーターの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="6a28a-109">The following table lists the parameters of these stored procedures.</span></span>  
  
|<span data-ttu-id="6a28a-110">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6a28a-110">Parameter</span></span>|<span data-ttu-id="6a28a-111">説明</span><span class="sxs-lookup"><span data-stu-id="6a28a-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6a28a-112">**VersionName**</span><span class="sxs-lookup"><span data-stu-id="6a28a-112">**VersionName**</span></span><br /><br /> <span data-ttu-id="6a28a-113">必須</span><span class="sxs-lookup"><span data-stu-id="6a28a-113">Required</span></span>|<span data-ttu-id="6a28a-114">バージョンの名前。</span><span class="sxs-lookup"><span data-stu-id="6a28a-114">The name of the version.</span></span> <span data-ttu-id="6a28a-115">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] コレクションの設定に応じて、このパラメーターは大文字と小文字が区別される場合とされない場合があります。</span><span class="sxs-lookup"><span data-stu-id="6a28a-115">This may or may not be case-sensitive, depending on your [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] collation setting.</span></span>|  
|<span data-ttu-id="6a28a-116">**LogFlag**</span><span class="sxs-lookup"><span data-stu-id="6a28a-116">**LogFlag**</span></span><br /><br /> <span data-ttu-id="6a28a-117">必須</span><span class="sxs-lookup"><span data-stu-id="6a28a-117">Required</span></span>|<span data-ttu-id="6a28a-118">ステージング処理中にトランザクションをログに記録するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="6a28a-118">Determines whether transactions are logged during the staging process.</span></span> <span data-ttu-id="6a28a-119">次のいずれかの値になります。</span><span class="sxs-lookup"><span data-stu-id="6a28a-119">Possible values are:</span></span><br /><br /> <span data-ttu-id="6a28a-120">**0**: トランザクションをログに記録しない。</span><span class="sxs-lookup"><span data-stu-id="6a28a-120">**0**: Do not log transactions.</span></span><br /><span data-ttu-id="6a28a-121">**1**: トランザクションをログに記録する。</span><span class="sxs-lookup"><span data-stu-id="6a28a-121">**1**: Log transactions.</span></span><br /><br /> <br /><br /> <span data-ttu-id="6a28a-122">詳細については、「[トランザクション (マスター データ サービス)](transactions-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a28a-122">For more information about transactions, see [Transactions &#40;Master Data Services&#41;](transactions-master-data-services.md).</span></span>|  
|<span data-ttu-id="6a28a-123">**BatchTag**</span><span class="sxs-lookup"><span data-stu-id="6a28a-123">**BatchTag**</span></span><br /><br /> <span data-ttu-id="6a28a-124">Web サービス以外は必須</span><span class="sxs-lookup"><span data-stu-id="6a28a-124">Required, except by web service</span></span>|<span data-ttu-id="6a28a-125">ステージング テーブルに指定した **BatchTag** の値。</span><span class="sxs-lookup"><span data-stu-id="6a28a-125">The **BatchTag** value as specified in the staging table.</span></span>|  
|<span data-ttu-id="6a28a-126">**Batch_ID**</span><span class="sxs-lookup"><span data-stu-id="6a28a-126">**Batch_ID**</span></span><br /><br /> <span data-ttu-id="6a28a-127">Web サービスでのみ必須</span><span class="sxs-lookup"><span data-stu-id="6a28a-127">Required by web service only</span></span>|<span data-ttu-id="6a28a-128">ステージング テーブルに指定した **Batch_ID** の値。</span><span class="sxs-lookup"><span data-stu-id="6a28a-128">The **Batch_ID** value as specified in the staging table.</span></span>|  
  
### <a name="staging-process-stored-procedure-example"></a><span data-ttu-id="6a28a-129">ステージング処理ストアド プロシージャの例</span><span class="sxs-lookup"><span data-stu-id="6a28a-129">Staging Process Stored Procedure Example</span></span>  
 <span data-ttu-id="6a28a-130">次の例は、ステージング ストアド プロシージャを使用してステージング処理を開始する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6a28a-130">The following example shows how to start the staging process by using the staging stored procedure.</span></span>  
  
```  
USE [DATABASE_NAME]  
GO  
  
EXEC[stg].[udp_name_Leaf]  
      @VersionName = N'VERSION_1',  
@LogFlag = 1,  
@BatchTag = N'batch1'  
  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="6a28a-131">参照</span><span class="sxs-lookup"><span data-stu-id="6a28a-131">See Also</span></span>  
 <span data-ttu-id="6a28a-132">[検証ストアドプロシージャ &#40;マスターデータサービス&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="6a28a-132">[Validation Stored Procedure &#40;Master Data Services&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md) </span></span>  
 <span data-ttu-id="6a28a-133">[ステージング処理を使用したマスターデータサービスのメンバーの読み込みまたは更新](add-update-and-delete-data-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="6a28a-133">[Load or Update Members in Master Data Services by Using the Staging Process](add-update-and-delete-data-master-data-services.md) </span></span>  
 [<span data-ttu-id="6a28a-134">ステージング処理中に発生したエラーを表示 &#40;マスターデータサービス&#41;</span><span class="sxs-lookup"><span data-stu-id="6a28a-134">View Errors that Occur During the Staging Process &#40;Master Data Services&#41;</span></span>](view-errors-that-occur-during-staging-master-data-services.md)  
  
  
