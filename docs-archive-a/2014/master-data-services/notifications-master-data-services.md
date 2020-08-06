---
title: 通知 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- notifications [Master Data Services]
- notifications [Master Data Services], about notifications
- e-mail [Master Data Services]
- e-mail [Master Data Services], about e-mail notifications
ms.assetid: d7ad32d5-9fe5-48fd-8c61-0b00c0aff082
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a61825f9450dd5b708aff8c3fc72f0f12732337b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645134"
---
# <a name="notifications-master-data-services"></a><span data-ttu-id="0bbd0-102">通知 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0bbd0-102">Notifications (Master Data Services)</span></span>
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]<span data-ttu-id="0bbd0-103">ビジネスルールの検証が失敗した場合、またはモデルのバージョンの状態が変更された場合に、電子メール通知を送信するようにを構成できます。</span><span class="sxs-lookup"><span data-stu-id="0bbd0-103">can be configured to send an email notification when business rule validation fails or the status of a model version changes.</span></span>  
  
## <a name="how-notifications-are-sent"></a><span data-ttu-id="0bbd0-104">通知の送信方法</span><span class="sxs-lookup"><span data-stu-id="0bbd0-104">How Notifications Are Sent</span></span>  
 <span data-ttu-id="0bbd0-105">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]の通知を構成します。</span><span class="sxs-lookup"><span data-stu-id="0bbd0-105">You configure notifications in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].</span></span> <span data-ttu-id="0bbd0-106">通知では、データベースをホストするのインスタンスでデータベースメールを使用して電子メールメッセージを送信し [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="0bbd0-106">Notifications send email messages by using Database Mail on the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] that hosts the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="0bbd0-107">データベース メールの詳細については、 [オンライン ブックの「](../relational-databases/database-mail/database-mail-configuration-objects.md) データベース メール構成オブジェクト [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0bbd0-107">For more information about Database Mail, see [Database Mail Configuration Objects](../relational-databases/database-mail/database-mail-configuration-objects.md) in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="when-notifications-are-sent"></a><span data-ttu-id="0bbd0-108">通知の送信タイミング</span><span class="sxs-lookup"><span data-stu-id="0bbd0-108">When Notifications Are Sent</span></span>  
 <span data-ttu-id="0bbd0-109">通知を構成すると、以降は次のインスタンスで自動の電子メール通知を送信できます。</span><span class="sxs-lookup"><span data-stu-id="0bbd0-109">After notifications are configured, automated email notifications can be sent in the following instances.</span></span>  
  
|<span data-ttu-id="0bbd0-110">インスタンス</span><span class="sxs-lookup"><span data-stu-id="0bbd0-110">Instance</span></span>|<span data-ttu-id="0bbd0-111">説明</span><span class="sxs-lookup"><span data-stu-id="0bbd0-111">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="0bbd0-112">データがビジネス ルール検証に失敗した場合</span><span class="sxs-lookup"><span data-stu-id="0bbd0-112">Data fails business rule validation</span></span>|<span data-ttu-id="0bbd0-113">属性値がビジネス ルールの検証に失敗した場合に電子メールを送信するように、個々のビジネス ルールを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bbd0-113">Individual business rules must be configured to send email when an attribute value fails business rule validation.</span></span> <span data-ttu-id="0bbd0-114">詳細については、「 [通知を送信するようにビジネス ルールを構成する (マスター データ サービス)](configure-business-rules-to-send-notifications-master-data-services.md)の通知を構成します。</span><span class="sxs-lookup"><span data-stu-id="0bbd0-114">For more information, see [Configure Business Rules to Send Notifications &#40;Master Data Services&#41;](configure-business-rules-to-send-notifications-master-data-services.md).</span></span>|  
|<span data-ttu-id="0bbd0-115">モデル バージョンの状態が変わった場合</span><span class="sxs-lookup"><span data-stu-id="0bbd0-115">Model version status changes</span></span>|<span data-ttu-id="0bbd0-116">モデル バージョンの状態が変わるたびに、モデル管理者であるユーザーは自動的に通知を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="0bbd0-116">Each time a model version's status changes, users that are model administrators receive notifications automatically.</span></span> <span data-ttu-id="0bbd0-117">詳細については、「[管理者 &#40;マスターデータサービス&#41;](../../2014/master-data-services/administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0bbd0-117">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>|  
  
## <a name="system-settings"></a><span data-ttu-id="0bbd0-118">システム設定</span><span class="sxs-lookup"><span data-stu-id="0bbd0-118">System Settings</span></span>  
 <span data-ttu-id="0bbd0-119">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] には、通知に影響を与える設定があります。</span><span class="sxs-lookup"><span data-stu-id="0bbd0-119">There are settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] that affect notifications.</span></span> <span data-ttu-id="0bbd0-120">これらの設定は、 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] で調整するか、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースの System Settings テーブルで直接調整することができます。</span><span class="sxs-lookup"><span data-stu-id="0bbd0-120">You can adjust these settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] or directly in the System Settings table in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="0bbd0-121">詳細については、「[システム設定 &#40;マスター データ サービス&#41;](../../2014/master-data-services/system-settings-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0bbd0-121">For more information, see [System Settings &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="0bbd0-122">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="0bbd0-122">Related Tasks</span></span>  
  
|<span data-ttu-id="0bbd0-123">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="0bbd0-123">Task Description</span></span>|<span data-ttu-id="0bbd0-124">トピック</span><span class="sxs-lookup"><span data-stu-id="0bbd0-124">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="0bbd0-125">電子メールの通知を送信するように [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] を構成する。</span><span class="sxs-lookup"><span data-stu-id="0bbd0-125">Configure [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] to send email notifications.</span></span>|[<span data-ttu-id="0bbd0-126">電子メール通知を構成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="0bbd0-126">Configure Email Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-email-notifications-master-data-services.md)|  
|<span data-ttu-id="0bbd0-127">属性値の変更時に通知を送信するように、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] を構成する。</span><span class="sxs-lookup"><span data-stu-id="0bbd0-127">Configure [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] to send notifications when attribute values change.</span></span>|[<span data-ttu-id="0bbd0-128">通知を送信するようにビジネス ルールを構成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="0bbd0-128">Configure Business Rules to Send Notifications &#40;Master Data Services&#41;</span></span>](configure-business-rules-to-send-notifications-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="0bbd0-129">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="0bbd0-129">Related Content</span></span>  
  
-   [<span data-ttu-id="0bbd0-130">ビジネス ルール (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="0bbd0-130">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
-   [<span data-ttu-id="0bbd0-131">バージョン (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="0bbd0-131">Versions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/versions-master-data-services.md)  
  
-   [<span data-ttu-id="0bbd0-132">電子メール通知のトラブルシューティング (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0bbd0-132">Troubleshooting Email Notifications (Master Data Services)</span></span>](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-email-notifications-master-data-services.aspx)  
  
  
