---
title: ユーザーおよび警告管理者にアクセス許可を付与する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 166808e1-ada7-48d2-bda8-8f7c017fb3aa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5bf7f030871287379ce9fb32a1789b95cff0fc0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644844"
---
# <a name="grant-permissions-to-users-and-alerting-administrators"></a><span data-ttu-id="8c64e-102">ユーザーおよび警告管理者に権限を付与する</span><span class="sxs-lookup"><span data-stu-id="8c64e-102">Grant Permissions to Users and Alerting Administrators</span></span>
  <span data-ttu-id="8c64e-103">ユーザーおよび警告管理者がデータ警告を作成、編集、削除、および表示できるようにするには、SharePoint 権限を付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c64e-103">Before users and alerting administrators can create, edit, delete, and view data alerts they must be granted SharePoint permissions.</span></span> <span data-ttu-id="8c64e-104">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のデータ警告機能と共に使用する特別な権限はありません。組み込みの SharePoint 権限を使用します。</span><span class="sxs-lookup"><span data-stu-id="8c64e-104">There are no special permissions to use with the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] data alerting feature, you use the built-in SharePoint permissions.</span></span>  
  
 <span data-ttu-id="8c64e-105">**インフォメーション ワーカー**: SharePoint の "通知の作成" 権限と "アイテムの表示" 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="8c64e-105">**Information workers**-Permissions must include the Create Alert and View Items SharePoint permissions.</span></span> <span data-ttu-id="8c64e-106">組み込みの SharePoint 権限レベル (デザイン、投稿、読み取り、および表示のみ) には、SharePoint の "通知の作成" 権限と "アイテムの表示" 権限が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8c64e-106">The built-in SharePoint permission levels named Design, Contribute, Read, and View Only include the Create Alert and View Items SharePoint permissions.</span></span> <span data-ttu-id="8c64e-107">データ警告を作成、編集、実行、および表示するユーザーをサポートするために必要な権限を持つカスタム権限レベルを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="8c64e-107">You can also create a custom permission level with the permissions required to support users that create, edit, run, and view data alerts.</span></span>  
  
 <span data-ttu-id="8c64e-108">**警告管理者**: SharePoint の "通知の管理" 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="8c64e-108">**Alerting administrators**-Permissions must include the Manage Alert SharePoint permission.</span></span> <span data-ttu-id="8c64e-109">既定では、"チーム サイト" サイト テンプレートを使用して作成されたサイトに対するこの権限は、フル コントロール権限レベルにのみ含まれます。</span><span class="sxs-lookup"><span data-stu-id="8c64e-109">By default only the Full Control permission level includes this permission for sites created with the Team Site site template.</span></span> <span data-ttu-id="8c64e-110">他のサイト テンプレートを使用した場合は、既定の SharePoint グループの、異なる一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8c64e-110">If you use other site templates, you will see different lists of default SharePoint groups.</span></span> <span data-ttu-id="8c64e-111">"通知の管理" 権限を組み込みの権限レベルのいずれかに追加したり、データ警告を表示および削除する警告管理者をサポートするために必要な権限を持つカスタム権限レベルを作成したりできます。</span><span class="sxs-lookup"><span data-stu-id="8c64e-111">You can add the Manage Alert permission to one of the built-in permission levels or create a custom permission level with the permission required to support alerting administrators that view and delete data alerts.</span></span>  
  
 <span data-ttu-id="8c64e-112">SharePoint 権限の詳細については、「 [ユーザー権限とアクセス許可レベル (SharePoint Server 2010)](https://technet.microsoft.com/library/cc721640.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c64e-112">To learn more about SharePoint permissions, see [User permissions and permission levels (SharePoint Server 2010)](https://technet.microsoft.com/library/cc721640.aspx).</span></span>  
  
### <a name="to-grant-permissions"></a><span data-ttu-id="8c64e-113">権限を付与するには</span><span class="sxs-lookup"><span data-stu-id="8c64e-113">To grant permissions</span></span>  
  
1.  <span data-ttu-id="8c64e-114">権限を付与する SharePoint サイトに移動します。</span><span class="sxs-lookup"><span data-stu-id="8c64e-114">Go to the SharePoint site to which you want to grant permissions.</span></span>  
  
2.  <span data-ttu-id="8c64e-115">ツール バーの **[サイトの操作]** をクリックし、 **[サイトの権限]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c64e-115">On the toolbar, click **Site Actions** and then click **Site Permissions**.</span></span>  
  
     <span data-ttu-id="8c64e-116">このオプションが表示されない場合は、他のユーザーに権限を付与する権限がありません。</span><span class="sxs-lookup"><span data-stu-id="8c64e-116">If you do not see this option, you do not sufficient permission to grant permissions to others.</span></span>  
  
3.  <span data-ttu-id="8c64e-117">**[アクセス許可の付与]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c64e-117">Click **Grant Permissions**.</span></span>  
  
4.  <span data-ttu-id="8c64e-118">**[ユーザー/グループ]** ボックスに、権限を付与するユーザー名、グループ名、または電子メール アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="8c64e-118">In **Users/Groups**, type the user names, group names, or e-mail addresses you want grant permission to.</span></span>  
  
5.  <span data-ttu-id="8c64e-119">**[SharePoint グループへのユーザーの追加]** または **[ユーザーにアクセス許可を直接付与する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c64e-119">Select the **Add users to a SharePoint group** or **Grant users permission directly** option.</span></span> <span data-ttu-id="8c64e-120">**[SharePoint グループへのユーザーの追加]** と **[ユーザーにアクセス許可を直接付与する]** のどちらを選択したかに応じて、次のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="8c64e-120">Depending on whether you selected **Add users to a SharePoint group** or **Grant users permissions directly** do one of the following:</span></span>  
  
    -   <span data-ttu-id="8c64e-121">**[SharePoint グループへのユーザーの追加]** をクリックした場合は、ドロップダウン リストで権限レベルを選択します。</span><span class="sxs-lookup"><span data-stu-id="8c64e-121">If you selected **Add users to a SharePoint group**, select a permission level in the drop-down list.</span></span>  
  
    -   <span data-ttu-id="8c64e-122">**[ユーザーにアクセス許可を直接付与する]** をクリックした場合は、権限レベルを選択します。</span><span class="sxs-lookup"><span data-stu-id="8c64e-122">If you selected **Grant users permissions directly**, select a permission level.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8c64e-123">参照</span><span class="sxs-lookup"><span data-stu-id="8c64e-123">See Also</span></span>  
 <span data-ttu-id="8c64e-124">[Sharepoint サイト上のレポートサーバーアイテムに対する権限を設定するには、SharePoint 統合モードで Reporting Services &#40;&#41;](security/set-permissions-for-report-server-items-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="8c64e-124">[Set Permissions for Report Server Items on a SharePoint Site &#40;Reporting Services in SharePoint Integrated Mode&#41;](security/set-permissions-for-report-server-items-on-a-sharepoint-site.md) </span></span>  
 [<span data-ttu-id="8c64e-125">Reporting Services のデータ警告</span><span class="sxs-lookup"><span data-stu-id="8c64e-125">Reporting Services Data Alerts</span></span>](../ssms/agent/alerts.md)  
  
  
