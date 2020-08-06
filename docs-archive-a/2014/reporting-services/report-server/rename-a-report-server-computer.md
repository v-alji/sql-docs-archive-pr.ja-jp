---
title: レポート サーバー コンピューターの名前の変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- renaming report servers
ms.assetid: 82fc4ba2-291a-4939-a025-271b8d687c54
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fe8f699c17f9e5f1e11406ac6e5c161488767ed1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645395"
---
# <a name="rename-a-report-server-computer"></a><span data-ttu-id="32fbb-102">レポート サーバー コンピューターの名前の変更</span><span class="sxs-lookup"><span data-stu-id="32fbb-102">Rename a Report Server Computer</span></span>
  <span data-ttu-id="32fbb-103">コンピューターの名前を変更すると、同じコンピューター上に存在する Web サーバーおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前が対応して変更されます。</span><span class="sxs-lookup"><span data-stu-id="32fbb-103">Renaming a computer causes a corresponding name change for the Web server and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance (if it is on the same computer).</span></span> <span data-ttu-id="32fbb-104">場合によっては、コンピューター名を変更した後に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] にアクセスできなくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="32fbb-104">In some cases, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] may not be accessible after a computer name change.</span></span> <span data-ttu-id="32fbb-105">コンピューター名を変更した後にレポート サーバーを再構成するには、このトピックで説明する手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="32fbb-105">Use the steps provided in this topic to reconfigure a report server after a computer name change.</span></span>  
  
## <a name="renaming-a-sql-server-database-engine"></a><span data-ttu-id="32fbb-106">SQL Server データベース エンジンの名前の変更</span><span class="sxs-lookup"><span data-stu-id="32fbb-106">Renaming a SQL Server Database Engine</span></span>  
 <span data-ttu-id="32fbb-107">レポートサーバーデータベースを実行するインスタンスの名前を変更する場合は [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="32fbb-107">If you rename the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] instance that runs the report server database, do the following:</span></span>  
  
1.  <span data-ttu-id="32fbb-108">Reporting Services 構成ツールを起動し、名前が変更されたサーバー上のレポート サーバー データベースを使用するレポート サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="32fbb-108">Start the Reporting Services Configuration tool and connect to the report server that uses the report server database on the renamed server.</span></span>  
  
2.  <span data-ttu-id="32fbb-109">[データベースのセットアップ] ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="32fbb-109">Open the Database Setup page.</span></span>  
  
3.  <span data-ttu-id="32fbb-110">**[サーバー名]** で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の名前を入力または選択し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="32fbb-110">In **Server Name**, type or select the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] name, and then click **Connect**.</span></span>  
  
