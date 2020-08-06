---
title: SharePoint ファームに必要なドメインアカウント (アップグレードアドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 90cd6d3e-a271-4cb8-81f2-fc555b2d3cab
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7d180fbc12a264256156c878916838f7caeec723
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645366"
---
# <a name="domain-accounts-required-for-sharepoint-farm-upgrade-advisor"></a><span data-ttu-id="23f7e-102">SharePoint ファームに必要なドメイン アカウント (アップグレード アドバイザー)</span><span class="sxs-lookup"><span data-stu-id="23f7e-102">Domain accounts required for SharePoint farm (Upgrade Advisor)</span></span>
  <span data-ttu-id="23f7e-103">ファーム環境向けに構成されている SharePoint 製品では、ドメイン アカウントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="23f7e-103">SharePoint products that are configured for a farm environment require that you use domain accounts.</span></span>  
  
||  
|-|  
|<span data-ttu-id="23f7e-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint モード。</span><span class="sxs-lookup"><span data-stu-id="23f7e-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="23f7e-105">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="23f7e-105">Component</span></span>  
 [!INCLUDE[ssRS](../../includes/ssrs.md)]  
  
### <a name="description"></a><span data-ttu-id="23f7e-106">説明</span><span class="sxs-lookup"><span data-stu-id="23f7e-106">Description</span></span>  
 <span data-ttu-id="23f7e-107">ファーム環境向けに構成されている SharePoint 製品では、サービスとデータベース接続にドメイン アカウントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="23f7e-107">SharePoint products that are configured for a farm environment require that you use domain accounts for services and database connections.</span></span> <span data-ttu-id="23f7e-108">これには、Reporting Services サービス アカウントに指定したアカウントも含まれます。</span><span class="sxs-lookup"><span data-stu-id="23f7e-108">This includes the account you have specified for the Reporting Services service account.</span></span>  
  
 <span data-ttu-id="23f7e-109">SharePoint 2010 のサーバーの全体管理ページを使用すると、1 か所で、Reporting Services にドメイン ユーザー アカウントを使用していない場合の問題を確認できます。</span><span class="sxs-lookup"><span data-stu-id="23f7e-109">SharePoint 2010 Central Administration pages are one place you will see problems if you are not using a domain user account for Reporting Services.</span></span> <span data-ttu-id="23f7e-110">Reporting Services 統合の構成を試みると、次のようなエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="23f7e-110">When you try to configure Reporting Services integration, you will see an error message similar to the following:</span></span>  
  
 <span data-ttu-id="23f7e-111">"レポート サーバーの実行に使用されているビルトイン NT AUTHORITY\NETWORK SERVICE アカウントは、SharePoint ファームのインストールでサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="23f7e-111">"The report server is running under the built-in NT AUTHORITY\NETWORK SERVICE account, which is not supported by a SharePoint farm installation.</span></span> <span data-ttu-id="23f7e-112">レポートサーバーを再構成して、ドメインアカウントで実行されるようにしてください。 "</span><span class="sxs-lookup"><span data-stu-id="23f7e-112">Please reconfigure the report server to run under a domain account."</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="23f7e-113">修正措置</span><span class="sxs-lookup"><span data-stu-id="23f7e-113">Corrective Action</span></span>  
 <span data-ttu-id="23f7e-114">以前のバージョンの場合は、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Reporting Services Configuration Manager を使用して、レポートサーバーサービスアカウントとして割り当てられているアカウントを変更します。</span><span class="sxs-lookup"><span data-stu-id="23f7e-114">For [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and previous versions, use the Reporting Services Configuration Manager to change the account that is assigned as the report server service account.</span></span>  
  
#### <a name="to-change-the-service-account-from-configuration-manager"></a><span data-ttu-id="23f7e-115">構成マネージャーでサービス アカウントを変更するには</span><span class="sxs-lookup"><span data-stu-id="23f7e-115">To change the service account from Configuration Manager</span></span>  
  
1.  <span data-ttu-id="23f7e-116">[**スタート**] メニューの [**すべてのプログラム**] をクリックし、[ **Microsoft SQL Server 2008 R2**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="23f7e-116">From the **Start** menu, select **All Programs**, and then click **Microsoft SQL Server 2008 R2**.</span></span>  
  
2.  <span data-ttu-id="23f7e-117">[**構成ツール**] を選択し、[ **Reporting Services Configuration Manager**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="23f7e-117">Select **Configuration Tools**, and then click **Reporting Services Configuration Manager**.</span></span>  
  
3.  <span data-ttu-id="23f7e-118">Configuration Manager で、[**サービスアカウント**] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="23f7e-118">In Configuration Manager, select the **Service Account** tab.</span></span>  
  
4.  <span data-ttu-id="23f7e-119">[**別のアカウントを使用する**] を選択し、ドメインアカウントの資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="23f7e-119">Select **Use another account** and enter the credentials for a domain account.</span></span>  
  
5.  <span data-ttu-id="23f7e-120">**[Apply]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="23f7e-120">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23f7e-121">参照</span><span class="sxs-lookup"><span data-stu-id="23f7e-121">See Also</span></span>  
 [<span data-ttu-id="23f7e-122">レポート サーバー サービス アカウントの構成 &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="23f7e-122">Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;</span></span>](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
  
  
