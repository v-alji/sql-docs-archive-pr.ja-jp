---
title: バージョン (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- version flags [Master Data Services], about version flags
- versions [Master Data Services]
- version flags [Master Data Services]
- versions [Master Data Services], version flags
ms.assetid: 752ec96d-53d7-4160-8ed2-92e0324645f3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6f8b55a32cdf2a5aabad38ee3d0d4154c2ad6a6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632008"
---
# <a name="versions-master-data-services"></a><span data-ttu-id="133a9-102">バージョン (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="133a9-102">Versions (Master Data Services)</span></span>
  <span data-ttu-id="133a9-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、モデル内に複数のバージョンのマスター データを作成できます。</span><span class="sxs-lookup"><span data-stu-id="133a9-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can create multiple versions of the master data within a model.</span></span> <span data-ttu-id="133a9-104">データを検証している間はバージョンをロックし、データが検証した後にコミットすることができます。</span><span class="sxs-lookup"><span data-stu-id="133a9-104">Versions can be locked while you validate your data and committed after the data is validated.</span></span> <span data-ttu-id="133a9-105">コミットされたバージョンは、変更の監査可能なレコードを形成します。</span><span class="sxs-lookup"><span data-stu-id="133a9-105">Committed versions form an auditable record of changes.</span></span> <span data-ttu-id="133a9-106">作成される各バージョンには、モデルのすべてのメンバー、属性値、階層メンバー、階層リレーションシップ、およびコレクションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="133a9-106">Each version you create contains all members, attribute values, hierarchy members, hierarchy relationships, and collections for the model.</span></span>  
  
## <a name="when-to-use-versions"></a><span data-ttu-id="133a9-107">バージョンを使用するタイミング</span><span class="sxs-lookup"><span data-stu-id="133a9-107">When to Use Versions</span></span>  
 <span data-ttu-id="133a9-108">バージョンは、次の場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="133a9-108">Use versions to:</span></span>  
  
-   <span data-ttu-id="133a9-109">時間と共に変化するマスター データの監査可能なレコードを保持する場合。</span><span class="sxs-lookup"><span data-stu-id="133a9-109">Maintain an auditable record of your master data as it changes over time.</span></span>  
  
-   <span data-ttu-id="133a9-110">ビジネス ルールに対してすべてのデータが正常に検証されるようにする間、ユーザーによる変更を防止する場合。</span><span class="sxs-lookup"><span data-stu-id="133a9-110">Prevent users from making changes while you ensure all data validates successfully against business rules.</span></span>  
  
-   <span data-ttu-id="133a9-111">サブスクライブ システムによって使用されるようにモデルをロック ダウンする場合。</span><span class="sxs-lookup"><span data-stu-id="133a9-111">Lock down a model for use by subscribing systems.</span></span>  
  
-   <span data-ttu-id="133a9-112">さまざまな階層をすぐに実装しないでテストする場合。</span><span class="sxs-lookup"><span data-stu-id="133a9-112">Test different hierarchies without implementing them right away.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="133a9-113">新しいエンティティまたはドメイン ベースの属性を作成するなど、モデルの構造を変更すると、その変更がすべてのバージョンに適用されます。</span><span class="sxs-lookup"><span data-stu-id="133a9-113">When you change the structure of your model, such as when you create a new entity or domain-based attribute, the change applies to all versions.</span></span> <span data-ttu-id="133a9-114">以前のバージョンのモデルを表示すると、エンティティまたは属性は表示されますが、データは存在しません。</span><span class="sxs-lookup"><span data-stu-id="133a9-114">If you view an earlier version of the model, the entity or attribute is displayed, but no data exists.</span></span>  
  
## <a name="version-flags"></a><span data-ttu-id="133a9-115">バージョン フラグ</span><span class="sxs-lookup"><span data-stu-id="133a9-115">Version Flags</span></span>  
 <span data-ttu-id="133a9-116">バージョンがユーザーまたはサブスクライブ システムによって使用される状態になったら、バージョンを識別するためのフラグを設定できます。</span><span class="sxs-lookup"><span data-stu-id="133a9-116">When a version is ready for users or for a subscribing system, you can set a flag to identify the version.</span></span> <span data-ttu-id="133a9-117">このフラグは、必要に応じてバージョン間で移動できます。</span><span class="sxs-lookup"><span data-stu-id="133a9-117">You can move this flag from version to version as needed.</span></span> <span data-ttu-id="133a9-118">フラグによって、ユーザーおよびサブスクライブ システムは使用するモデルのバージョンを識別できます。</span><span class="sxs-lookup"><span data-stu-id="133a9-118">Flags help users and subscribing systems identify which version of a model to use.</span></span>  
  
## <a name="workflow-for-version-management"></a><span data-ttu-id="133a9-119">バージョン管理のワークフロー</span><span class="sxs-lookup"><span data-stu-id="133a9-119">Workflow for Version Management</span></span>  
 <span data-ttu-id="133a9-120">次のワークフローを使用して、バージョン管理を行います。</span><span class="sxs-lookup"><span data-stu-id="133a9-120">Use the following workflow for version management:</span></span>  
  
1.  <span data-ttu-id="133a9-121">最初のバージョンは、モデルを作成して [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースに会社のマスター データを入力すると、自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="133a9-121">An initial version is created automatically when you create a model and populate the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database with your company's master data.</span></span> <span data-ttu-id="133a9-122">ユーザーは権限に基づいて、必要に応じてこのバージョンを変更できます。</span><span class="sxs-lookup"><span data-stu-id="133a9-122">Based on permissions, users can make changes to this version as needed.</span></span>  
  
2.  <span data-ttu-id="133a9-123">モデルのバージョンをコミットする場合は、モデル管理者のみがデータを更新できるように、バージョンをロックします。</span><span class="sxs-lookup"><span data-stu-id="133a9-123">When you want to commit a version of a model, lock the version so that only model administrators can update the data.</span></span> <span data-ttu-id="133a9-124">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="133a9-124">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span> <span data-ttu-id="133a9-125">通知が構成されている場合、バージョンのステータスが変更されるたびに電子メール通知がモデル管理者に送信されます。</span><span class="sxs-lookup"><span data-stu-id="133a9-125">If notifications are configured, an email notification is sent to model administrators each time the version's status changes.</span></span> <span data-ttu-id="133a9-126">詳細については、「[電子メール通知を構成する (マスター データ サービス)](../../2014/master-data-services/configure-email-notifications-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="133a9-126">For more information, see [Configure Email Notifications &#40;Master Data Services&#41;](../../2014/master-data-services/configure-email-notifications-master-data-services.md).</span></span>  
  
3.  <span data-ttu-id="133a9-127">ロックしたバージョンのデータにビジネス ルールを適用し、検証の問題がないか確認します。</span><span class="sxs-lookup"><span data-stu-id="133a9-127">Apply business rules to the locked version's data and review any validation issues.</span></span> <span data-ttu-id="133a9-128">必要に応じて、不足している情報を入力したり、問題の原因となったトランザクションを破棄したりできます。</span><span class="sxs-lookup"><span data-stu-id="133a9-128">If necessary, you can fill in missing information or revert the transaction that caused the issue.</span></span> <span data-ttu-id="133a9-129">ユーザーが変更できるように、バージョンのロックを解除することもできます。</span><span class="sxs-lookup"><span data-stu-id="133a9-129">You can also unlock the version for users to make changes.</span></span>  
  
4.  <span data-ttu-id="133a9-130">すべてのデータが検証に合格したら、バージョンをコミットし、サブスクライブ システムで使用できるようにバージョンにフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="133a9-130">When all the data passes validation, commit the version and flag it for use by subscribing systems.</span></span> <span data-ttu-id="133a9-131">コミットしたバージョンを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="133a9-131">Changes cannot be made to a committed version.</span></span>  
  
5.  <span data-ttu-id="133a9-132">コミットしたバージョンをコピーし、ユーザーに新しいバージョンのモデルで作業できるようになったことを通知します。</span><span class="sxs-lookup"><span data-stu-id="133a9-132">Copy the committed version and notify users that they can begin working in a new version of the model.</span></span>  
  
## <a name="sequential-or-simultaneous-versions"></a><span data-ttu-id="133a9-133">順次バージョンまたは同時バージョン</span><span class="sxs-lookup"><span data-stu-id="133a9-133">Sequential or Simultaneous Versions</span></span>  
 <span data-ttu-id="133a9-134">モデルの順次バージョンまたは同時バージョンを作成できます。</span><span class="sxs-lookup"><span data-stu-id="133a9-134">You can create sequential or simultaneous versions of your model.</span></span>  
  
-   <span data-ttu-id="133a9-135">**順次バージョン。**</span><span class="sxs-lookup"><span data-stu-id="133a9-135">**Sequential versions.**</span></span> <span data-ttu-id="133a9-136">バージョンをコミットするたびに、新しいコピーを作成して、バージョンに次の連続番号を付けます。</span><span class="sxs-lookup"><span data-stu-id="133a9-136">Each time you commit a version, create a new copy and give the version the next sequential number.</span></span> <span data-ttu-id="133a9-137">たとえば、 **バージョン 7** のモデルをコピーし、そのコピーに **バージョン 8**という名前を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="133a9-137">For example, you can copy **Version 7** of your model and name the copy **Version 8**.</span></span>  
  
-   <span data-ttu-id="133a9-138">**同時バージョン。**</span><span class="sxs-lookup"><span data-stu-id="133a9-138">**Simultaneous versions.**</span></span> <span data-ttu-id="133a9-139">一度に 2 つ以上のバージョンのデータで作業を行う場合は、モデルの同時バージョンを作成します。</span><span class="sxs-lookup"><span data-stu-id="133a9-139">Create simultaneous versions of your model when you want to work on two or more versions of your data at once.</span></span> <span data-ttu-id="133a9-140">同時バージョンは、通常の業務と並行して会社の再編や合併を行う場合に、新しいマスター データを既存の構造に適合させる方法を決める際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="133a9-140">This is useful when your company has reorganizations or mergers that coincide with the normal course of business and you want to determine how the new master data might fit into your existing structures.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="133a9-141">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] の設定によって、すべてのバージョンをコピーできるか、またはコミットされたバージョンのみをコピーできるかが決まります。</span><span class="sxs-lookup"><span data-stu-id="133a9-141">A setting in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] determines whether or not you can copy all versions or only those that are committed.</span></span> <span data-ttu-id="133a9-142">同時バージョンを作成するには、すべてのバージョンをコピーできるように [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="133a9-142">To create simultaneous versions you must configure [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] to allow you to copy all versions.</span></span> <span data-ttu-id="133a9-143">この設定は、System Settings テーブルでも行うことができます。</span><span class="sxs-lookup"><span data-stu-id="133a9-143">This setting is also available in the System Settings table.</span></span> <span data-ttu-id="133a9-144">詳細については、「[システム設定 &#40;マスター データ サービス&#41;](../../2014/master-data-services/system-settings-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="133a9-144">For more information, see [System Settings &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="133a9-145">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="133a9-145">Related Tasks</span></span>  
  
|<span data-ttu-id="133a9-146">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="133a9-146">Task Description</span></span>|<span data-ttu-id="133a9-147">トピック</span><span class="sxs-lookup"><span data-stu-id="133a9-147">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="133a9-148">既存のバージョンの名前を変更する。</span><span class="sxs-lookup"><span data-stu-id="133a9-148">Change the name of an existing version.</span></span>|[<span data-ttu-id="133a9-149">バージョン名を変更する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="133a9-149">Change a Version Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-version-name-master-data-services.md)|  
|<span data-ttu-id="133a9-150">管理者のみがデータを編集できるようにバージョンをロックする。</span><span class="sxs-lookup"><span data-stu-id="133a9-150">Lock a version so only administrators can edit its data.</span></span>|[<span data-ttu-id="133a9-151">バージョンをロックする (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="133a9-151">Lock a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/lock-a-version-master-data-services.md)|  
|<span data-ttu-id="133a9-152">ユーザーがデータを編集できるようにバージョンのロックを解除する。</span><span class="sxs-lookup"><span data-stu-id="133a9-152">Unlock a version so users can edit its data.</span></span>|[<span data-ttu-id="133a9-153">バージョンをロック解除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="133a9-153">Unlock a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/unlock-a-version-master-data-services.md)|  
|<span data-ttu-id="133a9-154">すべてのデータを検証した後にバージョンをコミットする。</span><span class="sxs-lookup"><span data-stu-id="133a9-154">Commit a version after all data is validated.</span></span>|[<span data-ttu-id="133a9-155">バージョンをコミットする (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="133a9-155">Commit a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/commit-a-version-master-data-services.md)|  
|<span data-ttu-id="133a9-156">新しいフラグを作成してバージョンをマークする。</span><span class="sxs-lookup"><span data-stu-id="133a9-156">Create a new flag to mark a version.</span></span>|[<span data-ttu-id="133a9-157">バージョン フラグを作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="133a9-157">Create a Version Flag &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-version-flag-master-data-services.md)|  
|<span data-ttu-id="133a9-158">既存のバージョンのフラグ名を変更する。</span><span class="sxs-lookup"><span data-stu-id="133a9-158">Change the name of an existing version flag.</span></span>|[<span data-ttu-id="133a9-159">バージョン フラグ名を変更する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="133a9-159">Change a Version Flag Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-version-flag-name-master-data-services.md)|  
|<span data-ttu-id="133a9-160">既存のフラグをバージョンに割り当てる。</span><span class="sxs-lookup"><span data-stu-id="133a9-160">Assign an existing flag to a version.</span></span>|[<span data-ttu-id="133a9-161">バージョンにフラグを割り当てる (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="133a9-161">Assign a Flag to a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-a-flag-to-a-version-master-data-services.md)|  
|<span data-ttu-id="133a9-162">既存のバージョンの新しいコピーを作成する。</span><span class="sxs-lookup"><span data-stu-id="133a9-162">Create a new copy of an existing version</span></span>|[<span data-ttu-id="133a9-163">バージョンをコピーする (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="133a9-163">Copy a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/copy-a-version-master-data-services.md)|  
|<span data-ttu-id="133a9-164">既存のバージョンを削除する。</span><span class="sxs-lookup"><span data-stu-id="133a9-164">Delete an existing version.</span></span>|[<span data-ttu-id="133a9-165">バージョンを削除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="133a9-165">Delete a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-version-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="133a9-166">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="133a9-166">Related Content</span></span>  
  
-   [<span data-ttu-id="133a9-167">トランザクションを破棄する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="133a9-167">Reverse a Transaction &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/reverse-a-transaction-master-data-services.md)  
  
-   [<span data-ttu-id="133a9-168">通知 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="133a9-168">Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/notifications-master-data-services.md)  
  
-   [<span data-ttu-id="133a9-169">ビジネス ルール (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="133a9-169">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