4.  <span data-ttu-id="32fbb-111">**[Apply]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="32fbb-111">Click **Apply**.</span></span>  
  
 <span data-ttu-id="32fbb-112">レポート サーバーがローカルの [!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスを使用している場合は、 *(local)* または *(local)\instancename* を使用して、サーバーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="32fbb-112">If the report server is using a local [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance, you can use *(local)* or *(local)\instancename* to specify the server.</span></span> <span data-ttu-id="32fbb-113">*(local)* を使用してサーバーを参照する場合は、サーバーの名前を変更しても、接続は引き続き機能します。</span><span class="sxs-lookup"><span data-stu-id="32fbb-113">If you use *(local)* to refer to the server, you can rename the server and the connections will continue to work.</span></span> <span data-ttu-id="32fbb-114">リモート サーバーを使用している場合や、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] がサーバー名を使用して構成されている場合は、サーバー名を変更するたびに、データベース接続情報を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32fbb-114">If you are using a remote server, or if [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is configured using the server name, you must update the database connection information whenever the server name is changed.</span></span>  
  
## <a name="renaming-a-report-server-computer"></a><span data-ttu-id="32fbb-115">レポート サーバー コンピューターの名前の変更</span><span class="sxs-lookup"><span data-stu-id="32fbb-115">Renaming a Report Server Computer</span></span>  
 <span data-ttu-id="32fbb-116">レポート サーバーを実行するコンピューターの名前を変更する場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="32fbb-116">If you rename a computer that runs a report server, do the following:</span></span>  
  
1.  <span data-ttu-id="32fbb-117">テキストエディターで**RSReportServer.config**を開き、 `UrlRoot` 新しいサーバー名を反映するように設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="32fbb-117">Open **RSReportServer.config** in a text editor and modify the `UrlRoot` setting to reflect the new server name.</span></span> <span data-ttu-id="32fbb-118">`UrlRoot` 設定は、レポート サーバーに格納されているアイテムへのアクセスに使用する URL を構成するために、配信拡張機能によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="32fbb-118">The `UrlRoot` setting is used by delivery extensions to compose the URL used to access items stored on the report server.</span></span> <span data-ttu-id="32fbb-119">レポート サーバーの URL アドレスを変更するには、`UrlRoot` 設定を更新し、サブスクリプションによってレポートが引き続き適切に配信されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="32fbb-119">Changing the report server URL address requires that you update the `UrlRoot` setting so that subscriptions continue to deliver reports as expected.</span></span>  
  
2.  <span data-ttu-id="32fbb-120">同じファイルで、`ReportServerUrl` が設定されている場合は、新しいサーバー名を反映するようにこの設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="32fbb-120">In the same file, if it is set, modify the `ReportServerUrl` setting to reflect the new server name.</span></span> <span data-ttu-id="32fbb-121">この設定はすべてのインストールで使用されているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="32fbb-121">Note that this setting is not used in every installation.</span></span> <span data-ttu-id="32fbb-122">この設定が空の場合は、何もしません。</span><span class="sxs-lookup"><span data-stu-id="32fbb-122">If it is empty, do nothing.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="32fbb-123">企業ネットワークで Windows インターネット ネーム サービス (WINS) を使用している場合は、レポート サーバーとレポート マネージャーを以前の名前でしばらく利用できることがあります。</span><span class="sxs-lookup"><span data-stu-id="32fbb-123">If you are using Windows Internet Naming Service (WINS) on your corporate network, the report server and Report Manager may continue to be available under the previous name for a period of time.</span></span> <span data-ttu-id="32fbb-124">WINS は、サービスを提供する各コンピューターに IP アドレスをマップします。</span><span class="sxs-lookup"><span data-stu-id="32fbb-124">WINS maps an IP address to each computer it services.</span></span> <span data-ttu-id="32fbb-125">名前を変更したコンピューターの IP アドレスを WINS が更新した後は、古いコンピューター名を使用してレポート サーバーまたはレポート マネージャーにアクセスすることはできなくなります。</span><span class="sxs-lookup"><span data-stu-id="32fbb-125">After WINS refreshes the IP address for the renamed computer, the old computer name can no longer be used to access a report server or Report Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32fbb-126">参照</span><span class="sxs-lookup"><span data-stu-id="32fbb-126">See Also</span></span>  
 <span data-ttu-id="32fbb-127">[RSReportServer 構成ファイル](rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="32fbb-127">[RSReportServer Configuration File](rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="32fbb-128">[Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="32fbb-128">[Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span></span>  
 <span data-ttu-id="32fbb-129">[Reporting Services レポート サーバー (ネイティブ モード)](reporting-services-report-server-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="32fbb-129">[Reporting Services Report Server &#40;Native Mode&#41;](reporting-services-report-server-native-mode.md) </span></span>  
 <span data-ttu-id="32fbb-130">[Start and Stop the Report Server Service](start-and-stop-the-report-server-service.md) </span><span class="sxs-lookup"><span data-stu-id="32fbb-130">[Start and Stop the Report Server Service](start-and-stop-the-report-server-service.md) </span></span>  
 [<span data-ttu-id="32fbb-131">rsconfig ユーティリティ &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="32fbb-131">rsconfig Utility &#40;SSRS&#41;</span></span>](../tools/rsconfig-utility-ssrs.md)  
  
  
