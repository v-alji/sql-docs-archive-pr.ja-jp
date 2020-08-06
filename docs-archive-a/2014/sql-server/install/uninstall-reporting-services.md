---
title: Reporting Services のアンインストール | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 5c764a00-d4bc-465d-b32e-e4efce052ce4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2870f7f84ea626b96560af586602996de3657276
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640396"
---
# <a name="uninstall-reporting-services"></a><span data-ttu-id="c8d40-102">Reporting Services のアンインストール</span><span class="sxs-lookup"><span data-stu-id="c8d40-102">Uninstall Reporting Services</span></span>
  <span data-ttu-id="c8d40-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をアンインストールすると、作成したコンテンツや変更した構成が削除されます。</span><span class="sxs-lookup"><span data-stu-id="c8d40-103">Uninstalling [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] does not remove the content you have created or configuration you have modified.</span></span> <span data-ttu-id="c8d40-104">ただし、アンインストールの完了後に必要なコンテンツがある場合は、アンインストール プロセスを開始する前に、コンテンツのコピーを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c8d40-104">However, if there is content you need after the uninstall is complete, it is recommended you make copies of content before you begin the uninstallation process.</span></span>

## <a name="uninstall-sharepoint-mode"></a><span data-ttu-id="c8d40-105">SharePoint モードのアンインストール</span><span class="sxs-lookup"><span data-stu-id="c8d40-105">Uninstall SharePoint Mode</span></span>
 <span data-ttu-id="c8d40-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードをアンインストールすると、次のものが削除されます。</span><span class="sxs-lookup"><span data-stu-id="c8d40-106">When you uninstall [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode, the following are removed:</span></span>

-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="c8d40-107">のサービスおよびサービス プロキシ。</span><span class="sxs-lookup"><span data-stu-id="c8d40-107">service and service proxy.</span></span>

-   <span data-ttu-id="c8d40-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインストールに使用するファイル</span><span class="sxs-lookup"><span data-stu-id="c8d40-108">Files used for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation.</span></span>

 <span data-ttu-id="c8d40-109">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションは削除されません。</span><span class="sxs-lookup"><span data-stu-id="c8d40-109">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications are not removed.</span></span> <span data-ttu-id="c8d40-110">サービス アプリケーションが必要なくなった場合は、Windows PowerShell または SharePoint サーバーの全体管理を使用して削除してください。</span><span class="sxs-lookup"><span data-stu-id="c8d40-110">If you no longer want the service applications, delete them by using Windows PowerShell or SharePoint Central Administration.</span></span>

 <span data-ttu-id="c8d40-111">レポート アイテムと関連するメタデータは削除されません。</span><span class="sxs-lookup"><span data-stu-id="c8d40-111">The report items and related meta data are not removed.</span></span> <span data-ttu-id="c8d40-112">この情報は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションに関連するコンテンツ データベースと構成データベースに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c8d40-112">This information is contained in the content and configuration databases related to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications.</span></span> <span data-ttu-id="c8d40-113">これらのデータベースは削除されません。SharePoint モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の別のインストールにデータベースを手動で移行できます。</span><span class="sxs-lookup"><span data-stu-id="c8d40-113">The databases are not removed and you can manually migrate the databases to another installation of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="c8d40-114">情報が必要なくなった場合は、データベースを削除してください。</span><span class="sxs-lookup"><span data-stu-id="c8d40-114">If you no longer want the information, delete the databases.</span></span> <span data-ttu-id="c8d40-115">詳細については、「 [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8d40-115">For more information, see [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).</span></span>

 <span data-ttu-id="c8d40-116">削除されない 3 つの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] データベースの名前の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c8d40-116">The following are example names of the three [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] databases that are not removed.</span></span>

-   <span data-ttu-id="c8d40-117">**レポート サーバー データベース:** ReportingService_7f616e2d253040e8ab5653b3c09a065e</span><span class="sxs-lookup"><span data-stu-id="c8d40-117">**Report server database:** ReportingService_7f616e2d253040e8ab5653b3c09a065e</span></span>

-   <span data-ttu-id="c8d40-118">**レポート サーバーの一時データベース:** ReportingService_7f616e2d253040e8ab5653b3c09a065eTempDB</span><span class="sxs-lookup"><span data-stu-id="c8d40-118">**Report server temp database:** ReportingService_7f616e2d253040e8ab5653b3c09a065eTempDB</span></span>

-   <span data-ttu-id="c8d40-119">**レポート サーバーの警告データベース:** ReportingService_7f616e2d253040e8ab5653b3c09a065e_Alerting</span><span class="sxs-lookup"><span data-stu-id="c8d40-119">**Report server alerting database:** ReportingService_7f616e2d253040e8ab5653b3c09a065e_Alerting</span></span>

