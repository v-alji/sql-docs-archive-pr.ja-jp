---
title: 通知を送信するようにビジネス ルールを構成する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], configuring notifications
- e-mail [Master Data Services], configuring business rules
- notifications [Master Data Services], configuring business rules
ms.assetid: b24f7b11-ab53-4642-999c-e17b543b3558
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cb1a12167dffe123e55760f031e21499fe22a945
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646204"
---
# <a name="configure-business-rules-to-send-notifications-master-data-services"></a><span data-ttu-id="77593-102">通知を送信するようにビジネス ルールを構成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="77593-102">Configure Business Rules to Send Notifications (Master Data Services)</span></span>
  <span data-ttu-id="77593-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、属性値の変更をユーザーに通知する場合は、通知を送信するようにビジネス ルールを構成します。</span><span class="sxs-lookup"><span data-stu-id="77593-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], configure business rules to send notifications when you want to notify users about attribute value changes.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="77593-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="77593-104">Prerequisites</span></span>  
 <span data-ttu-id="77593-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="77593-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="77593-106">**[システム管理]** および **[ユーザー/グループの権限]** 機能領域にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="77593-106">You must have permission to access the **System Administration** and **User and Group Permissions** functional areas.</span></span> <span data-ttu-id="77593-107">**[ユーザー/グループの権限]** 機能領域に対する権限がないと、通知を送信するユーザーおよびグループの一覧を表示できません。</span><span class="sxs-lookup"><span data-stu-id="77593-107">If you do not have permission to the **User and Group Permissions** functional area, you cannot view the list of users and groups to send notifications to.</span></span>  
  
-   <span data-ttu-id="77593-108">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="77593-108">You must be a model administrator.</span></span> <span data-ttu-id="77593-109">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77593-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="77593-110">検証アクションを使用するビジネス ルールが既に存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="77593-110">A business rule that uses a validation action must already exist.</span></span> <span data-ttu-id="77593-111">詳細については、「[ビジネス ルールを作成しパブリッシュする (マスター データ サービス)](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77593-111">For more information, see [Create and Publish a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="77593-112">通知を受け取るユーザーまたはグループには、検証に失敗した属性に対する **読み取り専用** 以上の権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="77593-112">The user or group that receives the notification must have at least **Read-only** permission to the attribute that fails validation.</span></span> <span data-ttu-id="77593-113">属性に対する権限が明示的または暗黙的に拒否されるユーザーまたはグループは、電子メールを受け取りますが、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で属性にアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="77593-113">Users or groups that are explicitly or implicitly denied permission to the attribute will receive the email but will not be able to access the attribute in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
-   <span data-ttu-id="77593-114">メールがグループに送信された場合は、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] にアクセスしたグループ メンバーのみが電子メールを受信します。</span><span class="sxs-lookup"><span data-stu-id="77593-114">If mail is sent to a group, only members of the group that have accessed [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] will get the email.</span></span>  
  
### <a name="to-configure-business-rules-to-send-notifications"></a><span data-ttu-id="77593-115">通知を送信するようにビジネス ルールを構成するには</span><span class="sxs-lookup"><span data-stu-id="77593-115">To configure business rules to send notifications</span></span>  
  
1.  <span data-ttu-id="77593-116">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77593-116">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="77593-117">メニュー バーから **[管理]** をポイントして **[ビジネス ルール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77593-117">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="77593-118">**[ビジネス ルールのメンテナンス]** ページの **[モデル]** の一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="77593-118">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="77593-119">**[エンティティ]** の一覧からエンティティを選択します。</span><span class="sxs-lookup"><span data-stu-id="77593-119">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="77593-120">[**メンバーの種類**] ボックスの一覧から、メンバーの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="77593-120">From the **Member Type** list, select a type of member.</span></span>  
  
6.  <span data-ttu-id="77593-121">**[属性]** の一覧で、属性を選択するか、 **[すべて]** の既定値のままにします。</span><span class="sxs-lookup"><span data-stu-id="77593-121">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="77593-122">グリッドのビジネスルールの行で、[**通知**] フィールドをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="77593-122">In the grid, in the row for the business rule, double-click the **Notification** field.</span></span>  
  
8.  <span data-ttu-id="77593-123">サブメニューから、電子メール通知を送信するユーザーまたはグループをクリックします。</span><span class="sxs-lookup"><span data-stu-id="77593-123">From the sub-menu, click a user or group to send the email notification to.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="77593-124">次の手順</span><span class="sxs-lookup"><span data-stu-id="77593-124">Next Steps</span></span>  
  
-   <span data-ttu-id="77593-125">以下のいずれかの手順でビジネス ルールをデータに適用します。</span><span class="sxs-lookup"><span data-stu-id="77593-125">Apply business rules to data by following one of these procedures:</span></span>  
  
    -   [<span data-ttu-id="77593-126">ビジネス ルールに対して特定のメンバーを検証する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="77593-126">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [<span data-ttu-id="77593-127">ビジネス ルールに対してバージョンを検証する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="77593-127">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   <span data-ttu-id="77593-128">電子メール プロトコルを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="77593-128">Configure the email protocol as follows:</span></span>  
  
    -   [<span data-ttu-id="77593-129">電子メール通知を構成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="77593-129">Configure Email Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-email-notifications-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="77593-130">参照</span><span class="sxs-lookup"><span data-stu-id="77593-130">See Also</span></span>  
 <span data-ttu-id="77593-131">[通知 &#40;マスターデータサービス&#41;](../../2014/master-data-services/notifications-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="77593-131">[Notifications &#40;Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md) </span></span>  
 [<span data-ttu-id="77593-132">電子メール通知を構成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="77593-132">Configure Email Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-email-notifications-master-data-services.md)  
  
  
