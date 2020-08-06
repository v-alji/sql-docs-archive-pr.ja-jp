---
title: 電子メール通知を構成する (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- e-mail [Master Data Services], configuring
- notifications [Master Data Services], configuring notifications
ms.assetid: 4241a6ab-7465-471b-9890-57c6b572037e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: baf60677435122af00f5ee5492e47bafaa45a3ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646203"
---
# <a name="configure-email-notifications-master-data-services"></a><span data-ttu-id="92181-102">電子メール通知を構成する (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="92181-102">Configure Email Notifications (Master Data Services)</span></span>
  <span data-ttu-id="92181-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] で電子メール メッセージを自動的に送信する場合は、通知電子メールを構成します。</span><span class="sxs-lookup"><span data-stu-id="92181-103">Configure notification emails when you want [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] to send email messages automatically.</span></span>  
  
### <a name="to-configure-notifications"></a><span data-ttu-id="92181-104">通知を構成するには</span><span class="sxs-lookup"><span data-stu-id="92181-104">To configure notifications</span></span>  
  
1.  <span data-ttu-id="92181-105">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]の **[データベース]** ページで、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="92181-105">In [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], on the **Database** page, select your [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="92181-106">**[システム設定]** セクションで、 **[プロファイルの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="92181-106">In the **System Settings** section, click **Create Profile**.</span></span>  
  
3.  <span data-ttu-id="92181-107">すべての必須フィールドを入力します。</span><span class="sxs-lookup"><span data-stu-id="92181-107">Complete all required fields.</span></span> <span data-ttu-id="92181-108">詳細については、「[[データベース メール プロファイルとアカウントの作成] ダイアログ ボックス (マスター データ サービス構成マネージャー)](../../2014/master-data-services/create-database-mail-profile-and-account-dialog-box.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92181-108">For more information, see [Create Database Mail Profile and Account Dialog Box &#40;Master Data Services Configuration Manager&#41;](../../2014/master-data-services/create-database-mail-profile-and-account-dialog-box.md).</span></span>  
  
4.  <span data-ttu-id="92181-109">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="92181-109">Click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="92181-110">通知を構成した後に [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] を使用して変更を加えることはできません。</span><span class="sxs-lookup"><span data-stu-id="92181-110">After you configure notifications, you cannot use [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] to make changes.</span></span> <span data-ttu-id="92181-111">変更は [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースで直接行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="92181-111">You must make changes directly in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="92181-112">詳細については、「 [データベース メール構成オブジェクト](../relational-databases/database-mail/database-mail-configuration-objects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92181-112">For more information, see [Database Mail Configuration Objects](../relational-databases/database-mail/database-mail-configuration-objects.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="92181-113">次の手順</span><span class="sxs-lookup"><span data-stu-id="92181-113">Next Steps</span></span>  
  
-   <span data-ttu-id="92181-114">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] には、通知に影響を与える設定があります。</span><span class="sxs-lookup"><span data-stu-id="92181-114">There are settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] that affect notifications.</span></span> <span data-ttu-id="92181-115">これらの設定は、 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] で調整するか、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースの System Settings テーブルで直接調整することができます。</span><span class="sxs-lookup"><span data-stu-id="92181-115">You can adjust these settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] or directly in the System Settings table in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="92181-116">詳細については、「[システム設定 &#40;マスター データ サービス&#41;](system-settings-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92181-116">For more information, see [System Settings &#40;Master Data Services&#41;](system-settings-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92181-117">参照</span><span class="sxs-lookup"><span data-stu-id="92181-117">See Also</span></span>  
 <span data-ttu-id="92181-118">[通知 &#40;マスターデータサービス&#41;](../../2014/master-data-services/notifications-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="92181-118">[Notifications &#40;Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md) </span></span>  
 <span data-ttu-id="92181-119">[電子メール通知のトラブルシューティング (マスターデータサービス)](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-email-notifications-master-data-services.aspx) </span><span class="sxs-lookup"><span data-stu-id="92181-119">[Troubleshooting Email Notifications (Master Data Services)](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-email-notifications-master-data-services.aspx) </span></span>  
 [<span data-ttu-id="92181-120">通知を送信するようにビジネス ルールを構成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="92181-120">Configure Business Rules to Send Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  
