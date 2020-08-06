---
title: サーバーの全体管理でサイトコレクションの PowerPivot 機能の統合をアクティブにする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 62a27e53-446a-42d7-b5db-c009e02d4904
author: minewiskan
ms.author: owend
ms.openlocfilehash: b565434cba197d04327e833d4ac6eab3caf96646
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714606"
---
# <a name="activate-powerpivot-feature-integration-for-site-collections-in-central-administration"></a><span data-ttu-id="0f360-102">サイト コレクションを対象とした PowerPivot 機能の統合をサーバーの全体管理でアクティブ化する方法</span><span class="sxs-lookup"><span data-stu-id="0f360-102">Activate PowerPivot Feature Integration for Site Collections in Central Administration</span></span>
  <span data-ttu-id="0f360-103">[既存のファーム] インストール オプションを使用して SQL Server PowerPivot for SharePoint をインストールした場合は、サイト コレクションごとに PowerPivot 機能の統合をアクティブ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f360-103">Activating PowerPivot feature integration for specific site collections is required if you used the Existing Farm installation option to install SQL Server PowerPivot for SharePoint.</span></span> <span data-ttu-id="0f360-104">[新しいサーバー] インストール オプションを使用して PowerPivot for SharePoint をインストールした場合は、この作業は必要ありません。このオプションでは、SQL Server セットアップで配置を構成するときに、PowerPivot 機能の統合がルート サイト コレクションに対してアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="0f360-104">If you installed PowerPivot for SharePoint using the New Server option, you can skip this task because SQL Server Setup already activated PowerPivot feature integration for the root site collection when it configured your deployment.</span></span>  
  
 <span data-ttu-id="0f360-105">サイトでアプリケーション ページやテンプレートを使用できるようにするには、サイト コレクション レベルで機能をアクティブ化する必要があります。これには、定期データを更新するための構成ページや、PowerPivot ギャラリーとデータ フィード ライブラリのアプリケーション ページなどが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0f360-105">Feature activation at the site collection level is necessary to make application pages and templates available to your sites, including configuration pages for scheduled data refresh and application pages for PowerPivot Gallery and Data Feed libraries.</span></span>  
  
 <span data-ttu-id="0f360-106">PowerPivot 統合は、PowerPivot クエリ処理をサポートするサイト コレクションごとにアクティブ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f360-106">You must activate PowerPivot integration for each site collection that supports PowerPivot query processing.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0f360-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="0f360-107">Prerequisites</span></span>  
 <span data-ttu-id="0f360-108">サイト コレクション管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f360-108">You must be a site collection administrator.</span></span>  
  
## <a name="activate-powerpivot-features"></a><span data-ttu-id="0f360-109">PowerPivot 機能のアクティブ化</span><span class="sxs-lookup"><span data-stu-id="0f360-109">Activate PowerPivot Features</span></span>  
  
1.  <span data-ttu-id="0f360-110">SharePoint サイトで、 **[サイトの操作]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0f360-110">On a SharePoint site, click **Site Actions**.</span></span>  
  
     <span data-ttu-id="0f360-111">既定では、SharePoint Web アプリケーションへのアクセスにはポート 80 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="0f360-111">By default, SharePoint web applications are accessed through port 80.</span></span> <span data-ttu-id="0f360-112">したがって、多くの場合、「http://\<computer name>」と入力してルート サイト コレクションを開くことで SharePoint サイトにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="0f360-112">This means that you can often access a SharePoint site by entering http://\<computer name> to open the root site collection.</span></span>  
  
2.  <span data-ttu-id="0f360-113">**[サイトの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0f360-113">Click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="0f360-114">[サイト コレクションの管理] で **[サイト コレクションの機能]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0f360-114">In Site Collection Administration, click **Site collection features**.</span></span>  
  
4.  <span data-ttu-id="0f360-115">[ **PowerPivot 統合サイトコレクション機能**] が表示されるまでページを下にスクロールします。</span><span class="sxs-lookup"><span data-stu-id="0f360-115">Scroll down the page until you find **PowerPivot Integration Site Collection Feature**.</span></span>  
  
5.  <span data-ttu-id="0f360-116">**[アクティブ化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0f360-116">Click **Activate**.</span></span>  
  
6.  <span data-ttu-id="0f360-117">他のサイト コレクションについても、各サイトを開き、 **[サイトの操作]** をクリックして手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="0f360-117">Repeat for additional site collections by opening each site and clicking **Site Actions**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f360-118">参照</span><span class="sxs-lookup"><span data-stu-id="0f360-118">See Also</span></span>  
 <span data-ttu-id="0f360-119">[サーバーの全体管理での PowerPivot サーバーの管理と構成](power-pivot-server-administration-and-configuration-in-central-administration.md) </span><span class="sxs-lookup"><span data-stu-id="0f360-119">[PowerPivot Server Administration and Configuration in Central Administration](power-pivot-server-administration-and-configuration-in-central-administration.md) </span></span>  
 <span data-ttu-id="0f360-120">[初期構成 &#40;PowerPivot for SharePoint&#41;](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="0f360-120">[Initial Configuration &#40;PowerPivot for SharePoint&#41;](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md) </span></span>  
 [<span data-ttu-id="0f360-121">PowerPivot for SharePoint 2010 のインストール</span><span class="sxs-lookup"><span data-stu-id="0f360-121">PowerPivot for SharePoint 2010 Installation</span></span>](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