### <a name="uninstall-the-add-in-for-sharepoint-products"></a><span data-ttu-id="c8d40-120">SharePoint 製品用のアドインのアンインストール</span><span class="sxs-lookup"><span data-stu-id="c8d40-120">Uninstall the Add-in for SharePoint Products.</span></span>
 <span data-ttu-id="c8d40-121">コンピューターからアドインをアンインストールする場合は、ファイルのみをアンインストールするか、ファームから [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の機能も削除するかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="c8d40-121">When you uninstall the add-in from a computer, you can choose to only uninstall the files or to also remove the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] feature from the farm.</span></span> <span data-ttu-id="c8d40-122">SharePoint 製品用アドインのアンインストールの詳細につい [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ては、「sharepoint [2010 および sharepoint 2013&#41;用 &#40;の Reporting Services アドインのインストールまたはアンインストール](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8d40-122">For information on uninstalling the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint products, see [Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).</span></span>

## <a name="uninstall-native-mode"></a><span data-ttu-id="c8d40-123">ネイティブ モードのアンインストール</span><span class="sxs-lookup"><span data-stu-id="c8d40-123">Uninstall Native Mode</span></span>
 <span data-ttu-id="c8d40-124">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モードをアンインストールすると、インストール後に **作成** または **変更** された内容がすべて残ります。</span><span class="sxs-lookup"><span data-stu-id="c8d40-124">When you uninstall [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] native mode, anything that was **created** or **modified** after the installation is left in place.</span></span> <span data-ttu-id="c8d40-125">たとえば、データベース ファイル、ログ ファイル、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ファイル、コンテンツ アイテム (レポートやデータソース ファイルなど) がこれに含まれます。</span><span class="sxs-lookup"><span data-stu-id="c8d40-125">For example database files, log files, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] configuration files, and content items such as reports and datasource files.</span></span>

 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="c8d40-126">はインスタンス機能であるため、Windows のコントロール パネルの [プログラムと機能] には表示されません。</span><span class="sxs-lookup"><span data-stu-id="c8d40-126">is an instance feature and therefore is not listed in Windows Control Panel, Programs and Features.</span></span> <span data-ttu-id="c8d40-127">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モードをアンインストールするには</span><span class="sxs-lookup"><span data-stu-id="c8d40-127">To uninstall [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode:</span></span>

1.  <span data-ttu-id="c8d40-128">Windows のコントロール パネルで **[プログラムと機能]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8d40-128">In Windows Control Panel, click **Programs and Features**.</span></span>

2.  <span data-ttu-id="c8d40-129">**[プログラムと機能]** で **[Microsoft SQL Server 2012]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c8d40-129">In **Programs and Features** select **Microsoft SQL Server 2012**.</span></span>

3.  <span data-ttu-id="c8d40-130">アンインストール ウィザードで、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インスタンス機能 **RS**を含むインスタンスを選択します。</span><span class="sxs-lookup"><span data-stu-id="c8d40-130">In the uninstall wizard, select the instance that includes the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance feature **RS**.</span></span>

     <span data-ttu-id="c8d40-131">![rs_nativemode_uninstall_selectinstance](../../../2014/sql-server/install/media/rs-nativemode-uninstall-selectinstance.gif "rs_nativemode_uninstall_selectinstance")</span><span class="sxs-lookup"><span data-stu-id="c8d40-131">![rs_nativemode_uninstall_selectinstance](../../../2014/sql-server/install/media/rs-nativemode-uninstall-selectinstance.gif "rs_nativemode_uninstall_selectinstance")</span></span>

4.  <span data-ttu-id="c8d40-132">インスタンスを選択した後で、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 機能を選択します。</span><span class="sxs-lookup"><span data-stu-id="c8d40-132">After you select the instance, select the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] feature.</span></span>

     <span data-ttu-id="c8d40-133">![rs_nativemode_uninstall_selectfeatures](../../../2014/sql-server/install/media/rs-nativemode-uninstall-selectfeatures.gif "rs_nativemode_uninstall_selectfeatures")</span><span class="sxs-lookup"><span data-stu-id="c8d40-133">![rs_nativemode_uninstall_selectfeatures](../../../2014/sql-server/install/media/rs-nativemode-uninstall-selectfeatures.gif "rs_nativemode_uninstall_selectfeatures")</span></span>

5.  <span data-ttu-id="c8d40-134">ウィザードを完了します。</span><span class="sxs-lookup"><span data-stu-id="c8d40-134">Complete the wizard.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8d40-135">参照</span><span class="sxs-lookup"><span data-stu-id="c8d40-135">See Also</span></span>
 <span data-ttu-id="c8d40-136">[SQL Server の既存のインスタンスをアンインストールする &#40;セットアップ&#41;](../../../2014/sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md) [PowerPivot for SharePoint アドイン &#40;sharepoint 2013 をインストール](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)またはアンインストール&#41;Sharepoint[用の Reporting Services アドイン &#40;sharepoint 2010 および sharepoint 2013 をインストールまたはアンインストール](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="c8d40-136">[Uninstall an Existing Instance of SQL Server &#40;Setup&#41;](../../../2014/sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md) [Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) [Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)</span></span>


